#### representação matricial #algebra/definição/representação-matricial
^representacao-matricial

Um [[aula-01-escalonamento#^sistemas-lineares|sistema linear]] pode ser escrito na forma matricial $Ax = b$, onde:

$$
\underbrace{\begin{bmatrix} a_{11} & a_{12} & \dots & a_{1n} \\ a_{21} & a_{22} & \dots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \dots & a_{mn} \end{bmatrix}}_{A} \cdot \underbrace{\begin{bmatrix} x_{1} \\ x_{2} \\ \vdots \\ x_{n} \end{bmatrix}}_{x} = \underbrace{\begin{bmatrix} b_{1} \\ b_{2} \\ \vdots \\ b_{m} \end{bmatrix}}_{b}
$$

- $A$ é a **matriz dos coeficientes** ($m \times n$)
- $x$ é o **vetor das incógnitas** ($n \times 1$)
- $b$ é o **vetor dos termos independentes** ($m \times 1$)
- A [[aula-01-escalonamento#^matriz-aumentada|matriz aumentada]] é $[A \mid b]$ ($m \times (n+1)$)

Quando $b = 0$ (vetor nulo), o sistema é chamado **homogêneo**. #algebra/definição/sistema-homogêneo

#### posto de uma matriz #algebra/definição/posto
^posto

O **posto** (ou **rank**) de uma matriz $A$, denotado $p(A)$, é o número de [[aula-01-escalonamento#^matriz-escalonada|pivôs]] da forma escalonada de $A$.

Equivalentemente, é o número de linhas não nulas após o escalonamento.

**Exemplo:**

$$
A = \begin{bmatrix} 1 & 2 & 3 \\ 2 & 4 & 6 \\ 0 & 1 & 1 \end{bmatrix}
$$

$L_{2} \leftarrow L_{2} - 2L_{1}$:

$$
\begin{bmatrix} 1 & 2 & 3 \\ 0 & 0 & 0 \\ 0 & 1 & 1 \end{bmatrix}
$$

$L_{2} \leftrightarrow L_{3}$:

$$
\begin{bmatrix} \boxed{1} & 2 & 3 \\ 0 & \boxed{1} & 1 \\ 0 & 0 & 0 \end{bmatrix}
$$

Há 2 pivôs, portanto $p(A) = 2$.

**Propriedades do posto:**
- $0 \leq p(A) \leq \min(m, n)$ para $A$ de tamanho $m \times n$
- $p(A) = p(A^{T})$
- $p(A) \leq p([A \mid b])$ (o posto da aumentada é sempre $\geq$ o da coeficientes)
- $p([A \mid b])$ é no máximo $p(A) + 1$

#### teorema do posto (Rouché-Capelli) #algebra/teorema/Rouché-Capelli
^rouche-capelli

Seja $Ax = b$ um sistema com $n$ incógnitas. Então:

| Condição | Classificação |
|---|---|
| $p(A) \neq p([A \mid b])$ | **[[aula-01-escalonamento#^criterio-si|SI]]** — sistema impossível |
| $p(A) = p([A \mid b]) = n$ | **[[aula-01-escalonamento#^criterio-spd|SPD]]** — solução única |
| $p(A) = p([A \mid b]) < n$ | **[[aula-01-escalonamento#^criterio-spi|SPI]]** — infinitas soluções |

Em palavras:
- O sistema **tem solução** se e somente se $p(A) = p([A \mid b])$
- Se tem solução, é **única** quando o posto iguala o número de incógnitas
- Se tem solução e o posto é menor que $n$, há $n - p(A)$ [[aula-01-escalonamento#^criterio-spi|variáveis livres]]

**Exemplo:** determine a classificação do sistema

$$
\begin{cases}
x + 2y - z = 3 \\
2x + 4y - 2z = 6 \\
x + y + z = 4
\end{cases}
$$

Matriz aumentada:

$$
\left[\begin{array}{ccc|c}
1 & 2 & -1 & 3 \\
2 & 4 & -2 & 6 \\
1 & 1 & 1 & 4
\end{array}\right]
$$

Aplicando [[aula-01-escalonamento#^operacoes-elementares-linhas|operações elementares]]: $L_{2} \leftarrow L_{2} - 2L_{1}$ e $L_{3} \leftarrow L_{3} - L_{1}$:

$$
\left[\begin{array}{ccc|c}
1 & 2 & -1 & 3 \\
0 & 0 & 0 & 0 \\
0 & -1 & 2 & 1
\end{array}\right]
$$

$L_{2} \leftrightarrow L_{3}$:

$$
\left[\begin{array}{ccc|c}
\boxed{1} & 2 & -1 & 3 \\
0 & \boxed{-1} & 2 & 1 \\
0 & 0 & 0 & 0
\end{array}\right]
$$

$p(A) = 2$ e $p([A \mid b]) = 2$. Como $p(A) = p([A \mid b]) = 2 < 3 = n$, o sistema é **SPI** com $3 - 2 = 1$ variável livre.

Fazendo $z = t$:
- $L_{2}: -y + 2t = 1 \implies y = 2t - 1$
- $L_{1}: x + 2(2t - 1) - t = 3 \implies x = 5 - 3t$

Solução: $(x, y, z) = (5 - 3t, \; 2t - 1, \; t)$ com $t \in \mathbb{R}$.

#### sistemas homogêneos
^sistemas-homogeneos

Um sistema $Ax = 0$ é chamado **homogêneo**. Propriedades fundamentais:

1. **Sempre possível**: $x = 0$ (vetor nulo) é sempre solução — chamada de **solução trivial** #algebra/definição/solução-trivial #algebra/proposição/homogêneo-sempre-possível
2. Portanto um sistema homogêneo é sempre **SPD** ou **SPI**, nunca SI
3. Se $m < n$ (menos equações que incógnitas), o sistema é necessariamente **SPI** — pois $p(A) \leq m < n$ #algebra/proposição/m-menor-n-implica-SPI

**Exemplo:**

$$
\begin{cases}
x + 2y - 3z = 0 \\
2x + y + z = 0
\end{cases}
$$

Matriz aumentada:

$$
\left[\begin{array}{ccc|c}
1 & 2 & -3 & 0 \\
2 & 1 & 1 & 0
\end{array}\right]
$$

$L_{2} \leftarrow L_{2} - 2L_{1}$:

$$
\left[\begin{array}{ccc|c}
\boxed{1} & 2 & -3 & 0 \\
0 & \boxed{-3} & 7 & 0
\end{array}\right]
$$

$p(A) = 2 < 3 = n$, logo é **SPI** com 1 variável livre. Fazendo $z = t$:

- $L_{2}: -3y + 7t = 0 \implies y = \frac{7t}{3}$
- $L_{1}: x + \frac{14t}{3} - 3t = 0 \implies x = 3t - \frac{14t}{3} = -\frac{5t}{3}$

Solução: $(x, y, z) = \left(-\frac{5t}{3}, \; \frac{7t}{3}, \; t\right)$ com $t \in \mathbb{R}$.

Fatorando $t$: $(x, y, z) = t \cdot \left(-\frac{5}{3}, \; \frac{7}{3}, \; 1\right)$.

Note que a solução de um sistema homogêneo sempre pode ser escrita como **combinação linear** de vetores com parâmetros livres.

#### relação entre sistema homogêneo e não homogêneo #algebra/proposição/solução-geral-particular-homogênea
^solucao-geral-particular

Se $Ax = b$ é um sistema possível, então:

$$
\text{Solução geral de } Ax = b = \text{(uma solução particular de } Ax = b\text{)} + \text{(solução geral de } Ax = 0\text{)}
$$

Ou seja, se $x_{p}$ é uma solução particular de $Ax = b$ e $x_{h}$ é a solução geral de $Ax = 0$:

$$
x = x_{p} + x_{h}
$$

**Exemplo:** no sistema da seção anterior sobre o teorema do posto, a solução foi

$$
(x, y, z) = (5 - 3t, \; 2t - 1, \; t) = \underbrace{(5, -1, 0)}_{x_{p}} + t \cdot \underbrace{(-3, 2, 1)}_{x_{h}}
$$

onde $(5, -1, 0)$ é uma solução particular (fazendo $t = 0$) e $(-3, 2, 1)$ é a direção das soluções do sistema homogêneo associado.

#### discussão de sistemas com parâmetro
^discussao-parametro

> Veja também: [[aula-01-escalonamento#^eliminacao-gaussiana|eliminação gaussiana]] para o método de escalonamento.

Quando os coeficientes ou termos independentes dependem de um parâmetro $k$, a classificação do sistema varia conforme o valor de $k$.

**Exemplo:** discuta o sistema em função de $k \in \mathbb{R}$

$$
\begin{cases}
x + y + kz = 1 \\
x + ky + z = 1 \\
kx + y + z = 1
\end{cases}
$$

Matriz aumentada:

$$
\left[\begin{array}{ccc|c}
1 & 1 & k & 1 \\
1 & k & 1 & 1 \\
k & 1 & 1 & 1
\end{array}\right]
$$

$L_{2} \leftarrow L_{2} - L_{1}$ e $L_{3} \leftarrow L_{3} - kL_{1}$:

$$
\left[\begin{array}{ccc|c}
1 & 1 & k & 1 \\
0 & k-1 & 1-k & 0 \\
0 & 1-k & 1-k^{2} & 1-k
\end{array}\right]
$$

Note que $1 - k^{2} = (1-k)(1+k)$ e os termos $k - 1 = -(1-k)$. Fatorando:

$$
\left[\begin{array}{ccc|c}
1 & 1 & k & 1 \\
0 & -(1-k) & (1-k) & 0 \\
0 & (1-k) & (1-k)(1+k) & (1-k)
\end{array}\right]
$$

**Caso $k = 1$:** as linhas $L_{2}$ e $L_{3}$ se anulam:

$$
\left[\begin{array}{ccc|c}
1 & 1 & 1 & 1 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{array}\right]
$$

$p(A) = 1 < 3$, logo é **SPI** com 2 variáveis livres. Fazendo $y = s$ e $z = t$:

$$
x = 1 - s - t
$$

Solução: $(x, y, z) = (1 - s - t, \; s, \; t)$ com $s, t \in \mathbb{R}$.

**Caso $k \neq 1$:** podemos dividir $L_{2}$ por $-(1-k)$ e simplificar $L_{3}$.

$L_{2} \leftarrow \frac{L_{2}}{-(1-k)}$:

$$
\left[\begin{array}{ccc|c}
1 & 1 & k & 1 \\
0 & 1 & -1 & 0 \\
0 & (1-k) & (1-k)(1+k) & (1-k)
\end{array}\right]
$$

$L_{3} \leftarrow L_{3} - (1-k)L_{2}$:

$$
\left[\begin{array}{ccc|c}
1 & 1 & k & 1 \\
0 & 1 & -1 & 0 \\
0 & 0 & (1-k)(1+k) - (1-k)(-1) & (1-k)
\end{array}\right]
$$

O elemento $a_{33}$:

$$
(1-k)(1+k) + (1-k) = (1-k)(1+k+1) = (1-k)(k+2)
$$

$$
\left[\begin{array}{ccc|c}
1 & 1 & k & 1 \\
0 & 1 & -1 & 0 \\
0 & 0 & (1-k)(k+2) & (1-k)
\end{array}\right]
$$

**Subcaso $k = -2$:** (e $k \neq 1$)

$$
\left[\begin{array}{ccc|c}
1 & 1 & -2 & 1 \\
0 & 1 & -1 & 0 \\
0 & 0 & 0 & 3
\end{array}\right]
$$

$L_{3}$ diz $0 = 3$ — **contradição**. Sistema **SI**.

**Subcaso $k \neq -2$ e $k \neq 1$:**

$p(A) = p([A \mid b]) = 3 = n$. Sistema **SPD**.

Dividindo $L_{3}$ por $(1-k)(k+2)$:

$$
z = \frac{(1-k)}{(1-k)(k+2)} = \frac{1}{k+2}
$$

Substituição reversa:
- $L_{2}: y = z = \frac{1}{k+2}$
- $L_{1}: x = 1 - y - kz = 1 - \frac{1}{k+2} - \frac{k}{k+2} = 1 - \frac{k+1}{k+2} = \frac{1}{k+2}$

Solução: $(x, y, z) = \left(\frac{1}{k+2}, \; \frac{1}{k+2}, \; \frac{1}{k+2}\right)$.

**Resumo:**

| Valor de $k$ | Classificação | Solução |
|---|---|---|
| $k = -2$ | SI | — |
| $k = 1$ | SPI (2 var. livres) | $(1 - s - t, \; s, \; t)$ |
| $k \neq 1$ e $k \neq -2$ | SPD | $\left(\frac{1}{k+2}, \; \frac{1}{k+2}, \; \frac{1}{k+2}\right)$ |
