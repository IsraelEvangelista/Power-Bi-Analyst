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

## Passo 01 – Criação do modelo padrão

Criação no Software Workbench o modelo padrão proposto no desafio

![image](https://user-images.githubusercontent.com/116984176/214466941-45889125-7b5c-4a3f-9159-4c147a483ab3.png)

## Passo 02 – Etapas de modelagem

Foi usada a metodologia de abstração das informações do dataset proposto de redimensionamento das tabelas para arquitetar tabelas dimensões com adição da tabela "data" e a tabela fato "professor".

- Tabela-fato: "Professor" pois possui informações numéricas sobre os professores, como número de disciplinas ministradas. As outras tabelas foram convertidas em tabelas-dimensão;

- A tabela "Departamento" foi usada como uma tabela-dimensão, pois contém informações descritivas sobre os professores, como o nome e o campus do departamento;

- A tabela "Disciplina" também foi usada como uma tabela-dimensão, pois contém informações descritivas sobre as disciplinas ministradas pelos professores;

- Foi incluído a tabela-dimensão "Data" com atributos data, dia, semana, mês, trimestre e ano;

- A tabela "Curso" foi usada como uma tabela-dimensão, pois contém informações descritivas sobre os cursos relacionados aos departamentos;

- A tabela "Aluno" e "Matriculado" não é necessário para o Star Schema proposto.

## Passo 03 – Resultado Star Schema - Universidade

![image](https://user-images.githubusercontent.com/116984176/214468270-ce3a75e7-f842-466a-ab1d-b5e3e2dd4d17.png)
