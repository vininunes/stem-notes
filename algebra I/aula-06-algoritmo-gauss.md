#### generalização: escalonamento de uma matriz $2 \times 3$
^generalizacao-escalonamento

Considere uma matriz genérica $2 \times 3$:

$$
\begin{bmatrix} a & b & e \\ c & d & f \end{bmatrix}
$$

Que corresponde ao sistema:

$$
\begin{cases} ax + by = e \\ cx + dy = f \end{cases}
$$

Vamos dividir em casos para escalonar.

---

#### caso 1: $a = c = 0$
^caso-1-a-c-zero

A primeira coluna é toda nula. A matriz fica:

$$
\begin{bmatrix} 0 & b & e \\ 0 & d & f \end{bmatrix}
$$

Agora olhamos para a segunda coluna ($b$ e $d$):

**Subcaso 1.1: $b = d = 0$**

$$
\begin{bmatrix} 0 & 0 & e \\ 0 & 0 & f \end{bmatrix}
$$

- Se $e = f = 0$: matriz nula, já escalonada.
- Se $e \neq 0$: pivô na posição $(1,3)$. Dividimos $L_1$ por $e$: $\begin{bmatrix} 0 & 0 & 1 \\ 0 & 0 & f \end{bmatrix}$. Depois $L_2 \leftarrow L_2 - fL_1$: $\begin{bmatrix} 0 & 0 & \boxed{1} \\ 0 & 0 & 0 \end{bmatrix}$.
- Se $e = 0$ e $f \neq 0$: trocamos $L_1 \leftrightarrow L_2$ e recaímos no caso anterior.

**Subcaso 1.2: $b \neq 0$**

Pivô na posição $(1,2)$. Dividimos $L_1$ por $b$:

$$
\begin{bmatrix} 0 & 1 & e/b \\ 0 & d & f \end{bmatrix}
$$

$L_2 \leftarrow L_2 - dL_1$:

$$
\begin{bmatrix} 0 & \boxed{1} & e/b \\ 0 & 0 & f - de/b \end{bmatrix}
$$

- Se $f - de/b = 0$: já escalonada (reduzida), um pivô.
- Se $f - de/b \neq 0$: segundo pivô na posição $(2,3)$. Dividimos $L_2$ e zeramos acima → forma escalonada reduzida com dois pivôs.

**Subcaso 1.3: $b = 0$ e $d \neq 0$**

Trocamos $L_1 \leftrightarrow L_2$ para colocar $d$ como pivô, e recaímos no subcaso 1.2.

---

#### caso 2: $a \neq 0$
^caso-2-a-nao-zero

$a$ é o pivô da posição $(1,1)$. Dividimos $L_1$ por $a$:

$$
\begin{bmatrix} 1 & b/a & e/a \\ c & d & f \end{bmatrix}
$$

$L_2 \leftarrow L_2 - cL_1$ (zeramos abaixo do pivô):

$$
\begin{bmatrix} \boxed{1} & b/a & e/a \\ 0 & d - cb/a & f - ce/a \end{bmatrix}
$$

Chamemos $d' = d - cb/a$ e $f' = f - ce/a$.

**Subcaso 2.1: $d' = 0$ e $f' = 0$**

$$
\begin{bmatrix} 1 & b/a & e/a \\ 0 & 0 & 0 \end{bmatrix}
$$

Já escalonada. Um pivô.

**Subcaso 2.2: $d' \neq 0$**

Segundo pivô na posição $(2,2)$. Dividimos $L_2$ por $d'$:

$$
\begin{bmatrix} 1 & b/a & e/a \\ 0 & \boxed{1} & f'/d' \end{bmatrix}
$$

$L_1 \leftarrow L_1 - (b/a)L_2$ (zeramos acima do segundo pivô) → forma escalonada reduzida com dois pivôs.

**Subcaso 2.3: $d' = 0$ e $f' \neq 0$**

$$
\begin{bmatrix} 1 & b/a & e/a \\ 0 & 0 & f' \end{bmatrix}
$$

Segundo pivô na posição $(2,3)$. Dividimos $L_2$ por $f'$:

$$
\begin{bmatrix} 1 & b/a & e/a \\ 0 & 0 & \boxed{1} \end{bmatrix}
$$

$L_1 \leftarrow L_1 - (e/a)L_2$ → forma escalonada reduzida com dois pivôs.

---

#### caso restante: $a = 0$ e $c \neq 0$
^caso-3-troca

Trocamos $L_1 \leftrightarrow L_2$:

$$
\begin{bmatrix} c & d & f \\ 0 & b & e \end{bmatrix}
$$

Agora $c \neq 0$ é o pivô. Recaímos no [[#^caso-2-a-nao-zero|caso 2]].

---

#### descrição do algoritmo de Gauss (eliminação gaussiana) #algebra/definição/algoritmo-gauss
^algoritmo-gauss

A análise de casos acima revela um padrão que se repete independentemente do tamanho da matriz. O **algoritmo de Gauss** para uma matriz $m \times n$ pode ser descrito assim:

**Passo 1.** Olhe para a primeira coluna. Se todos os elementos são zero, ignore-a e passe para a próxima coluna.

**Passo 2.** Se há algum elemento não nulo, troque linhas (se necessário) para colocá-lo na primeira linha. Este é o **pivô**.

**Passo 3.** Use operações do tipo 3 ($L_i \leftarrow L_i - \lambda L_1$) para zerar todas as entradas abaixo do pivô.

**Passo 4.** Repita os passos 1–3 para a **submatriz** formada pelas linhas e colunas restantes (abaixo e à direita do pivô encontrado).

O processo para quando não há mais linhas ou colunas a examinar. O resultado é uma matriz na [[aula-01-escalonamento#^matriz-escalonada|forma escalonada]]. Para obter a [[aula-05-escalonada-reduzida-inversa#^matriz-escalonada-reduzida|forma escalonada reduzida]], aplica-se a [[aula-05-escalonada-reduzida-inversa#^eliminacao-gauss-jordan|fase de redução]] (dividir pelos pivôs e zerar acima).

---

#### conclusão: o algoritmo sempre termina #algebra/proposição/escalonamento-sempre-termina
^escalonamento-sempre-termina

Em cada passo do algoritmo, ou encontramos um pivô ou avançamos de coluna. Como a matriz é finita ($m$ linhas, $n$ colunas), o processo **sempre termina**.

> **Conclusão:** Toda matriz $A \in M_{m \times n}(\mathbb{R})$ pode ser levada à [[aula-05-escalonada-reduzida-inversa#^matriz-escalonada-reduzida|forma escalonada reduzida]] pelo algoritmo de Gauss-Jordan.