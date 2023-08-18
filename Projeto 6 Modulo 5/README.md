<picture> <img align="left" src="https://hermes.digitalinnovation.one/tracks/b9b2973e-b2be-4bf0-b6b2-57a6c8354a95.png" width = 80px></picture> 
# Projeto 6

## Instruções de Entrega do Desafio

**Descrição do Projeto Desafio 6 – Atualizando Relatório no Power BI com Foco na Experiência do Usuário**

**Objetivo:**

Modificar o relatório criativo, o primeiro que criamos juntos, focando na experiência do usuário. Acompanhe o vídeo para que você entenda o que foi feito neste processo. Além disso, leve em consideração os seguintes pontos:

- Posicionamento

- Contraste

- Proporção áurea

- Segmentação dos dados

Como comentamos no curso, não é uma regra rígida. Entenda os pontos e cria seu relatório levando os em consideração. Contudo, saiba quando você deve quebrar as regras. Isso vai trazer mais criatividade ao seu relatório. Esses pontos fora da curva deixam seu relatório mais interessante.

**Próximos passos:**

- Insira os botões de navegabilidade

- Modifique a segunda página de forma similar a demostrada no desafio para a primeira página

- Modifique os botões de navegabilidade a fim de destacar o focalizar e selecionar

- Criar os menus de navegabilidade em cada página

- O estilo dos botões é livre!

- O relatório é composto por 3 páginas
______________________________________________________________________________________________________________________________________________

## Passo 01 – Repaginando Relatório Elegante

Readequação do visual do relatório elaborado no projeto desafio 2:

![image](https://user-images.githubusercontent.com/116984176/215349298-79bc496e-9021-4a65-b640-2fb88a5a9718.png)
![image](https://user-images.githubusercontent.com/116984176/215349308-be6d70d6-cc91-404f-9797-94725694bd90.png)

_Modelo anterior_

![image](https://user-images.githubusercontent.com/116984176/215349373-5f8767f1-6cfa-4eef-b526-530c76781d74.png)
![image](https://user-images.githubusercontent.com/116984176/215349383-1bfc4a8d-375b-4950-a64c-3f88797455a7.png)
![image](https://user-images.githubusercontent.com/116984176/215349395-8f3181c7-73dc-43bd-9af1-f1709bbd407b.png)

_Modelo atual_

**Etapas - Passo 01**

**_A página 1_** "Sales" foi redesenhada para um visual mais chamativo e adequado ao padrão de Fibonnaci. Não aepnas isso, mas as informações apresentadas neste visual retratam com maior nitidez as "Vendas".

Vamas analisar da direita pra esquerda: 

Temos um gráfico de área que retrata as vendas por ano e mês. Os rótulos foram ocultados e mantidos os valores no eixo.

Logo abaixo, foi criado uma matriz representada pelos valores de Venda e Unidades vendidas. Nas linhas foram agrupados os meses e produtos, e nas colunas ano, Country, Segment e Discount Band. 
A construção das linhas da matriz ocorreu desta forma, pois há a possibilidade de efetuar um drill down de meses para produtos, ou mesmo verificá-los em suas devidas hierarquias para uma perspectiva da informação apresentada. 
Já as colunas, foi escolhido que haveria todas as informações ditas, porém com um parâmetro de escolha de qual seria apresentada. Este recurso foi construído da seguinte forma:

O visual à esquerda inferior, trata-se de um gráfico de colunas empilhadas. Para a construção dos botões de qual informção seria persistida no gráfico (neste caso Segment e Product), foi usado o mesmo recurso do visual anterior (Matriz).

Por fim, à esquerda superior, dois cartões com informações de total de vendas e unidades vendidas respectivamente.

    Modelagem > Novo Parâmetro > Nomeado nome da tabela de parâmetro de escolha > Agrupamento dos atributos que fariam parte do parâmetro
    
Com isso, é possível definir de maneira simples qual informação será persistida nas colunas colunas da matriz.

**_A página 02_** não sofreu grandes mudanças. O visual foi utilizado o padrão da página anterior.

**_A página 03_** foi criada, já que o relatório original possuia apenas 2 páginas. Nesta página há um detalhamento das informações por período. Novamente analisando da direita pra esquerda, temos à direita superior, um filtro de ano para uma visão temporal anual.

Abaixo, temos um gráfico de colunas agrupadas e linhas representado no eixo X pelo meses do ano, e no eixo Y por colunas as Vendas e linhas o valor bruto.

À esquerda inferior, temos uma matriz de vendas e lucros de trimestres (linhas) por anos (colunas).

Na esquerda superior, foi representado um visual de colunas clusterizado de vendas, lucros, e valor bruto por semestre.

Por fim, na parte central do painel, temos três cartões representados de cima para baixo respectivamente por: Total de Vendas, Total de Lucros e Total Bruto.

Notem que cada visual possui uma perspectiva de um período do ano: O filtro nos permite a escolha de qual o ano vamos analisar. O segundo está agrupado por mês para uma visão mais detalahda. O terceiro representada por semestre e por último, o terceiro visual de dados apresentando valores por semestre. Isso nos da uma perspectiva descritiva de ambas as informações fatiadas por qualquer que seja o período, esteja ele na sua hierarquia mais baixa ou mais alta.

## Passo 02 – Publicando no Power BI Workspace

Nesta etapa, o relatório foi publicado no workspace e gerado um PDF e Power Point para apresentação do relatório. Os links estão logo abaixo:

[Link para arquivo em PDF](https://github.com/IsraelEvangelista/Power-Bi-Analyst/blob/main/Projeto%206%20Modulo%205/Projeto%20Elegante%20Atualizado.pdf)

[Link para arquivo Power Point](https://github.com/IsraelEvangelista/Power-Bi-Analyst/blob/main/Projeto%206%20Modulo%205/Projeto%20-%20Relat%C3%B3rio%20Elegante%20Atualizado.pptx)

*Publicado na Web
[Link para visualização](https://app.powerbi.com/view?r=eyJrIjoiOWY2NTk4Y2ItMDc1My00ZDhkLWI1MjktZTEyODk3YTFhYjY1IiwidCI6IjdjZWZiZWRhLWRjMmQtNGQ4Mi05ZThlLTg0NDA1MDRkNTk1NCJ9)
