# Dicionário de Dados — Sistema de E-commerce para Loja Virtual

# 1. Estrutura dos Atributos

## Tabela: cliente

**Descrição:** Armazena as informações cadastrais dos clientes da loja virtual.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_cliente | INTEGER | — | Sim | Não | Não | Identificador único do cliente |
| nome_completo | VARCHAR | 150 | Não | Não | Não | Nome completo do cliente |
| email | VARCHAR | 120 | Não | Não | Não | E-mail do cliente |
| cpf | CHAR | 11 | Não | Não | Não | CPF do cliente |
| status_conta | VARCHAR | 20 | Não | Não | Não | Situação da conta do cliente |
| senha | VARCHAR | 255 | Não | Não | Não | Senha de acesso do cliente |
| data_nascimento | DATE | — | Não | Não | Não | Data de nascimento do cliente |
| foto_perfil | VARCHAR | 255 | Não | Não | Sim | Caminho ou URL da foto de perfil |
| sexo | VARCHAR | 20 | Não | Não | Sim | Sexo informado pelo cliente |
| data_cadastro | DATE | — | Não | Não | Não | Data de cadastro do cliente |
| telefone | VARCHAR | 20 | Não | Não | Sim | Telefone de contato do cliente |

---

## Tabela: preferencia_cliente

**Descrição:** Armazena as preferências de compra associadas aos clientes. Representa o atributo multivalorado `preferencia_compra` do cliente.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_preferencia | INTEGER | — | Sim | Não | Não | Identificador da preferência |
| preferencia_compra | VARCHAR | 100 | Não | Não | Não | Descrição da preferência de compra |
| id_cliente | INTEGER | — | Não | Sim | Não | Cliente associado à preferência |

---

## Tabela: endereco

**Descrição:** Armazena os endereços cadastrados pelos clientes para entrega e cobrança.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_endereco | INTEGER | — | Sim | Não | Não | Identificador do endereço |
| tipo_endereco | VARCHAR | 30 | Não | Não | Não | Tipo do endereço |
| logradouro | VARCHAR | 150 | Não | Não | Não | Rua, avenida ou localidade |
| numero | VARCHAR | 20 | Não | Não | Não | Número do endereço |
| complemento | VARCHAR | 100 | Não | Não | Sim | Complemento do endereço |
| bairro | VARCHAR | 100 | Não | Não | Não | Bairro do endereço |
| cidade | VARCHAR | 100 | Não | Não | Não | Cidade do endereço |
| estado | CHAR | 2 | Não | Não | Não | Sigla do estado |
| cep | CHAR | 8 | Não | Não | Não | Código de Endereçamento Postal |
| pais | VARCHAR | 60 | Não | Não | Não | País do endereço |
| ponto_referencia | VARCHAR | 150 | Não | Não | Sim | Ponto de referência do endereço |
| endereco_principal | BOOLEAN | — | Não | Não | Não | Indica se é o endereço principal |
| id_cliente | INTEGER | — | Não | Sim | Não | Cliente dono do endereço |

---

## Tabela: categoria

**Descrição:** Armazena as categorias de produtos e permite categorias hierárquicas por meio de categoria pai.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_categoria | INTEGER | — | Sim | Não | Não | Identificador da categoria |
| nome_categoria | VARCHAR | 100 | Não | Não | Não | Nome da categoria |
| imagem | VARCHAR | 255 | Não | Não | Sim | Imagem representativa da categoria |
| status | VARCHAR | 20 | Não | Não | Não | Situação da categoria |
| descricao | TEXT | — | Não | Não | Sim | Descrição da categoria |
| id_categoria_pai | INTEGER | — | Não | Sim | Sim | Categoria superior na hierarquia |

---

## Tabela: produto

**Descrição:** Armazena o conceito geral dos produtos vendidos na loja.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_produto | INTEGER | — | Sim | Não | Não | Identificador do produto |
| nome_produto | VARCHAR | 150 | Não | Não | Não | Nome do produto |
| descricao_curta | VARCHAR | 255 | Não | Não | Sim | Descrição resumida do produto |
| descricao_detalhada | TEXT | — | Não | Não | Sim | Descrição completa do produto |
| marca | VARCHAR | 80 | Não | Não | Sim | Marca do produto |
| fabricante | VARCHAR | 100 | Não | Não | Sim | Fabricante do produto |
| peso | DECIMAL | 10,2 | Não | Não | Sim | Peso do produto |
| altura | DECIMAL | 10,2 | Não | Não | Sim | Altura do produto |
| largura | DECIMAL | 10,2 | Não | Não | Sim | Largura do produto |
| comprimento | DECIMAL | 10,2 | Não | Não | Sim | Comprimento do produto |
| garantia | VARCHAR | 100 | Não | Não | Sim | Informações de garantia |
| data_cadastro | DATE | — | Não | Não | Não | Data de cadastro do produto |
| status_produto | VARCHAR | 20 | Não | Não | Não | Situação do produto |
| avaliacao_media | DECIMAL | 3,2 | Não | Não | Sim | Média das avaliações recebidas |
| quantidade_visualizacoes | INTEGER | — | Não | Não | Sim | Quantidade total de visualizações |
| id_categoria | INTEGER | — | Não | Sim | Não | Categoria do produto |

---

## Tabela: item_produto

**Descrição:** Armazena as variações físicas dos produtos, como SKU, cor, tamanho e estoque individual.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_item_produto | INTEGER | — | Sim | Não | Não | Identificador do item de produto |
| sku | VARCHAR | 60 | Não | Não | Não | Código único da variação do produto |
| cor | VARCHAR | 50 | Não | Não | Sim | Cor da variação |
| tamanho | VARCHAR | 30 | Não | Não | Sim | Tamanho da variação |
| modelo | VARCHAR | 80 | Não | Não | Sim | Modelo da variação |
| codigo_barras | VARCHAR | 60 | Não | Não | Sim | Código de barras do item |
| preco | DECIMAL | 15,2 | Não | Não | Não | Preço atual do item |
| preco_promocional | DECIMAL | 15,2 | Não | Não | Sim | Preço promocional do item |
| quantidade_estoque | INTEGER | — | Não | Não | Não | Quantidade atual em estoque |
| estoque_minimo | INTEGER | — | Não | Não | Não | Quantidade mínima em estoque |
| peso | DECIMAL | 10,2 | Não | Não | Sim | Peso específico do item |
| imagem | VARCHAR | 255 | Não | Não | Sim | Imagem da variação |
| status_item | VARCHAR | 20 | Não | Não | Não | Situação do item |
| id_produto | INTEGER | — | Não | Sim | Não | Produto ao qual o item pertence |

---

## Tabela: interacao_produto

**Descrição:** Armazena as interações dos clientes com os produtos da plataforma.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_interacao | INTEGER | — | Sim | Não | Não | Identificador da interação |
| tipo_interacao | VARCHAR | 40 | Não | Não | Não | Tipo da interação realizada |
| data_hora | DATETIME | — | Não | Não | Não | Data e horário da interação |
| dispositivo_utilizado | VARCHAR | 80 | Não | Não | Sim | Dispositivo usado pelo cliente |
| tempo_interacao | INTEGER | — | Não | Não | Sim | Tempo de interação em segundos |
| id_cliente | INTEGER | — | Não | Sim | Não | Cliente que realizou a interação |
| id_produto | INTEGER | — | Não | Sim | Não | Produto relacionado à interação |

---

## Tabela: carrinho

**Descrição:** Armazena os carrinhos de compras dos clientes.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_carrinho | INTEGER | — | Sim | Não | Não | Identificador do carrinho |
| data_criacao | DATE | — | Não | Não | Não | Data de criação do carrinho |
| ultima_atualizacao | DATETIME | — | Não | Não | Sim | Data e hora da última atualização |
| situacao_carrinho | VARCHAR | 30 | Não | Não | Não | Situação do carrinho |
| valor_total | DECIMAL | 15,2 | Não | Não | Sim | Valor total do carrinho |
| quantidade_total_itens | INTEGER | — | Não | Não | Sim | Quantidade total de itens |
| id_cliente | INTEGER | — | Não | Sim | Não | Cliente dono do carrinho |

---

## Tabela: item_carrinho

**Descrição:** Armazena os itens adicionados a cada carrinho de compras.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_item_carrinho | INTEGER | — | Sim | Não | Não | Identificador do item do carrinho |
| quantidade | INTEGER | — | Não | Não | Não | Quantidade do item no carrinho |
| preco_unitario | DECIMAL | 15,2 | Não | Não | Não | Preço unitário no momento da inclusão |
| subtotal | DECIMAL | 15,2 | Não | Não | Sim | Subtotal do item |
| data_inclusao | DATETIME | — | Não | Não | Não | Data e hora de inclusão no carrinho |
| id_carrinho | INTEGER | — | Não | Sim | Não | Carrinho ao qual o item pertence |
| id_item_produto | INTEGER | — | Não | Sim | Não | Item de produto adicionado ao carrinho |

---

## Tabela: pedido

**Descrição:** Armazena os pedidos realizados pelos clientes a partir dos carrinhos de compras.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_pedido | INTEGER | — | Sim | Não | Não | Identificador do pedido |
| data_pedido | DATETIME | — | Não | Não | Não | Data e horário do pedido |
| status_pedido | VARCHAR | 30 | Não | Não | Não | Situação atual do pedido |
| valor_total | DECIMAL | 15,2 | Não | Não | Sim | Valor total dos itens do pedido |
| valor_frete | DECIMAL | 15,2 | Não | Não | Não | Valor do frete |
| desconto_aplicado | DECIMAL | 15,2 | Não | Não | Não | Desconto aplicado ao pedido |
| valor_final | DECIMAL | 15,2 | Não | Não | Sim | Valor final do pedido |
| prazo_estimado | DATE | — | Não | Não | Sim | Prazo estimado de entrega |
| observacoes_cliente | TEXT | — | Não | Não | Sim | Observações informadas pelo cliente |
| motivo_cancelamento | TEXT | — | Não | Não | Sim | Motivo do cancelamento |
| dados_entrega_snapshot | TEXT | — | Não | Não | Sim | Cópia dos dados de entrega no momento do pedido |
| id_cliente | INTEGER | — | Não | Sim | Não | Cliente que realizou o pedido |
| id_carrinho | INTEGER | — | Não | Sim | Não | Carrinho que gerou o pedido |
| id_endereco_entrega | INTEGER | — | Não | Sim | Não | Endereço usado para entrega |
| id_endereco_cobranca | INTEGER | — | Não | Sim | Não | Endereço usado para cobrança |

---

## Tabela: item_pedido

**Descrição:** Armazena os itens comprados em cada pedido.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_item_pedido | INTEGER | — | Sim | Não | Não | Identificador do item do pedido |
| quantidade | INTEGER | — | Não | Não | Não | Quantidade comprada |
| preco_unitario_cobrado | DECIMAL | 15,2 | Não | Não | Não | Preço unitário cobrado no momento da compra |
| subtotal | DECIMAL | 15,2 | Não | Não | Sim | Subtotal do item |
| desconto_aplicado | DECIMAL | 15,2 | Não | Não | Sim | Desconto aplicado no item |
| id_pedido | INTEGER | — | Não | Sim | Não | Pedido ao qual o item pertence |
| id_item_produto | INTEGER | — | Não | Sim | Não | Item de produto comprado |

---

## Tabela: pagamento

**Descrição:** Armazena os pagamentos realizados para os pedidos.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_pagamento | INTEGER | — | Sim | Não | Não | Identificador do pagamento |
| forma_pagamento | VARCHAR | 40 | Não | Não | Não | Forma de pagamento usada |
| valor_pago | DECIMAL | 15,2 | Não | Não | Não | Valor pago |
| data_pagamento | DATETIME | — | Não | Não | Não | Data e hora do pagamento |
| status_pagamento | VARCHAR | 30 | Não | Não | Não | Status do pagamento |
| numero_transacao | VARCHAR | 100 | Não | Não | Sim | Número da transação financeira |
| comprovante | VARCHAR | 255 | Não | Não | Sim | Caminho ou URL do comprovante |
| observacoes_financeiras | TEXT | — | Não | Não | Sim | Observações financeiras do pagamento |
| id_pedido | INTEGER | — | Não | Sim | Não | Pedido associado ao pagamento |

---

## Tabela: pagamento_pix

**Descrição:** Representa o subtipo de pagamento realizado por PIX.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_pagamento | INTEGER | — | Sim | Sim | Não | Identificador do pagamento PIX |

---

## Tabela: pagamento_boleto

**Descrição:** Representa o subtipo de pagamento realizado por boleto bancário.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_pagamento | INTEGER | — | Sim | Sim | Não | Identificador do pagamento por boleto |

---

## Tabela: pagamento_cartao_credito

**Descrição:** Representa o subtipo de pagamento realizado por cartão de crédito.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_pagamento | INTEGER | — | Sim | Sim | Não | Identificador do pagamento por cartão de crédito |
| quantidade_parcelas | INTEGER | — | Não | Não | Não | Quantidade de parcelas do pagamento |
| bandeira_cartao | VARCHAR | 40 | Não | Não | Não | Bandeira do cartão |

---

## Tabela: pagamento_cartao_debito

**Descrição:** Representa o subtipo de pagamento realizado por cartão de débito.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_pagamento | INTEGER | — | Sim | Sim | Não | Identificador do pagamento por cartão de débito |
| bandeira_cartao | VARCHAR | 40 | Não | Não | Não | Bandeira do cartão |

---

## Tabela: pagamento_carteira_digital

**Descrição:** Representa o subtipo de pagamento realizado por carteira digital.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_pagamento | INTEGER | — | Sim | Sim | Não | Identificador do pagamento por carteira digital |
| nome_carteira | VARCHAR | 80 | Não | Não | Não | Nome da carteira digital utilizada |

---

## Tabela: entrega

**Descrição:** Armazena os dados logísticos da entrega de um pedido.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_entrega | INTEGER | — | Sim | Não | Não | Identificador da entrega |
| transportadora | VARCHAR | 100 | Não | Não | Não | Transportadora responsável |
| codigo_rastreamento | VARCHAR | 100 | Não | Não | Sim | Código de rastreamento |
| data_envio | DATE | — | Não | Não | Sim | Data de envio |
| data_prevista | DATE | — | Não | Não | Não | Data prevista de entrega |
| data_entrega | DATE | — | Não | Não | Sim | Data efetiva da entrega |
| status_entrega | VARCHAR | 30 | Não | Não | Não | Status da entrega |
| responsavel_entrega | VARCHAR | 100 | Não | Não | Sim | Responsável pela entrega |
| custo_frete | DECIMAL | 15,2 | Não | Não | Não | Custo do frete |
| id_pedido | INTEGER | — | Não | Sim | Não | Pedido associado à entrega |

---

## Tabela: historico_entrega

**Descrição:** Armazena as movimentações e mudanças de status da entrega.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_historico_entrega | INTEGER | — | Sim | Não | Não | Identificador do histórico de entrega |
| data_hora | DATETIME | — | Não | Não | Não | Data e horário da movimentação |
| status | VARCHAR | 30 | Não | Não | Não | Status registrado no histórico |
| localizacao | VARCHAR | 150 | Não | Não | Sim | Localização da movimentação |
| descricao | TEXT | — | Não | Não | Sim | Descrição da movimentação |
| id_entrega | INTEGER | — | Não | Sim | Não | Entrega relacionada ao histórico |

---

## Tabela: movimentacao_estoque

**Descrição:** Armazena entradas, saídas, ajustes, devoluções, perdas e movimentações de inventário dos itens de produto.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_movimentacao_estoque | INTEGER | — | Sim | Não | Não | Identificador da movimentação de estoque |
| tipo_movimentacao | VARCHAR | 30 | Não | Não | Não | Tipo da movimentação |
| quantidade | INTEGER | — | Não | Não | Não | Quantidade movimentada |
| data | DATETIME | — | Não | Não | Não | Data da movimentação |
| responsavel | VARCHAR | 100 | Não | Não | Sim | Responsável pela movimentação |
| observacoes | TEXT | — | Não | Não | Sim | Observações sobre a movimentação |
| id_item_produto | INTEGER | — | Não | Sim | Não | Item de produto movimentado |

---

## Tabela: avaliacao

**Descrição:** Armazena avaliações realizadas pelos clientes sobre produtos adquiridos.

| Campo | Tipo | Tamanho | PK | FK | Nulo | Descrição |
|---|---|---|---|---|---|---|
| id_avaliacao | INTEGER | — | Sim | Não | Não | Identificador da avaliação |
| nota | INTEGER | — | Não | Não | Não | Nota atribuída ao produto |
| comentario | TEXT | — | Não | Não | Sim | Comentário do cliente |
| data_avaliacao | DATE | — | Não | Não | Não | Data da avaliação |
| status_avaliacao | VARCHAR | 20 | Não | Não | Não | Situação da avaliação |
| id_cliente | INTEGER | — | Não | Sim | Não | Cliente que realizou a avaliação |
| id_produto | INTEGER | — | Não | Sim | Não | Produto avaliado |
| id_item_pedido | INTEGER | — | Não | Sim | Não | Item de pedido que permite a avaliação |

---

# 2. Relacionamentos

| Tabela Origem | Campo FK | Tabela Destino | Campo PK | Cardinalidade | Descrição |
|---|---|---|---|---|---|
| preferencia_cliente | id_cliente | cliente | id_cliente | Cliente 1 : 0..N Preferencia_Cliente | Um cliente pode possuir nenhuma ou várias preferências de compra, e cada preferência pertence a um cliente |
| endereco | id_cliente | cliente | id_cliente | Cliente 1 : 0..N Endereco | Um cliente pode possuir nenhum ou vários endereços, e cada endereço pertence a um cliente |
| categoria | id_categoria_pai | categoria | id_categoria | Categoria Pai 0..1 : 0..N Categoria Filha | Uma categoria pode ter zero ou uma categoria pai, e uma categoria pai pode possuir várias subcategorias |
| produto | id_categoria | categoria | id_categoria | Categoria 1 : 0..N Produto | Uma categoria pode classificar nenhum ou vários produtos, e cada produto pertence a uma categoria |
| item_produto | id_produto | produto | id_produto | Produto 1 : 1..N Item_Produto | Um produto deve possuir uma ou mais variações, e cada item pertence a um produto |
| interacao_produto | id_cliente | cliente | id_cliente | Cliente 1 : 0..N Interacao_Produto | Um cliente pode realizar nenhuma ou várias interações, e cada interação pertence a um cliente |
| interacao_produto | id_produto | produto | id_produto | Produto 1 : 0..N Interacao_Produto | Um produto pode receber nenhuma ou várias interações, e cada interação está ligada a um produto |
| carrinho | id_cliente | cliente | id_cliente | Cliente 1 : 0..N Carrinho | Um cliente pode possuir nenhum ou vários carrinhos, e cada carrinho pertence a um cliente |
| item_carrinho | id_carrinho | carrinho | id_carrinho | Carrinho 1 : 0..N Item_Carrinho | Um carrinho pode estar vazio ou possuir vários itens, e cada item pertence a um carrinho |
| item_carrinho | id_item_produto | item_produto | id_item_produto | Item_Produto 1 : 0..N Item_Carrinho | Um item de produto pode aparecer em nenhum ou vários itens de carrinho, e cada item de carrinho referencia um item de produto |
| pedido | id_cliente | cliente | id_cliente | Cliente 1 : 0..N Pedido | Um cliente pode realizar nenhum ou vários pedidos, e cada pedido pertence a um cliente |
| pedido | id_carrinho | carrinho | id_carrinho | Carrinho 0..1 : 1 Pedido | Um carrinho pode gerar zero ou um pedido, e cada pedido deve ser gerado a partir de um carrinho |
| pedido | id_endereco_entrega | endereco | id_endereco | Endereco 1 : 0..N Pedido | Um endereço pode ser usado em nenhum ou vários pedidos como entrega, e cada pedido usa um endereço de entrega |
| pedido | id_endereco_cobranca | endereco | id_endereco | Endereco 1 : 0..N Pedido | Um endereço pode ser usado em nenhum ou vários pedidos como cobrança, e cada pedido usa um endereço de cobrança |
| item_pedido | id_pedido | pedido | id_pedido | Pedido 1 : 1..N Item_Pedido | Um pedido deve possuir um ou vários itens, e cada item de pedido pertence a um pedido |
| item_pedido | id_item_produto | item_produto | id_item_produto | Item_Produto 1 : 0..N Item_Pedido | Um item de produto pode aparecer em nenhum ou vários itens de pedido, e cada item de pedido referencia um item de produto |
| pagamento | id_pedido | pedido | id_pedido | Pedido 1 : 1..N Pagamento | Um pedido deve possuir um ou vários pagamentos, e cada pagamento pertence a um pedido |
| pagamento_pix | id_pagamento | pagamento | id_pagamento | Pagamento 1 : 0..1 Pagamento_PIX | Um pagamento pode ser do tipo PIX, e cada pagamento PIX especializa um pagamento |
| pagamento_boleto | id_pagamento | pagamento | id_pagamento | Pagamento 1 : 0..1 Pagamento_Boleto | Um pagamento pode ser do tipo boleto, e cada pagamento boleto especializa um pagamento |
| pagamento_cartao_credito | id_pagamento | pagamento | id_pagamento | Pagamento 1 : 0..1 Pagamento_Cartao_Credito | Um pagamento pode ser do tipo cartão de crédito, e cada pagamento cartão de crédito especializa um pagamento |
| pagamento_cartao_debito | id_pagamento | pagamento | id_pagamento | Pagamento 1 : 0..1 Pagamento_Cartao_Debito | Um pagamento pode ser do tipo cartão de débito, e cada pagamento cartão de débito especializa um pagamento |
| pagamento_carteira_digital | id_pagamento | pagamento | id_pagamento | Pagamento 1 : 0..1 Pagamento_Carteira_Digital | Um pagamento pode ser do tipo carteira digital, e cada pagamento carteira digital especializa um pagamento |
| entrega | id_pedido | pedido | id_pedido | Pedido 1 : 0..1 Entrega | Um pedido pode ainda não possuir entrega, mas cada entrega pertence a um pedido |
| historico_entrega | id_entrega | entrega | id_entrega | Entrega 1 : 0..N Historico_Entrega | Uma entrega pode possuir nenhuma ou várias movimentações, e cada histórico pertence a uma entrega |
| movimentacao_estoque | id_item_produto | item_produto | id_item_produto | Item_Produto 1 : 0..N Movimentacao_Estoque | Um item de produto pode possuir nenhuma ou várias movimentações de estoque, e cada movimentação pertence a um item |
| avaliacao | id_cliente | cliente | id_cliente | Cliente 1 : 0..N Avaliacao | Um cliente pode realizar nenhuma ou várias avaliações, e cada avaliação pertence a um cliente |
| avaliacao | id_produto | produto | id_produto | Produto 1 : 0..N Avaliacao | Um produto pode receber nenhuma ou várias avaliações, e cada avaliação está ligada a um produto |
| avaliacao | id_item_pedido | item_pedido | id_item_pedido | Item_Pedido 1 : 0..1 Avaliacao | Um item comprado pode gerar no máximo uma avaliação, e cada avaliação está vinculada a um item comprado |

---

# 3. Restrições de Domínio

| Campo | Restrição |
|---|---|
| cliente.cpf | Deve conter 11 dígitos e não pode se repetir |
| cliente.email | Deve possuir formato válido e não pode se repetir |
| categoria.status | Valores sugeridos: ativa, inativa |
| produto.status_produto | Valores sugeridos: ativo, inativo |
| item_produto.sku | Deve ser único na plataforma |
| item_produto.preco | Deve ser maior ou igual a zero |
| item_produto.quantidade_estoque | Não pode ser negativa |
| interacao_produto.tipo_interacao | Valores sugeridos: visualizacao, favorito, adicionado_ao_carrinho, navegacao, busca |
| carrinho.situacao_carrinho | Valores sugeridos: ativo, convertido, abandonado, inativo |
| pedido.status_pedido | Deve seguir as etapas definidas no processo de compra |
| pedido.desconto_aplicado | Deve ser maior ou igual a zero |
| pagamento.forma_pagamento | Valores sugeridos: pix, boleto, cartao_credito, cartao_debito, carteira_digital |
| pagamento.status_pagamento | Valores sugeridos: pendente, aprovado, recusado, cancelado |
| entrega.status_entrega | Deve seguir as etapas do processo logístico |
| movimentacao_estoque.tipo_movimentacao | Valores sugeridos: entrada, saida, ajuste, devolucao, perda, inventario |
| avaliacao.nota | Deve estar entre 1 e 5 |
| avaliacao.status_avaliacao | Valores sugeridos: pendente, aprovada, recusada |

---
