#### combinação linear #algebra/definição/combinação-linear
^combinacao-linear

Seja $V$ um [[aula-07-espacos-vetoriais#^espaco-vetorial|espaço vetorial]] e $v_1, v_2, \dots, v_n \in V$. Uma **combinação linear** desses vetores é qualquer vetor da forma

$$a_1 v_1 + a_2 v_2 + \cdots + a_n v_n, \qquad a_1, \dots, a_n \in \mathbb{R}.$$

Os $a_i$ são os **coeficientes** da combinação.

> Tomando todos os coeficientes iguais a zero obtemos sempre o vetor nulo: $0 \cdot v_1 + \cdots + 0 \cdot v_n = 0$. Essa é a **combinação trivial**. A pergunta da aula é: *existe alguma outra forma de obter o vetor nulo?*

---

#### independência linear (LI) #algebra/definição/independência-linear
^independencia-linear

Os vetores $v_1, \dots, v_n$ são **linearmente independentes (LI)** quando a única combinação linear deles que resulta no vetor nulo é a trivial. Isto é:

$$a_1 v_1 + a_2 v_2 + \cdots + a_n v_n = 0 \quad \Longrightarrow \quad a_1 = a_2 = \cdots = a_n = 0.$$

> Em palavras: a **única** maneira de "zerar" a combinação é com **todos** os coeficientes nulos.

---

#### dependência linear (LD) #algebra/definição/dependência-linear
^dependencia-linear

Os vetores $v_1, \dots, v_n$ são **linearmente dependentes (LD)** quando **não** são LI, ou seja: existe alguma combinação linear igual ao vetor nulo com **pelo menos um coeficiente diferente de zero**.

$$\exists\, (a_1, \dots, a_n) \neq (0, \dots, 0) \quad \text{tal que} \quad a_1 v_1 + \cdots + a_n v_n = 0.$$

---

#### caracterização da dependência #algebra/proposição/caracterizacao-LD
^caracterizacao-LD

Os vetores $v_1, \dots, v_n$ são LD se, e somente se, **pelo menos um deles é combinação linear dos outros**.

> Ideia: se $a_1 v_1 + \cdots + a_n v_n = 0$ com algum $a_k \neq 0$, podemos isolar $v_k = -\frac{1}{a_k}\sum_{i \neq k} a_i v_i$. Por isso dizemos que num conjunto LD um vetor "sobra" — ele não acrescenta nada de novo.

> **Observação (rumo à base):** todo conjunto LD pode ser **reduzido** — removendo os vetores redundantes (aqueles que são combinação dos demais) — a um **subconjunto LI que gera o mesmo subespaço**. A simplificação é por *remoção* (o resultado é subconjunto do original), e o que se preserva é o *alcance* (o subespaço gerado), não o tamanho. Esse procedimento é exatamente o que leva ao conceito de **base**: um conjunto LI que gera o espaço — o "menor" conjunto capaz de gerar tudo. *(a formalizar nas próximas aulas)*

---

#### critério prático: pivôs e sistemas homogêneos #algebra/proposição/criterio-LI-pivos
^criterio-LI-pivos

Testar se as colunas de uma matriz $A \in M_{m \times n}(\mathbb{R})$ são LI é exatamente perguntar se o [[aula-02-sistemas-lineares#^sistemas-homogeneos|sistema homogêneo]] $Ax = 0$ tem **só a solução trivial**. Escalonando $A$:

- **toda coluna tem [[aula-07-espacos-vetoriais#^solucao-homogeneo-subespaco|pivô]]** $\Rightarrow$ só solução trivial ([[aula-01-escalonamento#^criterio-spd|SPD]]) $\Rightarrow$ colunas **LI**;
- **alguma coluna sem pivô** (variável livre) $\Rightarrow$ existe solução não trivial ([[aula-01-escalonamento#^criterio-spi|SPI]]) $\Rightarrow$ colunas **LD**.

> Consequência imediata: em $\mathbb{R}^m$, qualquer conjunto com **mais de $m$ vetores** é necessariamente LD (mais colunas que linhas $\Rightarrow$ alguma coluna fica sem pivô).

---

#### casos particulares
^casos-particulares-li-ld

- Um único vetor $\{v\}$ é LI se, e somente se, $v \neq 0$.
- Qualquer conjunto que **contém o vetor nulo** é LD (basta pôr coeficiente $1$ no $0$ e $0$ nos demais).
- Dois vetores são LD se, e somente se, um é **múltiplo** do outro (paralelos).

---

#### subespaço gerado #algebra/definição/subespaço-gerado
^subespaco-gerado

Seja $V$ um espaço vetorial e $S = \{v_1, \dots, v_n\} \subseteq V$. O **subespaço gerado** por $S$ é o conjunto de **todas** as combinações lineares de $S$:

$$[S] = \langle v_1, \dots, v_n \rangle = \{\, a_1 v_1 + \cdots + a_n v_n : a_1, \dots, a_n \in \mathbb{R} \,\}.$$

> $[S]$ é de fato um [[aula-07-espacos-vetoriais#^criterio-subespaco|subespaço]] de $V$ (contém o $0$, é fechado para soma e produto por escalar). É o **menor** subespaço que contém $S$.

Quando $[S] = V$, dizemos que $S$ **gera** $V$, e $S$ é um **conjunto gerador** de $V$.

---

#### base #algebra/definição/base
^base

Uma **base** de um espaço vetorial $V$ é um conjunto $\mathcal{B} = \{v_1, \dots, v_n\}$ que é, simultaneamente:

1. **[[#^independencia-linear|linearmente independente (LI)]]**, e
2. **[[#^subespaco-gerado|gerador]]** de $V$ (isto é, $[\mathcal{B}] = V$).

> É a formalização da [[#^caracterizacao-LD|observação rumo à base]]: a base é o conjunto **sem redundância** (LI) que ainda **dá conta de gerar tudo**. É o conjunto gerador de tamanho mínimo.

**Exemplo (base canônica de $\mathbb{R}^n$):**

$$e_1 = (1, 0, \dots, 0),\quad e_2 = (0, 1, 0, \dots, 0),\quad \dots,\quad e_n = (0, \dots, 0, 1).$$

São LI e geram $\mathbb{R}^n$, pois $(x_1, \dots, x_n) = x_1 e_1 + \cdots + x_n e_n$.

> **Unicidade dos coeficientes:** se $\mathcal{B}$ é base, então **todo** vetor de $V$ se escreve de **uma única maneira** como combinação linear dos elementos de $\mathcal{B}$. (Esses coeficientes únicos são as **coordenadas** do vetor na base.)

> **Próximo passo:** todas as bases de um mesmo espaço têm o **mesmo número de elementos** — esse número é a **dimensão** de $V$. *(a formalizar)*
