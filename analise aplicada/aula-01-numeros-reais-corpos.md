#### visão geral do curso
^visao-geral-curso

- Números reais (o que são, ou o que queremos com eles)
- Sequência de números reais
- Funções $\mathbb{R} \to \mathbb{R}$, continuidade
- Sequência de funções e séries
- Série de Taylor

#### linguagem, lógica e modo de pensar em análise
^linguagem-logica-analise

A análise trabalha com o ciclo **intuição → formalização**. A formalização é o que permite a comunicação precisa das ideias matemáticas.

É natural sentir um "medo do que não se entende" — uma espécie de **vertigem** diante do formalismo. Faz parte do processo.

#### números reais — abordagem por propriedades
^numeros-reais-propriedades

Nós não vamos dizer **quem são** os números reais, mas sim quais **propriedades** queremos que eles tenham.

Para dizer quem são os reais, precisaríamos do contexto da base da matemática — os axiomas.

##### axiomas de Zermelo-Fraenkel (ZFC)
^axiomas-zfc

Os **Axiomas de Zermelo-Fraenkel** com o **Axioma da Escolha** (ZFC) são axiomas que dizem quais conjuntos podem ser construídos. A partir deles, podemos construir um conjunto com todas as propriedades estruturais dos números naturais, e a partir dos naturais (por várias construções) chegamos no conjunto com todas as propriedades dos números reais.

Vamos começar entendendo quais são essas propriedades.

#### o conjunto dos números reais
^conjunto-numeros-reais

O conjunto dos números reais é um **corpo ordenado completo**:

- **Corpo**: propriedades algébricas (operações de soma e produto)
- **Ordenado**: possui uma relação de ordem
- **Completo**: não tem "buracos"

#### corpo #analise/definição/corpo
^definicao-corpo

$K$ é um **corpo** se nele estiverem definidas as operações:

$$
+: K \times K \to K, \quad (a, b) \mapsto a + b
$$

$$
\cdot: K \times K \to K, \quad (a, b) \mapsto a \cdot b
$$

tais que valem as seguintes propriedades:

##### axiomas da adição
^axiomas-adicao

**A1 — Associatividade da adição:** #analise/axioma/A1-associatividade-adição

$$
(a + b) + c = a + (b + c), \quad \forall \; a, b, c \in K
$$

**A2 — Comutatividade da adição:** #analise/axioma/A2-comutatividade-adição

$$
a + b = b + a, \quad \forall \; a, b \in K
$$

**A3 — Existência do elemento neutro da adição:** #analise/axioma/A3-neutro-adição

Existe um elemento em $K$, que chamaremos de $0$ (zero), tal que:

$$
a + 0 = a, \quad \forall \; a \in K
$$

**Definição:** #analise/definição/oposto Seja $a \in K$. Dizemos que $b \in K$ é o **oposto** (ou simétrico) de $a$ em relação a um elemento neutro $\theta$ se $a + b = \theta$.

**A4 — Existência do oposto:** #analise/axioma/A4-existência-oposto

Todo elemento em $K$ tem um oposto em relação ao $0$.

##### axiomas da multiplicação
^axiomas-multiplicacao

**M1 — Associatividade da multiplicação:** #analise/axioma/M1-associatividade-multiplicação

$$
(a \cdot b) \cdot c = a \cdot (b \cdot c), \quad \forall \; a, b, c \in K
$$

**M2 — Comutatividade da multiplicação:** #analise/axioma/M2-comutatividade-multiplicação

$$
a \cdot b = b \cdot a, \quad \forall \; a, b \in K
$$

**M3 — Existência do elemento neutro da multiplicação:** #analise/axioma/M3-neutro-multiplicação

Existe um elemento em $K$, que chamaremos de $1$ (um), com $1 \neq 0$, tal que:

$$
a \cdot 1 = a, \quad \forall \; a \in K
$$

**M4 — Existência do inverso multiplicativo:** #analise/axioma/M4-inverso-multiplicativo

Todo elemento $a \neq 0$ em $K$ possui um inverso $a^{-1} \in K$ tal que:

$$
a \cdot a^{-1} = 1
$$

##### axioma distributivo #analise/axioma/D-distributividade
^axioma-distributivo

**D — Distributividade:**

$$
a \cdot (b + c) = a \cdot b + a \cdot c, \quad \forall \; a, b, c \in K
$$

#### lemas sobre a estrutura de corpo
^lemas-estrutura-corpo

**Lema:** O elemento neutro é único. #analise/lema/unicidade-neutro

**Prova:** Tome $\theta$ um elemento neutro qualquer. Objetivo: mostrar que $\theta = 0$.

Tome $a \in K$ qualquer. Como $\theta$ é neutro:

$$
a + \theta = a
$$

Somando $(-a)$ em ambos os lados:

$$
(a + \theta) + (-a) = a + (-a)
$$

Por A1 (associatividade) e pela definição de $-a$:

$$
\theta + (a + (-a)) = 0
$$

$$
\theta + 0 = 0
$$

$$
\theta = 0 \qquad \blacksquare
$$

**Lema:** Cada elemento $a \in K$ tem um único oposto. #analise/lema/unicidade-oposto

**Prova:** Suponha $b, c \in K$ tais que $a + b = 0$ e $a + c = 0$.

$$
c + (a + b) = c + 0 = c
$$

Por A1:

$$
(c + a) + b = c
$$

Como $a + c = 0$ e por A2 temos $c + a = 0$:

$$
0 + b = c
$$

$$
b = c \qquad \blacksquare
$$


