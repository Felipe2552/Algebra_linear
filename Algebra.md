# Álgebra Linear: Notas de Estudo

Início: 03/10/2026 · Revisado e organizado em 19/10/2026

> **Como usar:** as partes marcadas com ★ foram acrescentadas para completar seções que estavam em branco (adjunta, sistemas lineares) e reforçar a revisão (erros comuns, exercícios, ligação com bioinformática). As correções feitas nas anotações estão listadas no fim.

## Mapa do conteúdo

| Unidade | Tema | Ideia central |
|:----|:---------|:-----------------------|
| 1 | Matrizes e vetores | Organizar dados numéricos e operar elemento a elemento |
| 2 | Outras operações | Produto, transposta e inversa |
| 3 | Determinantes | Um número que diz se a matriz tem inversa |
| 4 | Sistemas lineares | Resolver $A\cdot x=b$ |
| 5 | Aplicações | Grafos, Markov e mínimos quadrados |

---

## Unidade 1: Matrizes e Vetores

Vetores e matrizes são **estruturas matemáticas usadas para organizar, armazenar e manipular conjuntos de dados numéricos** dispostos em uma ou mais dimensões.

### 1. Vetores ($v$ ou $\bar{v}$)

Um vetor é uma sequência **unidimensional e ordenada** de elementos (componentes). Pode fazer parte de matrizes.

Dois vetores são iguais quando têm a mesma quantidade de componentes e todas as componentes correspondentes são iguais, na mesma ordem.

A **ordem dos componentes importa**: $[v_1, v_2, v_3] \neq [v_3, v_2, v_1]$.

Os vetores podem ser classificados em vetores **linha** ou **coluna**:

- **Vetor linha:** $v = [v_1, v_2, \dots, v_n]$
- **Vetor coluna:**

$$v = \begin{bmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{bmatrix}$$

### 1.1 Operações com vetores

- **Igualdade:** sejam $u = [u_1, \dots, u_n]$ e $v = [v_1, \dots, v_n]$. Então $u = v$ se, e somente se, $u_1 = v_1,\ u_2 = v_2,\ \dots,\ u_n = v_n$.
- **Adição (componente a componente):** $u + v = [u_1+v_1, \dots, u_n+v_n]$. Só é possível entre vetores do mesmo tipo (linha com linha, coluna com coluna) e com o mesmo número de componentes.
- **Subtração:** igual, trocando a soma pela diferença.
- **Multiplicação por escalar (número real):** $\alpha\cdot[u_1, \dots, u_n] = [\alpha u_1, \dots, \alpha u_n]$.

**Exemplos**

*Adição e subtração entre vetores:*

$$
\begin{bmatrix} 2 \\ -1 \\ 0 \end{bmatrix} + \begin{bmatrix} 3 \\ 2 \\ 2 \end{bmatrix} = \begin{bmatrix} 5 \\ 1 \\ 2 \end{bmatrix}
\qquad
\begin{bmatrix} -3 \\ 2 \\ 0 \end{bmatrix} - \begin{bmatrix} -1 \\ 1 \\ 2 \end{bmatrix} = \begin{bmatrix} -2 \\ 1 \\ -2 \end{bmatrix}
$$

*Multiplicação por escalar:* multiplica-se o escalar $\alpha$ por cada componente.

$$2\cdot[8, 3, 6] = [16, 6, 12]$$

### 1.2 Propriedades das operações de vetores

| Propriedade | Adição | Multiplicação por escalar |
|:-----------|:-----------------|:-----------------|
| **Comutativa** (dois elementos) | $u + v = v + u$ | $\alpha\cdot u = u\cdot\alpha$ |
| **Associativa** (mais de dois elementos) | $(u + v) + w = u + (v + w)$ | $\alpha\cdot(\beta\cdot u) = (\alpha\cdot\beta)\cdot u$ |
| **Elemento neutro** | $u + 0 = u$ | $1\cdot u = u$ |
| **Elemento oposto** | $u + (-u) = 0$ (vetor nulo) | não se aplica |
| **Distributiva** | $\alpha\cdot(u + v) = \alpha\cdot u + \alpha\cdot v$ | $(\alpha + \beta)\cdot u = \alpha\cdot u + \beta\cdot u$ |

Na coluna da adição, a distributiva é um escalar multiplicando a soma de vetores. Na coluna da multiplicação por escalar, é um vetor sendo multiplicado pela soma de escalares.

### 2. Matrizes (2D)

Pode ser entendida como uma **tabela retangular** de números, $A = [a_{ij}]$, de dimensão (tamanho) $m \times n$ ($m$ linhas, $n$ colunas). O elemento $a_{ij}$ está na linha $i$ e na coluna $j$. Uma matriz pode ser vista como um conjunto de vetores (linhas ou colunas), por isso suas operações estendem as dos vetores.

### 2.1 Classificação das matrizes pelo tamanho

- **Matriz linha:** tem uma única linha, ou seja, $m = 1$. Sua dimensão é $1 \times n$.
- **Matriz coluna:** tem uma única coluna, ou seja, $n = 1$. Sua dimensão é $m \times 1$.
- **Matriz quadrada:** mesmo número de linhas e colunas ($m = n$). O valor de $n$ é a **ordem** da matriz.
- **Matriz retangular:** o número de linhas é diferente do número de colunas.

### 2.2 Diagonais principal e secundária de uma matriz quadrada

Considere uma matriz quadrada de ordem 3:

$$A = \begin{bmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23} \\ a_{31} & a_{32} & a_{33} \end{bmatrix}$$

- **Diagonal principal:** elementos com $i = j$ ($a_{11}, a_{22}, a_{33}$).
- **Diagonal secundária:** elementos com $i + j = n + 1$. Para saber a posição dos elementos, basta somar a ordem da matriz com 1. Aqui $n + 1 = 4$, e os elementos com $i + j = 4$ são $a_{13}, a_{22}, a_{31}$.

### 2.3 Classificação das matrizes pelas características de seus elementos

- **Matriz diagonal:** matriz quadrada com todos os elementos fora da diagonal principal iguais a zero.
- **Matriz nula:** matriz com todos os elementos iguais a 0.
- **Matriz identidade ($I$):** matriz com 1 na diagonal principal e 0 nos demais elementos.
- **Matriz triangular inferior:** quadrada, com zeros acima da diagonal principal.
- **Matriz triangular superior:** quadrada, com zeros abaixo da diagonal principal.

### 2.4 Operações com matrizes

As matrizes podem ser entendidas como um conjunto de vetores, então as operações observadas em vetores podem ser estendidas para matrizes.

- **Igualdade:** mesma dimensão e elementos correspondentes iguais.

$$\begin{bmatrix} 3 & 7 \\ 1 & 0 \end{bmatrix} = \begin{bmatrix} 3 & a \\ 1 & 0 \end{bmatrix} \iff a = 7$$

- **Adição e subtração:** exigem matrizes de mesma dimensão.

$$\begin{bmatrix} 1 & 7 \\ 2 & 1 \end{bmatrix} + \begin{bmatrix} 5 & -3 \\ 0 & 1 \end{bmatrix} = \begin{bmatrix} 6 & 4 \\ 2 & 2 \end{bmatrix}$$

$$\begin{bmatrix} 4 & 1 & 3 \\ 8 & 0 & 2 \end{bmatrix} - \begin{bmatrix} 1 & 2 & 3 \\ 2 & 1 & 6 \end{bmatrix} = \begin{bmatrix} 3 & -1 & 0 \\ 6 & -1 & -4 \end{bmatrix}$$

- **Multiplicação por escalar:**

$$2\cdot\begin{bmatrix} 3 & 2 \\ -1 & 9 \end{bmatrix} = \begin{bmatrix} 6 & 4 \\ -2 & 18 \end{bmatrix}$$

### 2.5 Propriedades das operações com matrizes

| Propriedade | Adição | Multiplicação por escalar |
|:-----------|:-----------------|:-----------------|
| **Comutativa** (dois elementos) | $A + B = B + A$ | $\alpha\cdot A = A\cdot\alpha$ |
| **Associativa** (mais de dois elementos) | $(A + B) + C = A + (B + C)$ | $\alpha\cdot(\beta\cdot A) = (\alpha\cdot\beta)\cdot A$ |
| **Elemento neutro** | $A + 0 = A$ (0 é a matriz nula) | $1\cdot A = A$ |
| **Elemento oposto** | $A + (-A) = 0$ (matriz nula) | não se aplica |
| **Distributiva** | $\alpha\cdot(A + B) = \alpha\cdot A + \alpha\cdot B$ | $(\alpha + \beta)\cdot A = \alpha\cdot A + \beta\cdot A$ |

---

## Unidade 2: Outras operações com matrizes

### 1. Multiplicação entre matrizes

**a) Produto interno (escalar) entre vetores:** $u\cdot v = u_1v_1 + \dots + u_nv_n$. **O produto resulta em um número.**

*Exemplo:*

$$[2,\ -1,\ 3]\cdot[1,\ 4,\ 2] = 2\cdot 1 + (-1)\cdot 4 + 3\cdot 2 = 4$$

**b) Produto entre matrizes.** Só é possível se o número de colunas de $A$ for igual ao número de linhas de $B$:

$$(m \times n)\cdot(n \times p) = (m \times p)$$

As linhas e as colunas são consideradas vetores, o que permite a aplicação do produto interno entre vetores. **O produto entre matrizes resulta em uma nova matriz.** Cada elemento $c_{ij}$ é o produto interno da linha $i$ de $A$ pela coluna $j$ de $B$.

*Exemplo:* o produto **não é comutativo**.

$$
\begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}\begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix} = \begin{bmatrix} 2 & 1 \\ 4 & 3 \end{bmatrix}
\qquad
\begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}\begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} = \begin{bmatrix} 3 & 4 \\ 1 & 2 \end{bmatrix}
$$

**Propriedades da multiplicação entre matrizes**

Sejam $A\,(m\times n)$, $B\,(n\times p)$ e $C\,(p\times r)$ matrizes e $\alpha$ um escalar, com dimensões compatíveis para que as operações existam.

**1. Associativa**

- $(AB)C = A(BC)$: a matriz resultante tem dimensões $m \times r$.
- $(\alpha A)B = A(\alpha B) = \alpha(AB)$: a matriz resultante tem dimensões $m \times p$.

**2. Distributiva**

- À esquerda: $A(B + C) = AB + AC$
- À direita: $(A + B)C = AC + BC$

**3. Elemento neutro:** a matriz identidade $I$ é o elemento neutro da multiplicação entre matrizes. Assim, $AI = IA = A$.

### 2. Matriz transposta

A matriz transposta ($A^T$) é obtida trocando linhas por colunas. Se $A$ é $m \times n$, $A^T$ é $n \times m$.

*Exemplo:*

$$A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \end{bmatrix} \qquad A^T = \begin{bmatrix} 1 & 4 \\ 2 & 5 \\ 3 & 6 \end{bmatrix}$$

### 2.1 Matriz simétrica

Matriz quadrada igual à sua transposta ($A = A^T$).

*Exemplo:*

$$A = \begin{bmatrix} 1 & 2 & 3 \\ 2 & 4 & 5 \\ 3 & 5 & 6 \end{bmatrix} = A^T$$

### 2.2 Propriedades da matriz transposta

- $(A^T)^T = A$
- $(A \pm B)^T = A^T \pm B^T$
- $(AB)^T = B^TA^T$ (a ordem se inverte)
- $(\alpha A)^T = \alpha\cdot A^T$
- $A^TA$ e $AA^T$ são sempre simétricas
- Se $A$ é quadrada, $A + A^T$ é simétrica

### 2.3 Importância da matriz transposta

- **Fazer o produto existir:** transpor uma matriz pode fazer as dimensões "encaixarem" para multiplicar.
- **Calcular comprimentos:** $v^Tv$ dá o quadrado do comprimento de um vetor.
- **Identificar matrizes especiais:** simétrica ($A^T = A$), antissimétrica ($A^T = -A$) e ortogonal ($A^TA = I$).
- **Ajustar dados:** o método dos mínimos quadrados usa $(A^TA)x = A^Tb$.
- **Resolver exercícios:** a regra $(AB)^T = B^TA^T$ aparece muito em provas.

### 3. Operações elementares (importantes para o estudo de matriz inversa)

Transformam uma matriz em outra mais simples (forma escalonada), preservando as soluções de um sistema e o posto.

- **Permutar duas linhas:** $L_2 \leftrightarrow L_3$
- **Multiplicar uma linha por um real diferente de zero:** $L_3 \to 2\cdot L_3$
- **Somar a uma linha outra linha multiplicada por um real:** $L_1 \to L_1 + 3\cdot L_2$

*Exemplo:*

$$\begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} \xrightarrow{\,L_2 \to L_2 - 3L_1\,} \begin{bmatrix} 1 & 2 \\ 0 & -2 \end{bmatrix}$$

### 4. Matriz inversa ($A^{-1}$)

- **Definição:** seja $A$ uma matriz quadrada de ordem $n$. Se existe uma matriz $B$, também de ordem $n$, tal que $A\cdot B = B\cdot A = I$, onde $I$ é a matriz identidade de ordem $n$, então $B$ é a matriz inversa de $A$. Ela é indicada por $A^{-1}$.
- **Condição de existência:**
    - Só matrizes quadradas podem ter inversa.
    - A matriz $A$ tem inversa se, e somente se, $\det A \neq 0$. Nesse caso, $A$ é chamada de invertível (ou não singular).
    - Se $\det A = 0$, $A$ é singular e não tem inversa.
    - A inversa é única: se existe, só há uma.
- **Por que precisamos dela:** não existe divisão de matrizes. Em $A\cdot x = b$, multiplicamos os dois lados por $A^{-1}$: $A^{-1}\cdot A\cdot x = A^{-1}\cdot b$, e como $A^{-1}\cdot A = I$ sobra $x = A^{-1}\cdot b$. Serve para resolver sistemas e desfazer transformações.
- **Propriedades:**
    - $(A^{-1})^{-1} = A$
    - $(AB)^{-1} = B^{-1}A^{-1}$ (ordem invertida)
    - $(A^T)^{-1} = (A^{-1})^T$
    - $\det(A^{-1}) = \dfrac{1}{\det A}$

#### Cálculo da inversa: Gauss-Jordan

Monta-se $[A \mid I]$ e aplicam-se operações elementares nas linhas até a esquerda virar a identidade $I$. A direita será $A^{-1}$.

*Exemplo:* $A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$

$$
\left[\begin{array}{cc|cc} 1 & 2 & 1 & 0 \\ 3 & 4 & 0 & 1 \end{array}\right]
\xrightarrow{L_2 \to L_2 - 3L_1}
\left[\begin{array}{cc|cc} 1 & 2 & 1 & 0 \\ 0 & -2 & -3 & 1 \end{array}\right]
$$

$$
\xrightarrow{L_2 \to -\frac{1}{2}L_2}
\left[\begin{array}{cc|cc} 1 & 2 & 1 & 0 \\ 0 & 1 & \frac{3}{2} & -\frac{1}{2} \end{array}\right]
\xrightarrow{L_1 \to L_1 - 2L_2}
\left[\begin{array}{cc|cc} 1 & 0 & -2 & 1 \\ 0 & 1 & \frac{3}{2} & -\frac{1}{2} \end{array}\right]
$$

Logo, $A^{-1} = \begin{bmatrix} -2 & 1 \\ \frac{3}{2} & -\frac{1}{2} \end{bmatrix}$.

#### Cálculo da inversa: pela adjunta

Serve para encontrar a matriz inversa $A^{-1}$ de uma matriz quadrada $A$ usando determinantes e cofatores, sem precisar de escalonamento.

$$A^{-1} = \frac{1}{\det A}\cdot \operatorname{adj}(A)$$

onde $\operatorname{adj}(A)$ é a transposta da matriz de cofatores. Para compreender o cálculo, precisamos entender alguns conceitos: menor complementar, cofator, matriz de cofatores e matriz adjunta.

**Limitação entre os métodos:** para matrizes grandes, o método da inversa pela adjunta é muito custoso, pois exige calcular muitos determinantes. Nesses casos, usa-se escalonamento (Gauss-Jordan) ou métodos numéricos, que são bem mais eficientes.

**Menor complementar ($M_{ij}$):** é o determinante da submatriz que sobra ao **eliminar a linha $i$ e a coluna $j$** de $A$.

*Exemplo:*

$$A = \begin{bmatrix} 1 & 2 & 3 \\ 4 & 5 & 6 \\ 7 & 8 & 10 \end{bmatrix}$$

Para $M_{11}$, remove-se a linha 1 e a coluna 1, sobrando $\begin{bmatrix} 5 & 6 \\ 8 & 10 \end{bmatrix}$:

$$M_{11} = 5\cdot 10 - 6\cdot 8 = 2$$

**Cofator ($C_{ij}$):** é o menor complementar com o sinal ajustado:

$$C_{ij} = (-1)^{i+j}\cdot M_{ij}$$

O sinal segue o padrão de tabuleiro (+ quando $i + j$ é par, − quando é ímpar):

$$\begin{bmatrix} + & - & + \\ - & + & - \\ + & - & + \end{bmatrix}$$

No exemplo: $C_{11} = (+1)\cdot 2 = 2$.

**Matriz de cofatores ($C$):** é a matriz formada por **todos os cofatores**, cada um na posição do elemento correspondente: $C = [C_{ij}]$. No exemplo, calculando os nove cofatores:

$$C = \begin{bmatrix} 2 & 2 & -3 \\ 4 & -11 & 6 \\ -3 & 6 & -3 \end{bmatrix}$$

**Matriz adjunta ($\operatorname{adj} A$):** é a **transposta da matriz de cofatores**, $\operatorname{adj}(A) = C^T$. No exemplo:

$$\operatorname{adj}(A) = \begin{bmatrix} 2 & 4 & -3 \\ 2 & -11 & 6 \\ -3 & 6 & -3 \end{bmatrix}$$

Expandindo pela primeira linha, $\det A = 1\cdot 2 + 2\cdot 2 + 3\cdot(-3) = -3$. Como $\det A \neq 0$, a inversa existe:

$$A^{-1} = \frac{1}{-3}\begin{bmatrix} 2 & 4 & -3 \\ 2 & -11 & 6 \\ -3 & 6 & -3 \end{bmatrix} = \begin{bmatrix} -\frac{2}{3} & -\frac{4}{3} & 1 \\ -\frac{2}{3} & \frac{11}{3} & -2 \\ 1 & -2 & 1 \end{bmatrix}$$

---

## Unidade 3: Determinantes

- O determinante é um número associado a uma matriz quadrada $A = [a_{ij}]$ de ordem $n$.
- Pode ser representado por $\det A$, $\lvert A\rvert$ ou $\det[a_{ij}]$.
- É usado para verificar se a matriz tem inversa, resolver sistemas lineares e analisar propriedades de transformações.
- Os determinantes podem ser calculados por meio da **regra de Sarrus** e da **regra de Laplace**.

### 1. Regra de Sarrus

- A regra de Sarrus é utilizada para calcular determinantes de matrizes de **ordem 2 e 3**.
- Sarrus **não vale** para matrizes $4 \times 4$ ou maiores. Recomenda-se usar a regra de Laplace.
- Para matrizes de **ordem 2** ($2\times 2$), o determinante é o produto da diagonal principal menos o produto da diagonal secundária:

$$\det\begin{bmatrix} a & b \\ c & d \end{bmatrix} = ad - bc$$

- O cálculo para matrizes de **ordem 3** ($3\times 3$) é semelhante. Primeiro repetimos as duas primeiras colunas à direita da matriz. Depois somamos os produtos das 3 diagonais que descem para a direita e subtraímos a soma dos produtos das 3 que descem para a esquerda:

$$\det A = a_{11}a_{22}a_{33} + a_{12}a_{23}a_{31} + a_{13}a_{21}a_{32} - a_{13}a_{22}a_{31} - a_{11}a_{23}a_{32} - a_{12}a_{21}a_{33}$$

*Exemplo:* $B = \begin{bmatrix} 1 & 2 & 3 \\ 0 & 1 & 4 \\ 5 & 6 & 0 \end{bmatrix}$

$$\det B = (0 + 40 + 0) - (15 + 24 + 0) = 40 - 39 = 1$$

### 2. Regra de Laplace

- É outro modo de calcular o determinante e uma **alternativa para matrizes quadradas de ordem acima de 3**.
- Antes de ver como calcular por essa regra, é importante conhecer alguns conceitos:
    - **Submatriz:** matriz resultante após a eliminação de algumas linhas e/ou colunas.
    - **Menor complementar $M_{ij}$:** o determinante da submatriz obtida ao eliminar a linha $i$ e a coluna $j$ de uma matriz quadrada.
    - **Cofator:** é o menor complementar com sinal ajustado, $C_{ij} = (-1)^{i+j}\cdot M_{ij}$. O sinal é + quando $i + j$ é par e − quando é ímpar. Os sinais formam o padrão de tabuleiro.
- Para calcular o determinante de uma matriz quadrada por **Laplace**, escolhe-se uma linha (ou coluna) e expande-se o determinante em cofatores. Escolhendo a linha $i$:

$$\det A = \sum_{j=1}^{n} a_{ij}\,C_{ij}$$

### 3. Propriedades dos determinantes

| Propriedade | Exemplo |
|:-------------------|:------------------------------|
| (i) O valor do determinante é único, qualquer que seja o método | $A = \begin{bmatrix} 1 & 2 \\ 3 & 1 \end{bmatrix}$: pela definição, $1\cdot 1 - 2\cdot 3 = -5$; por Laplace na 1ª linha ou na 2ª coluna também dá $-5$ |
| (ii) Fila nula: $\det A = 0$ | $\begin{bmatrix} 4 & 7 \\ 0 & 0 \end{bmatrix}$: $4\cdot 0 - 7\cdot 0 = 0$ |
| (iii) Trocar duas filas muda o sinal do determinante | $\begin{bmatrix} 1 & 2 \\ 3 & 1 \end{bmatrix}$ tem det $-5$; trocando $L_1 \leftrightarrow L_2$ obtém-se $\begin{bmatrix} 3 & 1 \\ 1 & 2 \end{bmatrix}$, com det $5$ |
| (iv) Duas filas iguais ou proporcionais: $\det A = 0$ | $\begin{bmatrix} 1 & 4 \\ 3 & 12 \end{bmatrix}$ ($L_2 = 3L_1$): $12 - 12 = 0$ |
| (v) Multiplicar uma fila por $\alpha$ multiplica o det por $\alpha$ | $\begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$ tem det $-2$; $L_1 \times 5$ dá $\begin{bmatrix} 5 & 10 \\ 3 & 4 \end{bmatrix}$, com det $-10 = 5\cdot(-2)$ |
| (vi) $\det(\alpha A) = \alpha^n\cdot\det A$, com $n$ a ordem de $A$ | $A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix}$, $\alpha = 3$: $\det(3A) = 36 - 54 = -18 = 3^2\cdot(-2)$ |
| (vii) $\det A = \det(A^T)$ | $\begin{bmatrix} 2 & 3 \\ 1 & 4 \end{bmatrix}$ e sua transposta têm det $5$ |
| (viii) $A$ é invertível se, e somente se, $\det A \neq 0$ | $\begin{bmatrix} 2 & 1 \\ 5 & 3 \end{bmatrix}$ tem det $1$ e inversa $\begin{bmatrix} 3 & -1 \\ -5 & 2 \end{bmatrix}$; $\begin{bmatrix} 2 & 4 \\ 1 & 2 \end{bmatrix}$ tem det $0$ e não tem inversa |
| (ix) $\det(A^{-1}) = \dfrac{1}{\det A}$ | $B = \begin{bmatrix} 3 & 1 \\ 2 & 2 \end{bmatrix}$, det $4$. $B^{-1} = \dfrac{1}{4}\begin{bmatrix} 2 & -1 \\ -2 & 3 \end{bmatrix}$ tem det $\dfrac{1}{4}$ |

### 4. Matriz inversa com o uso de determinantes

**Matriz de cofatores:** é a matriz formada por todos os cofatores, cada um na posição do elemento correspondente: $C = [C_{ij}]$.

**Matriz adjunta:** é a transposta da matriz de cofatores: $\operatorname{adj}(A) = C^T$.

**Matriz inversa:** se $\det A \neq 0$, a inversa é calculada por

$$A^{-1} = \frac{1}{\det A}\cdot\operatorname{adj}(A)$$

O exemplo completo, com uma matriz $3\times 3$, está na Unidade 2.

---

## Unidade 4: Sistemas Lineares

- Um **sistema linear** é um **conjunto finito de equações** em que as incógnitas aparecem só com **expoente 1**, sem produtos entre si. Um sistema linear pode ter mais de uma equação.
- Um sistema linear pode ser escrito na forma matricial

$$A\cdot X = B$$

sendo $A$ a **matriz dos coeficientes**, $X$ a **matriz das incógnitas** e $B$ a **matriz dos termos independentes**.

- Outra matriz de um sistema linear é a **matriz ampliada**, que consiste, no geral, na junção da matriz dos coeficientes com a matriz dos termos independentes. Ela é útil para resolver sistemas lineares.
- Nem sempre uma equação é linear: é possível se deparar com **equações não lineares**.
- Uma **solução** de um sistema é o vetor ordenado $S = [s_1, s_2, \dots, s_n]$ que é, ao mesmo tempo, solução de cada uma das equações do sistema.

*Exemplo:* o sistema $\begin{cases} 2x + y = 5 \\ x - y = 1 \end{cases}$ tem

$$A = \begin{bmatrix} 2 & 1 \\ 1 & -1 \end{bmatrix},\quad X = \begin{bmatrix} x \\ y \end{bmatrix},\quad B = \begin{bmatrix} 5 \\ 1 \end{bmatrix},\quad \left[\begin{array}{cc|c} 2 & 1 & 5 \\ 1 & -1 & 1 \end{array}\right] \text{ (matriz ampliada)}$$

### Classificação (de acordo com a quantidade de soluções)

| Tipo | O que é | Soluções |
|:----------|:-----------------------------|:--------|
| **SPD** (possível e determinado) | Apresenta uma única solução (um único vetor solução) | uma única |
| **SPI** (possível e indeterminado) | Apresenta infinitas soluções (infinitos vetores solução) | infinitas |
| **SI** (impossível) | Não possui soluções (nenhum vetor solução) | nenhuma |

Os sistemas são ditos **equivalentes** quando possuem o mesmo vetor solução.

### Métodos de resolução de sistema linear

**1. Método de substituição**

- Escolhe-se uma equação e uma das incógnitas, e isola-se essa incógnita em função das outras. Em seguida, substitui-se a expressão obtida na outra equação, de modo a obter o valor numérico de uma incógnita, e assim por diante.
- É aplicável em **sistemas pequenos**, onde as incógnitas são fáceis de isolar.

**2. Escalonamento**

- Aplicam-se operações elementares em um sistema de forma a transformá-lo em outro equivalente e mais fácil de resolver.
- É um método geral; ajuda também a classificar sistemas lineares.

**3. Regra de Cramer**

- A regra de Cramer resolve sistemas lineares usando **determinantes**.
- Ela se aplica a sistemas em que:
    - o número de equações é **igual ao número de incógnitas** (matriz quadrada $n \times n$);
    - o **determinante da matriz dos coeficientes é diferente de zero** ($\det A \neq 0$), o que garante solução única.
- A regra funciona do seguinte modo: cada incógnita é dada por

$$x_i = \frac{\det A_i}{\det A}$$

onde $A_i$ é a matriz $A$ com a coluna $i$ substituída pela coluna dos termos independentes $B$.

*Exemplo:* no sistema acima, $\det A = -2 - 1 = -3$.

$$x = \frac{\det\begin{bmatrix} 5 & 1 \\ 1 & -1 \end{bmatrix}}{-3} = \frac{-6}{-3} = 2 \qquad y = \frac{\det\begin{bmatrix} 2 & 5 \\ 1 & 1 \end{bmatrix}}{-3} = \frac{-3}{-3} = 1$$

**4. Eliminação de Gauss**

- Para entender a eliminação de Gauss, é preciso antes conhecer a **matriz escalonada por linhas**.
- Uma matriz escalonada por linhas é uma matriz em que:
    - todas as linhas que consistem **inteiramente em zeros** estão na parte **inferior** da matriz;
    - em cada linha não nula, o primeiro elemento não nulo (chamado de **elemento líder**) está em uma coluna à esquerda de qualquer outro elemento líder abaixo dele.
- O **método de eliminação de Gauss** consiste em escalonar a matriz ampliada de um sistema, de modo a criar um sistema equivalente que pode ser resolvido por substituição.

---

## Unidade 5: Aplicações de matrizes

**Grafos e matrizes de adjacência.** $a_{ij} = 1$ se existe aresta entre $i$ e $j$ (0 caso contrário). A potência $A^k$ conta caminhos: $(A^k)_{ij}$ é o número de caminhos de comprimento $k$ de $i$ até $j$.

*Exemplo:* o grafo 1–2–3 tem

$$A = \begin{bmatrix} 0 & 1 & 0 \\ 1 & 0 & 1 \\ 0 & 1 & 0 \end{bmatrix} \qquad A^2 = \begin{bmatrix} 1 & 0 & 1 \\ 0 & 2 & 0 \\ 1 & 0 & 1 \end{bmatrix}$$

O 2 na posição $(2,2)$ conta os caminhos $2\to 1\to 2$ e $2\to 3\to 2$.

**Redes e fluxos.** Em cada nó vale a conservação do fluxo (entrada = saída), o que gera um sistema linear. Aplica-se a tráfego, circuitos elétricos e redes em geral.

**Cadeias de Markov.** A matriz de transição $P$ tem entradas $p_{ij}$ = probabilidade de passar do estado $i$ para o estado $j$, e cada linha soma 1. O estado futuro vem de $\pi_{k+1} = \pi_k\cdot P$.

*Exemplo (clima, estados sol e chuva):*

$$P = \begin{bmatrix} 0{,}8 & 0{,}2 \\ 0{,}4 & 0{,}6 \end{bmatrix} \qquad \pi_0 = [1\ \ 0] \text{ (hoje é sol)}$$

$$\pi_1 = [0{,}8\ \ 0{,}2]$$

$$\pi_2 = [0{,}8\cdot 0{,}8 + 0{,}2\cdot 0{,}4\ \ \ 0{,}8\cdot 0{,}2 + 0{,}2\cdot 0{,}6] = [0{,}72\ \ 0{,}28]$$

A longo prazo converge para $\pi = \left[\tfrac{2}{3}\ \ \tfrac{1}{3}\right]$, que satisfaz $\pi = \pi\cdot P$.

**Mínimos quadrados.** Para ajustar retas, parábolas ou exponenciais a dados quando $A\cdot x = b$ não tem solução exata, resolve-se a **equação normal**:

$$A^TA\cdot x = A^Tb$$

Se $A^TA$ é invertível, $x = (A^TA)^{-1}A^Tb$.

*Exemplo:* ajustar $y = a + bx$ aos pontos $(1,1)$, $(2,2)$ e $(3,2)$.

$$A = \begin{bmatrix} 1 & 1 \\ 1 & 2 \\ 1 & 3 \end{bmatrix} \qquad b = \begin{bmatrix} 1 \\ 2 \\ 2 \end{bmatrix} \qquad A^TA = \begin{bmatrix} 3 & 6 \\ 6 & 14 \end{bmatrix} \qquad A^Tb = \begin{bmatrix} 5 \\ 11 \end{bmatrix}$$

Resolvendo $3a + 6b = 5$ e $6a + 14b = 11$: $b = \tfrac{1}{2}$ e $a = \tfrac{2}{3}$. A reta é $y = \tfrac{2}{3} + \tfrac{x}{2}$.

---

## ★ Onde isso aparece em bioinformática

- **Matriz de expressão (genes × amostras):** normalizações e transformações são operações matriciais.
- **Regressão linear e modelos lineares** (como os de expressão diferencial): usam a equação normal. Se duas variáveis são colineares, $A^TA$ tem $\det = 0$ e não há solução única.
- **Deconvolução celular:** a expressão de uma mistura é modelada como $y = S\cdot c$, com $S$ a matriz de assinaturas de cada tipo celular e $c$ as proporções, estimadas por mínimos quadrados.
- **Matriz de precisão:** é a inversa da matriz de covariância, e seus zeros indicam independência condicional entre genes (redes de co-expressão).
- **Grafos:** redes de interação proteína-proteína são matrizes de adjacência.
- **Markov:** base dos modelos ocultos de Markov usados em alinhamento e predição de genes.
- **Próximo passo do curso:** autovalores e autovetores, que levam ao PCA e à SVD.

## ★ Erros comuns

- Somar ou subtrair matrizes de dimensões diferentes, ou multiplicar sem conferir $(m \times n)\cdot(n \times p)$.
- Supor $AB = BA$.
- Escrever $(AB)^T = A^TB^T$ ou $(AB)^{-1} = A^{-1}B^{-1}$. Em ambos a ordem se inverte.
- Escrever $\det(A + B) = \det A + \det B$, ou $\det(\alpha A) = \alpha\cdot\det A$ (o correto é $\alpha^n$).
- Aplicar Sarrus a matrizes $4 \times 4$ ou maiores.
- Esquecer o sinal $(-1)^{i+j}$ no cofator.
- Tentar inverter uma matriz com $\det = 0$.
- Multiplicar uma linha por 0 durante o escalonamento.

## ★ Exercícios

1. Calcule $AB$ com $A = \begin{bmatrix} 2 & 0 \\ 1 & 3 \end{bmatrix}$ e $B = \begin{bmatrix} 1 & 4 \\ 2 & 1 \end{bmatrix}$.
2. Calcule $\det\begin{bmatrix} 2 & 1 & 0 \\ 1 & 3 & 1 \\ 0 & 1 & 2 \end{bmatrix}$.
3. Encontre a inversa de $\begin{bmatrix} 4 & 7 \\ 2 & 6 \end{bmatrix}$.
4. Para quais valores de $k$ o sistema $x + ky = 1$, $kx + y = 1$ tem solução única? Classifique o sistema nos demais casos.
5. Se $A$ é $3 \times 3$ e $\det A = 5$, quanto valem $\det(2A)$, $\det(A^{-1})$ e $\det(A^T)$?
6. Resolva por escalonamento: $x + y = 3$ e $2x - y = 0$.
7. Com $P = \begin{bmatrix} 0{,}9 & 0{,}1 \\ 0{,}5 & 0{,}5 \end{bmatrix}$ e $\pi_0 = [1\ \ 0]$, calcule $\pi_2$.

### Gabarito

1. $\begin{bmatrix} 2 & 8 \\ 7 & 7 \end{bmatrix}$
2. $8$ (expandindo pela 1ª linha: $2\cdot 5 - 1\cdot 2 = 8$)
3. $\dfrac{1}{10}\begin{bmatrix} 6 & -7 \\ -2 & 4 \end{bmatrix} = \begin{bmatrix} 0{,}6 & -0{,}7 \\ -0{,}2 & 0{,}4 \end{bmatrix}$, pois $\det = 24 - 14 = 10$
4. $\det = 1 - k^2$, então a solução é única para $k \neq 1$ e $k \neq -1$. Para $k = 1$ as equações coincidem (SPI); para $k = -1$, somando as equações dá $0 = 2$ (SI).
5. $2^3\cdot 5 = 40$; $\dfrac{1}{5}$; $5$
6. Somando as equações: $3x = 3$, logo $x = 1$ e $y = 2$.
7. $\pi_1 = [0{,}9\ \ 0{,}1]$; $\pi_2 = [0{,}86\ \ 0{,}14]$

## ★ Cola de fórmulas

- Produto: $(m \times n)\cdot(n \times p) = m \times p$. Não comutativo.
- $(AB)^T = B^TA^T$ e $(AB)^{-1} = B^{-1}A^{-1}$.
- $A^{-1}$ existe $\iff$ $A$ quadrada e $\det A \neq 0$. $A^{-1} = \dfrac{\operatorname{adj}(A)}{\det A}$.
- $\det(AB) = \det A\cdot\det B$; $\det(A^T) = \det A$; $\det(A^{-1}) = \dfrac{1}{\det A}$; $\det(\alpha A) = \alpha^n\cdot\det A$.
- Sistema $A\cdot x = b$: possível $\iff$ $\operatorname{posto}(A) = \operatorname{posto}([A \mid b])$.
- Mínimos quadrados: $A^TA\cdot x = A^Tb$.

## Correções feitas nas anotações

**Na revisão de 19/10/2026**

- Sarrus 3 × 3: o resultado final estava rotulado como det(A), mas a matriz do exemplo era B.
- Propriedade (iii): a frase estava incompleta; agora diz que o determinante troca de sinal.
- Colunas proporcionais 3 × 3: as contas intermediárias estavam erradas (4 − 40 e 20 − 2); o correto é 4 − 48 e 24 − 2. O resultado final, 0, já estava certo.
- Inversa de B = [3 1; 2 2]: na matriz (1/4)·[2 −1; 2 3] faltava o sinal; o correto é [2 −1; −2 3].
- Produto de matrizes: as matrizes foram renomeadas como A e B (antes eram u e v, que são usadas para vetores).
- Mínimos quadrados: a equação normal foi escrita como AᵀA·x = Aᵀb.
- Fluxo em redes: a frase estava truncada e foi reescrita.
- Seções em branco (inversa pela adjunta, aplicação da inversa em sistemas, Unidade 4) foram preenchidas.

**Na versão em Markdown e PDF**

- Propriedades das matrizes: $A + 0 = u$ virou $A + 0 = A$; na distributiva, $B\cdot v$ virou $\alpha\cdot B$; a associativa da adição foi completada.
- Títulos e numeração: "Propriedades da Multiplicação entre vetores" passou a falar de matrizes, "Matriz de contatores" virou "Matriz de cofatores" e as seções com numeração repetida foram renumeradas.
- Matriz simétrica: a definição foi reescrita (matriz quadrada igual à sua transposta).
- Exemplos que estavam em imagens (produto interno, transposta, matriz simétrica, operações elementares, Gauss-Jordan, Sarrus 3 × 3, Cramer) foram refeitos em texto, com valores conferidos.
- Matrizes escritas em notação matemática (LaTeX), e decimais com vírgula.
