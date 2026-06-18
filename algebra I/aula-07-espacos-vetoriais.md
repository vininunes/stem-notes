#### motivação: o que matrizes e $\mathbb{R}^n$ têm em comum
^motivacao-espaco-vetorial

Já vimos dois conjuntos onde podemos **somar** elementos e **multiplicar por escalar**, e em ambos essas operações têm exatamente as mesmas propriedades:

- as matrizes $M_{m \times n}(\mathbb{R})$, com a [[aula-03-matrizes#^soma-matrizes|soma]] e o [[aula-03-matrizes#^produto-escalar-matriz|produto por escalar]];
- os vetores de $\mathbb{R}^n$ (que aparecem como colunas em $Ax = b$).

A ideia desta aula é **abstrair** essa estrutura: dar um nome a qualquer conjunto que se comporte assim. Esse conjunto é o **espaço vetorial**, e seus elementos passam a ser chamados de **vetores** — mesmo que sejam matrizes, polinômios ou funções.

---

#### definição de espaço vetorial #algebra/definição/espaço-vetorial
^espaco-vetorial

Um **espaço vetorial** (sobre $\mathbb{R}$) é um conjunto $V$ munido de duas operações:

- **soma:** $+ : V \times V \to V$, que a cada par $u, v \in V$ associa $u + v \in V$;
- **produto por escalar:** $\cdot : \mathbb{R} \times V \to V$, que a cada $\lambda \in \mathbb{R}$ e $v \in V$ associa $\lambda v \in V$;

satisfazendo os **oito axiomas** a seguir. Para todos $u, v, w \in V$ e $\lambda, \mu \in \mathbb{R}$:

**Axiomas da soma** (fazem de $V$ um [[aula-03-matrizes#^propriedades-soma-matrizes|grupo abeliano]]):

1. **Associatividade:** $(u + v) + w = u + (v + w)$
2. **Comutatividade:** $u + v = v + u$
3. **Elemento neutro:** existe $0 \in V$ tal que $v + 0 = v$ para todo $v$
4. **Elemento oposto:** para todo $v$ existe $-v \in V$ tal que $v + (-v) = 0$

**Axiomas do produto por escalar:**

5. **Elemento neutro escalar:** $1 \cdot v = v$
6. **Compatibilidade:** $\lambda (\mu v) = (\lambda \mu) v$
7. **Distributiva sobre soma de vetores:** $\lambda (u + v) = \lambda u + \lambda v$
8. **Distributiva sobre soma de escalares:** $(\lambda + \mu) v = \lambda v + \mu v$

> Os elementos de $V$ são chamados de **vetores** e os de $\mathbb{R}$, de **escalares**. O vetor $0$ do axioma 3 é o **vetor nulo**.

> **Observação:** comparando com a [[aula-03-matrizes#^propriedades-soma-matrizes|aula 03]], vemos que $M_{m \times n}(\mathbb{R})$ satisfaz os 4 axiomas da soma, e na [[aula-03-matrizes#^propriedades-produto-escalar-matriz|lista de propriedades do produto por escalar]] estão os axiomas 5–8. Ou seja: **$M_{m \times n}(\mathbb{R})$ é um espaço vetorial.**

---

#### exemplos de espaços vetoriais #algebra/definição/espaço-vetorial
^exemplos-espaco-vetorial

1. **$\mathbb{R}^n$** — as $n$-uplas $(x_1, \dots, x_n)$ com soma e produto por escalar coordenada a coordenada. É o exemplo fundamental.
2. **$M_{m \times n}(\mathbb{R})$** — as matrizes, com as operações da [[aula-03-matrizes#^soma-matrizes|aula 03]].
3. **$P_n(\mathbb{R})$** — os polinômios de grau $\le n$, com a soma e o produto por escalar usuais.
4. **$\mathcal{F}(\mathbb{R}, \mathbb{R})$** — todas as funções $f : \mathbb{R} \to \mathbb{R}$, com $(f+g)(x) = f(x) + g(x)$ e $(\lambda f)(x) = \lambda f(x)$.
5. **$\{0\}$** — o espaço que contém só o vetor nulo (espaço trivial).

> Em todos eles os axiomas valem porque, no fundo, as operações são feitas a partir das operações de $\mathbb{R}$.

---

#### consequências dos axiomas #algebra/proposição/propriedades-espaco-vetorial
^propriedades-espaco-vetorial

Dos oito axiomas decorrem fatos que parecem "óbvios", mas precisam ser provados. Para todo $v \in V$ e $\lambda \in \mathbb{R}$:

1. $0 \cdot v = 0$ (escalar zero vezes vetor = vetor nulo)
2. $\lambda \cdot 0 = 0$ (escalar vezes vetor nulo = vetor nulo)
3. $(-1) \cdot v = -v$
4. Se $\lambda v = 0$, então $\lambda = 0$ **ou** $v = 0$
5. O vetor nulo $0$ e o oposto $-v$ são **únicos**

> Esses resultados mostram que a notação $0$ (escalar) e $0$ (vetor nulo) "conversam" bem, e que $-v$ é mesmo o oposto no sentido do axioma 4.

---

#### subespaço vetorial #algebra/definição/subespaço-vetorial
^subespaco-vetorial

Seja $V$ um espaço vetorial. Um subconjunto $W \subseteq V$ é um **subespaço vetorial** de $V$ se $W$, com as **mesmas** operações de $V$, é por si só um espaço vetorial.

Na prática não precisamos reverificar os 8 axiomas: como as operações são herdadas de $V$, os axiomas que são "identidades" (associatividade, comutatividade, distributivas, etc.) já valem automaticamente em $W$. Basta garantir que as operações **não saem de $W$** e que os elementos especiais estão lá.

---

#### critério do subespaço #algebra/proposição/critério-subespaço
^criterio-subespaco

Um subconjunto $W \subseteq V$ é subespaço vetorial de $V$ se, e somente se, as três condições valem:

1. **$W$ é não-vazio (contém o vetor nulo):** $0 \in W$
2. **Fechado para a soma:** se $u, v \in W$, então $u + v \in W$
3. **Fechado para o produto por escalar:** se $v \in W$ e $\lambda \in \mathbb{R}$, então $\lambda v \in W$

> **Atalho útil:** as condições 2 e 3 podem ser reunidas numa só — $W$ é subespaço se $0 \in W$ e, para todos $u, v \in W$ e $\lambda \in \mathbb{R}$, vale $\lambda u + v \in W$ (fechado para **combinações lineares**).

> A condição 1 costuma ser o teste mais rápido para **descartar** um candidato: se $0 \notin W$, $W$ **não** é subespaço.

---

#### exemplos e contraexemplos
^exemplos-subespaco

**São subespaços de $\mathbb{R}^2$:**
- $\{(x, y) : y = 2x\}$ — uma reta pela origem.
- $\{(0,0)\}$ e o próprio $\mathbb{R}^2$ — os subespaços **triviais** (todo $V$ tem esses dois).

**Não são subespaços de $\mathbb{R}^2$:**
- $\{(x, y) : y = 2x + 1\}$ — reta que **não passa pela origem** ($0 \notin W$, falha a condição 1).
- $\{(x, y) : x \ge 0\}$ — o semiplano não é fechado para produto por escalar negativo (ex.: $(1,0) \in W$ mas $(-1)(1,0) = (-1,0) \notin W$).
- $\{(x, y) : xy = 0\}$ (os dois eixos) — não é fechado para soma: $(1,0) + (0,1) = (1,1) \notin W$.

---

#### exemplo importante: solução de sistema homogêneo #algebra/proposição/solucao-homogeneo-subespaco
^solucao-homogeneo-subespaco

O conjunto-solução de um [[aula-02-sistemas-lineares#^sistemas-homogeneos|sistema homogêneo]] $Ax = 0$, com $A \in M_{m \times n}(\mathbb{R})$, é um **subespaço de $\mathbb{R}^n$**.

**Verificação pelo [[#^criterio-subespaco|critério]]:** seja $W = \{x \in \mathbb{R}^n : Ax = 0\}$.

1. $A \cdot 0 = 0$, logo $0 \in W$. ✓
2. Se $u, v \in W$, então $A(u+v) = Au + Av = 0 + 0 = 0$, logo $u + v \in W$. ✓
3. Se $v \in W$ e $\lambda \in \mathbb{R}$, então $A(\lambda v) = \lambda (Av) = \lambda \cdot 0 = 0$, logo $\lambda v \in W$. ✓

> Isso explica geometricamente por que a solução de um homogêneo, quando não é só $\{0\}$, é uma reta/plano **passando pela origem**, e conecta com a [[aula-02-sistemas-lineares#^solucao-geral-particular|relação solução geral = particular + homogênea]] da aula 02. O conjunto-solução de $Ax = b$ com $b \neq 0$ **não** é subespaço (não contém o $0$).

---

#### interseção de subespaços #algebra/proposição/intersecao-subespacos
^intersecao-subespacos

Se $W_1$ e $W_2$ são subespaços de $V$, então a interseção $W_1 \cap W_2$ também é subespaço de $V$.

> **Cuidado:** a **união** $W_1 \cup W_2$ em geral **não** é subespaço (ex.: a união de dois eixos em $\mathbb{R}^2$, vista acima). Para "juntar" subespaços usa-se a **soma** $W_1 + W_2$, que será tema das próximas aulas.

> **Próxima aula:** combinações lineares, subespaço gerado e dependência/independência linear.
