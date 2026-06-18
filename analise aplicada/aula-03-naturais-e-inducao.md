#### construção dos números naturais #analise/definição/naturais-construção
^construcao-naturais

Vamos construir um subconjunto $\mathbb{N}$ de $K$ (um [[aula-02-corpos-ordenados#^definicao-corpo-ordenado|corpo ordenado]]) e chamaremos de **números naturais**. A princípio, para cada corpo ordenado $K$ podemos fazer esta construção e obter $\mathbb{N}_K$, mas todos os $\mathbb{N}_K$ são essencialmente iguais.

**Intuição:** $1 \in K$, $1 + 1 \in K$, $1 + 1 + 1 \in K$, ...

A propriedade que queremos capturar: #analise/definição/propriedade-indutiva-informal
1. $1 \in \mathbb{N}$
2. $x \in \mathbb{N} \implies x + 1 \in \mathbb{N}$

O problema é que **vários conjuntos** têm essa propriedade e contêm elementos que não queremos:
- $\{-1, 0, 1, 1+1, 1+1+1, \dots\}$
- $\left\{\frac{1}{2}, 1, \frac{3}{2}, 2, \dots\right\}$
- $P$ (os positivos)
- $K$ inteiro

Queremos **filtrar** de forma que o único conjunto que tenha essa propriedade seja os naturais. A ideia: os naturais são a **interseção** de todos os conjuntos que tenham essas propriedades.

---

#### conjunto indutivo #analise/definição/conjunto-indutivo
^definicao-conjunto-indutivo

**Definição.** $I \subseteq K$ é um **conjunto indutivo** se satisfaz:

$$
\begin{cases} 1 \in I \\ x \in I \implies x + 1 \in I \end{cases}
$$

**Obs:** Os 4 exemplos anteriores ($\{-1, 0, 1, \dots\}$, $\{\frac{1}{2}, 1, \frac{3}{2}, \dots\}$, $P$, $K$) são todos conjuntos indutivos.

---

#### definição dos números naturais #analise/definição/naturais
^definicao-naturais

**Definição.**

$$
\mathbb{N} = \bigcap_{I \text{ indutivo}} I
$$

Ou seja: $x \in \mathbb{N} \iff x \in I$, para todo $I$ conjunto indutivo.

> Os números naturais são o **menor conjunto indutivo** de $K$.

---

#### proposição: $\mathbb{N}$ é indutivo #analise/proposição/N-indutivo
^proposicao-N-indutivo

**Proposição.** $\mathbb{N}$ é indutivo.

**Prova:**

$1 \in \mathbb{N}$? Sim: $1 \in I$ para todo $I$ indutivo $\iff 1 \in \mathbb{N}$. $\checkmark$

$x \in \mathbb{N} \implies x + 1 \in \mathbb{N}$? Temos $x \in \mathbb{N} \iff x \in I$ para todo $I$ indutivo $\implies x + 1 \in I$ para todo $I$ indutivo $\iff x + 1 \in \mathbb{N}$. $\checkmark$

Portanto $\mathbb{N}$ é indutivo. $\blacksquare$

---

#### princípio da indução (finita) #analise/proposição/principio-inducao
^principio-inducao

Muitas vezes queremos mostrar que algo vale para todo natural $n \in \mathbb{N}$.

Dada uma propriedade, definimos:

$$
X = \{ n \in \mathbb{N} \mid n \text{ satisfaz a propriedade} \}
$$

Gostaríamos de mostrar que a propriedade vale para todo $n \in \mathbb{N}$, ou seja, que $X = \mathbb{N}$.

Se pensarmos que $X$ é **indutivo**, qual a consequência?

$$
\mathbb{N} \subseteq X \quad \text{mas} \quad X \subseteq \mathbb{N} \implies \boxed{X = \mathbb{N}}
$$

Então basta verificar que $X$ é indutivo (i.e., $1 \in X$ e $n \in X \implies n+1 \in X$) para concluir que a propriedade vale para todo natural.

---

#### exemplo 1: soma dos naturais #analise/exemplo/inducao-soma
^exemplo-inducao-soma

**Propriedade:** $\displaystyle\sum_{k=1}^{n} k = \frac{n(n+1)}{2}$

Defina $X = \left\{ n \in \mathbb{N} \;\middle|\; \displaystyle\sum_{k=1}^{n} k = \frac{n(n+1)}{2} \right\}$.

**Base:** $1 \in X$, pois $\displaystyle\sum_{k=1}^{1} k = 1 = \frac{1 \cdot 2}{2}$. $\checkmark$

**Passo indutivo:** Se $n \in X$, então $n+1 \in X$?

Ou seja, supondo $\displaystyle\sum_{k=1}^{n} k = \frac{n(n+1)}{2}$ (hipótese indutiva), queremos mostrar que $\displaystyle\sum_{k=1}^{n+1} k = \frac{(n+1)(n+2)}{2}$ (tese indutiva).

**Prova:**

$$
\sum_{k=1}^{n+1} k = \sum_{k=1}^{n} k + (n+1) = \frac{n(n+1)}{2} + (n+1) = \frac{n(n+1) + 2(n+1)}{2} = \frac{(n+1)(n+2)}{2}
$$

Portanto $X$ é indutivo, logo $\displaystyle\sum_{k=1}^{n} k = \frac{n(n+1)}{2}$ para todo $n \in \mathbb{N}$. $\blacksquare$

---

#### exemplo 2: $2^{2n} - 1$ é múltiplo de 3 #analise/exemplo/inducao-multiplo
^exemplo-inducao-multiplo

**Afirmação:** $2^{2n} - 1$ é múltiplo de 3, para todo $n \geq 1$.

**Base:** $n = 1$: $2^{2 \cdot 1} - 1 = 4 - 1 = 3$. $\checkmark$

**Passo indutivo:** $2^{2n} - 1$ múltiplo de $3 \implies 2^{2(n+1)} - 1$ múltiplo de $3$.

$$
2^{2(n+1)} - 1 = 2^{2n+2} - 1 = 4 \cdot 2^{2n} - 1
$$

$$
= 4 \cdot 2^{2n} - 1 - 3 + 3 = 4(2^{2n} - 1) + 3
$$

Por indução, $2^{2n} - 1 = 3k$ para algum $k \in \mathbb{N}$. Logo:

$$
2^{2(n+1)} - 1 = 4(3k) + 3 = 3(4k + 1)
$$

que é múltiplo de 3. $\blacksquare$

> **Notação:** O símbolo $\vdash$ ("turnstile") indica "queremos provar que".

---

#### cuidado com indução — o passo indutivo não basta #analise/observação/cuidado-inducao
^cuidado-inducao

**Não é suficiente** escrever a propriedade para $n+1$ e provar a propriedade para $n$. A base é essencial.

**Exemplo idiota (se fizer isso):** Afirmação falsa: $n \leq 1$ para todo $n \in \mathbb{N}$.

"Prova" furada:
- $1 \leq 1$? Sim. $\checkmark$
- Suponha que $n+1$ satisfaz: $n + 1 \leq 1 \implies n \leq 0 < 1$. $\checkmark$

Mas a direção está **invertida** — provou-se "$P(n+1) \implies P(n)$" em vez de "$P(n) \implies P(n+1)$". A propriedade é falsa.

---

#### exemplo 3 (indução adaptada): $\sqrt{n} < \displaystyle\sum_{k=1}^{n} \frac{1}{\sqrt{k}}$ #analise/exemplo/inducao-adaptada
^exemplo-inducao-adaptada

**Afirmação:** $\displaystyle\sqrt{n} < \sum_{k=1}^{n} \frac{1}{\sqrt{k}}$, para todo $n \geq 2$.

**Prova adaptada:** A base começa em $n = 2$ (não em $n = 1$).

**Base:** $n = 2$: $\sqrt{2} < 1 + \frac{1}{\sqrt{2}} \iff 2 < \sqrt{2} + 1 \approx 2{,}41$. $\checkmark$

**Passo indutivo:** Supondo que vale para $n$ (com $n > 2$), provar para $n+1$.

Queremos: $\displaystyle\sqrt{n+1} < \sum_{k=1}^{n+1} \frac{1}{\sqrt{k}}$

$$
\sqrt{n+1} = \underbrace{\sqrt{n+1} - \sqrt{n}}_{(\star)} + \sqrt{n} < \underbrace{\sum_{k=1}^{n} \frac{1}{\sqrt{k}}}_{\text{por indução}} + (\sqrt{n+1} - \sqrt{n})
$$

Basta mostrar que $\sqrt{n+1} - \sqrt{n} < \dfrac{1}{\sqrt{n+1}}$.

**Racionalização:**

$$
\sqrt{n+1} - \sqrt{n} = \frac{(\sqrt{n+1} - \sqrt{n})(\sqrt{n+1} + \sqrt{n})}{\sqrt{n+1} + \sqrt{n}} = \frac{n+1-n}{\sqrt{n+1} + \sqrt{n}} = \frac{1}{\sqrt{n+1} + \sqrt{n}} < \frac{1}{\sqrt{n+1}}
$$

Portanto $\displaystyle\sqrt{n+1} < \sum_{k=1}^{n+1} \frac{1}{\sqrt{k}}$. $\blacksquare$
