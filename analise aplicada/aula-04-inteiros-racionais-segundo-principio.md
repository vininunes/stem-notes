#### recapitulação
^recapitulacao-aula-04

Onde estávamos? Objetivo: [[aula-01-numeros-reais-corpos#^conjunto-numeros-reais|corpo ordenado completo]] ($= \mathbb{R}$) — ainda no corpo ordenado.

$$
K = (K, \underbrace{+, \cdot}_{\text{operações}}, \underbrace{P}_{\text{positivos}}) \quad \text{corpo ordenado}
$$

---

#### naturais — resumo
^naturais-resumo

**Def.** $I \subseteq K$ é [[aula-03-naturais-e-inducao#^definicao-conjunto-indutivo|indutivo]] se $1 \in I$ e $x \in I \implies x + 1 \in I$.

**Def.** $\mathbb{N} = \displaystyle\bigcap_{I \text{ indutivo}} I$. Provamos que [[aula-03-naturais-e-inducao#^proposicao-N-indutivo|$\mathbb{N}$ também é indutivo]]. Portanto $\mathbb{N}$ é o "menor" conjunto indutivo.

---

#### proposição: $\mathbb{N} \subseteq P$ #analise/proposição/N-contido-P
^proposicao-N-contido-P

**Proposição.** $\mathbb{N} \subseteq P$.

**Prova:** $P$ é indutivo (pois $1 \in P$ pelo [[aula-02-corpos-ordenados#^corolario-um-positivo|corolário $1 > 0$]], e se $x \in P$ então $x + 1 \in P$ por [[aula-02-corpos-ordenados#^definicao-corpo-ordenado|(P1)]]). Como $\mathbb{N}$ é a interseção de todos os indutivos, $\mathbb{N} \subseteq P$. $\blacksquare$

---

#### definição dos inteiros #analise/definição/inteiros
^definicao-inteiros

$$
\mathbb{Z} \stackrel{\text{def}}{=} \mathbb{N} \cup \{0\} \cup (-\mathbb{N})
$$

$\mathbb{Z}$ é fechado por $+$ e $\cdot$.

**Obs:** $(\mathbb{Z}, +, \cdot)$ (com as mesmas operações de $K$) satisfaz:
- [[aula-01-numeros-reais-corpos#^axiomas-adicao|(A1), (A2), (A3)]] com o $0$ de $K$
- [[aula-01-numeros-reais-corpos#^axiomas-adicao|(A4)]]
- [[aula-01-numeros-reais-corpos#^axioma-distributivo|(D)]]
- [[aula-01-numeros-reais-corpos#^axiomas-multiplicacao|(M1), (M2), (M3)]] com o $1$ de $K$

Mas **não vale** [[aula-01-numeros-reais-corpos#^axiomas-multiplicacao|(M4)]]: $\forall\, x \notin \{-1, 1\}$, $\nexists\, x^{-1}$ em $\mathbb{Z}$.

$\implies$ $\mathbb{Z}$ **não é corpo**.

---

#### definição dos racionais #analise/definição/racionais
^definicao-racionais

$$
\mathbb{Q} = \left\{ x \in K \;\middle|\; x = \frac{p}{q},\; p \in \mathbb{Z},\; q \in \mathbb{N} \right\}
$$

---

#### $\mathbb{Q}$ é corpo #analise/proposição/Q-corpo
^proposicao-Q-corpo

$(\mathbb{Q}, +, \cdot)$ é corpo?

**1) $\mathbb{Q}$ é fechado por $+$ e $\cdot$:**

$$
\frac{p}{q} + \frac{p'}{q'} = \frac{pq' + qp'}{qq'} \quad \leftarrow \underbrace{pq' + qp'}_{\in \mathbb{Z}},\; \underbrace{qq'}_{\in \mathbb{N} \text{ (Ex. 12)}}
$$

$$
\frac{p}{q} \cdot \frac{p'}{q'} = \frac{pp'}{qq'}
$$

**2) Os axiomas de corpo:**

[[aula-01-numeros-reais-corpos#^axiomas-adicao|A1, A2, A3]], [[aula-01-numeros-reais-corpos#^axioma-distributivo|D]], [[aula-01-numeros-reais-corpos#^axiomas-multiplicacao|M1, M2, M3]] são imediatos (operações herdadas de $K$).

**A4 (oposto):** $-\dfrac{p}{q} = \dfrac{-p}{q}$. $\checkmark$

**M4 (inverso):** $\left(\dfrac{p}{q}\right)^{-1} = \dfrac{q}{p}$, se $\dfrac{p}{q} \neq 0$ ($\iff p \neq 0$). $\checkmark$

$\implies (\mathbb{Q}, +, \cdot)$ **é corpo**.

---

#### $\mathbb{Q}$ é corpo ordenado #analise/proposição/Q-corpo-ordenado
^proposicao-Q-corpo-ordenado

Além disso, $(\mathbb{Q}, +, \cdot, \mathbb{Q} \cap P)$ é corpo ordenado.

$$
\mathbb{Q} \cap P = \left\{ x \in K \;\middle|\; x = \frac{p}{q},\; p \in \mathbb{N},\; q \in \mathbb{N} \right\}
$$

**Exercício:** Mostrar que os axiomas de [[aula-02-corpos-ordenados#^definicao-corpo-ordenado|corpo ordenado]] valem.

> $\mathbb{Q}$ é o "menor" corpo ordenado (está em todos os corpos ordenados).

---

#### voltemos aos naturais — princípio da indução dissecado
^inducao-dissecado

Aula passada: [[aula-03-naturais-e-inducao#^principio-inducao|Princípio da Indução]].

$$
X \subseteq \mathbb{N},\; X \text{ indutivo} \implies X = \mathbb{N}
$$

Dissecando: se $X \subseteq \mathbb{N}$ e se

$$
\begin{cases} 1 \in X \\ n \in X \implies n + 1 \in X \end{cases} \quad \underbrace{\text{(X é indutivo)}}
$$

então $X = \mathbb{N}$ (pois $\mathbb{N} \subseteq X$, já que $X$ é indutivo).

**Uso mais comum:** propriedades dos naturais. $P(n)$: a propriedade $P$ vale para $n \in \mathbb{N}$. Define-se $X = \{m \in \mathbb{N} \mid P(m)\}$.

---

#### segmentos iniciais e segundo princípio da indução #analise/definição/segmento-inicial
^definicao-segmento-inicial

**Definição.** $I_n = \{k \in \mathbb{N} \mid k \leq n\}$ (segmento inicial).

---

#### segundo princípio da indução #analise/proposição/segundo-principio-inducao
^segundo-principio-inducao

**Segundo Princípio da Indução.** Se $X \subseteq \mathbb{N}$ e

$$
\begin{cases} 1 \in X \\ I_n \subseteq X \implies n + 1 \in X \end{cases}
$$

então $X = \mathbb{N}$.

> Aqui $I_n \subseteq X$ significa que $k \in X$ para todo $k \leq n$. A hipótese indutiva é mais forte: assumimos a propriedade para **todos** os antecessores, não só para $n$.

---

#### exemplo: decomposição em fatores primos #analise/exemplo/fatores-primos
^exemplo-fatores-primos

**Exemplo (Ex. 22):** Decomposição em fatores primos — usa o [[#^segundo-principio-inducao|Segundo Princípio da Indução]].

---

#### exemplo geométrico: soma dos ângulos internos #analise/exemplo/soma-angulos
^exemplo-soma-angulos

**Afirmação:** $\forall\, n \geq 1$ e $\forall$ polígono (plano) de $2 + n$ lados, a soma dos ângulos internos é $180 \cdot n$.

- $n = 1$: triângulo ($3$ lados), soma $= 180°$
- $n = 2$: quadrilátero ($4$ lados), soma $= 360°$
- ...

**Esboço de prova (por indução forte):**

**Base:** $n = 1$: vale, usando algum argumento geométrico.

**Passo indutivo:** Suponha que valha para todo $k \leq n$, com $n \geq 1$. Queremos provar para $n + 1$ (polígono de $2 + (n+1)$ lados).

**Caso 1:** O polígono $Q$ é convexo — corta-se com uma diagonal, dividindo em dois polígonos menores.

**Caso 2:** $Q$ não é convexo. Decompomos $Q$ em dois polígonos $Q'$ e $Q''$:
- $Q$ tem $2 + (n+1)$ lados
- $Q''$ tem $2 + k$ lados (por construção)

Quantos lados tem $Q'$?

$$
\#Q' = \#Q - (\#Q'' - 1) + 1 = 2 + \#Q - \#Q''
$$

$$
2 + k' = 2 + (2 + (n+1)) - (2+k)
$$

$$
k + k' = n + 1
$$

Logo $k, k' \leq n$. Pela hipótese indutiva (vale para $k, k' \leq n$):

$$
\Sigma(Q) = 360 \cdot k + \Sigma(Q') - \Sigma(Q'')
$$

$$
= 360 \cdot k + 180 \cdot 2k - 180 \cdot k' - 180 \cdot k
$$

Hmm, corrigindo pela lousa:

$$
\Sigma(Q'') + \Sigma(Q) = \Sigma(Q') + 360 \cdot k
$$

$$
\Sigma(Q) = 360 \cdot k + \Sigma(Q') - \Sigma(Q'')
$$

Pela hipótese indutiva (vale para $k, k' \leq n$):

$$
= 180 \cdot 2k + 180 \cdot k' - 180 \cdot k = 180 \cdot k + 180 \cdot k' = 180(k + k') = 180(n+1) \quad \blacksquare
$$

---

#### prova do segundo princípio da indução #analise/proposição/prova-segundo-principio
^prova-segundo-principio

**Prova do 2º Princípio da Indução** (usando o 1º).

**Hipótese:** $X \subseteq \mathbb{N}$ t.q. $1 \in X$ e $I_n \subseteq X \implies n+1 \in X$.

**Tese:** $X = \mathbb{N}$.

Seja $Y = \{n \in \mathbb{N} \mid I_n \subseteq X\}$.

**Estratégia:** mostrar que $Y$ é [[aula-03-naturais-e-inducao#^definicao-conjunto-indutivo|indutivo]]. Sendo indutivo, $Y = \mathbb{N}$.

$$
\implies \forall\, n \in \mathbb{N},\; n \in Y \implies \forall\, n \in \mathbb{N},\; I_n \subseteq X \implies \forall\, n \in \mathbb{N},\; n \in X \implies \mathbb{N} \subseteq X
$$

$$
\implies X = \mathbb{N}
$$

**Falta provar que $Y$ é indutivo:**

$\vdash$ $1 \in Y$: $1 \in X$ (hipótese) $\implies I_1 = \{1\} \subseteq X \implies 1 \in Y$. $\checkmark$

$\vdash$ $m \in Y \implies m+1 \in Y$:

$m \in Y \implies I_m \subseteq X \implies$ (pela hipótese, $I_m \subseteq X$, e também $m + 1 \in X$) $\implies$

$$
I_m \cup \{m+1\} \subseteq X \iff I_{m+1} \subseteq X \iff m + 1 \in Y \quad \checkmark
$$

Portanto $Y$ é indutivo, logo $Y = \mathbb{N}$, logo $X = \mathbb{N}$. $\blacksquare$

---

#### aula que vem: princípio da boa ordem
^preview-boa-ordem

**Princípio da Boa Ordem.** Seja $A \subseteq \mathbb{N}$, $A \neq \emptyset$. Então $A$ tem um menor elemento:

$$
\exists\, a \in A \;\text{t.q.}\; a \leq b, \;\forall\, b \in A
$$