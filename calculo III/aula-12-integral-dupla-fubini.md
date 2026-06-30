#### motivação: o que é integrar em duas variáveis #calculo/motivação/integral-dupla
^motivacao-integral-dupla

Na [[aula-01-funções#^superficies-e-curvas-de-nivel|aula 01]] vimos funções $f: \mathbb{R}^2 \to \mathbb{R}$ como superfícies $z = f(x, y)$. Agora queremos medir o **volume** entre o gráfico de $f$ e uma região $D \subset \mathbb{R}^2$ do plano $xy$.

A ideia é a mesma da integral em uma variável (área sob a curva), só que um nível acima:

| Uma variável | Duas variáveis |
|---|---|
| Intervalo $[a, b]$ | Região $D \subset \mathbb{R}^2$ |
| Soma de Riemann sobre subintervalos $\Delta x_i$ | Soma sobre sub-retângulos $\Delta A_{ij}$ |
| Área sob a curva $\int_a^b f\,dx$ | Volume sob a superfície $\iint_D f\,dA$ |

> **Pergunta geral:** dada $f: D \to \mathbb{R}$, como definir rigorosamente $\iint_D f\,dA$ e, principalmente, como **calcular** esse número na prática?

A definição (somas de Riemann) responde "o que é"; o [[#^teorema-fubini|Teorema de Fubini]] responde "como calcular".

---

#### a integral dupla sobre um retângulo #calculo/definição/integral-dupla
^definicao-integral-dupla

Começamos pelo caso mais simples: $D = R = [a, b] \times [c, d]$ um **retângulo**.

**Partição.** Dividimos $[a, b]$ em $n$ subintervalos e $[c, d]$ em $m$ subintervalos, formando uma grade de $n \cdot m$ sub-retângulos:

$$R_{ij} = [x_{i-1}, x_i] \times [y_{j-1}, y_j], \qquad \text{de área } \Delta A_{ij} = \Delta x_i \, \Delta y_j$$

**Soma de Riemann.** Em cada $R_{ij}$ escolhemos um ponto amostral $(x_{ij}^*, y_{ij}^*)$ e somamos os volumes das "colunas" de base $R_{ij}$ e altura $f(x_{ij}^*, y_{ij}^*)$:

$$S = \sum_{i=1}^{n} \sum_{j=1}^{m} f(x_{ij}^*, y_{ij}^*)\, \Delta A_{ij}$$

**Definição.** Se as somas $S$ convergem para um mesmo número quando a malha $\|P\| = \max(\Delta x_i, \Delta y_j) \to 0$ — independentemente da escolha dos pontos amostrais — dizemos que $f$ é **integrável** em $R$ e escrevemos:

$$\iint_R f(x, y)\, dA = \lim_{\|P\| \to 0} \sum_{i, j} f(x_{ij}^*, y_{ij}^*)\, \Delta A_{ij}$$

> A notação $dA$ (elemento de área) também aparece como $dx\,dy$. O símbolo duplo $\iint$ enfatiza que integramos sobre uma região **bidimensional**.

---

#### quais funções são integráveis #calculo/teorema/integrabilidade-continuas
^integrabilidade-continuas

Assim como em uma variável, não precisamos verificar a convergência das somas caso a caso:

> **Teorema.** Se $f$ é **contínua** num retângulo $R$ (ou contínua exceto sobre um conjunto de "área zero", como um número finito de curvas suaves), então $f$ é integrável em $R$.

Isso cobre praticamente todas as funções que encontramos na prática. A demonstração usa a **continuidade uniforme** de $f$ no compacto $R$ — o mesmo mecanismo que garante integrabilidade de funções contínuas em $[a, b]$ no caso unidimensional.

> **Intuição:** ao refinar a malha, a oscilação de $f$ dentro de cada sub-retângulo fica arbitrariamente pequena, então as somas com diferentes pontos amostrais ficam todas próximas — e portanto convergem ao mesmo limite.

---

#### propriedades da integral dupla #calculo/proposição/propriedades-integral-dupla
^propriedades-integral-dupla

Valem as mesmas propriedades estruturais da integral em uma variável (todas seguem direto da definição por somas):

- **Linearidade:** $\displaystyle\iint_R (\alpha f + \beta g)\,dA = \alpha \iint_R f\,dA + \beta \iint_R g\,dA$
- **Monotonicidade:** se $f \leq g$ em $R$, então $\displaystyle\iint_R f\,dA \leq \iint_R g\,dA$
- **Aditividade no domínio:** se $D = D_1 \cup D_2$ com $D_1, D_2$ sobrepondo-se apenas na fronteira (área zero), então $\displaystyle\iint_D f\,dA = \iint_{D_1} f\,dA + \iint_{D_2} f\,dA$
- **Área da região:** $\displaystyle\iint_D 1\,dA = \text{área}(D)$ — integrar a função constante $1$ dá a área de $D$

---

#### o teorema de Fubini #calculo/teorema/fubini
^teorema-fubini

O problema da definição é que o limite de somas duplas é impraticável de calcular. **Fubini** resolve isso reduzindo a integral dupla a duas integrais simples (**iteradas**), uma de cada vez:

> **Teorema de Fubini (em retângulo).** Se $f$ é contínua em $R = [a, b] \times [c, d]$, então:
>
> $$\iint_R f(x, y)\, dA = \int_a^b \left( \int_c^d f(x, y)\, dy \right) dx = \int_c^d \left( \int_a^b f(x, y)\, dx \right) dx$$

Ou seja: integramos primeiro em uma variável (tratando a outra como constante) e depois na outra — **e a ordem não importa**.

> **Intuição geométrica (princípio de Cavalieri):** fixar $x = x_0$ e calcular $\int_c^d f(x_0, y)\,dy$ dá a **área da fatia** do sólido no plano $x = x_0$. "Empilhar" essas áreas ao longo de $x \in [a, b]$ reconstrói o volume total. Fatiar na outra direção dá o mesmo volume.

---

#### exemplo 1: Fubini em retângulo #calculo/exemplo/fubini-retangulo
^exemplo-fubini-retangulo

Calcular $\displaystyle\iint_R x y^2 \, dA$ em $R = [0, 2] \times [0, 1]$.

**Integrando primeiro em $y$** (mantendo $x$ constante):

$$\int_0^1 x y^2\, dy = x \left[\frac{y^3}{3}\right]_0^1 = \frac{x}{3}$$

**Agora em $x$:**

$$\int_0^2 \frac{x}{3}\, dx = \frac{1}{3}\left[\frac{x^2}{2}\right]_0^2 = \frac{1}{3} \cdot 2 = \frac{2}{3}$$

**Conferindo pela ordem trocada** (primeiro $x$, depois $y$):

$$\int_0^1 \left(\int_0^2 x y^2\, dx\right) dy = \int_0^1 y^2 \left[\frac{x^2}{2}\right]_0^2 dy = \int_0^1 2y^2\, dy = \frac{2}{3} \checkmark$$

> **Caso especial útil:** quando $f(x,y) = g(x)\,h(y)$ **e** o domínio é um retângulo, a integral dupla **fatora** em produto de integrais simples:
> $$\iint_R g(x)h(y)\, dA = \left(\int_a^b g(x)\,dx\right)\left(\int_c^d h(y)\,dy\right)$$
> No exemplo: $\left(\int_0^2 x\,dx\right)\left(\int_0^1 y^2\,dy\right) = 2 \cdot \tfrac{1}{3} = \tfrac{2}{3}$.

---

#### regiões mais gerais: tipo I e tipo II #calculo/definição/regioes-tipo-I-II
^regioes-tipo-I-II

Na prática $D$ raramente é um retângulo. Duas famílias de regiões cobrem a maioria dos casos e permitem aplicar Fubini com **limites de integração variáveis**.

**Região do tipo I** — verticalmente simples (delimitada por duas funções de $x$):

$$D = \{(x, y) : a \leq x \leq b,\ \ g_1(x) \leq y \leq g_2(x)\}$$

$$\iint_D f\, dA = \int_a^b \left( \int_{g_1(x)}^{g_2(x)} f(x, y)\, dy \right) dx$$

**Região do tipo II** — horizontalmente simples (delimitada por duas funções de $y$):

$$D = \{(x, y) : c \leq y \leq d,\ \ h_1(y) \leq x \leq h_2(y)\}$$

$$\iint_D f\, dA = \int_c^d \left( \int_{h_1(y)}^{h_2(y)} f(x, y)\, dx \right) dy$$

> **Cuidado com a ordem dos limites:** os limites **internos** podem depender da variável externa (são funções), mas os limites **externos** são sempre constantes. O resultado de uma integral dupla é um número — nunca pode sobrar variável.

> **Dica prática:** desenhe a região. Se "varrê-la" com retas verticais for mais simples, use tipo I; se retas horizontais derem limites mais limpos, use tipo II. Muitas regiões são dos dois tipos, e trocar a ordem pode transformar uma integral difícil numa fácil.

---

#### exemplo 2: Fubini em região do tipo I #calculo/exemplo/fubini-triangulo
^exemplo-fubini-triangulo

Calcular $\displaystyle\iint_D (x + 2y)\, dA$ no triângulo $D$ de vértices $(0,0)$, $(1, 0)$ e $(1, 1)$.

**Descrevendo como tipo I:** para $x \in [0, 1]$, $y$ varia de $0$ até a reta $y = x$:

$$D = \{(x, y) : 0 \leq x \leq 1,\ \ 0 \leq y \leq x\}$$

**Integral interna (em $y$):**

$$\int_0^x (x + 2y)\, dy = \left[xy + y^2\right]_0^x = x \cdot x + x^2 = 2x^2$$

**Integral externa (em $x$):**

$$\int_0^1 2x^2\, dx = \frac{2}{3}$$

> Como exercício, vale refazer descrevendo $D$ como tipo II ($y \leq x \leq 1$, $0 \leq y \leq 1$) — o resultado é o mesmo $\frac{2}{3}$, confirmando a consistência de Fubini.

---

#### introdução: o teorema de mudança de variáveis #calculo/teorema/mudanca-de-variaveis
^teorema-mudanca-variaveis

Em uma variável, a substituição $u = \varphi(x)$ traz o fator $dx = \frac{dx}{du}\,du$. Em duas variáveis, uma **mudança de coordenadas** $T(u, v) = (x, y)$ traz um fator análogo, mas que mede como $T$ **distorce áreas** — o módulo do determinante jacobiano.

> **Teorema de mudança de variáveis (enunciado).** Seja $T: U \subset \mathbb{R}^2 \to \mathbb{R}^2$, $T(u, v) = (x(u,v),\, y(u,v))$, de [[aula-09-diferenciabilidade#^definicao-classe-c1|classe $C^1$]], injetora num aberto que contém a região $D^*$, com $\det JT \neq 0$ (i.e., um [[aula-10-teorema-da-funcao-inversa#^definicao-difeomorfismo|difeomorfismo]] sobre sua imagem). Se $D = T(D^*)$, então:
>
> $$\iint_D f(x, y)\, dx\, dy = \iint_{D^*} f\big(T(u, v)\big)\, \left| \det JT(u, v) \right|\, du\, dv$$

O fator $\left|\det JT\right|$ é o **jacobiano** da transformação. Ele aparece porque, localmente, $T$ leva um pequeno retângulo de área $du\,dv$ num paralelogramo de área $\left|\det JT\right|\,du\,dv$ — exatamente a interpretação do determinante jacobiano como [[apendice-notacoes#^notacao-diferenciabilidade|fator de escala de volume]] que vimos na [[aula-10-teorema-da-funcao-inversa#^enunciado-tfi|aula 10]].

> **Conexão com o TFI:** a hipótese $\det JT \neq 0$ é a mesma do [[aula-10-teorema-da-funcao-inversa#^enunciado-tfi|Teorema da Função Inversa]] — ela garante que $T$ é localmente inversível, ou seja, que a mudança de coordenadas não "colapsa" áreas. É o que permite que $T$ seja um difeomorfismo entre $D^*$ e $D$.

---

#### o caso central: coordenadas polares #calculo/exemplo/mudanca-polares
^mudanca-polares

A mudança mais usada é para [[aula-02-sistema-de-coordenadas#^coordenadas-polares|coordenadas polares]], $T(\rho, \theta) = (x, y)$ com:

$$x = \rho \cos\theta, \qquad y = \rho \sin\theta$$

**Jacobiano:**

$$JT = \begin{pmatrix} \dfrac{\partial x}{\partial \rho} & \dfrac{\partial x}{\partial \theta} \\[6pt] \dfrac{\partial y}{\partial \rho} & \dfrac{\partial y}{\partial \theta} \end{pmatrix} = \begin{pmatrix} \cos\theta & -\rho\sin\theta \\ \sin\theta & \rho\cos\theta \end{pmatrix}$$

$$\det JT = \rho\cos^2\theta + \rho\sin^2\theta = \rho$$

Portanto $\left|\det JT\right| = \rho$, e a fórmula vira:

$$\iint_D f(x, y)\, dx\, dy = \iint_{D^*} f(\rho\cos\theta,\, \rho\sin\theta)\, \rho\, d\rho\, d\theta$$

> **O famoso "$dx\,dy = \rho\,d\rho\,d\theta$":** o fator $\rho$ não é decorativo — é o jacobiano. Geometricamente, um "retângulo polar" de lados $d\rho$ e $\rho\,d\theta$ (arco) tem área $\rho\,d\rho\,d\theta$, que cresce com a distância à origem. Esquecer o $\rho$ é o erro mais comum em integrais polares.

##### exemplo: integral sobre o disco

Calcular $\displaystyle\iint_D (x^2 + y^2)\, dA$ no disco $D = \{x^2 + y^2 \leq 1\}$.

Em polares, $D^* = \{0 \leq \rho \leq 1,\ 0 \leq \theta \leq 2\pi\}$ (um retângulo!) e $x^2 + y^2 = \rho^2$:

$$\iint_{D^*} \rho^2 \cdot \rho\, d\rho\, d\theta = \int_0^{2\pi}\!\!\int_0^1 \rho^3\, d\rho\, d\theta = \int_0^{2\pi} \frac{1}{4}\, d\theta = \frac{\pi}{2}$$

> Em cartesianas, essa integral exigiria limites $-\sqrt{1-x^2} \leq y \leq \sqrt{1-x^2}$ e raízes desagradáveis. A mudança para polares transforma o domínio circular num retângulo e simplifica drasticamente o integrando — esse é o ganho do teorema.

---

#### contexto histórico #calculo/contexto/fubini-historia
^contexto-historico-fubini

O teorema das integrais iteradas leva o nome de **Guido Fubini** (matemático italiano), que provou a versão geral em **1907** no contexto da teoria da medida de **Lebesgue** — bem mais ampla do que o caso de funções contínuas que usamos aqui. Versões para funções contínuas já eram conhecidas e usadas por **Cauchy** e outros ao longo do século XIX, mas Fubini deu as condições precisas (integrabilidade no sentido de Lebesgue) sob as quais a troca da ordem de integração é legítima.

A fórmula de mudança de variáveis tem raízes no trabalho de **Euler** (substituições em integrais duplas, 1769) e foi sistematizada por **Carl Gustav Jacob Jacobi**, de quem vem o nome **jacobiano** — o determinante que mede a distorção local de área/volume.

> **Cuidado (por que as hipóteses importam):** existem funções para as quais as duas integrais iteradas dão **resultados diferentes** — a troca da ordem só é garantida sob as hipóteses de Fubini (continuidade, ou integrabilidade absoluta no caso geral). Para funções contínuas em regiões bem-comportadas, como as deste curso, não há com o que se preocupar.

---

> **Próximos passos:** estender a integral dupla para **integrais triplas** ($\iiint$) e aplicar mudança de variáveis em coordenadas **cilíndricas** e **esféricas** (tópicos 5–7 do [[apendice-disciplina#^programa|programa]]).
