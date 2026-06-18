# 📘 Manual do Usuário — Painel Administrativo Lojas Mundo Real

**Versão:** 1.0  
**Data:** Junho de 2026  
**Plataforma:** [https://admin.lojasmundoreal.com.br](https://admin.lojasmundoreal.com.br)

---

## Bem-vindo!

Este manual foi criado para te ajudar a usar o painel de administração da sua loja virtual de forma simples e segura. Aqui você vai aprender a gerenciar produtos, acompanhar pedidos, criar promoções e muito mais — tudo em um só lugar.

Sempre que tiver dúvidas, consulte este guia. Ele foi escrito de forma simples, sem complicações.

---

## Sumário

1. [Como Entrar no Sistema](#1-como-entrar-no-sistema)
2. [Tela Inicial — Visão Geral da Loja](#2-tela-inicial--visão-geral-da-loja)
3. [Produtos — Gerenciar o Catálogo](#3-produtos--gerenciar-o-catálogo)
4. [Categorias — Organizar os Produtos](#4-categorias--organizar-os-produtos)
5. [Pedidos — Acompanhar as Vendas](#5-pedidos--acompanhar-as-vendas)
6. [Clientes — Ver Quem Compra na Loja](#6-clientes--ver-quem-compra-na-loja)
7. [Banners — Imagens da Página Inicial](#7-banners--imagens-da-página-inicial)
8. [Cupons de Desconto](#8-cupons-de-desconto)
9. [Configurações — Entrega e Fidelidade](#9-configurações--entrega-e-fidelidade)
10. [Dicas Importantes](#10-dicas-importantes)

---

## 1. Como Entrar no Sistema

### Passo a Passo

1. Abra o navegador (Chrome, Edge ou Firefox) no seu computador
2. Digite o endereço: **https://admin.lojasmundoreal.com.br/login**
3. Preencha os campos:
   - **E-mail:** `admin@email.com`
   - **Senha:** `senha123`
4. Clique no botão **Entrar**

> ⚠️ **Atenção:** Não compartilhe seu e-mail e senha com ninguém. Esses dados dão acesso completo à sua loja.

### E se eu esquecer a senha?

Contate a equipe de desenvolvimento da bystartup para alteração de senha ou criação de um novo usuário.

---

## 2. Tela Inicial — Visão Geral da Loja

Assim que você entrar no sistema, a primeira tela que aparece é o **Painel Principal** (chamado de "Dashboard"). Ele mostra um resumo de tudo que está acontecendo na sua loja.

### O que você vê nessa tela:

#### Quatro cartões com números importantes:

| Cartão | O que significa |
|---|---|
| **Total de Vendas** | Quanto sua loja faturou neste mês, comparado ao mês anterior |
| **Novos Clientes** | Quantas pessoas se cadastraram na loja este mês |
| **Pedidos Pendentes** | Pedidos que ainda precisam de atenção ou processamento |
| **Baixo Estoque** | Quantos produtos estão acabando e precisam ser repostos |

#### Gráfico de Vendas Mensais

Logo abaixo dos cartões, há um gráfico que mostra o valor das suas vendas nos **últimos 6 meses**. Ele ajuda a ver se as vendas estão crescendo ou caindo ao longo do tempo.

#### Últimos Pedidos e Produtos Recentes

No final da tela, dois painéis mostram:
- **Últimos Pedidos:** os pedidos mais recentes com o nome do cliente, valor e situação atual
- **Produtos Recentes:** os últimos produtos cadastrados com a quantidade em estoque

> 💡 **Dica:** Fique de olho nos cartões de "Pedidos Pendentes" e "Baixo Estoque" — eles precisam de ação rápida!

---

## 3. Produtos — Gerenciar o Catálogo

No menu lateral, clique em **"Produtos"** para ver todos os itens disponíveis na sua loja.

### Ver a lista de produtos

Você verá uma tabela com todos os seus produtos. É possível **pesquisar** um produto pelo nome usando a barra de busca no topo.

### Cadastrar um novo produto

1. Clique no botão **"Novo Produto"** (canto superior direito)
2. Preencha as informações do produto:

#### Informações Básicas

| Campo | O que preencher |
|---|---|
| **Nome do Produto** *(obrigatório)* | O nome completo do produto, ex: "Tênis Esportivo Azul" |
| **SKU** | Um código interno para identificar o produto, ex: "TEN-001" |
| **Marca** | A marca do produto, ex: "Nike", "Adidas" |
| **Código de Barras** | O número do código de barras do produto (pode ter mais de um) |
| **Categorias** | Marque as categorias às quais o produto pertence |
| **Descrição Curta** | Uma frase resumida sobre o produto |
| **Descrição Completa** | Detalhes completos sobre o produto |

#### Preços e Estoque

| Campo | O que preencher |
|---|---|
| **Preço de Venda** *(obrigatório)* | O preço normal do produto |
| **Preço Promocional** | Se o produto estiver em promoção, coloque o preço com desconto aqui (deve ser menor que o preço normal) |
| **Quantidade em Estoque** *(obrigatório)* | Quantas unidades você tem disponível |
| **Alerta de Estoque Mínimo** | A partir de qual quantidade o sistema deve te avisar que o estoque está acabando (padrão: 10 unidades) |

#### Dimensões para Frete

Preencha o tamanho e o peso do produto já embalado. Esses dados são usados para calcular o valor do frete.

| Campo | Exemplo |
|---|---|
| **Peso (kg)** | 0.30 |
| **Altura (cm)** | 10 |
| **Largura (cm)** | 15 |
| **Comprimento (cm)** | 20 |

#### Imagens do Produto

- Clique na área de upload ou arraste as fotos do produto
- Você pode adicionar várias imagens
- A primeira imagem adicionada é automaticamente a **imagem principal** (a que aparece em destaque)
- Para trocar a imagem principal, passe o mouse sobre outra imagem e clique em **"Definir"**
- Formatos aceitos: JPG, PNG ou WEBP (tamanho máximo: 5MB por imagem)

#### Status do Produto

| Opção | O que faz |
|---|---|
| **Produto Ativo** | Liga/desliga a exibição do produto na loja. Se desativado, o cliente não consegue ver nem comprar |
| **Produto em Destaque** | Marca o produto para aparecer em posição especial na loja |

3. Quando terminar, clique em **"Salvar Produto"**

### Editar um produto existente

1. Na lista de produtos, clique no ícone de **lápis (editar)** na linha do produto
2. Faça as alterações necessárias
3. Clique em **"Salvar Alterações"**

### Remover um produto

1. Na lista de produtos, clique no ícone de **lixeira** na linha do produto
2. Confirme a exclusão

> ⚠️ **Cuidado:** Excluir um produto é uma ação permanente. Se quiser apenas deixar de mostrar o produto na loja temporariamente, prefira **desativar** o produto (desligue o "Produto Ativo") em vez de excluir.

---

## 4. Categorias — Organizar os Produtos

As categorias ajudam os clientes a encontrar os produtos mais facilmente na loja. Por exemplo: "Calçados", "Roupas", "Acessórios".

### Como acessar

No menu lateral, clique em **"Categorias"**.

### Criar uma nova categoria

1. Clique no botão **"Nova Categoria"**
2. Digite o nome da categoria
3. Salve

### Editar ou excluir uma categoria

Na lista de categorias, use os ícones de **lápis** (editar) ou **lixeira** (excluir) ao lado de cada uma.

> 💡 **Dica:** Crie as categorias antes de cadastrar os produtos. Assim você já pode associar os produtos às categorias corretas durante o cadastro.

---

## 5. Pedidos — Acompanhar as Vendas

No menu lateral, clique em **"Pedidos"** para ver todas as compras feitas na sua loja.

### Entendendo a lista de pedidos

Cada linha da tabela mostra:
- **Nº do Pedido:** número único de identificação
- **Cliente:** nome de quem comprou
- **Data:** quando o pedido foi feito
- **Valor Total:** quanto o cliente pagou
- **Status:** em que etapa o pedido está

### Situações possíveis de um pedido:

| Status | O que significa |
|---|---|
| **Pendente** | O pedido chegou, mas ainda não foi processado |
| **Processando** | Estamos verificando o pagamento |
| **Pago** | O pagamento foi confirmado — hora de separar o produto! |
| **Enviado** | O produto saiu para entrega |
| **Entregue** | O cliente recebeu o produto |
| **Cancelado** | O pedido foi cancelado |

### Filtrar pedidos

Use os campos no topo da tela para encontrar um pedido específico:
- **Busca:** pesquise pelo número do pedido ou nome do cliente
- **Filtro de Status:** selecione para ver somente os pedidos em uma etapa específica (ex: ver apenas os "Pendentes")

### Ver os detalhes de um pedido

1. Clique no ícone de **olho** na linha do pedido
2. Uma janela abrirá com todas as informações:
   - Nome e e-mail do cliente
   - Endereço de entrega (ou "Retirada na Loja")
   - Lista dos produtos comprados com quantidade e valores
   - Subtotal, desconto, frete e valor total
   - Informações de pagamento

### Atualizar o status de um pedido

1. Abra os detalhes do pedido (clique no ícone de olho)
2. Localize o campo **"Status do Pedido"**
3. Selecione o novo status na lista
4. Clique em **"Atualizar Pedido"**

### Adicionar código de rastreamento

Quando você postar o produto nos Correios ou transportadora, adicione o código de rastreamento para que o cliente possa acompanhar:

1. Abra os detalhes do pedido
2. Localize o campo **"Código de Rastreamento"**
3. Digite o código
4. Clique em **"Atualizar Pedido"**

### Liberar Realitos (Pontos de Fidelidade)

Após um pedido ser marcado como **"Entregue"**, você pode liberar os pontos que o cliente ganhou pela compra:

1. Abra os detalhes do pedido
2. Role até a seção **"Informações Realitos"**
3. Você verá quantos Realitos o cliente vai ganhar
4. Clique no botão **"Liberar Realitos"**

> 💡 **Importante:** Os Realitos só ficam disponíveis ao cliente após você clicar em "Liberar Realitos". Essa etapa é manual e deve ser feita sempre que um pedido for entregue com sucesso.

---

## 6. Clientes — Gerenciar Clientes e Saldo de Realitos

No menu lateral, clique em **"Clientes"** para visualizar e gerenciar as pessoas cadastradas na sua loja virtual.

### O que você vê na lista de clientes:

A tabela principal apresenta informações rápidas sobre os clientes cadastrados:
- **Nome e E-mail:** Dados de identificação do cliente.
- **Data de Cadastro:** Quando o cliente se registrou na loja.
- **Realitos:** Saldo atual de pontos de fidelidade acumulados.
- **Status:** Indica se a conta do cliente está ativa ou inativa.
- **Ações:** O ícone de **olho (visualizar)** abre o modal com o perfil detalhado do cliente.

> ℹ️ **Nota:** O cadastro de clientes é realizado automaticamente quando as pessoas se registram na loja virtual. A equipe administrativa visualiza e gerencia as contas a partir desta lista.

### Detalhes do Cliente e Ações Administrativas

Ao clicar no ícone de **olho** na linha de um cliente, uma janela se abrirá com informações completas e opções de ajuste. Nessa janela, você pode:

#### 1. Ativar ou Desativar a Conta do Cliente
No final da janela, no campo **"Status da Conta"**, você verá um interruptor (Switch).
- Para desativar a conta do cliente (impedindo o login e novas compras), desative o interruptor.
- Para reativar, clique novamente para ativar o interruptor.

#### 2. Consultar Endereços e Histórico de Transações de Realitos
- **Endereços Salvos:** Mostra todos os endereços cadastrados pelo cliente, destacando o endereço de entrega principal.
- **Histórico de Transações - Realitos:** Exibe um extrato detalhado de todas as entradas (créditos) e saídas (débitos) de pontos do cliente, com a respectiva data e descrição/motivo.

#### 3. Ajustar o Saldo de Realitos Manualmente (Adicionar ou Remover Pontos)
Caso precise dar uma bonificação para um cliente ou corrigir o saldo de pontos por fora do fluxo de pedidos padrão:

1. Na janela de detalhes do cliente, localize o painel em destaque com o **Saldo Realitos**.
2. Clique no botão **"Ajustar Saldo"**.
3. No formulário que abrir, selecione e preencha:
   - **Tipo de Operação:** Selecione **"Crédito (Adicionar)"** para creditar pontos, ou **"Débito (Remover)"** para retirar pontos da conta.
   - **Valor:** Insira a quantidade de pontos a ser adicionada ou removida.
   - **Motivo:** Escreva uma justificativa clara da alteração (ex: *"Bonificação de atendimento"* ou *"Ajuste manual de pontos"*). Este motivo ficará registrado de forma permanente no histórico do cliente.
4. Clique em **"Confirmar Ajuste"**. O saldo será atualizado instantaneamente na tela e uma nova linha de transação aparecerá no histórico.

---

## 7. Banners — Imagens da Página Inicial

Os banners são as imagens grandes que aparecem no topo da loja virtual. Eles costumam divulgar promoções, lançamentos ou campanhas sazonais.

No menu lateral, clique em **"Banners"**.

### Criar um novo banner

1. Clique no botão **"Novo Banner"**
2. Preencha as informações:

| Campo | O que preencher |
|---|---|
| **Título do Banner** *(obrigatório)* | Um nome para identificar o banner, ex: "Promoção de Inverno" |
| **Link de Destino** | Para onde o cliente vai ao clicar no banner (opcional), ex: `/categoria/inverno` |
| **Ordem de Exibição** | Em qual posição o banner aparece (0 = primeiro, 1 = segundo, etc.) |
| **Status** | Ativo = aparece na loja / Inativo = não aparece |
| **Imagem** | Faça upload da imagem. Tamanho recomendado: 1920×600 pixels |

3. Clique em **"Criar Banner"**

### Ativar ou desativar um banner sem excluir

Na lista de banners, cada item tem um **botão de liga/desliga**. Use-o para mostrar ou esconder um banner rapidamente, sem precisar excluí-lo.

> 💡 **Dica:** Ideal para guardar banners de datas comemorativas (ex: Natal, Black Friday) e reativar no próximo ano.

### Editar um banner

1. Clique no ícone de **lápis** ao lado do banner
2. Faça as alterações
3. Clique em **"Salvar"**

### Excluir um banner

1. Clique no ícone de **lixeira** ao lado do banner
2. Confirme a exclusão

> ⚠️ **Cuidado:** A exclusão de banners não pode ser desfeita. Se quiser apenas pausar, use a opção de desativar.

---

## 8. Cupons de Desconto

Os cupons permitem oferecer descontos especiais para seus clientes. No menu lateral, clique em **"Cupons de Desconto"**.

### Criar um novo cupom

1. Na seção "Criar Novo Cupom", preencha:

| Campo | O que preencher |
|---|---|
| **Código do Cupom** | A palavra que o cliente vai digitar, ex: `VERAO2024` |
| **Tipo de Desconto** | **Percentual (%)** = desconto em porcentagem / **Valor Fixo (R$)** = desconto em reais |
| **Valor do Desconto** | Se percentual: coloque 20 para 20%. Se fixo: coloque 50 para R$ 50,00 |
| **Data de Expiração** | Até quando o cupom pode ser usado |
| **Limite de Uso** | Quantas vezes no total o cupom pode ser usado por todos os clientes |

2. Clique em **"Criar Cupom"**

### Entender a lista de cupons

A tabela mostra todos os cupons com:
- **Código:** a palavra do cupom
- **Tipo:** percentual ou valor fixo
- **Valor:** o desconto que ele dá
- **Expiração:** quando vence
- **Uso:** quantas vezes foi usado / limite total (ex: "45 / 100")
- **Status:** Ativo ou Inativo

---

## 9. Configurações — Entrega e Fidelidade

No menu lateral, clique em **"Configurações"** para ajustar as regras de entrega e o programa de fidelidade Realitos.

### Retirada na Loja

Esta opção já vem ativada automaticamente. Todo cliente terá a opção de retirar o pedido pessoalmente na loja, sem custo de frete. Nenhuma configuração é necessária.

---

### Zonas de Entrega Local

Use esta seção para configurar as áreas onde **você mesmo faz a entrega** com um valor fixo — sem precisar de transportadora.

**Quando usar:** quando sua loja faz entregas próprias em bairros ou cidades próximas.

#### Como adicionar uma zona:

1. Preencha os campos:
   - **Nome da Zona:** ex. "Centro de Rosário do Sul"
   - **CEP Início e CEP Fim:** a faixa de CEPs que pertencem a essa zona (ex: 97590000 até 97599999)
   - **Valor da Entrega (R$):** quanto vai custar a entrega nessa área
   - **Prazo Mínimo e Máximo (dias):** em quantos dias a entrega é feita
2. Clique em **"Adicionar Zona Local"**

> 💡 **Como funciona:** Quando um cliente informar um CEP que esteja dentro de uma zona configurada aqui, ele verá automaticamente a opção "Entrega Local" com o valor fixo que você definiu.

#### Como remover uma zona:

Na tabela de zonas, clique no ícone de **lixeira** ao lado da zona que deseja remover.

---

### Regiões para Transportadora

Use esta seção para definir regras de **frete grátis** para regiões atendidas por transportadora (como Correios ou outras).

#### Como adicionar uma região:

1. Preencha os campos:
   - **Nome da Região:** ex. "Restante do Brasil"
   - **Prazo Mínimo e Máximo (dias):** estimativa de prazo de entrega
   - **Frete Grátis Acima (R$):** valor mínimo do pedido para o cliente ganhar frete grátis nessa região
2. Clique em **"Adicionar Região"**

> 💡 **Exemplo:** Se você colocar "Frete Grátis Acima de R$ 200,00", todo cliente dessa região que gastar mais de R$ 200 em um pedido terá o frete grátis automaticamente.

---

### Sistema Realitos (Programa de Fidelidade)

O **Realitos** é o programa de pontos da sua loja. A cada compra, o cliente acumula pontos que podem ser trocados por desconto em compras futuras.

#### Como funciona:

1. O cliente compra na loja e ganha uma quantidade de Realitos
2. Quando o pedido é marcado como entregue e você libera os Realitos, eles entram na conta do cliente
3. O cliente pode usar os Realitos como desconto na próxima compra (desde que o pedido seja acima do valor mínimo configurado)

#### Regras que você pode configurar:

**Regras de Ganho:**

| Campo | O que significa |
|---|---|
| **Valor Base de Compra (R$)** | A cada esse valor gasto, o cliente ganha pontos. Ex: a cada R$ 100,00 em compras |
| **Realitos Ganhos** | Quantos pontos o cliente ganha por cada "valor base". Ex: 10 pontos |

**Regras de Uso:**

| Campo | O que significa |
|---|---|
| **Valor do Realito (R$)** | Quanto cada ponto vale em dinheiro. Ex: R$ 0,50 por ponto |
| **Pedido Mínimo para Uso (R$)** | Valor mínimo do pedido para o cliente poder usar os Realitos. Ex: R$ 300,00 |

#### Exemplo prático com os valores padrão:

> A cada **R$ 100,00** em compras, o cliente ganha **10 Realitos**.  
> Cada Realito vale **R$ 0,50**, então 10 Realitos = **R$ 5,00 de desconto**.  
> O cliente só pode usar os Realitos em pedidos acima de **R$ 300,00**.

#### Como salvar as alterações:

Após ajustar os valores, clique em **"Salvar Regras do Realitos"**.

> ⚠️ **Atenção:** As regras novas valem para pedidos futuros. Pedidos já feitos não são afetados.

---

## 10. Dicas Importantes

### ✅ Boas Práticas do Dia a Dia

- **Confira os pedidos todos os dias:** clientes esperam respostas rápidas. Pedidos "Pendentes" e "Pagos" precisam de ação.
- **Mantenha o estoque atualizado:** sempre que vender produtos fora da plataforma (loja física, por exemplo), atualize a quantidade em estoque no sistema.
- **Libere os Realitos após a entrega:** não esqueça de liberar os pontos de fidelidade quando um pedido for entregue.
- **Use boas fotos nos produtos:** imagens claras e de qualidade aumentam a confiança do cliente e as chances de venda.

### 🔒 Segurança

- Não compartilhe sua senha com terceiros.
- Sempre saia do sistema ao terminar de usar, especialmente em computadores compartilhados. Para sair, clique no seu perfil no canto superior direito e selecione **"Sair"**.

### 🌐 Acesso

- O painel funciona melhor nos navegadores **Google Chrome**, **Microsoft Edge** ou **Mozilla Firefox** atualizados.
- Caso alguma página não carregue corretamente, tente atualizar o navegador (pressione F5).

---

## Resumo dos Endereços Importantes

| Finalidade | Endereço |
|---|---|
| **Acessar o painel** | https://admin.lojasmundoreal.com.br/login |
| **Recuperar senha** | Contar equipe de desenvolvimento |

---

*Manual preparado pela equipe ByStartup — Junho de 2026*
