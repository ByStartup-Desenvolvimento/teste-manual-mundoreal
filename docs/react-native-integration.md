# Integração React Native — Frete & Checkout Mercado Pago

## Visão Geral

O app React Native se comunica diretamente com as **Edge Functions** do Supabase. Não há backend adicional — tudo passa pelas functions já existentes.

```
App React Native
    │
    ├── supabase.functions.invoke('calculate-shipping')  → calcula opções de frete
    └── supabase.functions.invoke('create-checkout')     → cria pedido + link MP
```

---

## Pré-requisitos

```bash
npm install @supabase/supabase-js
```

```ts
// lib/supabase.ts
import { createClient } from '@supabase/supabase-js';

export const supabase = createClient(
  'https://itdmnlthxambdvsnntza.supabase.co',
  'SUA_ANON_KEY_AQUI'
);
```

> A `anon key` é pública e pode ficar no código. Nunca exponha a `service_role key`.

---

## 1. Cálculo de Frete

### Endpoint
```
POST /functions/v1/calculate-shipping
```

### Request

```ts
interface ShippingRequest {
  cep_destino: string;                              // ex: "97590000"
  items: Array<{
    product_id: string;                             // UUID do produto
    quantidade: number;
  }>;
}
```

### Response

```ts
interface ShippingResponse {
  options: Array<{
    service: string;   // "Entrega Local" | "SEDEX" | "PAC" | "Retirada na Loja" | "Frete Grátis"
    price: number;     // valor em R$ (0 = grátis)
    days: number;      // prazo estimado em dias (0 = retirada na loja)
  }>;
  free_shipping: boolean;
  free_shipping_above: number;   // valor mínimo para frete grátis
  subtotal: number;              // subtotal calculado dos itens
}
```

### Exemplo de uso

```ts
import { supabase } from './lib/supabase';

async function calcularFrete(cep: string, items: CartItem[]) {
  const { data, error } = await supabase.functions.invoke('calculate-shipping', {
    body: {
      cep_destino: cep.replace(/\D/g, ''), // remover máscara
      items: items.map(item => ({
        product_id: item.id,
        quantidade: item.quantidade,
      })),
    },
  });

  if (error) throw error;
  return data as ShippingResponse;
}
```

### Lógica de prioridade das opções retornadas

| Prioridade | Condição | Serviço retornado |
|---|---|---|
| 1 | CEP do cliente está em faixa de entrega local cadastrada | `Entrega Local` |
| 2 | Token Melhor Envio configurado | Opções reais: SEDEX, PAC, Jadlog, etc. |
| 3 | Subtotal ≥ limiar de frete grátis | `Frete Grátis` |
| 4 | Fallback (sem token ME) | `SEDEX` e `PAC` (estimativa matemática) |
| Sempre | — | `Retirada na Loja` (grátis, 0 dias) |

### Exemplo de resposta

```json
{
  "options": [
    { "service": "Entrega Local", "price": 8.00, "days": 1 },
    { "service": "Retirada na Loja", "price": 0, "days": 0 }
  ],
  "free_shipping": false,
  "free_shipping_above": 50,
  "subtotal": 35.90
}
```

### Exibição no app

```tsx
// components/ShippingOptions.tsx
function ShippingOptions({ options, onSelect, selected }) {
  return (
    <View>
      {options.map(option => (
        <TouchableOpacity
          key={option.service}
          onPress={() => onSelect(option)}
          style={selected?.service === option.service ? styles.selected : styles.option}
        >
          <Text style={styles.serviceName}>{option.service}</Text>
          <View style={styles.row}>
            <Text style={styles.price}>
              {option.price === 0 ? 'Grátis' : `R$ ${option.price.toFixed(2)}`}
            </Text>
            <Text style={styles.days}>
              {option.days === 0 ? 'Hoje' : `${option.days} dia(s)`}
            </Text>
          </View>
        </TouchableOpacity>
      ))}
    </View>
  );
}
```

---

## 2. Checkout com Mercado Pago

### Fluxo completo

```
1. Usuário confirma pedido → app chama create-checkout
2. Edge Function cria o pedido em orders/order_items
3. Cria preference no Mercado Pago
4. Retorna { order_id, init_point }
5. App abre init_point via Linking.openURL()
6. Usuário paga no browser/app do MP
7. Webhook do MP atualiza status do pedido automaticamente
8. App pode monitorar status via Realtime ou polling
```

### Endpoint
```
POST /functions/v1/create-checkout
```
> Requer autenticação — o usuário deve estar logado.

### Request

```ts
interface CheckoutRequest {
  items: Array<{
    product_id: string;
    quantidade: number;
  }>;
  endereco_id?: string;          // UUID do endereço (obrigatório quando tipo_entrega = "entrega")
  tipo_entrega: "entrega" | "retirada";
  usar_realitos?: number;        // quantidade de Realitos para desconto (opcional)

  // Opção A: enviar o objeto completo do frete selecionado (recomendado)
  frete_selecionado?: {
    service: string;   // ex: "Entrega Local" | "SEDEX" | "Retirada na Loja"
    price: number;     // valor em R$
    days?: number;
  };

  // Opção B: enviar apenas valor e nome separados
  valor_frete?: number;     // valor em R$ (usado se frete_selecionado não for enviado)
  servico_frete?: string;   // nome do serviço
}
```

### Response

```ts
interface CheckoutResponse {
  order_id: string;       // UUID do pedido criado
  init_point: string;     // URL para pagamento no Mercado Pago
  preference_id: string;  // ID da preference (para tracking)
  subtotal: number;
  valor_frete: number;
  desconto_realitos: number;
  total: number;
  realitos_ganhos: number;  // Realitos que serão creditados após entrega
}
```

### Exemplo de uso

```ts
import { Linking } from 'react-native';
import { supabase } from './lib/supabase';

async function finalizarPedido(checkoutData: CheckoutRequest) {
  // Usuário deve estar autenticado
  const { data: session } = await supabase.auth.getSession();
  if (!session.session) throw new Error('Usuário não autenticado');

  const { data, error } = await supabase.functions.invoke('create-checkout', {
    body: checkoutData,
  });

  if (error) throw error;

  const { order_id, init_point } = data as CheckoutResponse;

  // Abre o checkout do Mercado Pago
  const canOpen = await Linking.canOpenURL(init_point);
  if (canOpen) {
    await Linking.openURL(init_point);
  }

  return { order_id, init_point };
}
```

### Fluxo de checkout completo

```ts
// screens/CheckoutScreen.tsx
async function handleConfirmarPedido() {
  setLoading(true);
  try {
    // 1. Criar pedido e obter link MP
    const { order_id, checkout_url } = await finalizarPedido({
      items: cart.items.map(i => ({
        product_id: i.id,
        quantidade: i.quantidade,
      })),
      endereco_id: enderecoSelecionado?.id,
      tipo_entrega: freteSelecionado.service === 'Retirada na Loja' ? 'retirada' : 'entrega',
      frete_selecionado: {
        service: freteSelecionado.service,
        price: freteSelecionado.price,
        days: freteSelecionado.days,
      },
      usar_realitos: realitosParaUsar,
    });

    // 2. Navegar para tela de aguardando pagamento
    navigation.replace('AguardandoPagamento', { order_id });

    // 3. Abrir Mercado Pago
    if (checkout_url) {
      await Linking.openURL(checkout_url);
    }

  } catch (err) {
    Alert.alert('Erro', 'Não foi possível iniciar o pagamento.');
  } finally {
    setLoading(false);
  }
}
```

---

## 3. Monitorar status do pedido

Após abrir o link do MP, monitore o status do pedido para saber quando o pagamento foi aprovado.

### Opção A — Realtime (recomendado)

```ts
import { useEffect, useState } from 'react';
import { supabase } from './lib/supabase';

function useOrderStatus(orderId: string) {
  const [status, setStatus] = useState<string>('pending');

  useEffect(() => {
    // Busca status inicial
    supabase
      .from('orders')
      .select('status')
      .eq('id', orderId)
      .single()
      .then(({ data }) => data && setStatus(data.status));

    // Assina mudanças em tempo real
    const channel = supabase
      .channel(`order-${orderId}`)
      .on(
        'postgres_changes',
        {
          event: 'UPDATE',
          schema: 'public',
          table: 'orders',
          filter: `id=eq.${orderId}`,
        },
        (payload) => setStatus(payload.new.status)
      )
      .subscribe();

    return () => { supabase.removeChannel(channel); };
  }, [orderId]);

  return status;
}
```

### Opção B — Polling simples

```ts
function useOrderStatusPolling(orderId: string, intervalMs = 5000) {
  const [status, setStatus] = useState('pending');

  useEffect(() => {
    const poll = async () => {
      const { data } = await supabase
        .from('orders')
        .select('status')
        .eq('id', orderId)
        .single();
      if (data) setStatus(data.status);
    };

    poll();
    const interval = setInterval(poll, intervalMs);
    return () => clearInterval(interval);
  }, [orderId]);

  return status;
}
```

### Mapeamento de status

| Status | Significado | Ação no app |
|---|---|---|
| `pending` | Aguardando pagamento | Mostrar loading/aguardando |
| `paid` | Pagamento aprovado | Navegar para "Pedido confirmado" |
| `processing` | Em processamento | Informar cliente |
| `shipped` | Enviado | Mostrar código de rastreio |
| `delivered` | Entregue | Creditar Realitos + permitir avaliação |
| `cancelled` | Cancelado | Informar e liberar carrinho |

---

## 4. Realitos (pontos de fidelidade)

### Verificar saldo

```ts
async function getSaldoRealitos(customerId: string) {
  const { data } = await supabase
    .from('realitos_balances')
    .select('saldo')
    .eq('customer_id', customerId)
    .single();

  return data?.saldo ?? 0;
}
```

### Calcular desconto

```ts
// Busque a config do sistema
const { data: setting } = await supabase
  .from('system_settings')
  .select('value')
  .eq('key', 'realitos_config')
  .single();

const config = setting?.value as {
  valorRealito: number;       // valor em R$ de cada Realito
  pedidoMinimoUso: number;    // valor mínimo do pedido para usar Realitos
};

// Calcular desconto
const descontoEmReais = realitosParaUsar * config.valorRealito;
```

> **Importante:** Os Realitos ganhos numa compra são creditados automaticamente **apenas quando o pedido é marcado como `delivered`**, para evitar fraudes.

---

## 5. Checklist de implementação

- [ ] Instalar `@supabase/supabase-js` e configurar client
- [ ] Implementar autenticação (login/cadastro) com `supabase.auth`
- [ ] Tela de endereços: listar e criar via tabela `customer_addresses`
- [ ] Tela de carrinho com cálculo de frete ao digitar CEP
- [ ] Tela de checkout com seleção de frete + uso de Realitos
- [ ] Abrir `init_point` com `Linking.openURL()`
- [ ] Tela de aguardando pagamento com Realtime ou polling
- [ ] Tela de pedidos do cliente (tabela `orders` + RLS já configurada)
- [ ] Deep link (opcional) para retorno após pagamento no MP

---

## Referências

- [Supabase JS Docs](https://supabase.com/docs/reference/javascript)
- [Mercado Pago Checkout Pro](https://www.mercadopago.com.br/developers/pt/docs/checkout-pro/landing)
- [Melhor Envio API](https://docs.melhorenvio.com.br/)
