<picture> <img align="left" src="https://hermes.digitalinnovation.one/tracks/b9b2973e-b2be-4bf0-b6b2-57a6c8354a95.png" width = 80px></picture> 
# Projeto 3 - Processando e Transformando Dados com Power BI

## Instruções de Entrega do Desafio

**Descrição do desafio módulo 4 – Criando um Star Schema para Cenários de Vendas com Power BI**
_(Modelo Universidade)_

**Objetivo:**

Criar o diagrama dimensional – star schema – com base no diagrama relacional disponibilizado.

Foco:

Professor – objeto de análise

Vocês irão montar o esquema em estrela com o foco na análise dos dados dos professores. Sendo assim, a tabela fato deve refletir diversos dados sobre professor, cursos ministrados, departamento ao qual faz parte.... Por aí vocês já têm uma ideia do que deve compor a tabela fato do modelo em questão.

Obs.: Não é necessário refletir dados sobre os alunos!

O que deve ser feito?

Deverá ser criada a tabela Fato que contêm o contexto analisado. Da mesma forma, é necessária a criação das tabelas dimensão que serão compostas pelos detalhes relacionados ao contexto.

Por fim, mas não menos importante, adicione uma tabela dimensão de datas. Para compensar a falta de dados de datas do modelo relacional, suponha que você tem acesso aos dados e crie os campos necessários para modelagem.

Ex: data de oferta das disciplinas, data de oferta dos cursos, entre outros. O formato, ou melhor, a granularidade, não está fixada. Podem ser utilizados diferentes formatos que correspondem a diferentes níveis de granularidade.

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


