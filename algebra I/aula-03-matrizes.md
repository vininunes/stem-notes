#### definição de matriz #algebra/definição/matriz
^definicao-matriz

Uma **matriz** $m \times n$ é uma tabela de números reais com $m$ linhas e $n$ colunas:

$$A = \begin{bmatrix} a_{11} & a_{12} & \cdots & a_{1n} \\ a_{21} & a_{22} & \cdots & a_{2n} \\ \vdots & \vdots & \ddots & \vdots \\ a_{m1} & a_{m2} & \cdots & a_{mn} \end{bmatrix}$$

Denotamos $A = (a_{ij})_{m \times n}$, onde $a_{ij} \in \mathbb{R}$ é a entrada na linha $i$ e coluna $j$. O conjunto de todas as matrizes $m \times n$ com entradas reais é denotado por $M_{m \times n}(\mathbb{R})$.

---

#### soma de matrizes #algebra/definição/soma-matrizes
^soma-matrizes

Se $A, B \in M_{m \times n}(\mathbb{R})$ (mesmo tamanho), então $A + B$ é a matriz obtida somando entrada a entrada:

$$(A \oplus B)_{ij} = a_{ij} + b_{ij}$$

---

#### propriedades da soma de matrizes #algebra/proposição/propriedades-soma-matrizes
^propriedades-soma-matrizes

Para $A, B, C \in M_{m \times n}(\mathbb{R})$:

1. **Comutatividade:** $A \oplus B = B \oplus A$
2. **Associatividade:** $(A \oplus B) \oplus C = A \oplus (B \oplus C)$
3. **Elemento neutro:** $A \oplus 0_{m \times n} = A$, onde $0_{m \times n}$ é a matriz com todas as entradas iguais a zero
4. **Elemento oposto:** para toda $A$, existe $-A$ tal que $A \oplus (-A) = 0_{m \times n}$, onde $(-A)_{ij} = -a_{ij}$

> Essas propriedades são consequência direta das propriedades das operações dos números reais — a soma de matrizes é definida entrada a entrada, e cada entrada opera em $\mathbb{R}$.

> **Nota:** o professor mencionou que um conjunto com uma operação satisfazendo essas quatro propriedades é chamado de **grupo abeliano** (comutativo). (em homenagem a Niels Henrik Abel)

---

#### produto por escalar #algebra/definição/produto-escalar-matriz
^produto-escalar-matriz

Dado $\lambda \in \mathbb{R}$ e $A \in M_{m \times n}(\mathbb{R})$, o **produto por escalar** $\lambda \odot A$ é a matriz obtida multiplicando cada entrada por $\lambda$:

$$(\lambda \odot A)_{ij} = \lambda \cdot a_{ij}$$

---

#### propriedades do produto por escalar #algebra/proposição/propriedades-produto-escalar-matriz
^propriedades-produto-escalar-matriz

Para $A \in M_{m \times n}(\mathbb{R})$ e $\lambda \in \mathbb{R}$:

1. **Elemento neutro:** $1 \odot A = A$
2. **Compatibilidade:** $\lambda \odot (\mu \odot A) = (\lambda \cdot \mu) \odot A$
3. **Multiplicação por zero:** $0 \odot A = 0_{m \times n}$
4. **Distributiva (soma de escalares):** $(\alpha + \beta) \odot A = (\alpha \odot A) \oplus (\beta \odot A)$
5. **Distributiva (soma de matrizes):** $\alpha \odot (A \oplus B) = (\alpha \odot A) \oplus (\alpha \odot B)$

---

#### produto de matrizes — motivação #algebra/definição/produto-matrizes
^produto-matrizes-motivacao

A motivação vem dos [[aula-02-sistemas-lineares#^representacao-matricial|sistemas lineares]]. A [[aula-01-escalonamento#^matriz-aumentada|matriz aumentada]] $[A \mid b]$ pode ser separada: a matriz dos coeficientes $A$ ($m \times n$) e o vetor dos termos independentes $b$ ($m \times 1$).

O sistema $Ax = b$ significa exatamente que o produto da matriz $A$ pelo vetor $x$ resulta no vetor $b$:

$$\underbrace{A}_{m \times n} \cdot \underbrace{x}_{n \times 1} = \underbrace{b}_{m \times 1}$$

**Exemplo:** o sistema $\begin{cases} x + 2y = 5 \\ 3x - y = 1 \end{cases}$ corresponde a:

$$\begin{bmatrix} 1 & 2 \\ 3 & -1 \end{bmatrix} \begin{bmatrix} x \\ y \end{bmatrix} = \begin{bmatrix} 5 \\ 1 \end{bmatrix}$$

A primeira linha dá $1 \cdot x + 2 \cdot y = 5$ e a segunda dá $3 \cdot x + (-1) \cdot y = 1$. Cada entrada do vetor resultado é o **produto escalar** da linha de $A$ pelo vetor $x$.

---

#### definição do produto de matrizes #algebra/definição/produto-matrizes
^produto-matrizes

Dada $A \in M_{m \times n}(\mathbb{R})$ e $B \in M_{n \times p}(\mathbb{R})$, o **produto** $A \cdot B$ é a matriz $C \in M_{m \times p}(\mathbb{R})$ definida por:

$$c_{ij} = \sum_{k=1}^{n} a_{ik} \cdot b_{kj}$$

Ou seja, a entrada $(i,j)$ de $C$ é o produto escalar da **linha $i$** de $A$ pela **coluna $j$** de $B$.

> O número de **colunas** de $A$ deve ser igual ao número de **linhas** de $B$ para que o produto esteja definido.

> **Próxima aula:** propriedades do produto de matrizes.
