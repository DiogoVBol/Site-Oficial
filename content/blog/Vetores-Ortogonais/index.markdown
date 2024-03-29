---
title: "Ortogonalidade e Mínimos quadráticos"
subtitle: ""
excerpt: "Resumo sobre Álgebra Linear com visualização do começo de estudo de Regressão Linear resolvido com matriz!!"
date: 2024-01-29
author: "Diogo Vieri"
draft: false
images:
series:
tags:
categories:
  - Álgebra Linear
  - R
  - Regressão Linear
  - Latec
layout: single
---


# 1 - Produto Interno, Comprimento e Ortogonalidade

## 1.1 - O Produto Interno:

`\(\text{Produto Interno tem por objetivo verificar se dois vetores são ortogonais entre si (ou seja, tem 90 graus)}\)`
`\(\text{para serem ortogonais o produto interno deve dar zero}\)`

$$ \text{Só sera ortogonal se e somente se: }<u \cdot v> = (v1 \times u1 + v2 \times u2 + v3\times u3...) = 0.$$

## 1.2 - O comprimento de um vetor

`\(\text{Como em cálculo, quando queremos encontrar o comprimento de um vetor, cálculamos a norma dele:}\)`

$$||u|| = \sqrt{u_1^{2}+u_2^{2}+u_3^{3}...} $$

`\(\text{Se o vetor tiver comprimento 1, chamamos de vetor unitário, para transformar qualquer vetor em unitário basta fazer:}\)`

$$\text{Vetor unitário = }\frac{1}{||u||} $$

## 1.3 - A distância entre vetores

`\(\text{A distância é denotada por dist(u,v) e cálculada por:}\)`

`$$dist(u,v) = ||u-v||$$`

## 1.4 - Vetores Ortogonais

`\(\text{Dois vetores só são ortogonais se e somente se o produto interno da zero, assim um conjunto ortogonal é um conjunto de vetores}\)`
`\(\text{que o produto interno entre eles é zero}\)`

`\(\text{Verifique se }Y = {(1, −1, 2, 0),(−4, 2, 3, −3),(−1, 1, 1, 3)} ⊆ R^{4} \text{ é um conjunto ortogonal}\)`

$$\text{Resposta: Aqui temos 3 vetores que fazem parte do } R^{4} \text{ temos, v1,v2 e v3. Para verificar se é um conjunto ortogonal, } $$

$$\text{fazemos: }v1 \cdot v2 \text{ e verificamos se da zero} $$

$$\text{em seguida: }v2 \cdot v3 \text{ e verificamos se da zero} $$

$$\text{por fim: }v1 \cdot v3 \text{ e verificamos se da zero} $$

## 1.5 - Complemento Ortogonal 

`\(\text{Para entender complemento Ortogonal é fundamental entender a noção de espaços e subespaços.}\)`

`\(\text{Imagine uma caixa e dentro desta caixa há outras duas menores: }\)` 

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-1-1.png" width="672" />
`\(\text{A caixa grande é um subespaço de } R^{n}\text{ enquanto as caixas menores são subespaços da caixa maior.}\)`

`\(\text{Quando pedir para cálcular um complemento ortogonal de um subespaço gerado por algum }Span,\text{(geralmente é dado os valores do Span)}\)`

`\(\text{devemos pensar que a caixa A é esse subespaço gerado e queremos encontrar qual a equação que gera a caixa B.}\)`

`\(\text{De maneira simples é isso, porém a caixa B tem que ter os valores dos vetores dela todos ortogonais,}\)`
`\(\text{aos valores dos vetores da caixa A, como assim?}\)`

`\(\text{Imagine que a Caixa A contém todos os valores que dão origem ao eixo X, logo } Span\{(1,0)\} = \{(a,0): a \in R\}\)`

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-2-1.png" width="672" />

`\(\text{O complemento Ortognal é todos os vetores do eixo Y pois TODOS eles são ortogonais a TODOS do eixo X:}\)`

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-3-1.png" width="672" />

O metodo para encontrar um complemento ortogonal é:

1) Será dado um subespaço como V = Span{(1,2,3),(2,3,4)}

2) Encotrar conjunto de equações que fazem parte do Span:

(1,2,3) = x + 2y + 3z 

(2,3,4) = 2x + 3y + 4z 

3) Resolva o sistema Homogêneo:

x + 2y + 3z = 0

2x + 3y + 4z = 0

4) Simplifique o resultado:

x = z

y = -2z

logo: (z,-2z,z) = z(1,-2,1) = Span{(1,-2,1)} Perceba que a dimensão do span é 1 enquanto a do V é 2, portando a dimensão em que ambos estão incluídos (Caixa Grande) = 2 + 1 = 3. 

# 2 - Projeções Ortogonais

## 2.1 - Vetor B-Coordenada

`\(\text{Seja W um subespaço do }R^{n}\text{ e se } \{u_1,u_2,...\} \text{ é uma base ortogonal para W,} \text{ para encontrar a projeção de um vetor sobre o outro, temos que: }\)`

$$y = \frac{y \cdot u_1}{u_1 \cdot u_1} , ... , \frac{y \cdot u_p}{u_p \cdot u_p} $$

`\(\text{Isso é o que o professor chama de achar o B-Coordenada de v, sendo v um vetor qualquer, o b-coordenada sempre vai ser}\)`
`\(\text{um vetor não um número, exemplo:}\)`

`\(\text{Considere }B = {(1, 1, 1),(1, −2, 1),(1, 0, −1)} ⊆ R^{3}, v = (4, 6, 2) ∈ R\)`

`\(\text{Aqui temos que B tem 3 vetores, cada vetor na fórmula será representado por u. Então para cálcular o b-coordenada de v temos que:}\)`

`\(y = v = (4,6,2), u_1 = (1,1,1), u_2 = (1,-2,1),u_3 = (1,0,-1)\)`

# 3 - O Processo de Gram - Schmidt

## 3.1 - Algoritmo para Gram - Schmidt

`\(\text{Esse processo é usado para encontrar uma base ortogonal para qualquer subespaço de }R^{n}\)`

`\(\text{Desde já, tenha cuidado para não confundir com a fórmula usada em 2.1, já que são muito semelhantes.}\)`
`\(\text{O problema anterior trata de encontrar um vetor B-Coordenada, o de agora é de achar uma base ortogonal para um Subespaço!!}\)`

`$$\text{Dada uma base }\{x_1,x_2,... \} \text{ para um subespaço W, defina: }$$`

`$$w_1 = x_1$$` 

`$$w_2 = x_2 - \frac{x_2 \cdot w_1}{w_1 \cdot w_1}$$`

`$$w_3 = x_3 - \frac{x_3 \cdot w_1}{w_1 \cdot w_1}w_1 - \frac{x_3 \cdot w_2}{w_2 \cdot w_2}w_2$$`

`$$\cdot \cdot \cdot w_p = x_p - \frac{x_p \cdot w_1}{w_1 \cdot w_1}w_1-\frac{x_p \cdot w_2}{w_2 \cdot w_2}w_2...-\frac{x_p \cdot w_{p-1}}{w_{p-1} \cdot w_{p-1}}w_{p-1}$$`

`\(\text{Então }\{v_1,v_2...v_n\} \text{ é uma base ortogonal para W. Além disso o }Span\{v_1,v_2...v_k\} \text{ e } Span\{x_1,x_2...x_k\} \text{ são iguais para }1 \leq k \leq p.\)`

`\(\text{Exemplo Lista  7 ex. 8:}\)`

`\(\text{Considere os vetores v1 = (0, 4, 2), v2 = (5, 6, −7) e v3 = (4, −1, 2). A letra a pede para mostrar que é uma base.}\)`

`\(\text{Vamos assumir que já foi feito isso e ir para letra b.}\)`

`\(\text{b) Use o algoritmo de Gram-Schmidt para obter uma base ortogonal de R3, a partir da base B.}\)`

`$$\text{Aplicando a fórmula: }$$`

`$$w_1 = v_1 = (0,4,2)$$`

`$$w_2 = v_2 - \frac{v_2 \cdot w_1}{w_1 \cdot w_1}w_1 = (5,6,-7) - \frac{(5,6,-7) \cdot (0,4,2)}{(0,4,2) \cdot (0,4,2)}(5,6,-7)$$`

`$$= (5,6,-7) - \frac{10}{20} (5,6,-7) =  (5,6,-7) - (\frac{5}{2},3,\frac{-7}{2}) = w_2 =(\frac{5}{2},3,\frac{-7}{2})$$`

`$$w_3 = (4, −1, 2) - \frac{(4, −1, 2) \cdot (0,4,2)}{(0,4,2) \cdot (0,4,2)}(0,4,2) - \frac{(4, −1, 2) \cdot (\frac{5}{2},3,\frac{-7}{2})}{(\frac{5}{2},3,\frac{-7}{2}) \cdot (\frac{5}{2},3,\frac{-7}{2})}(\frac{5}{2},3,\frac{-7}{2})$$`

## 3.2 - Bases Ortonormais 

`\(\text{Para construir uma base Ortonormal basta ter a base ortogonal e fazer:}\)`

`$$\text{dado uma base Ortogonal }\{v_1,v_2,...v_n\}: u_1 = \frac{1}{||v_1||}v_1, u_2 = \frac{1}{||v_2||}v_2...$$`

# 4 - Problemas de Mínimos Quadráticos

`\(\text{O problema é semelhante a achar uma reta de regressão linear. Imagine que é um pesquisador e encontrou os seguintes dados:}\)`

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-4-1.png" width="672" />

`\(\text{O problema de minimizar é descobrir qual a reta que mais se aproxíma para explicar a dispersão dos dados.}\)`

`\(\text{Temos os seguintes dados:}\)`


`$$\left(\begin{array}{cc}
x & y \\
0 & 0 \\
1 & 2 \\
2 & 5 \\
\end{array}\right)$$`


`\(\text{Ou seja:}\)`


`$$\left(\begin{array}{c}
y(0)=a+b.0=0 \\
y(1)=a+b.1=2 \\
y(2)=a+b.2=5 \\
\end{array}\right)$$`


`\(\text{Dito isso de outra forma, precisamos resolver o sistema:}\)`


`$$\begin{cases}
  1a+0b=0 \\
  1a+1b=2 \\
  1a+2b=5 \\
\end{cases}$$`


`$$A = \left(\begin{array}{cc}
    1  & 0 \\
    1  & 1\\
    1  & 2\\
\end{array}\right)b = \left(\begin{array}{cc}
    0   \\
    2  \\
    5  \\
\end{array}\right)$$`

`\(\text{Logo, basta resolver esse sistema, porém segundo Definição 7.4.2, usada pelo professor}\)`

`\(\text{iremos chamar de solução para mínimos quadrados toda solução do sistema de equações lineares } Ax = proj_{col A}b\)`

`$$\text{Vamos usar a fórmula: }proj_{col A}b = (A^{t}A)x=A^{t}b$$`

`$$A^{t}A= \left(\begin{array}{cc}
  1 & 1 & 1 \\
  0 & 1 & 2 \\
\end{array}\right) \left(\begin{array}{cc}
  1 & 0  \\
  1 & 1  \\
  1 & 2 \\
\end{array}\right) = \left(\begin{array}{cc}
  3 & 3  \\
  3 & 5  \\
\end{array}\right)$$`

`\(\text{Lembre-se para cálcular essa multiplicação faça todos elementos da primeira linha }\)`

`\(\text{da primeira matriz vezes a primeira coluna da segunda matriz...}\)`

`$$A^{t}b= \left(\begin{array}{cc}
  1 & 1 & 1 \\
  0 & 1 & 2 \\
\end{array}\right) \left(\begin{array}{cc}
  0  \\
  2  \\
  5 \\
\end{array}\right) = \left(\begin{array}{cc}
  7  \\
  12  \\
\end{array}\right)$$`

`$$\text{Logo temos que: }
(A^{t}A)x=A^{t}b = \left(\begin{array}{cc}
  3 & 3  \\
  3 & 5  \\
\end{array}\right) \left(\begin{array}{cc}
  a  \\
  b  \\
\end{array}\right) = \left(\begin{array}{cc}
  7  \\
  12  \\
\end{array}\right) = \left(\begin{array}{cc}
  \frac{5}{12}  \\
  \frac{-1}{6}  \\
\end{array}\right)$$`

`\(\text{Assim temos a seguinte fórmula que explica os dados: }y(x) = \frac{5x}{2}-\frac{1}{6}\)`

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-5-1.png" width="672" />

`\(\text{Exemplo com equação Quadrática: }\)`

`\(\text{Ache a equação que mais se aproxíme de descrever os dados:}\)`

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-6-1.png" width="672" />

`\(\text{Portando a matriz que representa os dados é: }\)`

`$$\text{Logo temos que: }\left(\begin{array}{cc}
  x & y  \\
  2 & 0  \\
  3 & -10  \\
  5 & -48 \\
  6 & -76 \\
\end{array}\right)$$`

`\(\text{Supondo que o gráfico deste polinômio passe exatamente sobre os pontos dados, }\)`
`\(\text{então queremos encontrar coeficientes a, b, c ∈ R tais que os pontos (2,p(2)),(3, p(3)),(5, p(5)) e (6, p(6))}\)`

`\(\text{sejam pontos do gráfico da função polinomial definida pelo polinômio p(t) = c + bt + }at^{2}.\)`
`\(\text{Equivalentemente, queremos uma solução de mínimos quadrados do sistema de equações:}\)`

`$$\begin{cases}
  y(x) = 4a + 2b + c = 0  \\
  y(x) = 9a + 3b + a = -10  \\
  y(x) = 25a + 5b + c = -48\\
  y(x) = 36a + 6b + c = -76 \\
\end{cases}$$`

`\(\text{Escrevendo em forma de matriz:}\)`

`$$\left(\begin{array}{cc}
  4 & 2 & 1  \\
  9 & 3 & 1  \\
  25 & 5 & 1 \\
  36 & 6 & 1 \\
\end{array}\right) 
\left(\begin{array}{cc}
  a  \\
  b  \\
  c \\
\end{array}\right) =
\left(\begin{array}{cc}
  0  \\
  -10  \\
  -48 \\
  -76 \\
\end{array}\right)$$`

`\(\text{Usando a fórmula para cálcular a equação que mais se aproxíma: }proj_{col A}b = (A^{t}A)x=A^{t}b\)`

`$$(A^{t}A) =  \left(\begin{array}{cc}
  4 & 9 & 25 & 36  \\
  2 & 3 & 5 & 6 \\
  1 & 1 & 1 & 1 \\
\end{array}\right) \left(\begin{array}{cc}
  4 & 2 & 1  \\
  9 & 3 & 1  \\
  25 & 5 & 1 \\
  36 & 6 & 1 \\
\end{array}\right) = \left(\begin{array}{cc}
  2018 & 376 & 74 \\
  376 & 74 & 16  \\
  74 & 16 & 4\\
\end{array}\right)$$`

`$$A^{t}b = \left(\begin{array}{cc}
  4 & 9 & 25 & 36  \\
  2 & 3 & 5 & 6 \\
  1 & 1 & 1 & 1 \\
\end{array}\right) 
\left(\begin{array}{cc}
  0  \\
  -10  \\
  -48 \\
  -76 \\
\end{array}\right) = 
\left(\begin{array}{cc}
  -4026\\
  -726 \\
  -134 \\
\end{array}\right)$$`

`$$Logo = \left(\begin{array}{cc}
  2018 & 376 & 74 \\
  376 & 74 & 16  \\
  74 & 16 & 4\\
\end{array}\right)  
\left(\begin{array}{cc}
  x \\
  y \\
  z \\
\end{array}\right) =
\left(\begin{array}{cc}
  -4026\\
  -726 \\
  -134 \\
\end{array}\right) =
\left(\begin{array}{ccc|c}
  1 & 0 & 0 & -3\\
  0 & 1 & 0 & 5\\
  0 & 0 & 1 & 2\\
\end{array}\right)$$`

`\(\text{Assim temos que a = -3, b= 5 e c = 2, formando a seguinte equação:}\)`

`$$\text{p(t) = c + bt + }at^{2} =  2 + 5t - 3t^2$$`

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-7-1.png" width="672" />

## Erro de mínimos Quadrados

`\(\text{Atravez do cálculo do erro de mínimo quadrado podemos ver se a matriz é compatível ou não: }\)`

`$$\text{Erro de Mínimo = ||b - Ax||}$$`

`\(\text{onde b é matriz com os valores de y e A é a matriz A e x o resultado que é usado para construir a reta}\)`

`\(\text{Perceba que o x é o valor que você encontra para fazer as retas (a,b,c)}\)`

`\(\text{Vamos cálcular o erro para o exercício anterior:}\)`


`$$||b - Ax|| = 
\left(\begin{array}{ccc|c}
  0\\
  -10\\
  -48\\
  -76 \\
\end{array}\right) - 
\left(\begin{array}{cc}
  4 & 2 & 1  \\
  9 & 3 & 1  \\
  25 & 5 & 1 \\
  36 & 6 & 1 \\
\end{array}\right)
\left(\begin{array}{ccc|c}
  -3\\
  5\\
  2\\
\end{array}\right) = \left(\begin{array}{ccc|c}
  0\\
  -10\\
  -48\\
  -76 \\
\end{array}\right) - 
\left(\begin{array}{ccc|c}
  0\\
  -10\\
  -48\\
  -76 \\
\end{array}\right) = 0$$`

`\(\text{e, consequentemente, o erro de mínimos quadrados é nulo, pois }Ax = b, \text{ou seja } ||Ax = b|| = 0.\)`
`\(\text{ E portanto, o gráfico da função polinomial } f(t) = 2 + 5t − 3t^{2} \text{ passa exatamente sobre os pontos dados}\)`

`\(\text{E para o primeira exercício temos que:}\)`


`$$||b - Ax|| =  \left(\begin{array}{cc}
  0   \\
  2   \\
  5  \\
\end{array}\right) -
\left(\begin{array}{cc}
  1 & 0  \\
  1 & 1  \\
  1 & 2 \\
\end{array}\right)
\left(\begin{array}{cc}
  \frac{5}{12}  \\
  \frac{-1}{6}  \\
\end{array}\right) 
=$$`

`$$\left(\begin{array}{cc}
  0   \\
  2   \\
  5  \\
\end{array}\right) - \left(\begin{array}{cc}
  \frac{5}{12}   \\
  \frac{1}{4}    \\
  \frac{1}{12}   \\
\end{array}\right)  = 
||\left(\begin{array}{cc}
  \frac{-5}{12}   \\
  \frac{7}{4}    \\
  \frac{59}{12}   \\
\end{array}\right)|| = 5.23$$`

