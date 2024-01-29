---
title: "Resumo sobre Autovalores e Autovetores"
subtitle: ""
excerpt: "Resumo sobre Álgebra Linear com visualização!"
date: 2024-01-28
author: "Diogo Vieri"
draft: false
images:
series:
tags:
categories:
  - Álgebra Linear
  - R
layout: single
---


# Capítulo 6 - Autovetores e Autovalores

## Autovetores e Autovalores

`\(\text{Um } \textbf{autovetor} \text{ de uma matriz n x n, é um vetor não nulo x tal que }Ax=\lambda x \text{ para algum escalar }\lambda. \lambda \text{ será chamado de }\textbf{autovalor}\text{ para A.}\)`

`\(\text{Vamos verificar o que são autovetores geométricamente:}\)`

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-1-1.png" width="672" />

`\(\text{Geométricamente temos que um autovetor mesmo após aplicar a transformação matricial ele irá continar}\)`
`\(\text{na mesma direção alterando apenas o comprimento e sentido!}\)`

`\(\text{O comprimento e sentido será alterado por um multiplo, esse multiplo é o autovalor!}\)`

`\(\text{Em geral os exercícios irão pedir para verificar se é um autovalor ou autovetor}\)`
`\(\text{Para autovalor basta usar a seguinte fórmula: }(A-\lambda I)x=0\)`

`\(\text{Verifique se }\lambda \text{=7 é um autovalor para A:}\)`
`$$A = \left(\begin{array}{cc}
  1 & 6 \\
  5 & 2 \\
  \end{array}\right) e, \lambda=7 =>
  \left(\begin{array}{cc}
  1 & 6 \\
  5 & 2 \\
  \end{array}\right) - \left(\begin{array}{cc}
  7 & 0 \\
  0 & 7 \\
  \end{array}\right) = 
  \left(\begin{array}{cc}
  -6 & 6 \\
  5 & -5 \\
  \end{array}\right)$$`
`$$\text{Escalonando} = 
  \left(\begin{array}{cc|c}
  -6 & 6 & 0\\
  5 & -5 & 0\\
  \end{array}\right) = 
    \left(\begin{array}{cc|c}
  1 & -1 & 0\\
  0 & 0 & 0\\
  \end{array}\right)$$`
`\(\text{Temo que as colunas são Linearmente Dependentes pois não há pivo em cada coluna, logo é autovalor!}\)`

`\(\text{Para mostrar que é autovetor é simples basta multiplicar A pelo autovetor!}\)`

`\(\text{Considerando a matriz A, verifique se o vetor v = (1,1) é autovetor de A:}\)`
`$$A = \left(\begin{array}{cc}
  1 & 6 \\
  5 & 2 \\
  \end{array}\right) , v = 
  \left(\begin{array}{cc}
  1 \\
  1  \\
  \end{array}\right) =
  \left(\begin{array}{cc}
  7  \\
  7  \\
  \end{array}\right) =
  \left(\begin{array}{cc}
  1 \\
  1  \\
  \end{array}\right) * 7$$`
  
`\(\text{É fácil de ver gráficamente que v é um autovetor de A, que mesmo após aplicar a transformação linear,}\)`
`\(\text{continua crescendo na mesma direção mas com tamanho diferente (multiplicado pelo autovalor 7), enquanto os demais trocam de direção}\)`

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-1.png" width="672" />

`\(\text{Como veremos futuramente o 7 não é o único autovalor para essa matriz temos ainda o -4:}\)`

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

`\(\text{Verifique se v é autovetor de A:}\)`
`$$A =\left(\begin{array}{ccc}
  1 & -1 & 2\\
  4 & -3 & 1\\
  -1 & 4 & -1 \\
  \end{array}\right), v=
  \left(\begin{array}{cc|c}
  1 \\
  1 \\
  1 \\
  \end{array}\right) =  
  \left(\begin{array}{ccc}
  1*1 & -1*1 & 2*1\\
  4*1 & -3*1 & 1*1\\
  -1*1 & 4*1 & -1*1 \\
  \end{array}\right) = 
  \left(\begin{array}{ccc}
  2 \\
  2 \\
  2 \\
  \end{array}\right) = 2 * 
  \left(\begin{array}{cc|c}
  1 \\
  1 \\
  1 \\
  \end{array}\right) = \lambda = 2$$`
  
`\(\text{Esse último exemplo foi retirado da lista do professor!}\)`

`\(\text{OBS: Em alguns exercício o professor gosta de combinar assuntos, como encontrar o espaço nulo que é o mesmo que fazer }Nul(A-I\lambda) \text{ e ver quantas colunas são L.I}\)`
`\(\text{Se a matriz A for triÂngular (haver valorez iguais a zero em baixo da diagonal ou em cima), os autovetores já são os da diagonal.}\)`
`\(\text{A só é inversivel se 0 não for um autovalor pra A.}\)`
`\(\text{Se (v1,v2,v3...) são autovetores associados a autovalores diferentes, então o conjunto (v1,v2,v3..) é LI.}\)`

## A Equação Característica

`\(\text{Em determinado momento da álgebra, estamos interessados em descobrir quais são todos os valores de }\lambda \text{ que estão associados a autovalores.}\)`
`\(\text{Para isso existe uma fórmula para acha-los:}\)`
$$ det(A-\lambda I ) $$

`\(\text{Vamos tentar com o exemplo anterior:}\)`
`$$A = \left(\begin{array}{cc}
  1 & 6 \\
  5 & 2 \\
  \end{array}\right), \lambda I= 
  \left(\begin{array}{cc}
  \lambda & 0 \\
  0 & \lambda \\
  \end{array}\right) = 
  det\left(\begin{array}{cc}
  1-\lambda & 6 \\
  5 & 2-\lambda \\
  \end{array}\right) = (1-\lambda)(2-\lambda)-6*5 = \lambda^{2} - 3\lambda - 28 = \lambda = 7 \text{ ou  } -4$$`
  
`\(\text{Perceba que a parte mais difícil é cálcular o determinante! não há necessidade de fazer escalonamente nem nada, apenas isso!}\)`

`\(\text{Vamos cálcular os autovalores para o exemplo do professor usado no item anterior:}\)`
`$$A =\left(\begin{array}{ccc}
  1 & -1 & 2\\
  4 & -3 & 1\\
  -1 & 4 & -1 \\
  \end{array}\right) = det(A-\lambda I ) = \lambda I=\left(\begin{array}{ccc}
  \lambda & 0 & 0\\
  0 & \lambda & 0\\
  0 & 0 & \lambda \\
  \end{array}\right) =
  det\left(\begin{array}{ccc}
  1-\lambda & -1 & 2\\
  4 & -3-\lambda & 1\\
  -1 & 4 & -1-\lambda \\
  \end{array}\right) =$$`
  
`$$=\text{Para cálcular det de 3x3} =
 \left(\begin{array}{ccc|cc}
  1-\lambda  & -1 & 2 & 1-\lambda & -1\\
  4 & -3-\lambda & 1 & 4 & -3-\lambda\\
  -1 & 4 & -1-\lambda & -1 & 4 \\
  \end{array}\right)$$`
  
`$$= [[(1-\lambda)(-3-\lambda)(-1-\lambda)]+[(-1)(1)(-1)]+[(2)(4)(4)]]-[[(2)(-3-\lambda)(-1)]+[(1-\lambda)(1)(4)]+[(-1)(4)(-1-\lambda)]] =$$`

`$$= -\lambda^{3} - 3\lambda^{2} - \lambda + 22$$`

`\(\text{Em geral para matriz 3x3 você vai cair em uma expressão do 3º grau!}\)`

`\(\text{Encontrando as raízes dessa equação temos que: }\lambda = 2\)`

## Diagonalização 

`\(\text{Diagonalizar uma matriz é tornar todos os elementos de uma matriz iguais a zero menos os da diagonal! Para isso usamos:}\)`

`$$PDP^-1 = A$$`

`\(\text{Onde A é a matriz original}\)`

`\(\text{Onde P é a matriz dos Autovetores}\)`

`\(\text{Onde D é a matriz dos Autovalores diagonalizada}\)`

`\(\text{Onde P}^{-1}\text{ é a matriz inversa de P}\)`

`\(\text{Vamos diagonalizar a matriz 2x2 da lista do professor:}\)`

`$$A = \left(\begin{array}{cc}
  -3 & 3 \\
  -2 & 4 \\
  \end{array}\right)$$`
  
`\(\text{Primeiro vamos encontrar os autovalores fazendo }(A-\lambda I) = (-3-\lambda)(4-\lambda)+6 = \lambda^{2}-\lambda-6 = \lambda = 3 \text{ ou } - 2\)`

`$$\text{Segue que D =}
\left(\begin{array}{cc}
  3 & 0 \\
  0 & -2 \\
  \end{array}\right)$$`
  
`\(\text{Segundo passo é achar a matriz dos autovetores P, temos 2 autovalores portanto vamos encontrar os autovetores associados:}\)`

`$$\text{Para }\lambda = 3: (A-\lambda I )x = 0 \implies 
\left(\begin{array}{cc}
  -3 & 3 \\
  -2 & 4 \\
  \end{array}\right) -
  \left(\begin{array}{cc}
  3 & 0 \\
  0 & 3 \\
  \end{array}\right) = 
  \left(\begin{array}{cc}
  -6 & 3 \\
  -2 & 1 \\
  \end{array}\right) \implies \text{Escalonar Sistema Homogêneo}$$`
  
$$ = \left(\begin{array}{cc}
  1 & \frac{-1}{2} \\
  0 & 0 \\
  \end{array}\right) = 
  \begin{cases}
  x & \frac{y}{2} \\
  y & livre \\
  \end{cases} = Ger\{(\frac{y}{2},y)\} = y({\frac{1}{2},1}) = \text{Autovetor associado a 3 é } ({\frac{1}{2},1}).$$`
  
`$$\text{Para }\lambda = -2: (A-\lambda I )x = 0 \implies 
\left(\begin{array}{cc}
  -3 & 3 \\
  -2 & 4 \\
  \end{array}\right) -
  \left(\begin{array}{cc}
  -2 & 0 \\
  0 & -2 \\
  \end{array}\right) = 
  \left(\begin{array}{cc}
  -1 & 3 \\
  -2 & 6 \\
  \end{array}\right) \implies \text{Escalonar Sistema Homogêneo}$$`
  
`$$= \left(\begin{array}{cc}
  1 & -3 \\
  0 & 0 \\
  \end{array}\right) = 
  \begin{cases}
  x & 3y \\
  y & livre \\
  \end{cases} = Ger\{(3y,y)\} = y({3,1}) = \text{Autovetor associado a -2 é } ({3,1}).$$`
  
`$$\text{Logo temos que P = }
\left(\begin{array}{cc}
  \frac{1}{2} & 3 \\
  1 & 1 \\
  \end{array}\right)$$`
  
`\(\text{Falta ainda cálcular a inversa de P: }\)`

`$$P^{-1} = \left(\begin{array}{cc|cc}
  \frac{1}{2} & 3 & 1 & 0\\
  1 & 1 & 0 & 1\\
  \end{array}\right) = 
  \left(\begin{array}{cc|cc}
  0 & 1 & \frac{-2}{5} & \frac{6}{5}\\
  0 & 1 & \frac{2}{5} & \frac{-1}{5}\\
  \end{array}\right) = P^{-1} = 
  \left(\begin{array}{cc}
  \frac{-2}{5} & \frac{6}{5}\\
  \frac{2}{5} & \frac{-1}{5}\\
  \end{array}\right)$$`
  
`$$\text{E finalmente temos: } PDP^{-1} = A  \implies \left(\begin{array}{cc} 
  \frac{1}{2} & 3 \\
  1 & 1 \\
  \end{array}\right) 
  \left(\begin{array}{cc}
  3 & 0 \\
  0 & -2 \\
  \end{array}\right)  
  \left(\begin{array}{cc}
  \frac{-2}{5} & \frac{6}{5}\\
  \frac{2}{5} & \frac{-1}{5}\\
  \end{array}\right)  = A$$`
  
`\(\text{Nem sempre uma matriz pode ser diagonolizada, quando a matriz dos autovetores tiver sua dimensão diferente da matriz A, não vai ser possível.}\)`

