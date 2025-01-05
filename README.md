# Modelagem-Ecommerce-DIO
Refinamento de Modelagem Ecommerce DIO

## Descrição Geral do Esquema

### 1. *Cliente*
- O sistema suporta o cadastro de clientes tanto Pessoa Física (PF) quanto Pessoa Jurídica (PJ). No entanto, um cliente só pode ser de um tipo.
- A entidade *Cliente* inclui os seguintes atributos principais:
  - idCliente: Identificador único do cliente.
  - Nome: Nome completo do cliente.
  - Endereço: Informações de contato e localização.
  - tipoCliente: Tipo do cliente (valores possíveis: PJ ou PF).
  - CNPJ: Cadastro Nacional de Pessoa Jurídica (somente para PJ).
  - CPF: Cadastro de Pessoa Física (somente para PF).

### 2. *Forma de Pagamento*
- Para maior flexibilidade, os clientes podem cadastrar múltiplas formas de pagamento.
- A nova entidade *FormaPagamento* foi adicionada com os seguintes atributos:
  - idFormaPagamento: Identificador único da forma de pagamento.
  - tipoPagamento: Tipo de pagamento (Cartão de Crédito, Pix, Boleto, etc.).
  - dadosPagamento: Informações específicas, como número do cartão ou chave Pix.
  - Relacionamento 1:N com *Cliente*.

### 3. *Pedido*
- Um pedido é associado a um cliente e contém informações relacionadas ao status do pedido, descrição e frete.
- A entidade *Pedido* mantém os seguintes atributos:
  - idPedido: Identificador único do pedido.
  - Status do Pedido: Situação atual do pedido (exemplo: Aberto, Processando, Enviado, Finalizado).
  - Descrição: Resumo ou informações adicionais sobre o pedido.
  - Cliente_idCliente: Chave estrangeira associando o pedido a um cliente.
  - Frete: Custo do envio do pedido.

### 4. *Entrega*
- Uma nova entidade *Entrega* foi criada para gerenciar informações relacionadas ao envio de pedidos.
- A entidade *Entrega* possui os seguintes atributos:
  - idEntrega: Identificador único da entrega.
  - statusEntrega: Situação atual da entrega (exemplo: Aguardando envio, Em transporte, Entregue).
  - codigoRastreio: Código de rastreamento fornecido pelo transportador.
  - Pedido_idPedido: Chave estrangeira associando a entrega a um pedido específico.
- Relacionamento 1:1 com *Pedido*.

### 5. *Produto e Estoque*
- A entidade *Produto* armazena informações gerais sobre os itens disponíveis para venda, enquanto a entidade *Estoque* gerencia a quantidade e a localização dos produtos disponíveis.
- A tabela de relação *Produto em Estoque* registra a associação entre produtos e seus estoques, permitindo múltiplos locais para um mesmo produto.

### 6. *Produtos por Vendedor (Terceiros)*
- Para permitir que terceiros disponibilizem produtos na plataforma, a tabela de relação *Produtos por Vendedor (Terceiro)* foi definida, associando produtos a vendedores com informações de quantidade e local.

## Alterações Recentes
- *Cliente:* Adicionados os campos tipoCliente, CNPJ e CPF para diferenciar entre PF e PJ.
- *FormaPagamento:* Nova entidade criada para gerenciar múltiplas formas de pagamento por cliente.
- *Entrega:* Nova entidade criada para incluir status de entrega e código de rastreio, melhorando o controle sobre o envio de pedidos.


