#### objetivo da aula
^objetivo-aula-05

Falar de conjuntos finitos, infinitos, enumeráveis e não-enumeráveis (Cap. 1 do Elon).

Precisamos "plugar" nosso $\mathbb{N} \subseteq K$ corpo ordenado nos Axiomas de Peano.

---

#### axiomas de Peano #analise/definição/axiomas-peano
^axiomas-peano

Maneira de definir os naturais **sem construí-los**.

Existe um conjunto $\mathbb{N}$ (os números naturais) tal que existe uma função $S : \mathbb{N} \to \mathbb{N}$ (função **sucessora** ou **successor**) que cumpre:

**(i)** $S$ é injetora. #analise/axioma/peano-i

**(ii)** Exceto um elemento de $\mathbb{N}$, que chamaremos de "$1$", todos os outros são sucessor de alguém. #analise/axioma/peano-ii

Ou seja:

$$
\forall\, x \in \mathbb{N} \setminus \{1\},\; \exists\, y \in \mathbb{N} \;\text{t.q.}\; S(y) = x
$$

Ou ainda: $S : \mathbb{N} \to \mathbb{N} \setminus \{1\}$ é **sobrejetora**.

**(iii)** Para $X \subseteq \mathbb{N}$, se #analise/axioma/peano-iii

$$
\begin{cases} 1 \in X \\ m \in X \implies S(m) \in X \end{cases} \quad \text{(Princípio da Indução)}
$$

então $X = \mathbb{N}$.

> A partir desses Axiomas, constroem-se a adição e a multiplicação de naturais, e todas as propriedades dos números naturais.

---

#### $\mathbb{N} \subseteq K$ satisfaz os Axiomas de Peano? #analise/proposição/N-satisfaz-peano
^N-satisfaz-peano

**Definição.** $m \in \mathbb{N}$ é **antecessor** de $n \in \mathbb{N}$ se $S(m) = n$ (se existir).

> O Axioma (ii) diz: só $1$ não tem antecessor.

Vamos definir $S : \mathbb{N} \to \mathbb{N}$ por $S(n) = n + 1$.

---

#### verificação (i): $S$ é injetora #analise/proposição/S-injetora
^verificacao-S-injetora

**Prova:** Suponha $S(n) = S(m)$.

$$
\xrightarrow{\text{def. de } S} n + 1 = m + 1 \xrightarrow{\text{lei do cancelamento de } K} n = m \quad \checkmark \quad \blacksquare
$$

---

#### verificação (ii): só $1$ não tem antecessor #analise/proposição/S-sobrejetora
^verificacao-S-sobrejetora

**1ª parte** $\vdash$ Se $x \in \mathbb{N}$ não tem antecessor, então $x = 1$.

**Prova:** Suponha $x \neq 1$ sem antecessor. Vamos chegar num absurdo.

Vamos provar que $\mathbb{N} \setminus \{x\}$ é [[aula-03-naturais-e-inducao#^definicao-conjunto-indutivo|indutivo]]. Com isso, por Indução, $\mathbb{N} \setminus \{x\} = \mathbb{N}$, absurdo (pois $x \in \mathbb{N}$).

$\mathbb{N} \setminus \{x\}$ é indutivo:

- $1 \in \mathbb{N} \setminus \{x\}$? Sim: $1 \in \mathbb{N}$ e $1 \neq x$. $\checkmark$
- Suponha $m \in \mathbb{N} \setminus \{x\}$. Então $m + 1 \in \mathbb{N} \setminus \{x\}$?
  - Sim: pois $m \in \mathbb{N}$, logo $m + 1 \in \mathbb{N}$.
  - E $m + 1 \neq x$, pois $m + 1$ tem antecessor ($= m$) e $x$ não tem antecessor. $\checkmark$

Logo $\mathbb{N} \setminus \{x\}$ é indutivo $\implies \mathbb{N} \setminus \{x\} = \mathbb{N}$, absurdo. $\blacksquare$

**2ª parte:** $1$ tem antecessor? Seria o zero, mas $\mathbb{N} \subseteq P$ e $0 \notin P$. Logo $1$ não tem antecessor em $\mathbb{N}$. $\checkmark$

---

#### verificação (iii): princípio da indução
^verificacao-iii

A (iii) é imediata pois $\mathbb{N}$ construído em $K$ é [[aula-03-naturais-e-inducao#^proposicao-N-indutivo|indutivo]]. $\checkmark$

> Portanto $\mathbb{N} \subseteq K$ satisfaz os [[#^axiomas-peano|Axiomas de Peano]].

---

#### lema 1: não há natural entre $1$ e $2$ #analise/lema/nenhum-natural-entre-1-e-2
^lema-1

Estamos no $\mathbb{N} \subseteq K$.

**Lema 1.** $\nexists\, x \in \mathbb{N}$ tal que $1 < x < 2 = 1 + 1$.

**Prova:** Suponha que exista: $x \in \mathbb{N}$ e $x \neq 1$ (pois $x > 1$).

$\implies x$ tem antecessor em $\mathbb{N}$ (pelo [[#^verificacao-S-sobrejetora|Axioma (ii) demonstrado]])

$\implies x - 1 \in \mathbb{N}$

Mas $x - 1 < 2 - 1 = 1$, i.e., $x - 1 \in \mathbb{N}$ e $x - 1 < 1$.

Tem algum natural menor do que $1$?

---

#### afirmação: $\forall\, n \in \mathbb{N},\; n \geq 1$ #analise/proposição/natural-geq-1
^afirmacao-n-geq-1

**Afirmação.** $\forall\, n \in \mathbb{N},\; n \geq 1$ (ou seja, não há natural $< 1$).

**Prova** (por [[aula-03-naturais-e-inducao#^principio-inducao|indução]]):

**Base:** Vale para $n = 1$: $1 \geq 1$. $\checkmark$

**Passo:** Suponha que vale para $n$: $n \geq 1$.

$$
\implies n + 1 \geq 1 + 1 > 1 \implies n + 1 > 1 \implies n + 1 \geq 1 \quad \checkmark \quad \blacksquare
$$

> Voltando ao [[#^lema-1|Lema 1]]: obtivemos $x - 1 \in \mathbb{N}$ com $x - 1 < 1$, contradizendo esta afirmação. Logo não existe tal $x$. $\blacksquare$

---

#### lema 2: não há natural entre $n$ e $n+1$ #analise/lema/nenhum-natural-entre-n-e-n+1
^lema-2

**Lema 2.** $\forall\, n \in \mathbb{N}$, $\nexists\, x \in \mathbb{N}$ t.q. $n < x < n + 1$.

**Prova** (por [[aula-03-naturais-e-inducao#^principio-inducao|indução]] em $n$):

**Base:** Pelo [[#^lema-1|Lema 1]], vale para $n = 1$. $\checkmark$

**Passo:** Suponha que vale para $m$, i.e., $\nexists\, x \in \mathbb{N}$ t.q. $m < x < m + 1$.

Queremos mostrar que vale para $m + 1$, isto é, $\nexists\, y \in \mathbb{N}$ t.q. $m + 1 < y < m + 2$.

Para isso, tomamos $y \in K$ t.q. $m + 1 < y < m + 2$ e mostraremos que $y \notin \mathbb{N}$.

Tome $x = y - 1$: $m < x < m + 1$.

Pela hipótese indutiva, $x \notin \mathbb{N}$.

$$
\implies y = x + 1 = \begin{cases} 1 & (\implies x = 0, \text{ absurdo}) \\ \text{ou } y = x + 1 \in \mathbb{N} \setminus \{1\} & \implies x \in \mathbb{N} \text{ (antecessor), absurdo} \end{cases}
$$

$\implies y \notin \mathbb{N}$. $\blacksquare$

---

#### outra leitura do lema 2 #analise/corolário/leitura-lema-2
^outra-leitura-lema-2

Se $n, m \in \mathbb{N}$ e $m > n$, então $m \geq n + 1$.

> Senão, $n < m < n + 1$, e o [[#^lema-2|Lema 2]] não deixa.

---

#### teorema: princípio da boa ordenação #analise/proposição/boa-ordenacao
^principio-boa-ordenacao

**Teorema (Princípio da Boa Ordenação).** Se $A \subseteq \mathbb{N}$ e $A \neq \emptyset$, então $A$ tem um **menor elemento**, i.e.:

$$
\exists\, \ell \in A \;\text{t.q.}\; \forall\, k \in A,\; k \geq \ell
$$

**Prova:**

**Caso $1 \in A$:** $1$ é o menor elemento de $A$ (pois [[#^afirmacao-n-geq-1|$\forall\, n \in \mathbb{N},\; n \geq 1$]]). $\checkmark$

**Caso $1 \notin A$:** Olhemos para $A^c$ (complementar em $\mathbb{N}$): $1 \notin A \implies 1 \in A^c$.

Suponha que valha o [[aula-04-inteiros-racionais-segundo-principio#^segundo-principio-inducao|2º Princípio da Indução]] para $A^c$:
- $1 \in A^c$ $\checkmark$
- $I_n \subseteq A^c \implies n + 1 \in A^c$

Concluiríamos que $A^c = \mathbb{N}$, logo $A = \emptyset$. Mas $A \neq \emptyset$!

Então **existe** $n \in \mathbb{N}$ t.q.:

$$
I_n \subseteq A^c \quad \text{e} \quad n + 1 \notin A^c
$$

ou seja: $I_n \cap A = \emptyset$ e $n + 1 \in A$.

Seja $\ell = n + 1$.

**Af:** $\ell$ é o menor elemento de $A$.

**Prova:** $k \in A \implies k \notin I_n \implies k > n \implies k \geq n + 1 = \ell$. $\checkmark$ $\blacksquare$

---

#### justificativa: $k \notin I_n \implies k > n$
^justificativa-In

Por que $k \notin I_n \implies k > n$?

$$
I_n = \{j \in \mathbb{N} \mid j \leq n\}
$$

$$
\implies \text{se } k \notin I_n \implies \neg(k \leq n) \implies k > n
$$