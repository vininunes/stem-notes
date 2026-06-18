#### sistemas lineares #algebra/definição/sistema-linear
^sistemas-lineares

Um **sistema linear** é um conjunto de equações lineares com as mesmas incógnitas. Uma **solução** do sistema é uma $n$-upla $(s_{1}, s_{2}, \dots, s_{n})$ que satisfaz todas as equações simultaneamente. Um sistema pode ser representado na forma [[aula-02-sistemas-lineares#^representacao-matricial|matricial]] $Ax = b$.

Todo sistema linear se enquadra em exatamente um dos três casos: #algebra/definição/SI-SPD-SPI
- **SI** (Sistema Impossível): zero soluções
- **SPD** (Sistema Possível Determinado): exatamente uma solução
- **SPI** (Sistema Possível Indeterminado): infinitas soluções distintas

Não existe sistema com exatamente 2, 3 ou qualquer número finito (maior que 1) de soluções.

#### operações elementares entre equações #algebra/definição/operações-elementares
^operacoes-elementares

São três operações que, aplicadas a um sistema linear, **não alteram** o seu conjunto solução — isto é, o sistema obtido é **equivalente** ao original.

1. **Permutar** duas equações de posição:

$$
E_{i} \leftrightarrow E_{j}
$$

2. **Multiplicar** uma equação por uma constante $\lambda \neq 0$:

$$
E_{i} \leftarrow \lambda \cdot E_{i}
$$

3. **Substituir** uma equação por ela própria somada a uma constante $\lambda$ vezes outra equação:

$$
E_{i} \leftarrow E_{i} + \lambda \cdot E_{j}
$$

Essas operações são reversíveis:
- A permuta se desfaz repetindo a mesma troca
- A multiplicação por $\lambda$ se desfaz multiplicando por $\frac{1}{\lambda}$
- A terceira operação se desfaz com $E_{i} \leftarrow E_{i} - \lambda \cdot E_{j}$

Dois sistemas são **equivalentes** quando um pode ser obtido do outro por uma sequência finita dessas operações. #algebra/definição/sistemas-equivalentes Ao representar o sistema como matriz aumentada, essas operações correspondem exatamente às operações elementares sobre linhas.

#### matriz auxiliar de um sistema-linear #algebra/definição/matriz-aumentada
^matriz-aumentada

Dado um sistema linear com $m$ equações e $n$ incógnitas:

$$
\begin{cases}
a_{11}x_{1} + a_{12}x_{2} + \dots + a_{1n}x_{n} = b_{1} \\
a_{21}x_{1} + a_{22}x_{2} + \dots + a_{2n}x_{n} = b_{2} \\
\vdots \\
a_{m1}x_{1} + a_{m2}x_{2} + \dots + a_{mn}x_{n} = b_{m}
\end{cases}
$$

A sua matriz aumentada é:

$$
\left[\begin{array}{cccc|c}
a_{11} & a_{12} & \dots & a_{1n} & b_{1} \\
a_{21} & a_{22} & \dots & a_{2n} & b_{2} \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
a_{m1} & a_{m2} & \dots & a_{mn} & b_{m}
\end{array}\right]
$$

#### operações elementares sobre linhas
^operacoes-elementares-linhas

São três operações que **não alteram** o conjunto solução do sistema:

1. **Trocar** duas linhas de posição:

$$
L_{i} \leftrightarrow L_{j}
$$

2. **Multiplicar** uma linha por um escalar $\lambda \neq 0$:

$$
L_{i} \leftarrow \lambda \cdot L_{i}
$$

3. **Somar** a uma linha um múltiplo de outra linha:

$$
L_{i} \leftarrow L_{i} + \lambda \cdot L_{j}
$$

Duas matrizes são **equivalentes por linhas** se uma pode ser obtida a partir da outra por uma sequência finita dessas operações.

#### matriz escalonada #algebra/definição/pivô #algebra/definição/matriz-escalonada
^matriz-escalonada

O **pivô** de uma linha é o primeiro elemento não nulo dessa linha. O número de pivôs após o escalonamento define o [[aula-02-sistemas-lineares#^posto|posto]] da matriz.

Uma matriz está na forma **escalonada** se satisfaz:

1. Todas as linhas nulas (formadas só por zeros) estão **abaixo** das linhas não nulas
2. O pivô de cada linha está em uma coluna **à direita** do pivô da linha acima

Exemplo de matriz escalonada:

$$
\left[\begin{array}{cccc|c}
\boxed{2} & 3 & -1 & 4 & 5 \\
0 & \boxed{1} & 7 & 2 & 3 \\
0 & 0 & 0 & \boxed{5} & 1 \\
0 & 0 & 0 & 0 & 0
\end{array}\right]
$$

Os pivôs estão destacados. Note a "escada" formada: cada pivô está mais à direita que o anterior.

Exemplo de matriz **não** escalonada:

$$
\left[\begin{array}{ccc|c}
1 & 2 & 3 & 4 \\
0 & 0 & 5 & 6 \\
0 & 1 & 0 & 2
\end{array}\right]
$$

Aqui o pivô de $L_{3}$ não está à direita do pivô de $L_{2}$.

#### processo de escalonamento (eliminação gaussiana) #algebra/definição/eliminação-gaussiana
^eliminacao-gaussiana

O objetivo é transformar a matriz aumentada em uma matriz escalonada usando operações elementares.

**Algoritmo:**
1. Identifique a coluna mais à esquerda que tenha algum elemento não nulo
2. Se necessário, troque linhas para que o pivô (elemento não nulo) fique na primeira linha ainda não processada
3. Use operações do tipo $L_{i} \leftarrow L_{i} + \lambda \cdot L_{j}$ para zerar todos os elementos **abaixo** do pivô
4. Repita o processo para a submatriz restante (ignorando as linhas já escalonadas)

**Exemplo:** escalonar o sistema

$$
\begin{cases}
2x - y + z = 4 \\
x - y + z = 1 \\
3x - 6y + 7z = 0
\end{cases}
$$

Matriz aumentada:

$$
\left[\begin{array}{ccc|c}
2 & -1 & 1 & 4 \\
1 & -1 & 1 & 1 \\
3 & -6 & 7 & 0
\end{array}\right]
$$

$L_{1} \leftrightarrow L_{2}$ (troca para ter pivô 1):

$$
\left[\begin{array}{ccc|c}
1 & -1 & 1 & 1 \\
2 & -1 & 1 & 4 \\
3 & -6 & 7 & 0
\end{array}\right]
$$

$L_{2} \leftarrow L_{2} - 2L_{1}$ e $L_{3} \leftarrow L_{3} - 3L_{1}$:

$$
\left[\begin{array}{ccc|c}
1 & -1 & 1 & 1 \\
0 & 1 & -1 & 2 \\
0 & -3 & 4 & -3
\end{array}\right]
$$

$L_{3} \leftarrow L_{3} + 3L_{2}$:

$$
\left[\begin{array}{ccc|c}
1 & -1 & 1 & 1 \\
0 & 1 & -1 & 2 \\
0 & 0 & 1 & 3
\end{array}\right]
$$

Substituição reversa:
- $L_{3}: z = 3$
- $L_{2}: y - 3 = 2 \implies y = 5$
- $L_{1}: x - 5 + 3 = 1 \implies x = 3$

Solução: $(x, y, z) = (3, 5, 3)$ — sistema **SPD**.

#### discussão de sistemas lineares
^discussao-sistemas

##### sistema impossível (SI) #algebra/proposição/critério-SI
^criterio-si

Critério formalizado pelo [[aula-02-sistemas-lineares#^rouche-capelli|teorema de Rouché-Capelli]]: $p(A) \neq p([A \mid b])$.

Após escalonar, o sistema é **impossível** quando aparece uma linha do tipo:

$$
\left[\begin{array}{ccc|c}
0 & 0 & \dots & b
\end{array}\right] \quad \text{com } b \neq 0
$$

Isso equivale à equação $0x + 0y + \dots = b$, que é uma **contradição** — nenhuma $n$-upla pode satisfazê-la.

**Exemplo:**

$$
\begin{cases}
x + y + z = 2 \\
2x + 2y + 2z = 5 \\
x - y + 3z = 1
\end{cases}
$$

Matriz aumentada:

$$
\left[\begin{array}{ccc|c}
1 & 1 & 1 & 2 \\
2 & 2 & 2 & 5 \\
1 & -1 & 3 & 1
\end{array}\right]
$$

$L_{2} \leftarrow L_{2} - 2L_{1}$ e $L_{3} \leftarrow L_{3} - L_{1}$:

$$
\left[\begin{array}{ccc|c}
1 & 1 & 1 & 2 \\
0 & 0 & 0 & 1 \\
0 & -2 & 2 & -1
\end{array}\right]
$$

$L_{2}$ diz que $0 = 1$ — **contradição**. O sistema é **SI**.

##### sistema possível indeterminado (SPI) #algebra/proposição/critério-SPI
^criterio-spi

Critério formalizado pelo [[aula-02-sistemas-lineares#^rouche-capelli|teorema de Rouché-Capelli]]: $p(A) = p([A \mid b]) < n$.

Após escalonar, o sistema é **SPI** quando:
- Não há contradição (nenhuma linha $[0 \; 0 \; \dots \mid b]$ com $b \neq 0$)
- O número de pivôs é **menor** que o número de incógnitas

As incógnitas sem pivô na sua coluna são chamadas **variáveis livres** #algebra/definição/variável-livre — podem assumir qualquer valor real, gerando infinitas soluções. A estrutura dessas soluções é descrita pela [[aula-02-sistemas-lineares#^solucao-geral-particular|decomposição $x = x_p + x_h$]].

**Exemplo:**

$$
\begin{cases}
x + y + z = 3 \\
2x + 2y + z = 4 \\
x + y + 2z = 5
\end{cases}
$$

Matriz aumentada:

$$
\left[\begin{array}{ccc|c}
1 & 1 & 1 & 3 \\
2 & 2 & 1 & 4 \\
1 & 1 & 2 & 5
\end{array}\right]
$$

$L_{2} \leftarrow L_{2} - 2L_{1}$ e $L_{3} \leftarrow L_{3} - L_{1}$:

$$
\left[\begin{array}{ccc|c}
1 & 1 & 1 & 3 \\
0 & 0 & -1 & -2 \\
0 & 0 & 1 & 2
\end{array}\right]
$$

$L_{3} \leftarrow L_{3} + L_{2}$:

$$
\left[\begin{array}{ccc|c}
1 & 1 & 1 & 3 \\
0 & 0 & -1 & -2 \\
0 & 0 & 0 & 0
\end{array}\right]
$$

Há 2 pivôs e 3 incógnitas. A coluna de $y$ não tem pivô, então $y$ é **variável livre**. Fazendo $y = t$ com $t \in \mathbb{R}$:

- $L_{2}: -z = -2 \implies z = 2$
- $L_{1}: x + t + 2 = 3 \implies x = 1 - t$

Solução: $(x, y, z) = (1 - t, \; t, \; 2)$ com $t \in \mathbb{R}$ — sistema **SPI**.

##### sistema possível determinado (SPD) #algebra/proposição/critério-SPD
^criterio-spd

Critério formalizado pelo [[aula-02-sistemas-lineares#^rouche-capelli|teorema de Rouché-Capelli]]: $p(A) = p([A \mid b]) = n$.

Após escalonar, o sistema é **SPD** quando:
- Não há contradição
- O número de pivôs é **igual** ao número de incógnitas

Cada incógnita tem um pivô na sua coluna, então não há variáveis livres. A substituição reversa determina um único valor para cada incógnita.

**Exemplo:**

$$
\begin{cases}
x + y - z = 0 \\
2x - y + z = 7 \\
x + 2y + 2z = 5
\end{cases}
$$

Matriz aumentada:

$$
\left[\begin{array}{ccc|c}
1 & 1 & -1 & 0 \\
2 & -1 & 1 & 7 \\
1 & 2 & 2 & 5
\end{array}\right]
$$

$L_{2} \leftarrow L_{2} - 2L_{1}$ e $L_{3} \leftarrow L_{3} - L_{1}$:

$$
\left[\begin{array}{ccc|c}
1 & 1 & -1 & 0 \\
0 & -3 & 3 & 7 \\
0 & 1 & 3 & 5
\end{array}\right]
$$

$L_{2} \leftrightarrow L_{3}$:

$$
\left[\begin{array}{ccc|c}
1 & 1 & -1 & 0 \\
0 & 1 & 3 & 5 \\
0 & -3 & 3 & 7
\end{array}\right]
$$

$L_{3} \leftarrow L_{3} + 3L_{2}$:

$$
\left[\begin{array}{ccc|c}
1 & 1 & -1 & 0 \\
0 & 1 & 3 & 5 \\
0 & 0 & 12 & 22
\end{array}\right]
$$

Há 3 pivôs e 3 incógnitas. Substituição reversa:
- $L_{3}: 12z = 22 \implies z = \frac{11}{6}$
- $L_{2}: y + 3 \cdot \frac{11}{6} = 5 \implies y = 5 - \frac{11}{2} = -\frac{1}{2}$
- $L_{1}: x - \frac{1}{2} - \frac{11}{6} = 0 \implies x = \frac{1}{2} + \frac{11}{6} = \frac{7}{3}$

Solução: $(x, y, z) = \left(\frac{7}{3}, \; -\frac{1}{2}, \; \frac{11}{6}\right)$ — sistema **SPD**.
