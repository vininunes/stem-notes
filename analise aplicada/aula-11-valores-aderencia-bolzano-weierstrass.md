#### tema da aula: valores de aderência e Bolzano–Weierstrass
^titulo-aula-11

Continuação de [[aula-09-sequencias#^definicao-sequencia|sequências]] e [[aula-10-unicidade-do-limite#^titulo-aula-10|limites]]. Fechamos o estudo de limitação/divergência ao infinito, introduzimos **valores de aderência** (limites de subsequências) e provamos o **Teorema de Bolzano–Weierstrass**, culminando nos conceitos de **lim sup** e **lim inf**.

---

#### sequência limitada (recapitulação) #analise/definição/sequencia-limitada-recap
^seq-limitada-recap

Recordando as variantes de [[aula-09-sequencias#^definicao-limitada|limitação]]:

$$
(x_n) \text{ limitada}: \quad \exists\, M > 0 \;\text{t.q.}\; |x_n| \leq M, \;\; \forall\, n \in \mathbb{N}.
$$

$$
\text{limitada superiormente}: \quad \exists\, b \in \mathbb{R} \;\text{t.q.}\; x_n \leq b, \;\; \forall\, n \in \mathbb{N}.
$$

Negando a limitação superior, obtém-se **não limitada superiormente**:

$$
\forall\, b \in \mathbb{R}, \;\; \exists\, n \in \mathbb{N} \;\text{t.q.}\; x_n > b.
$$

> **Ex.** $(x_n) = (0,1,0,2,0,3,0,4,0,5,\dots)$ é não limitada superiormente (mas tampouco diverge a $+\infty$ — veja abaixo).

---

#### definição: divergência a $\pm\infty$ #analise/definição/divergencia-infinito
^def-divergencia-infinito

**Definição.** Diz-se que $x_n \to +\infty$ (ou $\lim_n x_n = +\infty$) se

$$
\forall\, b \in \mathbb{R}, \;\; \exists\, n_0 \in \mathbb{N}, \;\; \forall\, n \geq n_0, \;\; x_n > b.
$$

Analogamente define-se $x_n \to -\infty$ (trocando $x_n > b$ por $x_n < b$).

> **Cuidado:** $\to +\infty$ é **mais forte** que ser não limitada superiormente. A não limitação pede que *algum* termo ultrapasse cada $b$; a divergência pede que **todos os termos a partir de $n_0$** ultrapassem $b$.

**Exemplo.** $(x_n) = \big((-1)^n \cdot n\big) = (-1, 2, -3, 4, -5, \dots)$:

- **não é limitada** nem inferiormente nem superiormente;
- **não vai** a $+\infty$ nem a $-\infty$ (alterna de sinal);
- porém $|x_n| = n \to +\infty$.

---

#### proposição: limite preserva desigualdades #analise/proposição/limite-preserva-ordem
^prop-limite-ordem

*(Resultado que faltou na aula anterior.)*

**Proposição.** Sejam $(x_n)$ e $(y_n)$ tais que $x_n \to \bar{x}$ e $y_n \to \bar{y}$. Se

$$
x_n \leq y_n, \;\; \forall\, n \in \mathbb{N},
$$

então $\bar{x} \leq \bar{y}$.

> **Atenção:** a desigualdade **estrita** não se preserva no limite: $x_n = 0 < \tfrac{1}{n} = y_n$, mas ambos $\to 0$, e $0 \not< 0$.

---

#### prova: limite preserva ordem #analise/prova/limite-preserva-ordem
^prova-limite-ordem

**Prova (por absurdo — análoga à da [[aula-10-unicidade-do-limite#^prova-unicidade|unicidade do limite]]).** Suponha $\bar{x} > \bar{y}$. Então os pontos $\bar{x}$ e $\bar{y}$ podem ser separados: existe $\varepsilon > 0$ t.q.

$$
(\bar{y} - \varepsilon,\, \bar{y} + \varepsilon) \cap (\bar{x} - \varepsilon,\, \bar{x} + \varepsilon) = \emptyset,
$$

com o intervalo de $\bar{y}$ inteiramente **à esquerda** do de $\bar{x}$. Logo, se $z \in (\bar{y} - \varepsilon, \bar{y} + \varepsilon)$ e $w \in (\bar{x} - \varepsilon, \bar{x} + \varepsilon)$, então $z < w$. $\quad(\triangle)$

Por convergência:

$$
\exists\, \tilde{n}_0, \;\; \forall\, n \geq \tilde{n}_0, \;\; x_n \in (\bar{x} - \varepsilon,\, \bar{x} + \varepsilon), \qquad (\ast)
$$

$$
\exists\, \tilde{\tilde{n}}_0, \;\; \forall\, n \geq \tilde{\tilde{n}}_0, \;\; y_n \in (\bar{y} - \varepsilon,\, \bar{y} + \varepsilon). \qquad (\ast\ast)
$$

Tomando $n_0 = \max\{\tilde{n}_0,\, \tilde{\tilde{n}}_0\}$, para $n \geq n_0$ valem $(\ast)$ e $(\ast\ast)$. Por $(\triangle)$, $y_n < x_n$, **contradição** com $x_n \leq y_n$. Portanto $\bar{x} \leq \bar{y}$. $\blacksquare$

---

#### definição: valor de aderência #analise/definição/valor-aderencia
^def-valor-aderencia

**Definição.** $\bar{x}$ é um **valor de aderência** de $(x_n)$ se existe alguma [[aula-09-sequencias#^definicao-subsequencia|subsequência]] $(x_{n_k})$ de $(x_n)$ t.q.

$$
x_{n_k} \to \bar{x}.
$$

> Em palavras: valor de aderência = limite de **alguma** subsequência. O conjunto desses valores mede "para onde a sequência se acumula".

---

#### exemplos de valores de aderência #analise/exemplo/valores-aderencia
^exemplos-aderencia

1. **Convergente.** Se $x_n \to a$, então toda subsequência também converge para $a$ (visto em aulas passadas). Logo o conjunto de valores de aderência é $\{a\}$ — exatamente um.

2. $(x_n) = (0,1,2,0,1,2,0,1,2,\dots)$ tem valores de aderência $\{0, 1, 2\}$ (uma subsequência constante em cada resto).

3. $(x_n) = \big(0 + \tfrac{1}{1},\, 1 + \tfrac{1}{2},\, 2 + \tfrac{1}{3},\, 0 + \tfrac{1}{4},\, 1 + \tfrac{1}{5},\, 2 + \tfrac{1}{6},\, \dots\big)$ tem valores de aderência $\{0, 1, 2\}$ (mesmos "níveis", agora atingidos por convergência).

4. $(x_n) = \big(1,\, \tfrac{1}{2},\, 3,\, \tfrac{1}{4},\, 5,\, \tfrac{1}{6},\, 7,\, \tfrac{1}{8},\, \dots\big)$: os ímpares explodem, os pares $\to 0$. Único valor de aderência: $\{0\}$.

5. Uma enumeração que percorre todos os racionais de $[0,1]$ (por níveis $\tfrac{j}{k}$) tem como valores de aderência **todo** o intervalo $[0,1]$.

> **Acúmulo de irracionais.** Para $\tfrac{\sqrt{2}}{2} = 0{,}70710678\dots$, a sequência de truncamentos $\tfrac{7}{10}, \tfrac{70}{100}, \tfrac{707}{1000}, \tfrac{7071}{10000}, \dots \to \tfrac{\sqrt{2}}{2}$. Em geral, todo $a \in \mathbb{R}$ é limite de racionais dentro de qualquer janela $(a - \tfrac{1}{k}, a + \tfrac{1}{k})$ — densidade de $\mathbb{Q}$.

**Exemplo (sem demonstração).** $x_n = \operatorname{sen}(n)$ tem conjunto de valores de aderência $[-1, 1]$ (os múltiplos inteiros de $1$ rad distribuem-se densamente no círculo).

---

#### lema: caracterizações de valor de aderência #analise/lema/caracterizacao-aderencia
^lema-caracterizacao-aderencia

**Lema.** Para uma sequência $(x_n)$, são **equivalentes**:

$$
\textbf{(i)} \quad a \text{ é valor de aderência } \big(\exists\, (x_{n_k}) \text{ t.q. } x_{n_k} \to a\big).
$$

$$
\textbf{(ii)} \quad \forall\, \varepsilon > 0, \quad \{\, n \in \mathbb{N} \mid x_n \in (a - \varepsilon,\, a + \varepsilon) \,\} \text{ é infinito}.
$$

$$
\textbf{(iii)} \quad \forall\, \varepsilon > 0, \;\; \forall\, n_0 \in \mathbb{N}, \;\; \exists\, n > n_0, \;\; x_n \in (a - \varepsilon,\, a + \varepsilon).
$$

> **Prova (exercício).** Sugestão de ciclo: $(\text{i}) \Rightarrow (\text{ii}) \Rightarrow (\text{iii}) \Rightarrow (\text{i})$. A diferença para a [[aula-09-sequencias#^definicao-convergencia|convergência]] é o quantificador: convergência exige a janela "de $n_0$ em diante"; aderência só exige **infinitos** índices na janela (formulação (iii): sempre há um índice maior).

---

#### teorema: Bolzano–Weierstrass #analise/teorema/bolzano-weierstrass
^teorema-bolzano-weierstrass

**Teorema (Bolzano–Weierstrass).** Em $\mathbb{R}$, toda sequência **limitada** tem uma **subsequência convergente**.

> Equivalentemente: toda sequência limitada possui **pelo menos um** valor de aderência (o conjunto de valores de aderência não é vazio).

A prova é **construtiva**, baseada em [[aula-10-unicidade-do-limite#^teorema-convergencia-monotona|convergência monótona]] e na [[aula-07-supremo-completeza#^definicao-completo|completeza de $\mathbb{R}$]].

---

#### prova: Bolzano–Weierstrass #analise/prova/bolzano-weierstrass
^prova-bolzano-weierstrass

**Prova.** Seja $(x_n)$ limitada. Como estamos em $\mathbb{R}$ e $(x_n)$ é limitada, para cada $k$ os conjuntos abaixo são limitados, logo existem (completeza):

$$
b_k = \sup\{x_n \mid n \geq k\}, \qquad a_k = \inf\{x_n \mid n \geq k\}.
$$

**Afirmação 1: $(b_k)$ é não crescente, i.e. $b_k \geq b_{k+1}$.** De fato, $A = \{x_n \mid n \geq k+1\} \subseteq B = \{x_n \mid n \geq k\}$, e $A \subseteq B \Rightarrow \sup A \leq \sup B$. Assim:

$$
a_1 \leq a_2 \leq \cdots \leq a_k \leq \cdots \leq b_k \leq \cdots \leq b_2 \leq b_1.
$$

Logo $(b_k)$ é **monótona não crescente e limitada inferiormente**. Pela [[aula-10-unicidade-do-limite#^teorema-convergencia-monotona|convergência monótona]], existe

$$
\bar{b} = \lim_k b_k.
$$

> **Atenção:** os $b_k$ **não** são necessariamente termos da sequência (são supremos de caudas).

**Afirmação 2: $\bar{b}$ é valor de aderência de $(x_n)$.** Usaremos a formulação **(iii)** do [[#^lema-caracterizacao-aderencia|lema]]:

$$
\vdash \;\; \forall\, \varepsilon > 0, \;\; \forall\, n_0 \in \mathbb{N}, \;\; \exists\, n > n_0, \;\; x_n \in (\bar{b} - \varepsilon,\, \bar{b} + \varepsilon).
$$

*Ideia (rascunho):* como $b_k \to \bar{b}$, há $b_k$'s próximos de $\bar{b}$; e como $b_k = \sup\{x_n \mid n \geq k\}$, há $x_n$'s próximos de $b_k$.

Fixe $\varepsilon > 0$ e $n_0 \in \mathbb{N}$ quaisquer. Como $b_k \to \bar{b}$, existe $k_0 \geq n_0$ t.q. para todo $k \geq k_0$, $\; b_k \in (\bar{b} - \varepsilon,\, \bar{b} + \varepsilon)$. Fixe um $k \geq k_0$. Pelo [[aula-07-supremo-completeza#^lema-facilitador|lema facilitador do supremo]] aplicado a $b_k = \sup\{x_n \mid n \geq k\}$:

$$
\exists\, n \geq k \;\text{t.q.}\; x_n \in (b_k - \varepsilon,\, b_k].
$$

Como $b_k \in (\bar{b} - \varepsilon, \bar{b} + \varepsilon)$, segue que $x_n \in (\bar{b} - \varepsilon, \bar{b} + \varepsilon)$. E $n \geq k \geq k_0 \geq n_0 \Rightarrow n > n_0$ (ajustando índices). Isso verifica (iii), logo $\bar{b}$ é valor de aderência: existe $(x_{n_k})$ com $x_{n_k} \to \bar{b}$. $\blacksquare$

---

#### definição: lim sup e lim inf #analise/definição/limsup-liminf
^def-limsup-liminf

Os limites construídos na prova têm nome próprio:

$$
\bar{b} = \lim_{k \to \infty} b_k = \lim_{k \to \infty} \sup\{x_n \mid n \geq k\} \;\;\overset{\text{def}}{=}\;\; \limsup_{n \to \infty} x_n,
$$

$$
\bar{a} = \lim_{k \to \infty} a_k = \lim_{k \to \infty} \inf\{x_n \mid n \geq k\} \;\;\overset{\text{def}}{=}\;\; \liminf_{n \to \infty} x_n.
$$

> $\limsup$ é o **maior** valor de aderência e $\liminf$ o **menor**. A sequência converge $\iff \liminf x_n = \limsup x_n$ (e aí esse valor comum é o limite).

> **Exercício.** Toda subsequência convergente de $(x_n)$ converge para um valor no intervalo $[\,\bar{a},\, \bar{b}\,]$ — ou seja, todos os valores de aderência ficam entre o $\liminf$ e o $\limsup$.

---
