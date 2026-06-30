#### tema da aula: unicidade do limite
^titulo-aula-10

Continuação de [[aula-09-sequencias#^definicao-convergencia|convergência de sequências]]. Primeira propriedade fundamental do limite: quando existe, ele é **único**.

---

#### proposição: unicidade do limite #analise/proposição/unicidade-limite
^prop-unicidade

**Proposição.** Seja $(x_n)$ uma sequência. Se

$$
x_n \to a \quad \text{e} \quad x_n \to b,
$$

então $a = b$.

> Ou seja: o limite de uma sequência, **quando existe, é único**. Isso justifica a notação $\lim_n x_n = \bar{x}$ (com igualdade, falando de *o* limite).

---

#### prova da unicidade #analise/prova/unicidade-limite
^prova-unicidade

**Prova (por absurdo).** Suponha que $a \neq b$. Então $|a - b| > 0$. Tome

$$
\varepsilon = \frac{|a - b|}{2} > 0.
$$

Como $x_n \to a$, existe $n_1 \in \mathbb{N}$ t.q.

$$
\forall\, n \geq n_1, \quad |x_n - a| < \varepsilon.
$$

Como $x_n \to b$, existe $n_2 \in \mathbb{N}$ t.q.

$$
\forall\, n \geq n_2, \quad |x_n - b| < \varepsilon.
$$

Tome $n_0 = \max\{n_1, n_2\}$. Para $n \geq n_0$ valem as **duas** desigualdades. Pela desigualdade triangular:

$$
|a - b| = |a - x_n + x_n - b| \leq |a - x_n| + |x_n - b| < \varepsilon + \varepsilon = 2\varepsilon = |a - b|.
$$

Logo $|a - b| < |a - b|$, **absurdo**. Portanto $a = b$. $\blacksquare$

---

#### proposição: toda convergente é limitada #analise/proposição/convergente-limitada
^prop-convergente-limitada

**Proposição.** Se $(x_n)$ é **convergente**, então $(x_n)$ é **limitada**.

> A recíproca é **falsa**: $(x_n) = (0,1,0,1,\dots)$ é limitada mas [[aula-09-sequencias#^exercicio-alternada|diverge]].

---

#### prova: convergente ⟹ limitada #analise/prova/convergente-limitada
^prova-convergente-limitada

**Prova.** Suponha $x_n \to a$. Aplicando a definição de convergência com $\varepsilon = 1$, existe $n_0 \in \mathbb{N}$ t.q.

$$
\forall\, n \geq n_0, \quad |x_n - a| < 1.
$$

Daí, para $n \geq n_0$, pela desigualdade triangular:

$$
|x_n| = |x_n - a + a| \leq |x_n - a| + |a| < 1 + |a|.
$$

Sobram apenas os **finitos** termos iniciais $x_1, x_2, \dots, x_{n_0 - 1}$. Tome

$$
M = \max\{\, |x_1|,\, |x_2|,\, \dots,\, |x_{n_0 - 1}|,\; 1 + |a| \,\}.
$$

Então $|x_n| \leq M$ para **todo** $n \in \mathbb{N}$, ou seja, $(x_n)$ é limitada. $\blacksquare$

> **Ideia-chave:** convergência controla a sequência "do índice $n_0$ em diante" (uma faixa em torno de $a$); o **início finito** é sempre limitado. O $\max$ junta as duas partes.

---

#### teorema: monótona + limitada ⟹ convergente #analise/teorema/convergencia-monotona
^teorema-convergencia-monotona

**Teorema (Convergência Monótona).** Se $(x_n)$ é **monótona** e **limitada**, então $(x_n)$ é **convergente**.

Mais precisamente, no caso **não decrescente**:

$$
x_n \to \sup\{x_n \mid n \in \mathbb{N}\}.
$$

(No caso não crescente, $x_n \to \inf\{x_n \mid n \in \mathbb{N}\}$.)

> É o resultado-ponte entre o [[aula-07-supremo-completeza#^definicao-completo|axioma do supremo]] e [[aula-09-sequencias#^definicao-convergencia|convergência]]: a completeza de $\mathbb{R}$ garante o limite mesmo sem conhecê-lo de antemão.

---

#### prova: convergência monótona #analise/prova/convergencia-monotona
^prova-convergencia-monotona

**Prova.** Faremos o caso $(x_n)$ **monótona não decrescente** ($x_n \leq x_{n+1}$, $\forall\, n$). O outro caso é análogo (com ínfimo).

Seja

$$
X = \{x_n \mid n \in \mathbb{N}\}.
$$

$X \neq \emptyset$ e, como $(x_n)$ é limitada, $X$ é limitado superiormente. Pela [[aula-07-supremo-completeza#^definicao-completo|completeza de $\mathbb{R}$]], existe

$$
a = \sup X.
$$

**Afirmação:** $x_n \to a$. Seja $\varepsilon > 0$.

Como $a - \varepsilon < a$, por [[aula-07-supremo-completeza#^definicao-supremo|(ii')]] o número $a - \varepsilon$ **não** é cota superior de $X$. Logo existe $n_0$ t.q.

$$
x_{n_0} > a - \varepsilon.
$$

Como $(x_n)$ é não decrescente, para todo $n \geq n_0$:

$$
x_n \geq x_{n_0} > a - \varepsilon.
$$

Por outro lado, $a = \sup X$ é cota superior, então $x_n \leq a < a + \varepsilon$, $\forall\, n$. Juntando, para $n \geq n_0$:

$$
a - \varepsilon < x_n \leq a < a + \varepsilon \implies |x_n - a| < \varepsilon.
$$

Portanto $x_n \to a = \sup X$. $\blacksquare$

> **Obs:** A hipótese de monotonia é essencial: $(0,1,0,1,\dots)$ é limitada mas **diverge**. A limitação sozinha não basta.

---

#### proposição: propriedades aritméticas do limite #analise/proposição/aritmetica-limites
^prop-aritmetica-limites

**Proposição.** Sejam $(x_n)$ e $(y_n)$ convergentes, com $x_n \to a$ e $y_n \to b$, e seja $\lambda \in \mathbb{R}$. Então:

$$
\textbf{(1)} \quad x_n + y_n \to a + b
$$

$$
\textbf{(2)} \quad \lambda\, x_n \to \lambda\, a
$$

$$
\textbf{(3)} \quad x_n \, y_n \to a\, b
$$

$$
\textbf{(4)} \quad \text{se } b \neq 0: \quad \frac{x_n}{y_n} \to \frac{a}{b}
$$

> Em palavras: limite **comuta** com soma, produto por escalar, produto e quociente (sob $b \neq 0$).

---

#### lema: limitada × que tende a zero #analise/lema/limitada-vezes-zero
^lema-limitada-vezes-zero

**Lema.** Se $(z_n)$ é **limitada** e $w_n \to 0$, então $z_n w_n \to 0$.

**Prova.** Existe $M > 0$ com $|z_n| \leq M$, $\forall\, n$. Dado $\varepsilon > 0$, como $w_n \to 0$ existe $n_0$ t.q. $|w_n| < \dfrac{\varepsilon}{M}$ para $n \geq n_0$. Então, para $n \geq n_0$:

$$
|z_n w_n| = |z_n|\,|w_n| \leq M \cdot \frac{\varepsilon}{M} = \varepsilon.
$$

Logo $z_n w_n \to 0$. $\blacksquare$

---

#### prova das propriedades aritméticas #analise/prova/aritmetica-limites
^prova-aritmetica-limites

**(1) Soma.** Dado $\varepsilon > 0$, existem $n_1, n_2$ t.q.

$$
n \geq n_1 \implies |x_n - a| < \tfrac{\varepsilon}{2}, \qquad n \geq n_2 \implies |y_n - b| < \tfrac{\varepsilon}{2}.
$$

Para $n \geq n_0 = \max\{n_1, n_2\}$, pela desigualdade triangular:

$$
|(x_n + y_n) - (a + b)| \leq |x_n - a| + |y_n - b| < \tfrac{\varepsilon}{2} + \tfrac{\varepsilon}{2} = \varepsilon. \checkmark
$$

**(2) Escalar.** Caso $\lambda = 0$ é trivial. Se $\lambda \neq 0$, dado $\varepsilon > 0$ existe $n_0$ t.q. $|x_n - a| < \dfrac{\varepsilon}{|\lambda|}$ para $n \geq n_0$. Daí $|\lambda x_n - \lambda a| = |\lambda|\,|x_n - a| < \varepsilon$. $\checkmark$

**(3) Produto.** Escreva, somando e subtraindo $x_n b$:

$$
x_n y_n - a b = x_n y_n - x_n b + x_n b - a b = x_n (y_n - b) + (x_n - a)\, b.
$$

Como $(x_n)$ converge, é [[#^prop-convergente-limitada|limitada]]; e $y_n - b \to 0$, logo pelo [[#^lema-limitada-vezes-zero|lema]] $x_n(y_n - b) \to 0$. Também $(x_n - a)\,b \to 0$ (escalar $\times$ algo que tende a $0$). Pela soma **(1)**, $x_n y_n - ab \to 0$, ou seja, $x_n y_n \to ab$. $\checkmark$

**(4) Quociente.** Basta mostrar $\dfrac{1}{y_n} \to \dfrac{1}{b}$ (e usar **(3)** com $x_n$). Como $b \neq 0$, tome $\varepsilon = \dfrac{|b|}{2}$: existe $n_1$ t.q. $|y_n - b| < \dfrac{|b|}{2}$ para $n \geq n_1$, donde

$$
|y_n| \geq |b| - |y_n - b| > \frac{|b|}{2} > 0 \quad (n \geq n_1),
$$

logo $y_n \neq 0$ a partir de $n_1$ e $\left(\dfrac{1}{y_n}\right)$ fica bem definida e **limitada**. Agora

$$
\left| \frac{1}{y_n} - \frac{1}{b} \right| = \frac{|b - y_n|}{|y_n|\,|b|} \leq \frac{2}{|b|^2}\,|y_n - b| \to 0,
$$

usando $|y_n| > \dfrac{|b|}{2}$. Portanto $\dfrac{1}{y_n} \to \dfrac{1}{b}$ e, por **(3)**, $\dfrac{x_n}{y_n} \to \dfrac{a}{b}$. $\blacksquare$

---

