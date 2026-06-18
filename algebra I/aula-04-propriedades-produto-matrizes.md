#### matriz identidade #algebra/definição/matriz-identidade
^matriz-identidade

A **matriz identidade** $I_n \in M_{n \times n}(\mathbb{R})$ é a matriz cujas entradas são dadas pelo **delta de Kronecker**:

$$(I_n)_{ij} = \delta_{ij} = \begin{cases} 1, & \text{se } i = j \\ 0, & \text{se } i \neq j \end{cases}$$

$$I_n = \begin{bmatrix} 1 & 0 & \cdots & 0 \\ 0 & 1 & \cdots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \cdots & 1 \end{bmatrix}$$

**Propriedade:** Para toda $A \in M_{m \times n}(\mathbb{R})$, vale $I_m \cdot A = A \cdot I_n = A$.

---

#### propriedades do produto de matrizes #algebra/proposição/propriedades-produto-matrizes
^propriedades-produto-matrizes

Sejam $A \in M_{m \times n}(\mathbb{R})$, $B \in M_{n \times p}(\mathbb{R})$, $C \in M_{p \times q}(\mathbb{R})$ e $\alpha \in \mathbb{R}$.

1. **Associatividade:** $(AB)C = A(BC)$ — a ordem das multiplicações não importa, podemos escrever simplesmente $ABC$
2. **Elemento neutro:** $I_m \cdot A = A \cdot I_n = A$ — a [[#^matriz-identidade|matriz identidade]] não altera o produto
3. **Distributiva à esquerda:** $A(B + C) = AB + AC$ — o produto distribui sobre a soma à esquerda
4. **Distributiva à direita:** $(A + B)C = AC + BC$ — o produto distribui sobre a soma à direita
5. **Compatibilidade com escalar:** $A(\alpha B) = (\alpha A)B = \alpha(AB)$ — o escalar pode ser "puxado" para fora do produto

> **Observação:** O produto de matrizes **não é comutativo** em geral: $AB \neq BA$.

> **Observação:** No produto $AB$:
> - Se a linha $i$ de $A$ é toda nula, então a linha $i$ de $AB$ também é toda nula
> - Se a coluna $j$ de $B$ é toda nula, então a coluna $j$ de $AB$ também é toda nula

---

#### matrizes elementares #algebra/definição/matrizes-elementares
^matrizes-elementares

Uma **matriz elementar** é uma matriz obtida a partir da identidade $I_n$ por uma única [[aula-01-escalonamento#^operacoes-elementares|operação elementar]]. Multiplicar uma matriz $A$ à esquerda por uma matriz elementar equivale a aplicar a operação elementar correspondente nas linhas de $A$.

**Tipo 1 — Permutação de linhas** ($L_i \leftrightarrow L_j$):

Obtida de $I_n$ permutando as linhas $i$ e $j$. Por exemplo, para $n = 3$ e $L_1 \leftrightarrow L_2$:

$$E_1 = \begin{bmatrix} 0 & 1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$

O produto $E_1 \cdot A$ resulta em $A$ com as linhas 1 e 2 trocadas.

**Tipo 2 — Multiplicação de linha por escalar** ($L_i \leftarrow \lambda \cdot L_i$, $\lambda \neq 0$):

Obtida de $I_n$ substituindo $(I_n)_{ii} = 1$ por $\lambda$. 
Por exemplo, para $n = 3$ e $L_1 \leftarrow \alpha \cdot L_1$:

$$E_2 = \begin{bmatrix} \alpha & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$

O produto $E_2 \cdot A$ resulta em $A$ com a linha 1 multiplicada por $\alpha$.

**Tipo 3 — Soma de múltiplo de linha** ($L_i \leftarrow L_i + \lambda \cdot L_j$):

Obtida de $I_n$ colocando $\lambda$ na posição $(i, j)$. Por exemplo, para $n = 3$ e $L_2 \leftarrow L_2 + \alpha \cdot L_1$:

$$E_3 = \begin{bmatrix} 1 & 0 & 0 \\ \alpha & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$

O produto $E_3 \cdot A$ resulta em $A$ com a linha 2 substituída por $L_2 + \alpha L_1$.

> **Observação:** Toda operação elementar é reversível, logo toda matriz elementar é invertível. A inversa de uma matriz elementar é também uma matriz elementar (do mesmo tipo).

**Inversas das matrizes elementares:**

- **Tipo 1:** $(E_1)^{-1} = E_1$ (aplicar a mesma permutação desfaz a troca)

$$E_1^{-1} = \begin{bmatrix} 0 & 1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$

- **Tipo 2:** $(E_2)^{-1}$ é obtida substituindo $\alpha$ por $\frac{1}{\alpha}$:

$$E_2^{-1} = \begin{bmatrix} \frac{1}{\alpha} & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$

- **Tipo 3:** $(E_3)^{-1}$ é obtida trocando $\alpha$ por $-\alpha$:

$$E_3^{-1} = \begin{bmatrix} 1 & 0 & 0 \\ -\alpha & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}$$

> **Nota:** Nas próximas aulas veremos que o processo de escalonamento de uma matriz $A$ pode ser interpretado como uma série de multiplicações por matrizes elementares à esquerda: $E_k \cdots E_2 \cdot E_1 \cdot A = A'$ (forma escalonada).
