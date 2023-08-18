<picture> <img align="left" src="https://hermes.digitalinnovation.one/tracks/b9b2973e-b2be-4bf0-b6b2-57a6c8354a95.png" width = 80px></picture> 
# Projeto 3 - Processando e Transformando Dados com Power BI

## Instruções de Entrega do Desafio

**Descrição do desafio módulo 3 – Processamento de Dados Simplificado com Power BI**

1. Criação de uma instância na Azure para MySQL

2. Criar o Banco de dados com base disponível no github

3. Integração do Power BI com MySQL no Azure

4. Verificar problemas na base a fim de realizar a transformação dos dados

**Diretrizes para transformação dos dados**

1. Verifique os cabeçalhos e tipos de dados

2. Modifique os valores monetários para o tipo double preciso

3. Verifique a existência dos nulos e analise a remoção

4. Os employees com nulos em Super_ssn podem ser os gerentes. Verifique se há algum colaborador sem gerente

5. Verifique se há algum departamento sem gerente

6. Se houver departamento sem gerente, suponha que você possui os dados e preencha as lacunas

7. Verifique o número de horas dos projetos

8. Separar colunas complexas

9. Mesclar consultas employee e departament para criar uma tabela employee com o nome dos departamentos associados aos colaboradores. A mescla terá como base a tabela employee. Fique atento, essa informação influencia no tipo de junção

10. Neste processo elimine as colunas desnecessárias.

11. Realize a junção dos colaboradores e respectivos nomes dos gerentes . Isso pode ser feito com consulta SQL ou pela mescla de tabelas com Power BI. Caso utilize SQL, especifique no README a query utilizada no processo.

12. Mescle as colunas de Nome e Sobrenome para ter apenas uma coluna definindo os nomes dos colaboradores

13. Mescle os nomes de departamentos e localização. Isso fará que cada combinação departamento-local seja único. Isso irá auxiliar na criação do modelo estrela em um módulo futuro.

14. Explique por que, neste caso supracitado, podemos apenas utilizar o mesclar e não o atribuir.

15. Agrupe os dados a fim de saber quantos colaboradores existem por gerente

16. Elimine as colunas desnecessárias, que não serão usadas no relatório, de cada tabela

______________________________________________________________________________________________________________________________________________

## Passo 01 – Criação da instância Azure DB

Para persistir os dados do BD “Company”, foi instanciado o banco de dados “desafio-projeto-company” na plataforma Azure. Em seguida, foi baixado o certificado SSL para uso de conexão com o MySQL Workbench, e por fim, estabelecida conexão da Azure com o Power BI e coleta dos dados.

![image](https://user-images.githubusercontent.com/116984176/212576791-9a3580c3-5e70-44fa-9a9a-304ecb7a84a7.png)

![image](https://user-images.githubusercontent.com/116984176/212576776-47f03043-9704-4323-b91d-b7627056674b.png)

![image](https://user-images.githubusercontent.com/116984176/212576871-34716c46-a0bc-4cf2-954f-dd39b61c6f56.png)

## Passo 02 – Formatando os Dados

_Tabela company departament_

  - Remoção das colunas: company.dept_locations, company.employee e company.project;
  - Formatação da coluna Dnumber de número para texto, por tratar-se de uma chave.

_Tabela company dependent_

  - Remoção da coluna: company.employee;
  - Substituição de valores da coluna “Sex” de M = “Male” e F = “Female”.

_Tabela company dept_location_

  - Remoção da coluna: company.departament;
  - Formatação da coluna Dnumber de número para texto, por tratar-se de uma chave.
  
_Tabela company employee_

  - Remoção das colunas: company.departament, company.dependent, company.employee(Ssn), company.employee(Super_ssn) e company.works_on;
  - Formatação da coluna Dno de número para texto, por tratar-se de um chave;
  - Substituição de valores da coluna “Sex” de M = “Male” e F = “Female”;
  - Colunas Fname, Minit e Lname, mescladas pelo delimitador “espaço” para uma única coluna “Nome completo”.

_Tabela company project_

  - Remoção das colunas: company.departament e company.works_on;
  - Formatação das colunas Dnum e Pnumber de número para texto, por tratar-se de uma chave.

_Tabela company works_on_

  - Remoção das colunas: company.employee e company.project;
  - Formatação da coluna Pno de número para texto, por tratar-se de uma chave.

## Passo 03 – Transformando Tabelas

_Tabela company employee_

Coluna “Super_ssn” possui um registro nulo, indicando que há um empregado sem gerente.
  ->	James S Wallace
  
 ![image](https://user-images.githubusercontent.com/116984176/212577200-b713b465-6567-4f19-a002-c33bfd993d2d.png)

_Tabela company departament_

Todos os departamentos possuem um gerente associado, datas de início da gestão e criação do departamento.

![image](https://user-images.githubusercontent.com/116984176/212577228-16343078-d22c-43b1-bf3e-a60d0f3bcbe6.png)

_Tabela company project_

Plocation removido, pois possui chave referencial em dept_locations.

![image](https://user-images.githubusercontent.com/116984176/212577245-9ed9c91f-af47-4661-bb9d-df3162f66bf0.png)

_Tabela company works_on_

Coluna “Pno” e “Essn” formatado de número para texto, pois trata-se de uma chave;
“Hours” formatado como decimal.

## Passo 04 – Criando Novas Tabelas
**Obs.: Todas as funções abaixo foram utilizadas no próprio Power Query.**

_Empregados / Departamentos_

Mesclar consultas employee e departament para criar uma tabela employee com o nome dos departamentos associados aos colaboradores.
  ->	Foi utilizado um outter left join à tabela employee e a chave Dno com a tabela departament e chave Dnumber;
  ->	Foi utilizado um outter left Join na coluna Super_ssn para recuperar o nome completo dos gerentes de cada departamento;
  ->	Por fim, as colunas Ssn, Super_ssn, Dno, company departament.Dnumber, company departament.Mgr_ssn, foram removidas.
  
![image](https://user-images.githubusercontent.com/116984176/212577838-83efc722-24d6-4c9c-a743-b0c3e6f60f19.png)

_Departamentos / Localização_
Mescle os nomes de departamentos e localização. Isso fará que cada combinação departamento-local seja único.
  ->	Foi utilizado um outter left Join à tabela departament e a chave Dnumber com a tabela dept_location e a chave Dnumber;
  ->	Nas informações recuperadas, foi expandida apenas a informação Dlocation que teve o nome da coluna alterada para Localização;
  ->	As colunas Dnumber e Mgr_ssn foram apagadas.
  
 ![image](https://user-images.githubusercontent.com/116984176/212577421-81beaa60-d308-4688-8fe5-e0a4e2f1d842.png)
 
 **TABELAS FINAIS**
 
 Segue Link abaixo para imagens de tabelas finais:
 
 [Departament_Location](https://github.com/IsraelEvangelista/Power-Bi-Analyst/blob/main/Projeto%203%20Modulo%203/Tabelas%20Final/Departament_Location%20Final%20-%20Power%20Query.jpg?raw=true)
 
 [Dependent](https://github.com/IsraelEvangelista/Power-Bi-Analyst/blob/main/Projeto%203%20Modulo%203/Tabelas%20Final/Dependent%20Final%20-%20Power%20Query.jpg?raw=true)
 
 [Employee_Departament](https://github.com/IsraelEvangelista/Power-Bi-Analyst/blob/main/Projeto%203%20Modulo%203/Tabelas%20Final/Employee_Departament%20Final%20-%20Power%20Query.jpg?raw=true)
 
 [Project](https://github.com/IsraelEvangelista/Power-Bi-Analyst/blob/main/Projeto%203%20Modulo%203/Tabelas%20Final/Project%20Final%20-%20Power%20Query.jpg?raw=true)
 
 [Works_On](https://github.com/IsraelEvangelista/Power-Bi-Analyst/blob/main/Projeto%203%20Modulo%203/Tabelas%20Final/Works%20on%20Final%20-%20Power%20Query.jpg?raw=true)

## Passo 05 – Distribuições de Colunas

**Visão geral de distribuição estatística**

_Empregados / Departamentos_

![image](https://user-images.githubusercontent.com/116984176/212577897-c076d134-1093-4b6e-9997-fd90671bb2c2.png)

_Empregados / Gerentes_

![image](https://user-images.githubusercontent.com/116984176/212577935-2d2e8e95-4d6d-45de-a5ba-48dafd2761b2.png)

_Departamentos / Localização_

![image](https://user-images.githubusercontent.com/116984176/212580261-2f5d126f-685f-4829-a739-1aa1540f9d3b.png)

## Passo 06 - Relatório BI

Após o tratamento dos dados no Power Query, foi criado o relatório em Power BI para representação gráfica dos dados e dinâmica dos dados persistidos. 

![image](https://user-images.githubusercontent.com/116984176/212580210-d108423b-c574-441e-8b01-efb6b716df33.png)

**Componentes do relatório:**

  - Três cartões na parte superior nos quais descrevem respectivamente: Contagem de projetos, Soma de Salário e Soma de Horas de Projeto;
  - Na parte central do relatório, um gráfico de área, no qual descreve no eixo Y a soma de horas, enquanto no eixo X reflete a agregação de dois atributos, Departamentos e Projetos;
  - As visões na parte inferior do relatório, encontra-se disposto inicialmente mais a esquerda uma matriz com agrupamento de Departamento e Gerente, refletindo a contagem de Empregados e soma de Salário. A visão foi mantida com expansão total para uma melhor perspectiva dos dados;
  - Ainda na parte inferior, mas disposto na parte central, um gráfico de colunas empilhadas de contagem de projetos por departamentos;
  - Por fim, a última visão da parte inferior do relatório, um gráfico de Treemap. Neste foram agrupados a contagem de departamentos por Localização.
  
  
Arquivo Power Point integrado ao relatório Power BI - Company

[Link para Download](https://github.com/IsraelEvangelista/Power-Bi-Analyst/raw/main/Projeto%203%20Modulo%203/Projeto_Company.pptx)  

Página de visualização do relatório BI publicado na WEB (Caso hajam problemas de acesso ao arquivo Power Point)

[Link para Visualização](https://app.powerbi.com/view?r=eyJrIjoiZmQxMWIxNTMtZDM2MC00NThkLTg3YWQtNjdiNjExZTViMGYwIiwidCI6IjdjZWZiZWRhLWRjMmQtNGQ4Mi05ZThlLTg0NDA1MDRkNTk1NCJ9)
