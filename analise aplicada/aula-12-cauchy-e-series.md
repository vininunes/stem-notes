#### tema da aula: sequências de Cauchy e séries
^titulo-aula-12

Continuação de [[aula-11-valores-aderencia-bolzano-weierstrass#^teorema-bolzano-weierstrass|Bolzano–Weierstrass]]. Introduzimos a **propriedade de Cauchy** ("convergência implícita", sem mencionar o limite) e provamos que em $\mathbb{R}$ ela equivale à convergência. Em seguida começamos o estudo de **séries** de números reais.

> **Recapitulação.** Aula passada: *valor de aderência* = limite de uma subsequência; **Teo. 1 (Bolzano–Weierstrass):** em $\mathbb{R}$, toda sequência limitada tem um valor de aderência (i.e., subsequência convergente). Usamos o **supremo**.

---

#### definição: sequência de Cauchy #analise/definição/cauchy
^def-cauchy

A ideia é caracterizar convergência **sem citar o limite** $a$ — os termos se aproximam *uns dos outros*. Compare:

$$
\textbf{Convergência (p/ um ponto } a\text{):} \quad \forall\, \varepsilon > 0, \;\; \exists\, n_0 \in \mathbb{N}, \;\; \forall\, n \geq n_0, \;\; |x_n - a| < \varepsilon.
$$

**Definição.** $(x_n)$ é uma **sequência de Cauchy** se

$$
\forall\, \varepsilon > 0, \;\; \exists\, n_0 \in \mathbb{N}, \;\; \forall\, n, m \geq n_0, \;\; |x_n - x_m| < \varepsilon.
$$

> Também chamada de **propriedade de Cauchy** ou "convergência implícita": não aparece nenhum candidato a limite, só a distância entre termos da cauda.

---

#### proposição 2: convergente ⟹ Cauchy #analise/proposição/convergente-cauchy
^prop-convergente-cauchy

**Proposição.** Toda sequência **convergente** é de **Cauchy**.

**Prova.** Se $(x_n)$ converge, existe $a \in \mathbb{R}$ t.q. $x_n \to a$. Dado $\varepsilon > 0$, existe $n_0$ t.q.

$$
\forall\, n \geq n_0, \quad |x_n - a| < \frac{\varepsilon}{2}.
$$

Tome $m, n \geq n_0$ quaisquer: valem $|x_n - a| < \tfrac{\varepsilon}{2}$ e $|x_m - a| < \tfrac{\varepsilon}{2}$. Pela desigualdade triangular,

$$
|x_n - x_m| = |x_n - a + a - x_m| \leq |x_n - a| + |x_m - a| < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon. \quad\blacksquare
$$

> **Ilustração:** todos os termos com índice $\geq n_0$ estão dentro de uma faixa de raio $\tfrac{\varepsilon}{2}$ em torno de $a$; logo dois quaisquer distam menos que $\varepsilon$.

> **OBS (cuidado!):** ser de Cauchy **não** é apenas $|x_n - x_{n+1}| \to 0$. Termos *consecutivos* podem se aproximar sem que a sequência seja de Cauchy (ex.: somas parciais da [[#^serie-harmonica|série harmônica]]). A definição exige controle de **todos** os pares $n, m \geq n_0$ de uma vez.

---

#### teorema 3: critério de Cauchy em $\mathbb{R}$ #analise/teorema/cauchy-converge
^teorema-cauchy-converge

**Vale a recíproca da Proposição 2?** Depende do espaço. Em $\mathbb{R}$, **sim**.

**Teorema.** Em $\mathbb{R}$, toda sequência de **Cauchy converge**.

> Esta é a propriedade de **completeza** sob outra roupagem: $\mathbb{R}$ não tem "buracos" para onde uma sequência de Cauchy escaparia. (Em $\mathbb{Q}$ é falso: a sequência de truncamentos de $\sqrt{2}$ é de Cauchy mas não converge em $\mathbb{Q}$.)

A prova usa duas proposições auxiliares e o [[aula-11-valores-aderencia-bolzano-weierstrass#^teorema-bolzano-weierstrass|Teorema 1]].

---

#### proposição 4: Cauchy ⟹ limitada #analise/proposição/cauchy-limitada
^prop-cauchy-limitada

**Proposição.** Toda sequência de Cauchy é **limitada**.

**Prova.** Como $(x_n)$ é de Cauchy, tomando $\varepsilon = 1$ existe $n_0 \in \mathbb{N}$ t.q.

$$
n, m \geq n_0 \implies |x_n - x_m| < 1.
$$

Em particular, fixando $m = n_0$: $\; |x_n - x_{n_0}| < 1$ para todo $n \geq n_0$, donde $|x_n| < |x_{n_0}| + 1$. Sobram os **finitos** termos iniciais. Tome

$$
M = \max\{\, |x_1|,\, \dots,\, |x_{n_0 - 1}|,\; |x_{n_0}| + 1 \,\}.
$$

Então $|x_n| \leq M$ para todo $n \in \mathbb{N}$. $\blacksquare$

> Mesma estrutura da prova de que [[aula-10-unicidade-do-limite#^prova-convergente-limitada|convergente ⟹ limitada]]: a propriedade controla a cauda, e o $\max$ engole o início finito.

---

#### proposição 5: Cauchy + subseq. convergente ⟹ convergente #analise/proposição/cauchy-subseq
^prop-cauchy-subseq

Pela [[#^prop-cauchy-limitada|Prop. 4]], toda seq. de Cauchy é limitada; logo, pelo [[aula-11-valores-aderencia-bolzano-weierstrass#^teorema-bolzano-weierstrass|Teorema 1]]:

$$
(\ast) \quad \text{Toda sequência de Cauchy tem uma subsequência convergente.}
$$

**Proposição.** Se uma sequência de Cauchy tem uma subsequência convergente, então **ela própria** converge.

**Prova.** Hipótese: existe subsequência $(x_{n_k})$ e $a \in \mathbb{R}$ t.q. $x_{n_k} \to a$. Queremos $x_n \to a$, isto é, $\forall\, \varepsilon > 0, \;\exists\, n_0, \;\forall\, n \geq n_0, \;|x_n - a| < \varepsilon$.

Dado $\varepsilon > 0$, usamos as duas hipóteses com raio $\tfrac{\varepsilon}{2}$:

$$
\text{Cauchy:} \quad \exists\, n_0, \;\; \forall\, n, m \geq n_0, \;\; |x_n - x_m| < \frac{\varepsilon}{2},
$$

$$
x_{n_k} \to a: \quad \exists\, k_0, \;\; \forall\, k \geq k_0, \;\; |x_{n_k} - a| < \frac{\varepsilon}{2}.
$$

Tome $k \geq k_0$ grande o bastante para que $n_k \geq n_0$ (possível pois $n_k \to \infty$). Esse índice satisfaz $|x_{n_k} - a| < \tfrac{\varepsilon}{2}$ e, sendo $n_k \geq n_0$, serve de "âncora" na desigualdade de Cauchy. Então, para todo $n \geq n_0$:

$$
|x_n - a| = |x_n - x_{n_k} + x_{n_k} - a| \leq \underbrace{|x_n - x_{n_k}|}_{< \,\varepsilon/2} + \underbrace{|x_{n_k} - a|}_{< \,\varepsilon/2} < \varepsilon.
$$

Logo $x_n \to a$. $\blacksquare$

**Prova do Teorema 3.** Seja $(x_n)$ de Cauchy. Por $(\ast)$ ela tem subsequência convergente; pela [[#^prop-cauchy-subseq|Prop. 5]], ela converge. $\blacksquare$

---

#### definição: série de números reais #analise/definição/serie
^def-serie

**Séries** são sequências produzidas pelas **somas parciais** de outras sequências.

**Definição.** Dada $(a_n)$, a série $\sum a_n$ é a **sequência das somas parciais** $(s_n)$, onde

$$
s_n = \sum_{k=1}^{n} a_k.
$$

Se $s_n \to S$, escreve-se

$$
S = \lim_n s_n = \lim_n \sum_{k=1}^{n} a_k \;\;\overset{\text{def}}{=}\;\; \sum_{k=1}^{\infty} a_k = \sum_{n=1}^{\infty} a_n,
$$

e $S$ é a **soma da série**. Neste caso diz-se que a série **converge**; caso contrário, **diverge**.

> A série é, por definição, uma sequência (a das somas parciais). Todo o vocabulário de [[aula-09-sequencias#^definicao-convergencia|convergência]] se aplica diretamente.

---

#### exemplo: série geométrica #analise/exemplo/serie-geometrica
^serie-geometrica

Seja $\lambda \in \mathbb{R}$, $\lambda \notin \{-1, 0, 1\}$. A série $\sum \lambda^n$ é a **série geométrica**.

Suponha $\lambda \in (-1, 0) \cup (0, 1)$. Já vimos que $|\lambda^n| = |\lambda|^n \to 0 \iff \lambda^n \to 0$. As somas parciais (de $k = 0$) calculam-se pelo truque telescópico:

$$
(1 - \lambda)\, s_n = (1 - \lambda)(1 + \lambda + \lambda^2 + \cdots + \lambda^n) = (1 - \lambda) + (\lambda - \lambda^2) + \cdots + (\lambda^n - \lambda^{n+1}) = 1 - \lambda^{n+1}.
$$

Logo

$$
s_n = \sum_{k=0}^{n} \lambda^k = \frac{1 - \lambda^{n+1}}{1 - \lambda} \;\;\xrightarrow[n \to \infty]{}\;\; \frac{1 - 0}{1 - \lambda} = \frac{1}{1 - \lambda},
$$

já que $\lambda^{n+1} \to 0$ quando $|\lambda| < 1$. Portanto:

$$
\boxed{\;\sum_{k=0}^{\infty} \lambda^k = \frac{1}{1 - \lambda}, \quad |\lambda| < 1.\;}
$$

---

#### proposição: convergência ⟹ termo geral → 0 #analise/proposição/termo-geral-zero
^prop-termo-geral-zero

**Proposição.** Se $\sum a_n$ converge, então $a_n \to 0$.

**Prova.** Seja $s_n = \sum_{k=1}^{n} a_k$. Então $a_n = s_n - s_{n-1}$. Se a série converge, $s_n \to S$ e também $s_{n-1} \to S$ (mesma sequência, defasada). Pela [[aula-10-unicidade-do-limite#^prop-aritmetica-limites|aritmética de limites]]:

$$
\lim_n a_n = \lim_n (s_n - s_{n-1}) = \lim_n s_n - \lim_n s_{n-1} = S - S = 0. \quad\blacksquare
$$

> **A recíproca é FALSA!** $a_n \to 0$ **não** garante que $\sum a_n$ converge. Este é o erro mais comum com séries: o teste $a_n \to 0$ só serve para detectar **divergência** (se $a_n \not\to 0$, diverge), nunca para concluir convergência.

**Contraexemplo.** Tome a sequência por blocos

$$
(a_n) = \Big(1,\; \tfrac{1}{2}, \tfrac{1}{2},\; \tfrac{1}{3}, \tfrac{1}{3}, \tfrac{1}{3},\; \tfrac{1}{4}, \tfrac{1}{4}, \tfrac{1}{4}, \tfrac{1}{4},\; \tfrac{1}{5}, \dots\Big),
$$

onde o valor $\tfrac{1}{k}$ aparece $k$ vezes. Cada bloco soma $1$, então as somas parciais nos finais de bloco são $s_{n_k} = k \to \infty$: há subsequência divergente, logo a série **diverge**. No entanto $a_n \to 0$. Conclusão: $a_n \to 0$ mas $\sum a_n$ diverge.

---

#### exemplo: série harmônica #analise/exemplo/serie-harmonica
^serie-harmonica

A **série harmônica** $\sum \tfrac{1}{n}$ é o exemplo clássico de divergência com termo geral $\to 0$. Agrupando em blocos de potências de $2$:

$$
\sum \frac{1}{n} = 1 + \frac{1}{2} + \underbrace{\Big(\frac{1}{3} + \frac{1}{4}\Big)}_{> \,\frac{1}{4} + \frac{1}{4} = \frac{1}{2}} + \underbrace{\Big(\frac{1}{5} + \cdots + \frac{1}{8}\Big)}_{> \,\frac{4}{8} = \frac{1}{2}} + \underbrace{\Big(\frac{1}{9} + \cdots + \frac{1}{16}\Big)}_{> \,\frac{1}{2}} + \cdots
$$

Cada bloco contribui mais que $\tfrac{1}{2}$, logo existe uma subsequência das somas parciais com

$$
s_{n_k} \geq \frac{k + 1}{2} \;\xrightarrow[k \to \infty]{}\; \infty.
$$

Portanto $\sum \tfrac{1}{n}$ **diverge** — apesar de $\tfrac{1}{n} \to 0$.

---

#### propriedades de séries #analise/proposição/propriedades-series
^propriedades-series

Se $\sum a_n$ e $\sum b_n$ convergem e $\rho \in \mathbb{R}$, então *(exercício — herdadas da [[aula-10-unicidade-do-limite#^prop-aritmetica-limites|aritmética de limites]] das somas parciais)*:

$$
\sum_{n=1}^{\infty} a_n + \sum_{n=1}^{\infty} b_n = \sum_{n=1}^{\infty} (a_n + b_n), \qquad \sum_{n=1}^{\infty} \rho\, a_n = \rho \sum_{n=1}^{\infty} a_n.
$$

---

#### curiosidade: série telescópica #analise/exemplo/serie-telescopica
^serie-telescopica

$$
\sum_{k=1}^{\infty} \frac{1}{k(k+1)} = \sum_{k=1}^{\infty} \left( \frac{1}{k} - \frac{1}{k+1} \right).
$$

As somas parciais **telescopam** (termos intermediários se cancelam):

$$
s_n = \sum_{k=1}^{n} \frac{1}{k(k+1)} = \Big(1 - \tfrac{1}{2}\Big) + \Big(\tfrac{1}{2} - \tfrac{1}{3}\Big) + \cdots + \Big(\tfrac{1}{n} - \tfrac{1}{n+1}\Big) = 1 - \frac{1}{n+1} \;\xrightarrow[n \to \infty]{}\; 1.
$$

$$
\boxed{\;\sum_{k=1}^{\infty} \frac{1}{k(k+1)} = 1.\;}
$$

> Contraste com a [[#^serie-harmonica|harmônica]]: aqui os termos $\sim \tfrac{1}{k^2}$ decaem rápido o suficiente para a soma ser **finita**.

---
