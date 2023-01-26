<picture> <img align="left" src="https://hermes.digitalinnovation.one/tracks/b9b2973e-b2be-4bf0-b6b2-57a6c8354a95.png" width = 80px></picture> 
# Projeto 5

## Instruções de Entrega do Desafio

**Descrição do desafio módulo 4 – Modelagem e Transformação de dados com DAX com Power BI**

**Objetivo:**

Utilizaremos a tabela única de Financial Sample para criar as tabelas dimensão e fato do nosso modelo baseado em star schema.

O processo consiste na criação das tabelas com base na tabela original. A partir da cópia serão selecionadas as colunas que irão compor a visão da nova tabela. Sendo assim, a partir da tabela principal serão criadas as tabelas:

Financials_origem (modo oculto – backup)

D_Produtos (ID_produto, Produto, Média de Unidades Vendidas, Médias do valor de vendas, Mediana do valor de vendas, Valor máximo de Venda, Valor mínimo de Venda)

D_Produtos_Detalhes(ID_produtos, Discount Band, Sale Price, Units Sold, Manufactoring Price)

D_Descontos (ID_produto, Discount, Discount Band)

D_Detalhes (*)

D_Calendário – Criada por DAX com calendar()

F_Vendas (SK_ID , ID_Produto, Produto, Units Sold, Sales Price, Discount Band, Segment, Country, Salers, Profit, Date (campos))

*Verifique as informações que não foram contempladas nas demais tabelas dimensão que fornecem maiores detalhes sobre vendas.
______________________________________________________________________________________________________________________________________________

## Passo 01 – Criação das tabelas dimensões

Foram criadas 5 tabelas dimensões e 1 tabela fato, derivadas da tabela "financials_origem". As tabelas são descritas a seguir:

![image](https://user-images.githubusercontent.com/116984176/214748523-365556dd-b5b1-41e2-ac38-6546b86d20b1.png)

**D_Produtos**

Tabela dimensão criada para persistir valores agregados de vendas e medidas estatísticas. Possui os atributos "id_produto", "Product", Soma de Unidades Vendidas", "Valor Mín de Venda", "Valor Máx de Venda", "Média do Valor de Venda", "Mediana do Valor de Venda" e "Média da Manufatura". Estes atributos foram criados a partir da funcionalidade do Power Query 'Agrupar por'. O atributo "id_produto" foi criado a partir da funcionalidade 'Tabela Índice' após a agregação.

**D_Detalhes**

Tabela dimensão criada para detalhar informações adicionais da tabela fato. Seus atributos são "id_detalhes", "id_produto", "Gross Sales", "COGS" e "Profit". Havia a possibilidade de atribuir substituições de valores ao atributo "Produtos" para recuperar "id_produto", porém achei mais performático efetuar uma combinação de mescla para recuperar a informação. No caso proposto haviam poucas informações para substituíções, porém esta solução seria até mesmo viável em um caso de inúmeros índices para substituir.

**D_Data**

A Tabela dimensão data foi criada a partir da data base e usada a fórmula DAX para criação das demais. 

_Coluna Month Number_

Number.From(
    Date.Month([Date])
)

_Coluna Month Name_

Date.MonthName([Date])

_Coluna Year_

Number.From(
    Date.Year([Date])
)

**D_Categoria**

Tabela Dimensão persistida para classificação dos dados da tabela fato. Formada a partir de dois atributos base, "Segment" e "Country" e um terceiro que é a chave id da combinação destes dois sem repetição.

**D_Desconto**

Tabela Dimensão com a função de referenciar os descontos "Discounts" e a faixa de desconto "Discounts Band". Estes atributos estão referenciados pelo "id_produto" e uma chave única "id_desconto".

**F_Vendas**

Por fim, a tabela fato que carrega as principais chaves das tabelas dimensões "id_categoria", "id_produto", "id_detalhes", "id_desconto" e uma "SK_id" (surrogate key). A tabela também carrega consigo alguns atributos únicos "Units Sold", "Sale Price", "Sales", "Manufacturing Price" e "Date" onde este último referencia a tabela D_Data.

## Passo 02 – Referenciando as chaves

Como último passo, é hora de dar forma ao _Star Schema_. Nesta etapa, faz-se a ligação de todas as chaves referenciais das tabelas dimensões com a tabela fato (sem ligações entre as dimensões. Estamos tratando de um Star Schema e não de um Snowflake Schema). 

Segue abaixo o resultado final:

![image](https://user-images.githubusercontent.com/116984176/214752906-8aa35e75-fc14-4b9a-b93c-db9e3a058151.png)

Podemos perceber que algumas tabelas foram retiradas da proposta original ou reestruturadas. Procedi desta forma para efetivar o Star Schema e evitar problemas referenciais entre as tabelas. Sabe-se também que relacionamentos N:M não são bem vindos no Power BI (na verdade nem eu mesmo gosto) então procurei evitá-los para performar o projeto.
