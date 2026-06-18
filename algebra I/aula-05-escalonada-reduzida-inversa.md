#### matriz escalonada reduzida #algebra/definição/matriz-escalonada-reduzida
^matriz-escalonada-reduzida

Uma matriz está na forma **escalonada reduzida** (ou **forma canônica por linhas**) se satisfaz:

1. Está na [[aula-01-escalonamento#^matriz-escalonada|forma escalonada]]
2. Todo [[aula-01-escalonamento#^matriz-escalonada|pivô]] é igual a $1$
3. Cada pivô é o **único elemento não nulo** da sua coluna (zeros acima e abaixo)

**Exemplo:**

$$
\left[\begin{array}{cccc|c}
\boxed{1} & 0 & 3 & 0 & 2 \\
0 & \boxed{1} & -1 & 0 & 5 \\
0 & 0 & 0 & \boxed{1} & 4
\end{array}\right]
$$

Compare com a forma apenas escalonada, onde os pivôs podem ser diferentes de 1 e pode haver entradas não nulas acima dos pivôs:

$$
\left[\begin{array}{cccc|c}
\boxed{2} & 3 & -1 & 4 & 5 \\
0 & \boxed{1} & 7 & 2 & 3 \\
0 & 0 & 0 & \boxed{5} & 1
\end{array}\right]
$$

Para passar da forma escalonada à reduzida, usa-se a **eliminação de Gauss-Jordan**: após escalonar, divide-se cada linha pelo seu pivô e elimina-se as entradas **acima** dos pivôs (de baixo para cima).

---

#### unicidade da forma escalonada reduzida #algebra/teorema/unicidade-escalonada-reduzida
^unicidade-escalonada-reduzida

**Teorema:** Toda matriz $A$ possui uma **única** forma escalonada reduzida.

Ou seja, independentemente da sequência de [[aula-01-escalonamento#^operacoes-elementares-linhas|operações elementares]] escolhida para escalonar $A$, o resultado final na forma escalonada reduzida é sempre o mesmo.

> **Observação:** A forma escalonada (não reduzida) **não** é única — diferentes sequências de operações podem gerar formas escalonadas distintas. A unicidade vale apenas para a forma **reduzida**.

---

#### eliminação de Gauss-Jordan #algebra/definição/eliminação-gauss-jordan
^eliminacao-gauss-jordan

O processo para transformar qualquer matriz na sua [[#^matriz-escalonada-reduzida|forma escalonada reduzida]] usando as três [[aula-04-propriedades-produto-matrizes#^matrizes-elementares|operações elementares]]:

**Fase 1 — Escalonamento (de cima para baixo):**

Usa [[aula-01-escalonamento#^eliminacao-gaussiana|eliminação gaussiana]] para obter a forma escalonada:

1. **Tipo 1** ($L_i \leftrightarrow L_j$): se necessário, permuta linhas para colocar um elemento não nulo na posição do pivô
2. **Tipo 3** ($L_i \leftarrow L_i + \lambda L_j$): zera todas as entradas **abaixo** de cada pivô

**Fase 2 — Redução (de baixo para cima):**

Partindo da forma escalonada, transforma-a na forma escalonada reduzida:

3. **Tipo 2** ($L_i \leftarrow \frac{1}{\text{pivô}} \cdot L_i$): divide cada linha pelo seu pivô, tornando todos os pivôs iguais a $1$
4. **Tipo 3** ($L_i \leftarrow L_i + \lambda L_j$): começando pelo último pivô e subindo, zera todas as entradas **acima** de cada pivô

**Exemplo:** reduzir a matriz

$$
A = \begin{bmatrix} 1 & 2 & 1 \\ 2 & 5 & 3 \\ 0 & 1 & 2 \end{bmatrix}
$$

*Fase 1 — escalonamento:*

$L_2 \leftarrow L_2 - 2L_1$ — **Tipo 3** (soma de múltiplo de linha): subtrai $2 \times L_1$ de $L_2$ para zerar a entrada $(2,1)$ abaixo do pivô:

$$
\begin{bmatrix} \boxed{1} & 2 & 1 \\ 0 & 1 & 1 \\ 0 & 1 & 2 \end{bmatrix}
$$

$L_3 \leftarrow L_3 - L_2$ — **Tipo 3**: subtrai $L_2$ de $L_3$ para zerar a entrada $(3,2)$ abaixo do pivô:

$$
\begin{bmatrix} \boxed{1} & 2 & 1 \\ 0 & \boxed{1} & 1 \\ 0 & 0 & \boxed{1} \end{bmatrix}
$$

Forma escalonada obtida. Todos os pivôs já são $1$, então a **Tipo 2** (dividir pelo pivô) não é necessária.

*Fase 2 — redução (zerar acima dos pivôs):*

$L_2 \leftarrow L_2 - L_3$ — **Tipo 3**: subtrai $L_3$ de $L_2$ para zerar a entrada $(2,3)$ acima do pivô da coluna 3:

$$
\begin{bmatrix} 1 & 2 & 1 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}
$$

$L_1 \leftarrow L_1 - L_3$ — **Tipo 3**: subtrai $L_3$ de $L_1$ para zerar a entrada $(1,3)$ acima do pivô da coluna 3:

$$
\begin{bmatrix} 1 & 2 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}
$$

$L_1 \leftarrow L_1 - 2L_2$ — **Tipo 3**: subtrai $2 \times L_2$ de $L_1$ para zerar a entrada $(1,2)$ acima do pivô da coluna 2:

$$
\begin{bmatrix} \boxed{1} & 0 & 0 \\ 0 & \boxed{1} & 0 \\ 0 & 0 & \boxed{1} \end{bmatrix} = I_3
$$

A forma escalonada reduzida de $A$ é $I_3$.

---

#### matrizes invertíveis #algebra/definição/matriz-inversa
^matriz-inversa

**Definição:** Uma matriz $A \in M_{n \times n}(\mathbb{R})$ é **invertível** se existe $B \in M_{n \times n}(\mathbb{R})$ tal que:

$$AB = BA = I_n$$

**Exemplo:** a matriz

$$
A = \begin{pmatrix} 1 & 0 & 1 \\ 0 & 1 & 2 \\ 1 & 1 & 4 \end{pmatrix}
$$

é invertível, pois tomando

$$
B = \begin{pmatrix} 2 & 1 & -1 \\ 2 & 3 & -2 \\ -1 & -1 & 1 \end{pmatrix}
$$

temos $AB = I$ e $BA = I$:

$$
AB = \begin{pmatrix} 1 & 0 & 1 \\ 0 & 1 & 2 \\ 1 & 1 & 4 \end{pmatrix} \begin{pmatrix} 2 & 1 & -1 \\ 2 & 3 & -2 \\ -1 & -1 & 1 \end{pmatrix} = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix} = I
$$

---

#### nem toda matriz é invertível #algebra/observação/nao-invertivel
^nao-invertivel

**(i)** Nem toda matriz é invertível. Por exemplo:

- Se $A$ possui uma **linha de zeros**, então para qualquer $B$, o produto $AB$ também terá uma linha de zeros, logo $AB \neq I$
- Se $A$ possui uma **coluna de zeros**, então para qualquer $B$, o produto $BA$ também terá uma coluna de zeros, logo $BA \neq I$

Em ambos os casos, $A$ não pode ser invertível.

---

#### propriedades da inversa #algebra/proposição/propriedades-inversa
^propriedades-inversa

**(ii)** Se $A$ é invertível e $\alpha \neq 0$, então $\alpha A$ é invertível:

Como $\exists\, B$ tal que $AB = BA = I$, temos:

$$(\alpha A)\left(\tfrac{1}{\alpha}B\right) = \left(\alpha \cdot \tfrac{1}{\alpha}\right)AB = AB = I$$

$$\left(\tfrac{1}{\alpha}B\right)(\alpha A) = \left(\tfrac{1}{\alpha} \cdot \alpha\right)BA = BA = I$$

Logo $(\alpha A)^{-1} = \frac{1}{\alpha}A^{-1}$.

---

**(iii)** Se $A, B \in M_n(\mathbb{R})$ são invertíveis, então o produto $AB$ é invertível:

Como $A$ é invertível, $\exists\, C$ tal que $AC = CA = I$. Como $B$ é invertível, $\exists\, D$ tal que $BD = DB = I$.

Então:

$$(AB)(DC) = A(BD)C = AIC = AC = I$$

$$(DC)(AB) = D(CA)B = DIB = DB = I$$

Logo $(AB)^{-1} = B^{-1}A^{-1}$ — a inversa do produto **inverte a ordem**.

---

#### unicidade da inversa #algebra/proposição/unicidade-inversa
^unicidade-inversa

**(iv)** Se $B, C \in M_n(\mathbb{R})$ são tais que $AB = CA = I$, então $B = C$ (e portanto $A$ é invertível).

**Demonstração:**

$$B = IB = (CA)B = C(AB) = CI = C$$

Em particular, se $A$ é invertível, então sua inversa é **única**, denotada por $A^{-1}$.

---

#### transposta de invertível é invertível #algebra/proposição/transposta-inversa
^transposta-inversa

Se $A$ é invertível com $AB = BA = I$, então $A^T$ também é invertível, pois:

$$A^T B^T = (BA)^T = I^T = I$$
$$B^T A^T = (AB)^T = I^T = I$$

Logo $(A^T)^{-1} = (A^{-1})^T$.

---

**(v)** Toda [[aula-04-propriedades-produto-matrizes#^matrizes-elementares|matriz elementar]] é invertível, e sua inversa é também uma matriz elementar **do mesmo tipo**:

- **Tipo 1** ($L_i \leftrightarrow L_j$): a inversa é ela mesma — aplicar a mesma permutação desfaz a troca
- **Tipo 2** ($L_i \leftarrow \alpha L_i$): a inversa é $L_i \leftarrow \frac{1}{\alpha} L_i$
- **Tipo 3** ($L_i \leftarrow L_i + \alpha L_j$): a inversa é $L_i \leftarrow L_i - \alpha L_j$
