
#### exercício importante — $\mathbb{Z}_n$ é corpo?
^exercicio-zn-corpo

Vamos adotar como hipótese (nos axiomas) que $0 \neq 1$, e utilizamos $K$ arbitrário.

Considere $\mathbb{Z}_n = \{0, 1, 2, \dots, n-1\}$ com as operações $\mod n$.

**Exemplo:** $n = 6$, $\mathbb{Z}_6 = \{0, 1, 2, 3, 4, 5\}$.

Quem é $(3 \cdot 5) \mod 6$? Temos $3 \cdot 5 = 15$ e $15 \mod 6 = 3$.

$\mathbb{Z}_6$ **não é corpo**. Precisamos que todo elemento não nulo tenha [[aula-01-numeros-reais-corpos#^axiomas-multiplicacao|inverso multiplicativo (M4)]], mas:

$$
2 \cdot 3 \equiv 0 \pmod{6}
$$

com $2 \neq 0$ e $3 \neq 0$. Existem **divisores de zero**, o que impede $\mathbb{Z}_6$ de ser [[aula-01-numeros-reais-corpos#^definicao-corpo|corpo]].

> Para entender corpos, é importante considerar exemplos que **não** satisfazem os axiomas.

---

#### corpo ordenado #analise/definição/corpo-ordenado
^definicao-corpo-ordenado

**Definição.** $(K, +, \cdot, P)$ é um **corpo ordenado** se $(K, +, \cdot)$ é um [[aula-01-numeros-reais-corpos#^definicao-corpo|corpo]] e $P \subseteq K$ é um subconjunto que chamamos de **números positivos**, satisfazendo:

**(P1) Invariância pelas operações:** #analise/axioma/P1-fechamento-positivos

$$
x, y \in P \implies x + y \in P \quad \text{e} \quad x \cdot y \in P
$$

**(P2) Tricotomia:** #analise/axioma/P2-tricotomia

$$
\forall \; x \in K, \quad \text{exatamente uma das três vale:} \quad x \in P, \quad x = 0, \quad -x \in P
$$

---

#### relações de ordem #analise/definição/ordem
^relacoes-de-ordem

**Definição.** Sejam $x, y \in K$. Dizemos que:

$$
x < y \iff y - x \in P
$$

$$
x \leq y \iff x < y \;\text{ ou }\; x = y
$$

$$
x > y \iff y < x
$$

---

#### propriedades (consequências dos axiomas)
^propriedades-ordem

**(O1) Transitividade:** #analise/proposição/O1-transitividade

$$
x < y \;\text{ e }\; y < z \implies x < z
$$

**Prova:** $y - x \in P$ e $z - y \in P$. Por (P1):

$$
(y - x) + (z - y) = z - x \in P
$$

Logo $x < z$. $\blacksquare$

**(O2) Tricotomia:** #analise/proposição/O2-tricotomia-ordem

$$
\forall \; x, y \in K, \quad \text{exatamente uma vale:} \quad x < y, \quad x = y, \quad x > y
$$

**(O3) Compatibilidade com a adição:** #analise/proposição/O3-compatibilidade-adição

$$
x < y \implies x + z < y + z, \quad \forall \; z \in K
$$

**Prova:** $y - x \in P$. Observe que $(y + z) - (x + z) = y - x \in P$. $\blacksquare$

**(O4) Compatibilidade com a multiplicação:** #analise/proposição/O4-compatibilidade-multiplicação

$$
x < y \;\text{ e }\; 0 < z \implies x \cdot z < y \cdot z
$$

**Prova:** $y - x \in P$ e $z \in P$. Por (P1), $(y - x) \cdot z = yz - xz \in P$. $\blacksquare$

---

#### proposição: $a \neq 0 \implies a^2 > 0$ #analise/proposição/quadrado-positivo
^proposicao-quadrado-positivo

**Prova:** Por (P2) tricotomia, como $a \neq 0$, temos dois casos:

**Caso 1:** $a \in P$.

Por (P1), $a \cdot a = a^2 \in P$, logo $a^2 > 0$.

**Caso 2:** $-a \in P$.

Por (P1), $(-a)(-a) = a^2 \in P$, logo $a^2 > 0$. $\blacksquare$

#### corolário: $1 > 0$ #analise/corolário/um-positivo
^corolario-um-positivo

**Prova:** Pela hipótese $1 \neq 0$. Pela [[aula-02-corpos-ordenados#^proposicao-quadrado-positivo|proposição anterior]], $1^2 = 1 > 0$. $\blacksquare$

---

> **Próximo passo:** definir os números naturais e a divisão dentro de um corpo ordenado.
