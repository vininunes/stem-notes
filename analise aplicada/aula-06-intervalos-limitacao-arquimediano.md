#### observação inicial
^obs-aula-06

> Aula de conjuntos finitos, infinitos etc. foi **adiada**.

---

#### definições de intervalos #analise/definição/intervalos
^definicao-intervalos

$K = (K, +, \cdot, P)$ [[aula-02-corpos-ordenados#^definicao-corpo-ordenado|corpo ordenado]].

Sejam $a, b \in K$.

**Intervalos finitos** ($a \leq b$):

$$
[a, b] \stackrel{\text{def}}{=} \{x \in K \mid a \leq x \leq b\}
$$

$$
(a, b) \stackrel{\text{def}}{=} \{x \in K \mid a < x < b\}
$$

$$
(a, b], \quad [a, b)
$$

---

#### intervalos infinitos #analise/definição/intervalos-infinitos
^intervalos-infinitos

$$
(-\infty, a] = \{x \in K \mid x \leq a\}
$$

> $-\infty$ é só uma notação, **não** é um elemento de $K$. Não existe "$[-\infty$".

$$
(-\infty, a), \quad (a, +\infty), \quad [a, +\infty), \quad (-\infty, +\infty) = K
$$

---

#### classificação dos intervalos
^classificacao-intervalos

**Intervalos abertos:** $(a,b)$, $(-\infty, a)$, $(a, +\infty)$, $(-\infty, +\infty)$

**Intervalos fechados:** $[a,b]$, $(-\infty, a]$, $[a, +\infty)$, $(-\infty, +\infty)$

**Semi-abertos (ou semi-fechados):** $(a, b]$, $[a, b)$

> **Obs:** $a = b$ somente faz sentido para $[a, b]$, e nesse caso $[a, a] = \{a\}$.

---

#### definição: conjunto limitado #analise/definição/conjunto-limitado
^definicao-conjunto-limitado

**Definição.** Seja $X \subseteq K$. Dizemos que $X$ é **limitado superiormente** (respectivamente, **limitado inferiormente**) sse $\exists\, a \in K$ t.q.:

$$
X \subseteq (-\infty, a] \qquad (\text{resp., } X \subseteq [a, +\infty))
$$

Em outras palavras:

- Limitado superiormente: $\forall\, x \in X,\; x \leq a$
- Limitado inferiormente: $\forall\, x \in X,\; a \leq x$

$X$ é **limitado** se é limitado inferior e superiormente.

Ou seja: $\exists\, a \leq b$ t.q. $X \subseteq [a, b]$.

---

#### lema: caracterização de limitado #analise/lema/limitado-valor-absoluto
^lema-limitado-valor-absoluto

**Lema (exercício).** $X$ é limitado $\iff$ $\exists\, M > 0$ t.q. $X \subseteq [-M, M]$, i.e., $\forall\, x \in X,\; |x| \leq M$.

---

#### cotas superiores e inferiores #analise/definição/cotas
^definicao-cotas

Quando $X \subseteq (-\infty, a]$, diz-se que $a$ é **cota (ou limitante) superior** de $X$.

Quando $X \subseteq [a, +\infty)$, diz-se que $a$ é **cota (ou limitante) inferior** de $X$.

---

#### pergunta: o conjunto vazio é limitado?
^vazio-limitado

$\emptyset \subseteq [a, b]$ para todo $a, b \in K$. Logo $\emptyset$ é limitado (vacuamente).

---

#### $\mathbb{N}$ é limitado inferiormente #analise/exemplo/N-limitado-inferiormente
^N-limitado-inferiormente

**1) $\mathbb{N}$ é limitado inferiormente?**

Sim. São cotas inferiores todos os negativos, o zero e o $1$, pois $1 \leq n$, $\forall\, n \in \mathbb{N}$ (pela [[aula-05-peano-e-boa-ordenacao#^afirmacao-n-geq-1|afirmação $n \geq 1$]]).

**2) $\mathbb{N}$ é limitado superiormente?**

A resposta **depende do corpo ordenado** $K$!!!

---

#### exemplo: $\mathbb{N}$ não é limitado superiormente em $\mathbb{Q}$ #analise/proposição/N-ilimitado-Q
^N-ilimitado-Q

**Exemplo.** Suponha $K = \mathbb{Q}$. $\mathbb{N}$ é limitado superiormente? **Não!**

**Prova.** Ser limitado superiormente significaria:

$$
\exists\, a \in K,\; \forall\, n \in \mathbb{N},\; n \leq a
$$

Não ser limitado superiormente é a negação:

$$
\neg(\exists\, a \in K,\; \forall\, n \in \mathbb{N},\; n \leq a)
$$

$$
\iff \forall\, a \in K,\; \neg(\forall\, n \in \mathbb{N},\; n \leq a)
$$

$$
\iff \forall\, a \in K,\; \exists\, n \in \mathbb{N},\; \neg(n \leq a)
$$

$$
\iff \forall\, a \in K,\; \exists\, n \in \mathbb{N},\; n > a \qquad (\ast)
$$

Para provar que $\mathbb{N}$ não é limitado superiormente em $\mathbb{Q}$, precisamos mostrar $(\ast)$.

Tome $a \in \mathbb{Q}$ qualquer:

$$
a = \frac{p}{q}, \quad p \in \mathbb{Z},\; q \in \mathbb{N}
$$

Queremos achar $n \in \mathbb{N}$ t.q. $n > \dfrac{p}{q}$.

- Se $p \leq 0$: tome $n = 1$.
- Se $p > 0$: tome $n = p + 1$, pois:

$$
n = p + 1 > p \geq \frac{p}{q} = a \quad \blacksquare
$$

---

#### exemplo de corpo em que $\mathbb{N}$ é limitado #analise/exemplo/corpo-N-limitado
^corpo-N-limitado

Detalhes na lista (exercícios 25 a 39).

---

#### o corpo $\mathbb{Q}(t)$: funções racionais #analise/definição/corpo-funcoes-racionais
^definicao-Q-t

$\mathbb{Q}(t)$: **funções racionais** (a coeficientes racionais) — frações de polinômios na variável $t$:

$$
\frac{p(t)}{q(t)}, \quad \text{com } q(t) \text{ não identicamente nulo}
$$

> Mesmo que $q(t)$ tenha algumas raízes, não importa.

Algumas frações são "iguais". Por exemplo: $\dfrac{1}{1+t} = \dfrac{1-t}{1-t^2}$.

**Definição.** $\dfrac{p(t)}{q(t)} = \dfrac{\tilde{p}(t)}{\tilde{q}(t)}$ sse $p(t)\tilde{q}(t) = q(t)\tilde{p}(t)$.

---

#### $\mathbb{Q}(t)$ é corpo #analise/proposição/Q-t-corpo
^Q-t-corpo

$\mathbb{Q}(t)$ é corpo com as operações de adição e multiplicação definidas por soma e produto de frações usuais:

**Multiplicação:**

$$
\frac{p(t)}{q(t)} \cdot \frac{\tilde{p}(t)}{\tilde{q}(t)} = \frac{p(t)\tilde{p}(t)}{q(t)\tilde{q}(t)}
$$

**Adição:**

$$
\frac{p(t)}{q(t)} + \frac{\tilde{p}(t)}{\tilde{q}(t)} = \frac{q(t)\tilde{p}(t) + \tilde{q}(t)p(t)}{q(t)\tilde{q}(t)}
$$

---

#### ordem em $\mathbb{Q}(t)$: definição dos positivos #analise/definição/positivos-Q-t
^positivos-Q-t

É corpo ordenado. Precisamos definir os positivos.

**Intuição:** quando $t \to +\infty$, a "função" $\dfrac{p(t)}{q(t)}$ é positiva.

**Exemplo.** $\dfrac{1}{1 - t}$ é negativa (para $t$ grande).

**Exemplo.** $\dfrac{-2t^2 + 100t + 1}{-3t^3 + t^2}$:

$$
= \frac{-2t^2\left[1 + \frac{100t}{-2t^2} + \frac{1}{-2t^2}\right]}{-3t^3\left[1 + \frac{t^2}{-3t^3}\right]} = \frac{-2}{-3} \cdot \frac{1}{t} \cdot [\to 1] \cdot [\to 1]^{-1} \to \frac{2}{3} \cdot \frac{1}{t} \cdot [\cdots] > 0
$$

**Definição.** $\dfrac{p(t)}{q(t)}$ é **positivo** sse o produto dos coeficientes de grau mais alto de $p(t)$ e $q(t)$ é positivo.

---

#### $\mathbb{N} \subseteq \mathbb{Q}(t)$ é limitado superiormente #analise/proposição/N-limitado-Q-t
^N-limitado-Q-t

**Afirmação.** $\mathbb{N} \subseteq \mathbb{Q}(t)$ é limitado superiormente.

**Candidato a limitante:** $\dfrac{t}{1}$.

$\forall\, n \in \mathbb{N}$, $n < \dfrac{t}{1}$?

$$
n < \frac{t}{1} \iff \frac{t}{1} - n \in P
$$

Mas:

$$
\frac{t}{1} - n = \frac{t - n}{1} = \frac{1 \cdot t^1 - n \cdot t^0}{1 \cdot t^0}
$$

O coeficiente de grau mais alto de $p(t) = t - n$ é $1$, e o de $q(t) = 1$ é $1$. O produto é $1 \cdot 1 > 0$.

$$
\implies \frac{t}{1} - n \in P \quad \checkmark
$$

Logo $\dfrac{t}{1}$ é cota superior de $\mathbb{N}$ em $\mathbb{Q}(t)$. $\blacksquare$

---

#### definição: corpo arquimediano #analise/definição/arquimediano
^definicao-arquimediano

**Definição.** $K$ corpo ordenado é **arquimediano** sse $\mathbb{N}$ **não** é limitado superiormente.

- $\mathbb{Q}$ é arquimediano (pelo [[#^N-ilimitado-Q|exemplo acima]])
- $\mathbb{Q}(t)$ **não** é arquimediano

---

#### teorema: equivalência com propriedade infinitesimal #analise/proposição/equivalencia-arquimediano
^equivalencia-arquimediano

**Teorema.** $K$ arquimediano $\iff$ $\forall\, x > 0,\; \exists\, n \in \mathbb{N}$ t.q. $0 < \dfrac{1}{n} < x$.

**Prova.**

$(\implies)$ **Hipótese:** $K$ arquimediano, i.e., $\mathbb{N}$ é ilimitado.

Tome $x > 0$ qualquer. Pela hipótese, $\exists\, n \in \mathbb{N}$ t.q. $n > \dfrac{1}{x}$.

$$
\implies \frac{1}{n} < x \quad \checkmark
$$

$(\impliedby)$ Queremos mostrar que $K$ é arquimediano.

Tome $a \in K$ (basta supor $a > 0$). Queremos mostrar que $\exists\, n \in \mathbb{N},\; n > a$.

Tome $x = \dfrac{1}{a}$ ($\implies x > 0$). Pela hipótese: $\exists\, n \in \mathbb{N},\; \dfrac{1}{n} < x$.

$$
\implies n > \frac{1}{x} = a \quad \checkmark \quad \blacksquare
$$

---

#### corolário: segunda forma de equivalência #analise/corolário/segunda-equivalencia-arquimediano
^segunda-equivalencia-arquimediano

**Corolário (2ª forma de equivalência do arquimediano).**

$$
K \text{ arquimediano} \iff \forall\, y \in K,\; \forall\, x > 0,\; \exists\, n \in \mathbb{N},\; nx > y
$$

> Geometricamente: dado qualquer $y$ e qualquer $x > 0$, é possível "somar $x$ consigo mesmo" $n$ vezes até ultrapassar $y$.

---

#### contraexemplo: $\mathbb{Q}(t)$ não é arquimediano #analise/exemplo/Q-t-nao-arquimediano
^Q-t-nao-arquimediano

Queremos um elemento positivo de $\mathbb{Q}(t)$ menor que $\dfrac{1}{n}$ para todo $n \in \mathbb{N}$.

Candidato: $\dfrac{1}{t}$.

$\forall\, n \in \mathbb{N}$:

$$
\frac{1}{n} - \frac{1}{t} = \frac{t - n}{nt} = \frac{1 \cdot t^1 - n \cdot t^0}{n \cdot t^1}
$$

O produto dos coeficientes de grau mais alto é $1 \cdot n > 0$.

$$
\implies \frac{1}{n} - \frac{1}{t} > 0 \implies \frac{1}{n} > \frac{1}{t} > 0
$$

Logo $\dfrac{1}{t}$ é um "infinitesimal" em $\mathbb{Q}(t)$: positivo mas menor que todo $\dfrac{1}{n}$. $\blacksquare$

---

#### próxima aula
^preview-aula-07

Esperamos que $\mathbb{R}$ seja arquimediano — vai seguir da **completeza**.