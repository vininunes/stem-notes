#### tema da aula: sequências
^titulo-aula-09

Sequências (de números reais, ou em $\mathbb{R}$).

---

#### definição: sequência #analise/definição/sequencia
^definicao-sequencia

**Definição.** Uma **sequência** em $X$ ($X = $ qualquer conjunto) é uma função

$$
f : \mathbb{N} \to X, \qquad n \mapsto f(n)
$$

> $X$, em geral, será $\mathbb{R}$.

**Notação própria de sequências:** em vez de $f(n)$ escreve-se $x_n$ — o **$n$-ésimo ponto** (ou termo) da sequência.

A sequência, nesse caso, é indicada por

$$
(x_n)
$$

que é uma contração de $(x_n)_{n \in \mathbb{N}}$ ou $(x_n)_n$.

---

#### como se define uma sequência #analise/exemplo/definir-sequencia
^formas-de-definir

**Pode ser explícita.** Por exemplo:

$$
x_n = \frac{e^n}{n!}\left(1 + (-1)^n\right), \qquad \forall\, n \in \mathbb{N}
$$

**Pode ser por recorrência.** Por exemplo:

$$
x_1 = 0, \quad x_2 = 1, \qquad x_n = x_{n-1} + x_{n-2}, \quad \forall\, n \geq 3
$$

---

#### recorrência via função iterada #analise/exemplo/recorrencia-iterada
^recorrencia-phi

Outra forma de recorrência: seja $\varphi : \mathbb{R} \to \mathbb{R}$,

$$
x_{n+1} = \varphi(x_n) \qquad (x_0 \text{ dado})
$$

> Aqui começamos em $n = 0$.

Importante como **ferramenta para aproximar soluções de equações** (p.ex. o **Método de Newton**, que serve para achar zeros / raízes de funções).

---

#### conjunto de valores de uma sequência #analise/definição/imagem-sequencia
^conjunto-valores

$$
\{x_n\} = \{x_n \mid n \in \mathbb{N}\}
$$

é o conjunto (em $X$) dos valores $x_n$. É a **imagem** da função $n \mapsto x_n$.

> **Obs:** $\{x_n\}$ pode ser **finito!** Por exemplo:
> $$
> (x_n) = (0, 1, 0, 1, 0, 1, \dots), \qquad x_n = \frac{1 + (-1)^n}{2}
> $$
> Aqui $\{x_n\} = \{0, 1\}$.

---

#### definição: sequência limitada #analise/definição/sequencia-limitada
^definicao-limitada

Sequências em $\mathbb{R}$.

**Definição.** $(x_n)$ é **limitada superiormente** se existe $b \in \mathbb{R}$ t.q.

$$
x_n \leq b, \quad \forall\, n \in \mathbb{N}
$$

**Limitada inferiormente:** existe $b \in \mathbb{R}$ t.q. $b \leq x_n$, $\forall\, n$.

**Limitada:** $a \leq x_n \leq b$, $\forall\, n$ (inferior **e** superiormente).

---

#### caracterizações da limitação #analise/proposição/limitada-modulo
^limitada-modulo

> **Exercício:** escreva as provas das duas equivalências abaixo.

$$
(x_n) \text{ limitada} \iff \exists\, M > 0 \text{ t.q. } |x_n| \leq M, \quad \forall\, n
$$

$$
(x_n) \text{ é limitada} \iff (|x_n|) \text{ é limitada}
$$

---

#### definição: sequência ilimitada #analise/definição/sequencia-ilimitada
^definicao-ilimitada

**Definição.** $(x_n)$ é **ilimitada** se não é limitada.

**Explicitamente** (negando a definição de limitada):

$$
\neg\left(\exists\, M > 0,\; \forall\, n \in \mathbb{N},\; |x_n| \leq M\right)
$$

$$
\iff \forall\, M > 0,\; \neg\left(\forall\, n \in \mathbb{N},\; |x_n| \leq M\right)
$$

$$
\iff \forall\, M > 0,\; \exists\, n \in \mathbb{N},\; |x_n| > M
$$

> **Obs:** Esse $n$ que existe depois do "$\forall\, M > 0$" depende (em geral) de $M$. Denota-se $n = n(M)$:
> $$
> \forall\, M > 0,\; \exists\, n = n(M) \in \mathbb{N},\; |x_n| > M
> $$

---

#### definição: subsequência #analise/definição/subsequencia
^definicao-subsequencia

**Subsequências.** Seja $(x_n)$ sequência. Uma subsequência é uma **parte** da sequência:

$$
x_{n_1},\, x_{n_2},\, x_{n_3},\, x_{n_4},\, \dots,\, x_{n_k},\, \dots
\qquad \text{com } n_1 < n_2 < n_3 < n_4 < \cdots
$$

**Mais formalmente:** é uma **composta de sequências**:

$$
\mathbb{N} \xrightarrow{\;\;} \mathbb{N} \xrightarrow{\;\;} \mathbb{R}, \qquad k \mapsto n_k \mapsto x_{n_k}
$$

onde $k \mapsto n_k$ é uma sequência em $\mathbb{N}$ **crescente**: $n_k < n_{k+1}$.

**Exemplo.** $(x_n) = (0, 1, 0, 1, \dots)$, com $n_k = 2k$, i.e. $(n_k) = (2, 4, 6, 8, \dots)$:

$$
(x_{n_k})_k = (x_2, x_4, x_6, x_8, \dots) = (1, 1, 1, \dots)
$$

> **Notação:** $(x_{n_k})_k$ ou, simplesmente, $(x_{n_k})$.

---

#### proposição: limitação ⟺ toda subsequência limitada #analise/proposição/subseq-limitada
^prop-subseq-limitada

**Proposição.**

$$
(x_n) \text{ é limitada (inf./sup.)} \iff \forall \text{ subseq. } (x_{n_k}) \text{ de } (x_n) \text{ é limitada (inf./sup.)}
$$

**Prova.**

**($\implies$)** $(x_n)$ limitada $\implies \exists\, M > 0$ t.q. $|x_n| \leq M$, $\forall\, n \in \mathbb{N}$. Tomo $(x_{n_k})$ qualquer: $|x_{n_k}| \leq M$, $\forall\, k \in \mathbb{N}$.

**($\impliedby$)** Se $(x_{n_k})$ é limitada para toda subsequência, então em particular a subsequência $(x_k)_k$ (caso $n_k = k$) é limitada $\implies (x_n)$ é limitada. $\blacksquare$

---

#### definição: sequência monótona #analise/definição/sequencia-monotona
^definicao-monotona

**Definição.** $(x_n)$ é **monótona** (ou monotônica) se:

$$
\boxed{x_n \leq x_{n+1}, \quad \forall\, n \in \mathbb{N}} \qquad \text{(monótona não decrescente)}
$$

ou

$$
\boxed{x_n \geq x_{n+1}, \quad \forall\, n \in \mathbb{N}} \qquad \text{(monótona não crescente)}
$$

**Casos especiais:**

$$
x_n < x_{n+1}, \quad \forall\, n \in \mathbb{N} \qquad \text{(crescente)}
$$

$$
x_n > x_{n+1}, \quad \forall\, n \in \mathbb{N} \qquad \text{(decrescente)}
$$

---

#### observações sobre monotonia #analise/observação/monotona-limitada
^obs-monotona

> **Obs:** Se $(x_n)$ é monótona não decrescente ($x_n \leq x_{n+1}$), então é **limitada inferiormente** ($x_1$ é um limitante inferior). [Analogamente para monótona não crescente / limitante superior.]
>
> **Portanto**, se $(x_n)$ é monótona não decrescente:
> $$
> (x_n) \text{ é limitada} \iff (x_n) \text{ é limitada superiormente}
> $$

> **Obs:** Se $(x_n)$ é monótona não decrescente, então **toda subsequência** de $(x_n)$ é monótona não decrescente. [Analogamente, ...]

---

#### proposição: monótona limitada ⟺ tem subsequência limitada #analise/proposição/monotona-subseq-limitada
^prop-monotona-subseq

**Proposição.** Suponha $(x_n)$ **monótona**. Então:

$$
(x_n) \text{ é limitada} \iff \exists \text{ subseq. } (x_{n_k}) \text{ limitada}
$$

> (Compare com a [[#^prop-subseq-limitada|proposição anterior]].)

**Prova.**

**($\implies$)** Já feita na proposição anterior.

**($\impliedby$)** Existe subsequência $(x_{n_k})$ limitada: **tome uma**. Vamos fazer o caso de $(x_n)$ monótona não decrescente ($x_n \leq x_{n+1}$, $\forall\, n$). (O outro caso é análogo.)

Pela [[#^obs-monotona|observação anterior]], $(x_{n_k})$ é monótona não decrescente e, por hipótese, limitada, logo **limitada superiormente**. Logo

$$
\exists\, b \in \mathbb{R} \text{ t.q. } x_{n_k} \leq b, \quad \forall\, k \in \mathbb{N}
$$

Suponha, **por absurdo**, que $(x_n)$ não seja limitada. Pela observação, $(x_n)$ não é limitada superiormente:

$$
\implies \exists\, n \in \mathbb{N} \text{ t.q. } b < x_n
$$

Agora tome $k \in \mathbb{N}$ t.q. $n_k > n$. Neste caso, $n_k > n$ e

$$
x_{n_k} \leq b < x_n \implies \boxed{x_{n_k} < x_n}
$$

o que **contradiz** $(x_n)$ monótona não decrescente. $\blacksquare$

---

#### definição: convergência de sequências #analise/definição/convergencia
^definicao-convergencia

**Definição.** $(x_n)$ **converge a** $\bar{x}$ (é convergente a $\bar{x}$). Nomes equivalentes:

$$
x_n \xrightarrow{n \to \infty} \bar{x}, \qquad x_n \to \bar{x}, \qquad \lim_{n \to \infty} x_n = \bar{x}, \qquad \lim_n x_n = \bar{x}, \qquad \lim x_n = \bar{x}
$$

"o limite de $(x_n)$ é $\bar{x}$".

**Definição ($\varepsilon$–$n_0$):**

$$
\boxed{\forall\, \varepsilon > 0,\; \exists\, n_0 \in \mathbb{N},\; \forall\, n \geq n_0,\; |x_n - \bar{x}| < \varepsilon}
$$

> Geometricamente: a partir de $n_0$, todos os $x_n$ caem no intervalo $(\bar{x} - \varepsilon,\; \bar{x} + \varepsilon)$.

---

#### definição: convergente e divergente #analise/definição/divergencia
^definicao-divergencia

**Definição.** $(x_n)$ **converge** (ou é convergente) se

$$
\exists\, \bar{x} \in \mathbb{R} \text{ t.q. } x_n \to \bar{x}
$$

**Definição.** $(x_n)$ **diverge** (ou é divergente) se não converge.

**Explicitamente** (negando "converge"):

$$
\neg\left(\exists\, \bar{x} \in \mathbb{R},\; \forall\, \varepsilon > 0,\; \exists\, n_0 \in \mathbb{N},\; \forall\, n \geq n_0,\; |x_n - \bar{x}| < \varepsilon\right)
$$

$$
\iff \forall\, \bar{x} \in \mathbb{R},\; \exists\, \varepsilon > 0,\; \forall\, n_0 \in \mathbb{N},\; \exists\, n \geq n_0,\; |x_n - \bar{x}| \geq \varepsilon
$$

---

#### exercício: sequência alternada diverge #analise/exercício/alternada-diverge
^exercicio-alternada

> **Exercício.** $(x_n) = (0, 1, 0, 1, 0, 1, \dots)$ é **divergente**. Prove! (usando a formulação explícita).
>
> **Sugestão:** tome $\varepsilon = \tfrac{1}{2}$ para todo $\bar{x} \in \mathbb{R}$.
>
> A ideia: nenhum $\bar{x}$ pode estar a distância $< \tfrac{1}{2}$ de $0$ **e** de $1$ simultaneamente, mas a sequência visita ambos infinitas vezes.
