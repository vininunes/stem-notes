#### recordação: produto interno
^recordacao-produto-interno

O **produto interno** (ou produto escalar) de dois vetores $u, v \in \mathbb{R}^n$ é:

$$\langle u, v \rangle = u \cdot v = \sum_{i=1}^{n} u_i v_i$$

Tipos de produto que aparecem dependendo das dimensões:

| Operação | Dimensões | Resultado |
|---|---|---|
| $u \cdot v$ (vetores) | $\mathbb{R}^n \times \mathbb{R}^n \to \mathbb{R}$ | escalar |
| $A \cdot v$ (matriz $\times$ vetor) | $M_{m \times n} \times \mathbb{R}^n \to \mathbb{R}^m$ | vetor |
| $A \cdot B$ (matriz $\times$ matriz) | $M_{m \times n} \times M_{n \times p} \to M_{m \times p}$ | matriz |
| $u \times v$ (produto vetorial) | $\mathbb{R}^3 \times \mathbb{R}^3 \to \mathbb{R}^3$ | vetor |

---

#### produto vetorial em $\mathbb{R}^3$
^produto-vetorial

O **produto vetorial** $u \times v$ é definido apenas em $\mathbb{R}^3$ e resulta em um vetor **perpendicular** a $u$ e $v$. Pode ser calculado pelo determinante simbólico:

$$u \times v = \det \begin{pmatrix} e_1 & e_2 & e_3 \\ u_1 & u_2 & u_3 \\ v_1 & v_2 & v_3 \end{pmatrix}$$

$$= e_1(u_2 v_3 - u_3 v_2) - e_2(u_1 v_3 - u_3 v_1) + e_3(u_1 v_2 - u_2 v_1)$$

---

#### derivada do produto de duas funções #calculo/proposição/derivada-produto
^derivada-produto

Sejam $\gamma, \mu: I \subset \mathbb{R} \to \mathbb{R}^n$ diferenciáveis. Queremos provar que:

$$\frac{d}{dt}\big[\gamma(t) \cdot \mu(t)\big] = \gamma'(t) \cdot \mu(t) + \gamma(t) \cdot \mu'(t)$$

##### Prova 1 — por somatório (direta)

Escrevendo $\gamma(t) \cdot \mu(t) = \sum_{i=1}^{n} \gamma_i(t) \cdot \mu_i(t)$, derivamos cada termo pela regra do produto em $\mathbb{R}$:

$$\frac{d}{dt} \sum_{i=1}^{n} \gamma_i \mu_i = \sum_{i=1}^{n} (\gamma_i' \mu_i + \gamma_i \mu_i') = \sum_{i=1}^{n} \gamma_i' \mu_i + \sum_{i=1}^{n} \gamma_i \mu_i' = \gamma' \cdot \mu + \gamma \cdot \mu'$$

##### Prova 2 — pelo limite (via definição de derivada)

$$\frac{d}{dt}\big[\gamma(t) \cdot \mu(t)\big] = \lim_{h \to 0} \frac{\gamma(t+h) \cdot \mu(t+h) - \gamma(t) \cdot \mu(t)}{h}$$

Somando e subtraindo $\gamma(t+h) \cdot \mu(t)$ no numerador:

$$= \lim_{h \to 0} \frac{\gamma(t+h) \cdot \mu(t+h) - \gamma(t+h) \cdot \mu(t) + \gamma(t+h) \cdot \mu(t) - \gamma(t) \cdot \mu(t)}{h}$$

$$= \lim_{h \to 0} \left[ \gamma(t+h) \cdot \frac{\mu(t+h) - \mu(t)}{h} + \frac{\gamma(t+h) - \gamma(t)}{h} \cdot \mu(t) \right]$$

$$= \gamma(t) \cdot \mu'(t) + \gamma'(t) \cdot \mu(t)$$

> **Por que a prova 2 é melhor?** A prova 1 funciona porque expandimos o produto escalar como somatório de produtos de funções reais. Mas a prova 2 usa apenas o fato de que o produto escalar é **bilinear** — linear em cada argumento separadamente. Isso significa que a mesma prova se aplica a **qualquer** produto bilinear (produto de matrizes, produto vetorial, etc.) sem precisar abrir coordenadas. A estrutura do argumento é mais geral.

> Em particular, a mesma demonstração vale para o [[aula-07-derivadas-de-produtos#^produto-vetorial|produto vetorial]] em $\mathbb{R}^3$: se $\gamma, \mu: I \to \mathbb{R}^3$ são diferenciáveis, então:
>
> $$\frac{d}{dt}\big[\gamma(t) \times \mu(t)\big] = \gamma'(t) \times \mu(t) + \gamma(t) \times \mu'(t)$$

---

#### exemplo em física: energia cinética e trabalho #calculo/exemplo/energia-cinetica
^exemplo-energia-cinetica

A energia cinética de uma partícula de massa $m$ e velocidade $\vec{v}(t)$, onde $v = |\vec{v}|$:

$$E_c = \frac{1}{2} m v^2 = \frac{1}{2} m \, (\vec{v} \cdot \vec{v})$$

Derivando e usando a [[aula-07-derivadas-de-produtos#^derivada-produto|regra do produto]]:

$$\frac{dE_c}{dt} = \frac{1}{2} m \left( \frac{d\vec{v}}{dt} \cdot \vec{v} + \vec{v} \cdot \frac{d\vec{v}}{dt} \right) = m \, \vec{a} \cdot \vec{v}$$

onde $\vec{a} = \frac{d\vec{v}}{dt}$ é a aceleração. Pela segunda lei de Newton, $m\vec{a} = \vec{F}$, logo:

$$\boxed{\frac{dE_c}{dt} = \vec{F} \cdot \vec{v}}$$

Integrando entre $t_1$ e $t_2$:

$$E_c(t_2) - E_c(t_1) = \int_{t_1}^{t_2} \frac{dE_c}{dt} \, dt = \int_{t_1}^{t_2} \vec{F} \cdot \vec{v} \, dt = \text{trabalho realizado pela força } \vec{F}$$

##### Caso força constante vs. força variável

Se $\vec{F}$ é **constante** e desloca uma partícula de $P_1$ a $P_2$ por um deslocamento $\vec{d}$:

$$\text{trabalho} = \vec{F} \cdot \vec{d}$$

Se $\vec{F}(t)$ **varia** ao longo de uma curva $\vec{n}(t)$, o deslocamento infinitesimal é $\Delta \vec{n} = \vec{n}(t + \Delta t) - \vec{n}(t)$ e o trabalho infinitesimal é:

$$\Delta W \approx \vec{F}(t) \cdot \Delta \vec{n} \approx \vec{F}(t) \cdot \frac{d\vec{n}}{dt} \, \Delta t$$

Somando (integrando) todos os pedaços:

$$W = \int_{t_1}^{t_2} \vec{F}(t) \cdot \frac{d\vec{n}}{dt} \, dt = \int_{t_1}^{t_2} \vec{F} \cdot \vec{v} \, dt$$

> Isso conecta a fórmula $\frac{dE_c}{dt} = \vec{F} \cdot \vec{v}$ com o conceito de trabalho: a variação da energia cinética entre dois instantes é o trabalho realizado pela força ao longo da trajetória.

##### Forças conservativas e conservação de energia

Se $\vec{F}$ é uma **força conservativa**, ou seja, $\vec{F} = -\nabla V$ onde $V$ é a energia potencial, então:

$$\int_{t_1}^{t_2} \vec{F} \cdot \vec{v} \, dt = -\int_{t_1}^{t_2} \nabla V(\vec{n}(t)) \cdot \frac{d\vec{n}}{dt} \, dt$$

Pela [[aula-06-regra-da-cadeia-e-funcao-diferenciavel#^caso-gradiente-produto-escalar|regra da cadeia]], $\nabla V(\vec{n}(t)) \cdot \frac{d\vec{n}}{dt} = \frac{d}{dt} V(\vec{n}(t))$, logo:

$$= -\int_{t_1}^{t_2} \frac{d}{dt} V(\vec{n}(t)) \, dt = -\big[V(\vec{n}(t_2)) - V(\vec{n}(t_1))\big]$$

Mas esse integral também é igual a $E_c(\vec{n}(t_2)) - E_c(\vec{n}(t_1))$, portanto:

$$E_c(\vec{n}(t_2)) - E_c(\vec{n}(t_1)) = -V(\vec{n}(t_2)) + V(\vec{n}(t_1))$$

$$\boxed{(E_c + V)(\vec{n}(t_2)) - (E_c + V)(\vec{n}(t_1)) = 0}$$

> **Conservação de energia:** a energia total $E_c + V$ é constante ao longo do movimento. Isso é consequência direta da regra da cadeia e da derivada do produto escalar.

---

#### exemplo: derivada do momento angular #calculo/exemplo/momento-angular
^exemplo-momento-angular

Considere uma partícula com posição $\vec{n}(t)$. O **momento angular** é definido por:

$$\vec{L}(t) = \vec{n}(t) \times \vec{p}(t)$$

onde $\vec{p}(t) = m\vec{v}(t)$ é o momento linear e $\vec{v} = \frac{d\vec{n}}{dt}$.

Derivando usando a regra do produto para o [[aula-07-derivadas-de-produtos#^produto-vetorial|produto vetorial]]:

$$\frac{d\vec{L}}{dt} = \frac{d\vec{n}}{dt} \times \vec{p} + \vec{n} \times \frac{d\vec{p}}{dt}$$

$$= \vec{v} \times \vec{p} + \vec{n} \times \vec{F}$$

Mas $\vec{v} \times \vec{p} = \vec{v} \times (m\vec{v}) = m(\vec{v} \times \vec{v}) = 0$ (produto vetorial de um vetor consigo mesmo é nulo), logo:

$$\boxed{\frac{d\vec{L}}{dt} = \vec{n} \times \vec{F}}$$

> Note que se $\vec{F} = 0$ (sem força), então $\frac{d\vec{L}}{dt} = 0$ e o momento angular é **conservado**.

##### Generalização: sistema de $n$ partículas

Num sistema de $n$ partículas com posições $\vec{n}_i$, definimos o momento angular total:

$$\vec{L} = \sum_{i=1}^{n} \vec{L}_i$$

Temos:

$$\frac{d\vec{L}}{dt} = \sum_{i=1}^{n} \frac{d\vec{L}_i}{dt} = \sum_{i=1}^{n} \vec{n}_i \times \vec{F}_i$$

Se considerarmos apenas **forças externas** (as forças internas entre partículas se cancelam aos pares):

$$\sum_{i=1}^{n} \sum_{j=1}^{n} \vec{n}_i \times \vec{F}_{ij} = \vec{0}$$

> Sem forças externas, o momento angular total do sistema é conservado.

---

#### exemplos de regras de derivada do produto #calculo/proposição/regras-derivada-produto
^regras-derivada-produto

**(1) Produto escalar** — $f, g: I \subset \mathbb{R} \to \mathbb{R}^n$:

$$(f \cdot g)' = f' \cdot g + f \cdot g'$$

**(2) Produto vetorial** — $f, g: I \subset \mathbb{R} \to \mathbb{R}^3$:

$$(f \times g)' = f' \times g + f \times g'$$

**(3) Produto matricial** — $f: I \subset \mathbb{R} \to M_{m \times n}(\mathbb{R})$, $g: I \subset \mathbb{R} \to M_{n \times p}(\mathbb{R})$:

$$(f \cdot g)' = f' \cdot g + f \cdot g'$$

> A mesma regra de Leibniz vale para **qualquer** produto bilinear (ver abaixo).

---

#### generalização: produto bilinear #calculo/definição/produto-bilinear
^produto-bilinear

A regra do produto vale para qualquer produto que seja **bilinear**, ou seja, uma operação $\bullet$ que satisfaz:

1. **Distributiva:** $(v_1 + v_2) \bullet w = v_1 \bullet w + v_2 \bullet w$ e $v \bullet (w_1 + w_2) = v \bullet w_1 + v \bullet w_2$
2. **Homogeneidade:** $(\lambda v) \bullet w = v \bullet (\lambda w) = \lambda (v \bullet w)$

---

#### regra do produto para várias variáveis #calculo/proposição/regra-produto-varias-variaveis
^regra-produto-varias-variaveis

Essas regras do produto também podem ser generalizadas para funções de várias variáveis, usando derivadas parciais ou direcionais.

Dado $f, g: U \subset \mathbb{R}^m \to \mathbb{R}^n$ diferenciáveis, com $f \cdot g: U \subset \mathbb{R}^m \to \mathbb{R}$ (produto escalar), vale:

$$\frac{\partial (f \cdot g)}{\partial x_i} = \frac{\partial f}{\partial x_i} \cdot g + f \cdot \frac{\partial g}{\partial x_i}$$

E mais geralmente, para a [[aula-05-diferencial-e-regra-da-cadeia#^derivada-direcional-formal|derivada direcional]]:

$$\frac{\partial (f \cdot g)}{\partial v} = \frac{\partial f}{\partial v} \cdot g + f \cdot \frac{\partial g}{\partial v}$$


