#### prova da regra da cadeia #calculo/proposição/regra-da-cadeia-prova
^prova-regra-da-cadeia

Enunciamos a [[aula-05-diferencial-e-regra-da-cadeia#^regra-da-cadeia|regra da cadeia]] na aula anterior. Agora a prova.

> **Regra da cadeia.** Sejam $f: U \subset \mathbb{R}^m \to \mathbb{R}^n$ diferenciável em $x$ e $g: V \subset \mathbb{R}^n \to \mathbb{R}^p$ diferenciável em $f(x)$. Então $g \circ f$ é diferenciável em $x$ e:
>
> $$d(g \circ f)(x) = dg(f(x)) \circ df(x)$$

**Prova.** Como $f$ é [[aula-04-funcoes-diferenciaveis#^definicao-diferenciavel|diferenciável]] em $x$:

$$f(x + \Delta x) = f(x) + df(x)(\Delta x) + r_1(\Delta x), \quad \frac{\|r_1(\Delta x)\|}{\|\Delta x\|} \to 0$$

Definindo $\Delta y = f(x + \Delta x) - f(x) = df(x)(\Delta x) + r_1(\Delta x)$, como $g$ é diferenciável em $y = f(x)$:

$$g(y + \Delta y) = g(y) + dg(y)(\Delta y) + r_2(\Delta y), \quad \frac{\|r_2(\Delta y)\|}{\|\Delta y\|} \to 0$$

Substituindo:

$$g(f(x + \Delta x)) = g(f(x)) + dg(f(x))\big(df(x)(\Delta x) + r_1(\Delta x)\big) + r_2(\Delta y)$$

$$= g(f(x)) + \underbrace{dg(f(x)) \circ df(x)(\Delta x)}_{\text{parte linear}} + \underbrace{dg(f(x))(r_1(\Delta x)) + r_2(\Delta y)}_{\text{resto}}$$

Falta verificar que o resto é desprezível frente a $\|\Delta x\|$:
- $\frac{\|dg(f(x))(r_1(\Delta x))\|}{\|\Delta x\|} \to 0$ porque $dg(f(x))$ é linear (limitada) e $\frac{\|r_1\|}{\|\Delta x\|} \to 0$
- $\frac{\|r_2(\Delta y)\|}{\|\Delta x\|} \to 0$ porque $\|\Delta y\|$ é da ordem de $\|\Delta x\|$ (já que $df(x)$ é linear) e $\frac{\|r_2\|}{\|\Delta y\|} \to 0$

Portanto $g \circ f$ é diferenciável em $x$ com diferencial $dg(f(x)) \circ df(x)$. $\blacksquare$

Na [[aula-05-diferencial-e-regra-da-cadeia#^regra-cadeia-caso-geral|linguagem de matrizes]]:

$$J(g \circ f)(x) = Jg(f(x)) \cdot Jf(x)$$

---

#### consequência: derivada ao longo de uma curva #calculo/proposição/derivada-ao-longo-de-curva
^derivada-ao-longo-de-curva

Seja $\gamma: I \subset \mathbb{R} \to \mathbb{R}^m$ uma [[aula-01-funções#^curvas-parametrizadas|curva parametrizada]] diferenciável e $f: U \subset \mathbb{R}^m \to \mathbb{R}^n$ diferenciável. Pela regra da cadeia:

$$(f \circ \gamma)'(t) = df(\gamma(t))(\gamma'(t)) = Jf(\gamma(t)) \cdot \gamma'(t)$$

Aqui $Jf(\gamma(t))$ é $n \times m$ e $\gamma'(t)$ é $m \times 1$, resultando em um vetor $n \times 1$.

##### Exemplo: coordenadas polares para cartesianas #calculo/exemplo/jacobiana-polar
^exemplo-jacobiana-polar

Seja $f: \mathbb{R}^+ \times \mathbb{R} \to \mathbb{R}^2$ a mudança de [[aula-02-sistema-de-coordenadas#^coordenadas-polares|coordenadas polares]] para cartesianas:

$$f(\rho, \theta) = (\rho \cos\theta, \; \rho \sin\theta)$$

A jacobiana é:

$$Jf(\rho, \theta) = \begin{pmatrix} \dfrac{\partial f_1}{\partial \rho} & \dfrac{\partial f_1}{\partial \theta} \\[10pt] \dfrac{\partial f_2}{\partial \rho} & \dfrac{\partial f_2}{\partial \theta} \end{pmatrix} = \begin{pmatrix} \cos\theta & -\rho\sin\theta \\ \sin\theta & \rho\cos\theta \end{pmatrix}$$

O determinante $\det(Jf) = \rho\cos^2\theta + \rho\sin^2\theta = \rho$ é o fator de escala que aparece na mudança de variável em integrais: $dx\,dy = \rho\,d\rho\,d\theta$.

Se $\gamma(t) = (\rho(t), \theta(t))$ é uma curva no plano $(\rho, \theta)$, a curva correspondente em coordenadas cartesianas é $f \circ \gamma$ e sua velocidade é:

$$(f \circ \gamma)'(t) = Jf(\gamma(t)) \cdot \gamma'(t) = \begin{pmatrix} \cos\theta & -\rho\sin\theta \\ \sin\theta & \rho\cos\theta \end{pmatrix} \begin{pmatrix} \rho'(t) \\ \theta'(t) \end{pmatrix}$$

---

#### derivada curvilínea vs. retilínea
^derivada-curvilinea-vs-retilinea

> **Observação.** A [[aula-05-diferencial-e-regra-da-cadeia#^derivada-direcional-formal|derivada direcional]] $\frac{\partial f}{\partial v}(x)$ é definida como um limite ao longo de uma **reta** ($x + tv$). Mas pela regra da cadeia, se $\gamma$ é **qualquer curva** diferenciável com $\gamma(0) = x$ e $\gamma'(0) = v$, então:
>
> $$(f \circ \gamma)'(0) = df(x)(\gamma'(0)) = df(x)(v) = \frac{\partial f}{\partial v}(x)$$

Ou seja, não importa **qual curva** usamos para passar pelo ponto $x$ com velocidade $v$ — a taxa de variação de $f$ é sempre a mesma. A derivada retilínea (ao longo de $x + tv$) e a derivada curvilínea (ao longo de $\gamma(t)$) coincidem, desde que $\gamma'(0) = v$.

Isso é uma consequência direta da diferenciabilidade: a [[aula-05-diferencial-e-regra-da-cadeia#^definicao-diferencial|diferencial]] $df(x)$ só depende da **direção instantânea** $v$, não do formato da curva.

---

#### caso particular: $f: \mathbb{R}^m \to \mathbb{R}$ e o gradiente
^caso-gradiente-produto-escalar

Quando $f$ chega em $\mathbb{R}$, a [[aula-04-funcoes-diferenciaveis#^exemplo-jacobiana|jacobiana]] é uma **matriz linha** ($1 \times m$), que corresponde ao [[aula-05-diferencial-e-regra-da-cadeia#^gradiente-como-diferencial|gradiente]] $\nabla f(x)$.

A fórmula da [[aula-06-regra-da-cadeia-e-funcao-diferenciavel#^derivada-ao-longo-de-curva|derivada ao longo de uma curva]] se torna um **produto escalar**:

$$(f \circ \gamma)'(t) = Jf(\gamma(t)) \cdot \gamma'(t) = \nabla f(\gamma(t)) \cdot \gamma'(t)$$

> Isso conecta três ideias: a regra da cadeia (álgebra), a derivada direcional (cálculo) e o produto escalar (geometria). A taxa de variação de $f$ ao longo de $\gamma$ é a projeção do gradiente na direção da velocidade.

---

#### função diferenciável #calculo/proposição/fatos-basicos-diferenciabilidade
^fatos-basicos-diferenciabilidade

Como saber se uma função é [[aula-04-funcoes-diferenciaveis#^definicao-diferenciavel|diferenciável]]? Na prática, usamos uma lista de fatos que permitem **construir** funções diferenciáveis a partir de peças simples.

##### 1. Diferenciabilidade por componentes
^diferenciabilidade-por-componentes

> **Fato.** Seja $f: U \subset \mathbb{R}^m \to \mathbb{R}^n$, $x \in U$, com $f = (f_1, \dots, f_n)$. Então:
>
> $$f \text{ é diferenciável em } x \iff f_i \text{ é diferenciável em } x, \; \forall \, i = 1, \dots, n$$

Basta verificar a diferenciabilidade de cada componente separadamente.

##### 2. Soma de funções diferenciáveis
^soma-diferenciavel

> **Fato.** Se $f$ e $g$ são diferenciáveis em $x$, então $f + g$ é diferenciável em $x$ e:
>
> $$d(f + g)(x) = df(x) + dg(x)$$

A diferencial da soma é a soma das diferenciais.

##### 3. Produto de funções diferenciáveis
^produto-diferenciavel

> **Fato.** Se $f, g: U \subset \mathbb{R}^m \to \mathbb{R}$ são diferenciáveis em $x$, então $fg$ é diferenciável em $x$.

(A fórmula da diferencial do produto será discutida na [[aula-06-regra-da-cadeia-e-funcao-diferenciavel#^proxima-aula-regras-produto|próxima aula]].)

##### 4. Função constante
^constante-diferenciavel

> **Fato.** Se $f$ é constante, então $f$ é diferenciável em qualquer $x$ e:
>
> $$df(x) = 0$$

A melhor aproximação linear de algo que não varia é a transformação nula.

##### 5. Função linear
^linear-diferenciavel

> **Fato.** Se $f$ é linear, então $f$ é diferenciável em qualquer $x$ e:
>
> $$df(x) = f$$

A melhor aproximação linear de algo que já **é** linear é a própria função. Isso faz sentido: se $f$ é linear, $f(x + \Delta x) = f(x) + f(\Delta x)$ exatamente, sem resto.

> Combinando esses fatos: qualquer função construída por somas, produtos e composições de funções lineares e constantes é diferenciável. Isso cobre polinômios, funções racionais (onde definidas), e — junto com o fato de que $\sin$, $\cos$, $e^x$, etc. são diferenciáveis — praticamente todas as funções que encontramos na prática.

---

#### próxima aula: regras de derivação para produtos de vetores
^proxima-aula-regras-produto

O professor indicou que na próxima aula serão discutidas **regras de derivação para produtos**:

- **Produto escalar** de curvas em $\mathbb{R}^n$: se $\gamma(t)$ e $\mu(t)$ são curvas diferenciáveis, como derivar $\gamma(t) \cdot \mu(t)$?

$$\frac{d}{dt}\big[\gamma(t) \cdot \mu(t)\big] = \gamma'(t) \cdot \mu(t) + \gamma(t) \cdot \mu'(t)$$

- **Produto de matrizes**: regra análoga para matrizes que dependem de um parâmetro
