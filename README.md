# Mini-Projeto-1 Aplicado: Análise de Campanhas de Marketing com o Power BI

## Objetivo:

O objetivo deste projeto é colocar em prática os conceitos aprendidos durante o capítulo 04 do curso ['Microsoft Power BI Para Business Intelligence e Data Science'](https://www.datascienceacademy.com.br/course/microsoft-power-bi-para-business-intelligence-e-data-science) da Data Science Academy. Nesse capítulo, foram desenvolvidos 4 dashboards com uma base de dados fornecida pela DSA sobre campanha de marketing. No entanto, com este projeto, pretendo replicar os mesmos conceitos com outra fonte de dados.

## Os dados:

A nova fonte de dados escolhida para este projeto é a Superstore [Marketing Campaign Dataset](https://www.kaggle.com/datasets/rodsaldanha/arketing-campaign) disponível na plataforma gratuita da Kaggle.

### O contexto:

Uma grande loja está planejando uma liquidação de fim de ano. Com isso, vou usar a base de dados gerado na campanha do ano anterior para criar gráficos com base em 4 viés: Cliente, Comportamento, Performance da campanha e Grupos de Compras.

### Dicionário dos dados:

|     |     |
| --- | --- |
| **COLUNAS** | **SIGNIFICADOS** |
| Response (target) | 1 se o cliente aderiu a oferta, 0 se não aderiu |
| ID  | Identificador exclusivo de cada cliente |
| Year_Birth | Idade do cliente |
| Complain | 1 se o cliente fez alguma reclamação nos últimos dois anos |
| Dt_Customer | Data de cadastro do cliente na empresa |
| Education | Nível de escolaridade do cliente |
| Marital | Estado civil do cliente |
| Kidhome | Quantidade de crianças em casa |
| Teenhome | Quantidade de adolescente em casa |
| Income | Renda familiar anual do cliente |
| MntFishProducts | Valor gasto em produtos de pesca nos últimos 2 anos |
| MntMeatProducts | Valor gasto em produtos cárneos nos últimos 2 anos |
| MntFruits | Valor gasto em frutas nos últimos 2 anos |
| MntSweetProducts | Valor gasto em produtos doces nos últimos 2 anos |
| MntWines | Valor gasto em produtos vinícolas nos últimos 2 anos |
| MntGoldProds | Valor gasto em produtos de alta qualidade nos últimos 2 anos |
| NumDealsPurchases | Quantidade de compras feitas com desconto |
| NumCatalogPurchases | Quantidade de compras feitas pelo catálogo |
| NumStorePurchases | Quantidade de compras feitas em lojas |
| NumWebPurchases | Quantidade de compras feitas pelo site da empresa |
| NumWebVisitsMonth | Quantidade de visitas no site da empresa no ultimo mês |
| Recency | Quantidade de dias desde a ultima compra |

## Iniciando o projeto: Visão do Cliente

![Painel_1.png](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/Painel_1.png)

> O primeiro painel elaborado durante o curso teve como propósito analisar os clientes, identificando onde realizaram suas compras e compreendendo seu comportamento com base na escolaridade e no estado civil.

### Os cartões

![cartoes](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/Cartoes.png)

> O objetivo dos cartões é transmitir informações de maneira simples. Com eles, é possível concluir:

> - A amostra dos dados é formada por 2235 clientes.
> - A renda anual familiar é cerca de 51 mil.
> - A maioria dos clientes compra diretamente na loja.
> - Compras pelo site representam o segundo método mais comum.
> - Compras por catálogos e com descontos são as menos registradas.

### Gráficos de barras

![Grafico de barras](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/grafico_barras.png)

> Os gráficos de barras são uma das visualizações mais versáteis, representando dados quantitativos por meio de barras retangulares. Com esses gráficos, é notável que os dados apresentam alguns problemas que precisarão de correção.

> - Todas as informações em inglês terão que ser substituídas por valores em português, pois é a língua usada neste relatório.
> - Valores como "Alone," "Absurd" e "YOLO" não fazem muito sentido para a coluna "Marital_Status" (Estado Civil)

#### Resolvendo os problemas

> **Passo 1:**  
> As variáveis "Absurd" e "YOLO" não parecem ter muita lógica em comparação com as outras informações da coluna "Marital Status." Portanto, elas serão removidas, enquanto "Alone" será substituída pelo valor "Solteiro."

> **Passo 2 (As traduções):**
> 
> - "Graduation" = "Curso Superior"
> - "Phd" = "Doutorado"
> - "Master" = "Mestrado"
> - "2n Cycle" = "Médio"
> - "Basic" = "Fundamental"
> - "Married" = "Casado"
> - "Together" = "União Estável"
> - "Single" = "Solteiro"
> - "Widow" = "Viúvo"
> - "Divorced" = "Divorciado"

### Após o tratamento dos dados, o resultado é:

![Grafico de barras 2](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/grafico_barras_2.png)

> Com base nos gráficos, é evidente que tanto a escolaridade quanto o estado civil exercem influência nas decisões de compra, quanto analisados de forma isolada:

> **Escolaridade:**
> 
> Clientes com níveis mais elevados de escolaridade costumam fazer mais compras. Isso pode se dever ao fato de que um nível mais alto de escolaridade muitas vezes está ligado a uma renda mais elevada. O destaque no grupo com nível superior pode ser explicado pela menor proporção de pessoas que continuam a formação acadêmica após concluir o ensino superior.

### Ultima visualização:

> A última representação gráfica no primeiro painel do curso é a filtragem por país. Contudo, como essa coluna não está presente na base de dados atual, o filtro foi substituído por uma linha do tempo

![linha do tempo](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/linha_tempo.png)

> A linha do tempo tem como objetivo observar a distribuição dos dados ao longo do tempo, permitindo a identificação de eventuais mudanças nos padrões dos clientes.

### Primeiro Dashboard finalizado:

![Visao_Cliente](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/Visao_cliente.gif)

* * *

## Visão Comportamento:

![Painel 2](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/Painel_2.png)

> O objetivo do segundo painel é dar uma olhada em como os clientes gastam. Para fazer isso, o primeiro passo é criar a medida "TotalGasto", que é a soma de tudo que os clientes compram.

### Codigo dax para a medida TotalGasto:

> `TotalGasto = SUMX(superstore_data, superstore_data[MntFishProducts] + superstore_data[MntFruits] + superstore_data[MntGoldProds] + superstore_data[MntMeatProducts] + superstore_data[MntSweetProducts] +superstore_data[MntWines])`

### Gráfico de Dispersão

![Grafico de dispersão](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/grafico_dispersao.png)

> O propósito do gráfico de dispersão é apresentar a relação entre duas variáveis contínuas, sendo útil para identificar padrões, tendências, correlações ou mesmo outliers nos dados. Vale ressaltar que esse gráfico contém um outlier significativo que dificulta a visualização.   
> A forma mais simples e formal de corrigir esse outlier é removê-lo dos dados.

### Após corrigir o outlier, o resultado é:

![Grafico de dispersão 2](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/grafico_dispersao_2.png)

> Com este gráfico, é evidente que a correlação entre os gastos dos clientes e o salário anual é positiva, indicando que à medida que a renda aumenta, os gastos também tendem a aumentar.

### Árvore Hierárquica

![Arvores hierarquica](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/grafico_hieraquico.png)

> O gráfico de Árvore Hierárquica é usado como uma representação visual clara das estruturas hierárquicas ou organizacionais das informações. Com este gráfico, observa-se que:

> O total de gastos do cliente está relacionado à hierarquia do estado civil, e o estado civil, por sua vez, está associado à hierarquia da educação. Dessa forma, é possível notar como ambas as variáveis, estado civil e educação, influenciam no comportamento de gasto do cliente.

### As últimas duas visualizações do segundo painel.

![Grafico de barras 3](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/grafico_barras_3.png)

> Essa visualização indica que clientes sem filhos (Crianças e Adolescentes em casa) tendem a ter um gasto maior em comparação com aqueles que têm filhos.

### Segundo Dashboard concluído:

![Visão_comportamento](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/Visao_comportamento.gif)

* * *

## Visão Performance das Campanhas:

![Painel 3](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/Painel_3.png)

> O terceiro painel ilustra o desempenho das campanhas de marketing anteriores. Portanto, as análises serão centradas na coluna "Response"

### Gráfico de barras com legendas

![Grafico de barras com legendas](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/grafico_barras_legendas.png)

> Na primeira visualização, a coluna "FilhosEmCasa" foi criada somando os valores de "Kidhome" e "Teenhome".

> Observa-se já de início que grande parte dos clientes não aderiu à campanha. Além disso, nota-se que clientes com menos filhos morando com eles são aqueles que tiveram a resposta mais positiva à campanha.

### Gráfico de Círculo:

![grafico de circulo](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/grafico_circulo.png)

> Gráficos de Círculo, também conhecidos como gráficos de pizza, têm como objetivo representar a distribuição proporcional de categorias. São úteis para demonstrar como uma quantidade total é dividida em diferentes partes

> A visualização confirma que a base de dados é formada, em sua maioria, por clientes que não aderiram à oferta da campanha de marketing.

### Tabelas:

![Tabelas](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/tabelas.png)

> As tabelas são uma forma essencial de apresentar dados de maneira estruturada, sendo bastante compreensíveis para análise e interpretação.

> Com a tabela, nota-se que tanto as colunas "Education" e "Marital" influenciam na resposta da campanha.

### Ultima vizualização do terceiro painel:

![Grafico de barras 4](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/grafico_barras_4.png)

> É perceptível com este gráfico que, à medida que o cliente possui um salário maior, ele tende a aderir mais à campanha.

### Terceiro Dashboard concluído:

![VIsão_Capanhas](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/Visao_performance.gif)

* * *

## Visão Padrões de Compra por Escolaridade e Estado Civil.

![Painel 4](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/Painel_4.png)

> Nos dados utilizados no projeto, não há a coluna 'País', portanto, ele será um pouco diferente do original.

### Grafico de colunas agrupadas e linha:

![Grafico de colunas agrupadas](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/grafico_colunas_agrupadas.png)

> São gráficos que exibem muita informação, mas são úteis em apresentações e análises de dados, fornecendo insights visuais de maneira eficaz e compreensível. No entanto, seu uso depende dos objetivos específicos das análises.

> Carnes e vinhos representam os principais gastos dos clientes, sendo que aqueles que são casados ou estão em união com alguém tendem a gastar mais em todos os tipos de produtos do que os demais clientes.

![Grafico de colunas agrupadas 2](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/grafico_colunas_agrupadas_2.png)

> A mesma tendência se repete, onde pessoas com diploma de nível superior são as que mais gastam; em seguida, vêm os outros níveis educacionais.

### Último painel concluído:

![Padroes_de_compra](https://github.com/VanJoaoPedro/PowerBi_MarketingData/blob/main/Arquivos/Visao_padrao_compras.gif)
