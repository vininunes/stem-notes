#### padrões estruturais de demonstração
^padroes-demonstracao

> O objetivo deste documento é identificar os **esqueletos lógicos** por trás das provas. Toda demonstração, por mais criativa que pareça, segue um padrão estrutural determinado pela **forma lógica** do enunciado. Reconhecer o padrão é o primeiro passo; o conteúdo matemático vem depois.

---

## 1. anatomia de um enunciado

Todo enunciado tem duas partes:

- **Hipótese** ($H$): o que é dado / assumido
- **Tese** ($T$): o que se quer provar

**Exemplo:** "Seja $K$ um corpo e $a, b \in K$ com $ab = 0$. Mostre que $a = 0$ ou $b = 0$."

- $H$: $K$ é corpo, $a, b \in K$, $ab = 0$
- $T$: $a = 0$ ou $b = 0$

> **Regra de ouro:** antes de começar qualquer prova, separar explicitamente $H$ e $T$. Isso determina o padrão a usar.

---

## 2. os quantificadores e o que eles pedem de você

A forma lógica da tese dita a estrutura da prova:

| Forma da tese | O que você faz |
|---------------|---------------|
| $\forall\, x,\; P(x)$ | "Seja $x$ **arbitrário**." (você não escolhe, o adversário escolhe) |
| $\exists\, x,\; P(x)$ | "**Tome** $x = \ldots$" (você exibe o elemento) |
| $P \implies Q$ | Assuma $P$, deduza $Q$ |
| $P \iff Q$ | Prove $P \implies Q$ **e** $Q \implies P$ separadamente |
| $P$ ou $Q$ | Geralmente por contradição: suponha $\neg P$, deduza $Q$ |
| $\neg P$ | Suponha $P$, chegue num absurdo |

### a diferença entre "seja" e "tome"

- **"Seja $x$ arbitrário"** → prova de $\forall$. Você não pode assumir nada sobre $x$ além do domínio. O $x$ é genérico.
- **"Tome $x = \ldots$"** → prova de $\exists$. Você constrói ou exibe o $x$ que funciona.

**Exemplo (Ex. 44):**

$\vdash$ $\sup(a,b) = b$

"*Seja* $c < b$ arbitrário" → precisamos mostrar que $c$ não é cota superior (prova de $\forall$).

"*Tome* $x = \dfrac{c+b}{2}$" → exibimos um elemento de $(a,b)$ maior que $c$ (prova de $\exists$).

---

## 3. os padrões de demonstração

### 3.1. prova direta

**Quando usar:** a tese é da forma $H \implies T$ e há um caminho dedutivo natural.

**Esqueleto:**
1. Assuma $H$
2. Deduza consequências de $H$ usando axiomas/teoremas
3. Chegue em $T$

**Exemplo (Ex. 1 — regras de sinal):**
$\vdash$ $(-x)y = -(xy)$

Prova: basta mostrar que $xy + (-x)y = 0$ (pois o oposto é único).
$$xy + (-x)y = (x + (-x))y = 0 \cdot y = 0 \quad \blacksquare$$

> **Dica:** quando a tese é "$a = b$", frequentemente convém mostrar que $a - b = 0$, ou que $a \leq b$ e $b \leq a$.

---

### 3.2. prova por contradição (absurdo)

**Quando usar:** quando provar diretamente é difícil, ou a tese é uma negação ($\neg P$), ou envolve "ou".

**Esqueleto:**
1. Suponha a **negação** da tese
2. Deduza consequências até chegar numa contradição com alguma hipótese ou fato conhecido
3. Conclua que a tese é verdadeira

**Exemplo ($\sqrt{2} \notin \mathbb{Q}$):**

$\vdash$ Não existe $x \in \mathbb{Q}$ com $x^2 = 2$.

1. Suponha que exista: $x = p/q$, $\gcd(p,q) = 1$, $x^2 = 2$
2. $p^2 = 2q^2 \implies 2 \mid p \implies p = 2k \implies 4k^2 = 2q^2 \implies 2 \mid q$
3. Contradição: $2$ divide $p$ e $q$, mas $\gcd(p,q) = 1$. $\blacksquare$

> **Cuidado:** a negação de $\forall x, P(x)$ é $\exists x, \neg P(x)$. Negar corretamente é metade da prova por absurdo.

---

### 3.3. prova por contrapositiva

**Quando usar:** quando $H \implies T$ é difícil, mas $\neg T \implies \neg H$ é natural.

**Esqueleto:** em vez de provar $P \implies Q$, prove $\neg Q \implies \neg P$ (são logicamente equivalentes).

**Exemplo:** "Se $n^2$ é par, então $n$ é par."

Contrapositiva: "Se $n$ é ímpar, então $n^2$ é ímpar." $n = 2k+1 \implies n^2 = 4k^2 + 4k + 1 = 2(2k^2+2k)+1$. $\blacksquare$

> **Diferença da contradição:** na contrapositiva, você assume $\neg T$ e deduz $\neg H$. Na contradição, você assume $H$ **e** $\neg T$ e deduz qualquer absurdo.

---

### 3.4. prova por indução (1º princípio)

**Quando usar:** a tese é da forma $\forall n \in \mathbb{N}, P(n)$.

**Esqueleto:**
1. **Base:** mostrar $P(1)$ (ou $P(n_0)$ se a propriedade começa em $n_0$)
2. **Passo indutivo:** assumir $P(n)$ (**hipótese indutiva**, H.I.), provar $P(n+1)$

**Exemplo (Ex. 20 — Bernoulli):**

$\vdash$ $(1+x)^n \geq 1 + nx$ para todo $n \in \mathbb{N}$, $x > 0$.

- Base: $n = 1$: $(1+x)^1 = 1 + x \geq 1 + 1 \cdot x$. $\checkmark$
- Passo: supondo $(1+x)^n \geq 1 + nx$:
$$
(1+x)^{n+1} = \underbrace{(1+x)^n}_{\geq 1+nx}(1+x) \geq (1+nx)(1+x) = 1 + (n+1)x + nx^2 \geq 1 + (n+1)x \quad \blacksquare
$$

> **Armadilha clássica:** provar $P(n+1) \implies P(n)$ em vez de $P(n) \implies P(n+1)$. A direção importa!

---

### 3.5. prova por indução forte (2º princípio)

**Quando usar:** no passo indutivo, você precisa de $P(k)$ para **vários** $k \leq n$, não só para $n$.

**Esqueleto:**
1. **Base:** mostrar $P(1)$
2. **Passo:** assumir $P(k)$ para todo $k \leq n$ (H.I. forte), provar $P(n+1)$

**Exemplo (Ex. 22 — decomposição em primos):**

$\vdash$ Todo $n \geq 2$ é produto de primos.

- Base: $n = 2$ é primo. $\checkmark$
- Passo: suponha que vale para todo $k$ com $2 \leq k \leq n$.
  - Se $n+1$ é primo: pronto.
  - Se $n+1$ não é primo: $n+1 = a \cdot b$ com $2 \leq a, b \leq n$. Por H.I., $a$ e $b$ se decompõem em primos, logo $n+1$ também. $\blacksquare$

> **Por que o 2º princípio funciona aqui:** o caso "não primo" divide $n+1$ em dois fatores que podem ser qualquer coisa $\leq n$, não necessariamente $n$.

---

### 3.6. prova de unicidade

**Quando usar:** a tese é da forma "existe um **único** $x$ tal que $P(x)$".

**Esqueleto:**
1. **Existência:** exibir ou provar que existe pelo menos um $x$ com $P(x)$
2. **Unicidade:** suponha que $x$ e $\tilde{x}$ satisfaçam $P$, mostre que $x = \tilde{x}$

**Exemplo (unicidade do supremo):**

$\vdash$ Se $b$ e $\tilde{b}$ são ambos supremo de $X$, então $b = \tilde{b}$.

- $b$ é a menor c.s. e $\tilde{b}$ é c.s. $\implies b \leq \tilde{b}$
- $\tilde{b}$ é a menor c.s. e $b$ é c.s. $\implies \tilde{b} \leq b$
- Logo $b = \tilde{b}$. $\blacksquare$

> **Padrão "sanduíche":** para mostrar $a = b$, mostrar $a \leq b$ e $b \leq a$.

---

### 3.7. prova por dupla inclusão (igualdade de conjuntos)

**Quando usar:** a tese é $A = B$ para conjuntos.

**Esqueleto:**
1. $(\subseteq)$: tome $x \in A$ arbitrário, mostre $x \in B$
2. $(\supseteq)$: tome $x \in B$ arbitrário, mostre $x \in A$

> Análogo ao "sanduíche" $a \leq b$ e $b \leq a$ para números.

---

### 3.8. prova por casos (disjunção)

**Quando usar:** quando a hipótese ou a estrutura do problema se divide naturalmente em casos exaustivos.

**Esqueleto:**
1. Identificar os casos (devem cobrir todas as possibilidades)
2. Provar a tese em cada caso separadamente

**Exemplo ($a \neq 0 \implies a^2 > 0$):**

Por tricotomia (P2): $a \in P$ ou $-a \in P$.
- Caso 1: $a \in P \implies a^2 = a \cdot a \in P$ (por P1). $\checkmark$
- Caso 2: $-a \in P \implies a^2 = (-a)(-a) \in P$ (por P1). $\checkmark$ $\blacksquare$

---

## 4. negação de quantificadores

Negar corretamente é essencial para provas por contradição e para formular a contrapositiva.

| Enunciado | Negação |
|-----------|---------|
| $\forall x, P(x)$ | $\exists x, \neg P(x)$ |
| $\exists x, P(x)$ | $\forall x, \neg P(x)$ |
| $\forall x, \exists y, P(x,y)$ | $\exists x, \forall y, \neg P(x,y)$ |
| $P \implies Q$ | $P \;\text{e}\; \neg Q$ |
| $P$ e $Q$ | $\neg P$ ou $\neg Q$ |
| $P$ ou $Q$ | $\neg P$ e $\neg Q$ |

**Exemplo fundamental — negar "$X$ é limitado superiormente":**

$$\text{Limitado sup.:} \quad \exists\, a \in K,\; \forall\, x \in X,\; x \leq a$$

$$\text{Negação:} \quad \forall\, a \in K,\; \exists\, x \in X,\; x > a$$

> "Para qualquer candidato a cota, consigo achar um elemento que o ultrapassa."

---

## 5. padrões compostos recorrentes em análise

### 5.1. provar que $b = \sup X$

**Estrutura:** duas subprovas.

**(i) $b$ é cota superior** ($\forall$):
"Seja $x \in X$ arbitrário. Mostre que $x \leq b$."

**(ii) $b$ é a menor cota superior** (equivalente a $\forall$ + $\exists$):
"Seja $c < b$ arbitrário. Tome $x = \ldots \in X$ com $x > c$."

> A parte (ii) é onde entra a criatividade. Técnicas comuns:
> - **Truque da média:** $x = (c + b)/2$
> - **Propriedade arquimediana:** achar $n$ com $1/n$ pequeno o suficiente
> - **Lema facilitador:** se já sabe que $b = \sup X$, usar diretamente

---

### 5.2. provar que $a = b$ via $\varepsilon$ arbitrário

**Quando usar:** quando não se consegue mostrar $a = b$ diretamente, mas se consegue mostrar que $|a - b| < \varepsilon$ para todo $\varepsilon > 0$.

**Esqueleto:**
1. "Seja $\varepsilon > 0$ arbitrário."
2. Mostre que $|a - b| < \varepsilon$ (ou $a \geq b - \varepsilon$, etc.)
3. "Como $\varepsilon > 0$ é arbitrário, $a = b$."

**Justificativa:** se $|a - b| > 0$, tome $\varepsilon = |a-b|$ e obtém contradição.

**Exemplo ($\sup(A+B) = \sup A + \sup B$, parte $\geq$):**

Seja $\varepsilon > 0$. Tome $a \in A$ com $a > \sup A - \varepsilon/2$ e $b \in B$ com $b > \sup B - \varepsilon/2$.

$$a + b > \sup A + \sup B - \varepsilon$$

Como $a + b \in A + B$: $\sup(A+B) \geq a + b > \sup A + \sup B - \varepsilon$.

Como $\varepsilon$ é arbitrário: $\sup(A+B) \geq \sup A + \sup B$. $\blacksquare$

> **Variação:** o truque do $\varepsilon/2$ aparece quando você precisa dividir a "folga" entre dois objetos.

---

### 5.3. provar que um conjunto é indutivo

**Quando usar:** para aplicar o Princípio da Indução.

**Esqueleto:**
1. Definir $X = \{n \in \mathbb{N} \mid P(n)\}$
2. Mostrar $1 \in X$ (base)
3. Mostrar $n \in X \implies n+1 \in X$ (passo)
4. Concluir: $X$ é indutivo, logo $X = \mathbb{N}$, logo $P(n)$ vale $\forall n$.

> **Obs:** formalmente, a indução não é um "método de prova" separado — é a consequência de $X$ ser indutivo e $\mathbb{N}$ ser o menor conjunto indutivo.

---

### 5.4. provar por tricotomia + exclusão

**Quando usar:** para mostrar que $a = b$ quando $a < b$ e $a > b$ levam a contradição.

**Esqueleto:**
1. Por tricotomia: $a < b$, $a = b$, ou $a > b$
2. Supor $a < b$: deduzir contradição
3. Supor $a > b$: deduzir contradição
4. Resta $a = b$. $\blacksquare$

**Exemplo ($b^2 = 2$ na prova de $\exists \sqrt{2}$):**

Mostra-se que $b^2 < 2$ e $b^2 > 2$ ambos contradizem $b = \sup S$. Resta $b^2 = 2$.

---

## 6. checklist antes de começar uma prova

1. **Separar hipótese e tese.** O que é dado? O que preciso mostrar?
2. **Identificar a forma lógica da tese.** É $\forall$? $\exists$? $\implies$? Negação? Isso determina o esqueleto.
3. **Escolher o padrão.** Direta? Contradição? Indução?
4. **Montar o esqueleto** antes de preencher os detalhes.
5. **Verificar:** a prova usa todas as hipóteses? Se não usou alguma, provavelmente algo está errado.

> **Regra prática:** se o enunciado diz "mostre que $\forall\, x, P(x)$", comece com "Seja $x$ arbitrário". Se diz "$\exists\, x, P(x)$", pense em **quem** é o $x$ que funciona. Se tem cara de difícil, tente contradição.
