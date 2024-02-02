---
title: "Simples aplicação de Mínimos quadráticos"
subtitle: ""
excerpt: "Uma aplicação de mínimos quadráticos em Álgebra Linear!"
date: 2024-02-02
author: "Diogo Vieri"
draft: false
images:
series:
tags:
categories:
  - Álgebra Linear
  - R
  - Latec
layout: single
---

## Motivação!

A motivação para essa aplicação surgiu após ver o tema do dia 09/01/2024 do [TidyTuesday!](https://github.com/rfordatascience/tidytuesday)

Basicamente, se trata de fazer uma análise de um data base para responder a seguinte pergunda: ["As datas de nascimento ainda são um destino para os jogadores canadenses da NHL?"](https://jlaw.netlify.app/2023/12/04/are-birth-dates-still-destiny-for-canadian-nhl-players/), tema bastante discutido no link!

Os dados foram coletados do [Statistics Canada, NHL team list endpoint e NHL API](https://www150.statcan.gc.ca/t1/tbl1/en/tv.action?pid=1310041501&pickMembers%5B0%5D=3.1&cubeTimeFrame.startYear=1991&cubeTimeFrame.endYear=2022&referencePeriods=19910101%2C20220101)

## Análise

Para ter uma ideia do banco de dados:


| player_id|first_name |last_name  |birth_date |birth_city  |birth_country |birth_state_province | birth_year| birth_month|
|---------:|:----------|:----------|:----------|:-----------|:-------------|:--------------------|----------:|-----------:|
|   8462176|Brent      |Sopel      |1977-01-07 |Calgary     |CAN           |Alberta              |       1977|           1|
|   8462032|Bryan      |Berard     |1977-03-05 |Woonsocket  |USA           |Rhode Island         |       1977|           3|
|   8448959|Donald     |MacIver    |1955-05-03 |Montréal    |CAN           |Quebec               |       1955|           5|
|   8467834|Gregg      |Naumenko   |1977-03-30 |Chicago     |USA           |Illinois             |       1977|           3|
|   8446699|Glen       |Harmon     |1921-01-02 |Holland     |CAN           |Manitoba             |       1921|           1|
|   8445512|Charlie    |Conacher   |1909-12-20 |Toronto     |CAN           |Ontario              |       1909|          12|
|   8445334|Gene       |Carrigan   |1907-07-05 |Edmonton    |CAN           |Alberta              |       1907|           7|
|   8466436|Martin     |Sonnenberg |1978-01-23 |Wetaskiwin  |CAN           |Alberta              |       1978|           1|
|   8447997|Gordie     |Nelson     |1947-05-10 |Kinistino   |CAN           |Saskatchewan         |       1947|           5|
|   8451513|Derek      |Smith      |1954-07-31 |Quebec City |CAN           |Quebec               |       1954|           7|

A análise que irá ser feita, usará apenas a coluna birth_month que representa o mês de nascimento do jogador!


|birth_month | Freq|
|:-----------|----:|
|Jan         |  876|
|Fev         |  819|
|Mar         |  834|
|Abr         |  796|
|Mai         |  783|
|Jun         |  692|
|Jul         |  696|
|Ago         |  602|
|Set         |  639|
|Out         |  620|
|Nov         |  561|
|Dez         |  556|

Como queremos transformar esses dados em formato de matriz para aplicar técnicas da Álgebra Linear vamos entender esse data base como uma matriz:

`$$\left(\begin{array}{cc}
  x & y \\
  1 & 876 \\
  2 & 819 \\
  3 & 834 \\
  4 & 796 \\
  5 & 783 \\
  6 & 692 \\
  7 & 696 \\
  8 & 602 \\
  9 & 639 \\
  10 & 620 \\
  11 & 561 \\
  12 & 556 \\
  \end{array}\right) = A = 
  \left(\begin{array}{cc}
  1 & 1 \\
  1 & 2 \\
  1 & 3 \\
  1 & 4 \\
  1 & 5 \\
  1 & 6 \\
  1 & 7 \\
  1 & 8 \\
  1 & 9 \\
  1 & 10 \\
  1 & 11 \\
  1 & 12 \\
  \end{array}\right),B = 
  \left(\begin{array}{c}
  876 \\
  819 \\
  834 \\
  796 \\
  783 \\
  692 \\
  696 \\
  602 \\
  639 \\
  620 \\
  561 \\
  556 \\
  \end{array}\right)$$`

Conforme visto em [Ortogonalidade e Mínimos quadráticos](https://diogovieri.rbind.io/blog/vetores-ortogonais/):

`$$\text{Vamos usar a fórmula: }proj_{col A}b = (A^{t}A)x=A^{t}b$$`

`$$A^{t}A = \left(\begin{array}{cc}
  1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 \\
  1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 & 9 & 10 & 11 & 12 \\
  \end{array}\right)   \left(\begin{array}{cc}
  1 & 1 \\
  1 & 2 \\
  1 & 3 \\
  1 & 4 \\
  1 & 5 \\
  1 & 6 \\
  1 & 7 \\
  1 & 8 \\
  1 & 9 \\
  1 & 10 \\
  1 & 11 \\
  1 & 12 \\
  \end{array}\right) =   \left(\begin{array}{cc}
  12 & 78 \\
  78 & 650 \\
  \end{array}\right)$$`
  
Temos ainda que:
  
`$$A^{t}b = \left(\begin{array}{cc}
  1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 & 1 \\
  1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 & 9 & 10 & 11 & 12 \\
  \end{array}\right) \left(\begin{array}{c}
  876 \\
  819 \\
  834 \\
  796 \\
  783 \\
  692 \\
  696 \\
  602 \\
  639 \\
  620 \\
  561 \\
  556 \\
  \end{array}\right) = 
  \left(\begin{array}{c}
  8474 \\
  50749 \\
  \end{array}\right)$$`
  
Agora escalonamos a matriz:

`$$\left(\begin{array}{cc|c}
  78 & 650 & 50749 \\
  12 & 78 & 8474 \\
  \end{array}\right) = \left(\begin{array}{cc|c}
  0 & 1 & -30.29 \\
  1 & 0 & 903.07 \\
  \end{array}\right)$$`
  
Logo temos a nossa reta y = -30.29x + 903.07




<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />
