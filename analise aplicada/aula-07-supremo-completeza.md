#### dia do supremo
^titulo-aula-07

$K$ [[aula-02-corpos-ordenados#^definicao-corpo-ordenado|corpo ordenado]].

---

#### definição: cota superior e inferior (recapitulação) #analise/definição/cotas-recap
^cotas-recap

**Definição.** Seja $X \subseteq K$.

- $b$ é **cota superior** de $X$ se $\forall\, x \in X,\; x \leq b$.
- $b$ é **cota inferior** de $X$ se $\forall\, x \in X,\; b \leq x$.

---

#### definição: supremo #analise/definição/supremo
^definicao-supremo

**Ideia informal:** é a menor cota superior, se existir.

**Definição.** $b \in K$ é **supremo** de $X$ se:

**(i)** $b$ é cota superior de $X$

**(ii)** Para qualquer cota superior $c$ de $X$, tem-se $b \leq c$

**Afirmação.** Equivalente a (ii):

**(ii')** Se $c < b$, então $c$ **não** é cota superior de $X$.

> **Obs:** Nem sempre existe o supremo de um conjunto $X$:
> - $X$ pode não ter cota superior (p.ex., $\mathbb{N}$ no corpo $\mathbb{Q}$)
> - $X$ tem cota superior mas não tem a **menor** cota superior

---

#### exemplo trivial: $X = \emptyset$
^supremo-vazio

$\emptyset \subseteq (-\infty, b]$ para todo $b \in K$, i.e., todo $b \in K$ é cota superior de $\emptyset$.

$\implies$ não existe a menor cota superior (não há mínimo de $K$).

---

#### exemplo: $X = \{x \in \mathbb{Q} \mid x \geq 0,\; x^2 < 2\}$ em $K = \mathbb{Q}$
^exemplo-raiz-2

$X$ tem cota superior (em $\mathbb{Q}$), mas **não tem supremo** em $\mathbb{Q}$.

> Discutiremos adiante.

---

#### exemplo: $\sup(0,1) = 1$ em $\mathbb{Q}$ #analise/exemplo/sup-intervalo-aberto
^exemplo-sup-intervalo-aberto

$X = (0,1) \subseteq \mathbb{Q}$.

**$1$ é cota superior:** $\forall\, x \in (0,1),\; x < 1 \implies x \leq 1$. $\checkmark$

**$1$ é a menor cota superior:** Tome $c < 1$. Queremos mostrar que $c$ **não** é cota superior de $X = (0,1)$.

Precisamos achar $a \in X$ t.q. $c < a$ (i.e., $\neg(a \leq c)$).

Tome $a = \dfrac{c + 1}{2}$.

- $a \in (0,1)$? Como $c < 1$: $a = \dfrac{c+1}{2} < \dfrac{1+1}{2} = 1$. E $a > c \geq 0$ (se $c \geq 0$). $\checkmark$

**Prova:** $a = \dfrac{c+1}{2} > \dfrac{c+c}{2} = \dfrac{2c}{2} = c$. $\checkmark$

Logo $\sup(0,1) = 1$. $\blacksquare$

---

#### definição: ínfimo #analise/definição/infimo
^definicao-infimo

**Ínfimo:** maior cota inferior (tudo análogo ao supremo).

---

#### exemplo: $\inf\{1/n \mid n \in \mathbb{N}\} = 0$ em $\mathbb{Q}$ #analise/exemplo/inf-1-sobre-n
^exemplo-inf-1-sobre-n

$X = \{1/n \mid n \in \mathbb{N}\} \subseteq \mathbb{Q}$.

**$0$ é cota inferior?** $0 \leq \dfrac{1}{n}$, $\forall\, n \in \mathbb{N}$ $\implies$ é cota inferior. $\checkmark$

**$0$ é a maior cota inferior?** Tome $c > 0$. Queremos mostrar que existe um elemento de $X$ menor do que $c$.

Como $\mathbb{Q}$ é [[aula-06-intervalos-limitacao-arquimediano#^definicao-arquimediano|arquimediano]], $\exists\, n \in \mathbb{N}$ t.q.:

$$
0 < \frac{1}{n} < c
$$

E $\dfrac{1}{n} \in X$. $\implies 0$ é ínfimo. $\blacksquare$

---

#### proposição: unicidade do supremo #analise/proposição/unicidade-supremo
^unicidade-supremo

**Proposição.** O supremo, se existir, é único.

**Prova.** Seja $X \subseteq K$, e sejam $b, \tilde{b}$ supremos de $X$.

$b$ e $\tilde{b}$ são cotas superiores.

Como $b$ é a menor cota superior: $b \leq \tilde{b}$.

Como $\tilde{b}$ é a menor cota superior: $\tilde{b} \leq b$.

$\implies b = \tilde{b}$. $\blacksquare$

Portanto, se existir supremo para $X$, será "**o** supremo".

**Notação:** $\sup X$, e para o ínfimo: $\inf X$.

---

#### definição: máximo #analise/definição/maximo
^definicao-maximo

**Definição.** $b$ é **máximo** de $X$ se:

**(i)** $b$ é cota superior de $X$

**(ii)** $b \in X$

---

#### proposição: máximo implica supremo #analise/proposição/maximo-implica-supremo
^maximo-implica-supremo

**Proposição.** Se $b$ é máximo de $X$, então $b = \sup X$.

**Prova.**

**(i)** $b = \max X \implies b$ é cota superior. $\checkmark$

**(ii')** Tome $c < b$. $c$ pode ser cota superior de $X$?

Não, pois $b \in X$ é um ponto de $X$ não limitado superiormente por $c$. $\checkmark$ $\blacksquare$

---

#### proposição: supremo que pertence ao conjunto é máximo #analise/proposição/sup-em-X-e-maximo
^sup-em-X-e-maximo

**Proposição.** Se $b = \sup X$ e $b \in X$, então $b = \max X$.

**Prova.**

- $b \in X$ $\checkmark$ (hipótese)
- $b = \sup X \implies b$ é cota superior $\implies$ (i) $\checkmark$

$\implies b = \max X$. $\blacksquare$

---

#### lema facilitador #analise/lema/lema-facilitador-sup
^lema-facilitador

**Lema.** $K$ corpo ordenado, $X \subseteq K$, $b = \sup X$.

Então para qualquer $a < b$, existe um elemento de $X$ em $(a, b]$.

**Prova.** $b = \sup X \implies b$ é cota superior de $X \implies X \subseteq (-\infty, b]$.

Suponha por absurdo que não exista elemento de $X$ em $(a, b]$.

Isso implicaria que $X \subseteq (-\infty, a]$, ou seja, $a$ é cota superior de $X$ com $a < b$.

Mas isso contradiz $b = \sup X$ (menor cota superior). $\blacksquare$

> **Obs:** Pode acontecer $b = \max X$ "isolado" de $X$: os elementos de $X \setminus \{b\}$ ficam todos antes de algum $a < b$, e $b$ fica sozinho.
>
> Mas se $b$ **não** é máximo (i.e., $b \notin X$), então para todo $a < b$ existe elemento de $X$ em $(a, b)$ — os elementos de $X$ se "acumulam" perto de $b$.

---

#### definição: corpo ordenado completo (axioma do supremo) #analise/definição/completo
^definicao-completo

**Definição.** $K$ corpo ordenado. Dizemos que $K$ é **completo** se para todo conjunto $X \subseteq K$, $X \neq \emptyset$, limitado superiormente, existe $\sup X$.

> **Obs:** $\mathbb{Q}$ **não** é completo (vide [[#^exemplo-raiz-2|exemplo da $\sqrt{2}$]]).

---

#### definição de $\mathbb{R}$ #analise/definição/reais
^definicao-reais

Chamamos de $\mathbb{R}$ qualquer [[aula-01-numeros-reais-corpos#^conjunto-numeros-reais|corpo ordenado completo]].

---

#### unicidade essencial de $\mathbb{R}$ #analise/proposição/unicidade-R
^unicidade-R

**Obs:** $\mathbb{R}$ é essencialmente único.

Sejam $K$ e $L$ corpos ordenados completos. Então existe uma bijeção $f : K \to L$ que satisfaz:

$$
f(x + y) = f(x) + f(y) \qquad \text{(soma em } K \to \text{soma em } L\text{)}
$$

$$
f(x \cdot y) = f(x) \cdot f(y) \qquad \text{(produto em } K \to \text{produto em } L\text{)}
$$

$$
f(P_K) = P_L
$$

$$
\sup f(X) = f(\sup X)
$$

**Afirmação.** $x \leq y \implies f(x) \leq f(y)$.

**Prova:**

$$
x < y \iff y - x \in P_K \iff f(y - x) \in P_L \iff f(y) - f(x) \in P_L \iff f(x) < f(y)
$$

**Conclusão:** As propriedades provadas em um corpo ordenado completo se transferem para o outro, desde que usem apenas aritmética ([[aula-01-numeros-reais-corpos#^axiomas-adicao|(A1)–(A4)]], [[aula-01-numeros-reais-corpos#^axiomas-multiplicacao|(M1)–(M4)]], [[aula-01-numeros-reais-corpos#^axioma-distributivo|(D)]]), ordem ([[aula-02-corpos-ordenados#^definicao-corpo-ordenado|(P1), (P2)]]) e completeza.

---

#### existência do ínfimo em $\mathbb{R}$ #analise/proposição/existencia-infimo
^existencia-infimo

**Proposição.** Em $\mathbb{R}$, se $X \neq \emptyset$ e é limitado inferiormente, então existe $\inf X$.

**Prova.** Fica como exercício.

**Dica:** Tome $Y = -X$. $X$ limitado inferiormente $\implies Y$ limitado superiormente.

$$
\inf X = -\sup Y = -\sup(-X) \qquad (\exists\, \sup Y \text{ pela completeza})
$$

---

#### teorema: $\mathbb{R}$ é arquimediano #analise/proposição/R-arquimediano
^R-arquimediano

**Teorema.** $\mathbb{R}$ (corpo ordenado completo) é [[aula-06-intervalos-limitacao-arquimediano#^definicao-arquimediano|arquimediano]].

**Prova.** Por contradição. Suponha que $\mathbb{N} \subseteq \mathbb{R}$ seja limitado superiormente.

$\mathbb{R}$ completo, $\mathbb{N} \neq \emptyset$, limitado superiormente $\implies \exists\, b = \sup \mathbb{N}$.

Em particular, $b$ é cota superior:

$$
n \leq b, \quad \forall\, n \in \mathbb{N}
$$

Mas também é verdade que:

$$
n + 1 \leq b, \quad \forall\, n \in \mathbb{N}
$$

$$
\implies n \leq b - 1, \quad \forall\, n \in \mathbb{N}
$$

Logo $b - 1$ é cota superior de $\mathbb{N}$, e $b - 1 < b$.

Mas $b$ é a **menor** cota superior de $\mathbb{N}$. **Contradição.**

Logo $\mathbb{N}$ é ilimitado e $\mathbb{R}$ é arquimediano. $\blacksquare$