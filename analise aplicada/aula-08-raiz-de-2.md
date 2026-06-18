#### tema da aula: $\sqrt{2}$
^titulo-aula-08

$\sqrt{2}$ = o "número" positivo que elevado ao quadrado dá $2$.

---

#### $\sqrt{2}$ não é racional #analise/proposição/raiz-2-irracional
^raiz-2-irracional

Vejamos dentro dos racionais: $\exists\, x \in \mathbb{Q}$ t.q. $x^2 = 2$?

**Não existe!**

**Prova.** Escreva $x = \dfrac{p}{q}$ com $x > 0$, $p, q > 0$.

Suponha que $p$ e $q$ não têm fatores comuns (se tiver, cancele-os!).

Suponha por contradição que $x^2 = 2$, i.e.:

$$
\left(\frac{p}{q}\right)^2 = 2
$$

$$
\boxed{p^2 = 2q^2} \quad (\ast)
$$

Pelo Teorema da Fatoração em Primos, $2$ é um fator de $p^2$.

Então $2$ é fator de $p$. Portanto, $p = 2\tilde{p}$.

Inserimos em $(\ast)$:

$$
(2\tilde{p})^2 = 2q^2
$$

$$
4\tilde{p}^2 = 2q^2
$$

$$
\boxed{2\tilde{p}^2 = q^2}
$$

Agora concluímos que $2$ é fator de $q^2$, logo de $q$.

Temos que $2$ é fator comum de $p$ e $q$. **Contradição**, pois assumimos que $p$ e $q$ não têm fator comum. $\blacksquare$

---

#### existência de $\sqrt{2}$ em $\mathbb{R}$ #analise/proposição/existencia-raiz-2
^existencia-raiz-2

Mas em $\mathbb{R}$, $\exists\, x$ t.q. $x^2 = 2$?

Temos que responder usando que $\mathbb{R}$ é [[aula-07-supremo-completeza#^definicao-completo|corpo ordenado completo]].

A resposta é **afirmativa**.

**Roteiro da prova.** Defina:

$$
S = \{x \in \mathbb{R} \mid x > 0,\; x \in \mathbb{Q},\; x^2 < 2\}
$$

---

#### $S \neq \emptyset$ e $S$ é limitado superiormente
^S-nao-vazio-limitado

**$S \neq \emptyset$?** Sim, pois $1 \in S$:
- $1 > 0$ $\checkmark$
- $1 \in \mathbb{Q}$ $\checkmark$
- $1^2 < 2$ $\checkmark$

**$S$ é limitado superiormente?** $2$ é cota superior. Por quê?

$\forall\, x \in S$, $x^2 < 2 < 4$.

> **Exercício:** $x, y > 0$: $x < y \iff x^2 < y^2$.

$$
x^2 < 4 \iff x^2 < 2^2 \iff x < 2 \quad \checkmark
$$

---

#### existência de $\sup S$ e o objetivo
^sup-S-objetivo

Portanto existe $b = \sup S$ (pelo [[aula-07-supremo-completeza#^definicao-completo|Axioma da Completeza]]).

Parte mais trabalhosa: provar que $b^2 = 2$.

---

#### lema: quadrados perfeitos em intervalos (Ex. 40) #analise/lema/quadrados-em-intervalos
^lema-quadrados-intervalos

> **Parênteses** para citar um Lema que é o Exercício 40.

**Lema.** $\forall\, m \in \mathbb{N}$, $\exists\, r_0 \in \mathbb{N}$, $\forall\, r \geq r_0$ ($r \in \mathbb{N}$), os intervalos $\left(r - \dfrac{r}{m},\, r\right]$ e $\left(r,\, r + \dfrac{r}{m}\right)$ contêm números naturais ao quadrado.

> **Obs:** O tamanho desses intervalos relativos a $r$ é $1/m$.

---

#### intuição sobre o lema
^intuicao-lema

A proporção entre a distância de quadrados sucessivos com respeito a seus valores vai a zero.

Na reta numérica: $n^2$ e $(n+1)^2$ estão a distância $2n + 1$.

$$
\frac{2n+1}{n^2} = \frac{2}{n} + \frac{1}{n^2} \to 0
$$

**Ideia da prova.** Considere os intervalos $\left(r - \dfrac{r}{m},\, r\right]$ e $\left(r,\, r + \dfrac{r}{m}\right)$.

Seja $n^2$ o maior quadrado $\leq r$. Se tivermos:

$$
(n+1)^2 - n^2 < \frac{r}{m} \implies n^2 \text{ e } (n+1)^2 \text{ estão nos intervalos citados no Lema.}
$$

Ora:

$$
2n + 1 = (2n+1) \cdot \frac{r}{r} \leq \frac{2n+1}{n^2} \cdot r = \left(\frac{2}{n} + \frac{1}{n^2}\right) r
$$

(pois $r \geq n^2$). O $m$ foi fixado. Então, se $r$ for suficientemente grande, $n$ será grande e $\dfrac{2}{n} + \dfrac{1}{n^2} \ll \dfrac{1}{m}$.

---

#### consequência do lema #analise/proposição/racionais-perto-de-2
^racionais-perto-de-2

Suponha $r = 2q^2$, $q \in \mathbb{N}$.

Pelo Lema, se $q$ for suficientemente grande, existem naturais $p^2$ e $\tilde{p}^2$ nesses dois intervalos:

$$
2q^2 - \frac{2q^2}{2m} < p^2 \leq 2q^2 < \tilde{p}^2 < 2q^2 + \frac{2q^2}{2m}
$$

> O igual com $2q^2$ não pode haver, pois [[#^raiz-2-irracional|já vimos]] que $\sqrt{2} \notin \mathbb{Q}$.

Dividindo por $q^2$:

$$
2 - \frac{1}{m} < \left(\frac{p}{q}\right)^2 < 2 < \left(\frac{\tilde{p}}{q}\right)^2 < 2 + \frac{1}{m}
$$

**Conclusão:** Dado $m \in \mathbb{N}$, existem racionais ao quadrado à distância menor do que $1/m$ de $2$, à esquerda e à direita de $2$.

---

#### prova de que $b^2 = 2$ #analise/proposição/sup-S-ao-quadrado
^prova-b2-igual-2

Vamos provar que $b^2 = 2$, onde $b = \sup S$.

Por [[aula-02-corpos-ordenados#^definicao-corpo-ordenado|tricotomia]]: ou $b^2 < 2$ ou $b^2 = 2$ ou $b^2 > 2$.

Vamos mostrar que não valem $b^2 < 2$ e $b^2 > 2$.

---

#### caso $b^2 < 2$: contradição
^caso-b2-menor-2

Lembrando: $b = \sup\{x \in \mathbb{R} \mid x > 0,\; x \in \mathbb{Q},\; x^2 < 2\}$.

**Suponha $b^2 < 2$.**

$\mathbb{R}$ [[aula-07-supremo-completeza#^definicao-completo|completo]] $\implies$ $\mathbb{R}$ [[aula-07-supremo-completeza#^R-arquimediano|arquimediano]] $\implies$ $\exists\, m \in \mathbb{N}$, $0 < \dfrac{1}{m} < 2 - b^2$.

$$
2 - \frac{1}{m} > 2 - (2 - b^2) = b^2
$$

Logo, pela [[#^racionais-perto-de-2|consequência do lema]], existe $x = \dfrac{p}{q}$ t.q.:

$$
b^2 < x^2 < 2 \implies b < x
$$

Mas aí temos $x \in S$, com $b < x$. **Contradiz** que $b$ é cota superior de $S$. $\blacksquare$

---

#### caso $b^2 > 2$: contradição
^caso-b2-maior-2

**Suponha $b^2 > 2$.**

$\exists\, m \in \mathbb{N}$ (pois $\mathbb{R}$ é arquimediano) t.q. $0 < \dfrac{1}{m} < b^2 - 2$.

Pela [[#^racionais-perto-de-2|consequência do lema]], existe $\dfrac{\tilde{p}}{q}$ t.q.:

$$
2 < \left(\frac{\tilde{p}}{q}\right)^2 < 2 + \frac{1}{m}
$$

**Afirmação.** $\dfrac{\tilde{p}}{q}$ é cota superior de $S$.

Tome $x \in S$: $x^2 < 2$. Mas $2 < \left(\dfrac{\tilde{p}}{q}\right)^2$.

$$
\implies x^2 < \left(\frac{\tilde{p}}{q}\right)^2 \implies x < \frac{\tilde{p}}{q}
$$

E aí contradiz que $b$ é a **menor** cota superior, pois $\dfrac{\tilde{p}}{q} < b$. $\blacksquare$

---

#### conclusão: $b^2 = 2$ #analise/proposição/existencia-raiz-n
^conclusao-raiz-2

Portanto só resta $b^2 = 2$. $\blacksquare$

O mesmo raciocínio serve para mostrar que:

$$
\forall\, n \in \mathbb{N},\; \forall\, a > 0,\; \exists\, \text{``}\sqrt[n]{a}\text{''}
$$