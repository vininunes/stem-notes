#### recordação: derivada direcional e derivadas parciais
^recordacao-derivada-direcional

Seja $f: U \subseteq \mathbb{R}^m \to \mathbb{R}^n$ ([[apendice-notacoes#^notacao-funcoes|notação]]) e $x \in U$. A [[aula-05-diferencial-e-regra-da-cadeia#^derivada-direcional-formal|derivada direcional]] de $f$ no ponto $x$ na direção de $v \in \mathbb{R}^m$ é:

$$\frac{\partial f}{\partial v}(x) = \lim_{t \to 0} \frac{f(x + tv) - f(x)}{t} = \frac{d}{dt}\bigg|_{t=0} f(x + tv)$$

As [[aula-05-diferencial-e-regra-da-cadeia#^derivada-parcial-formal|derivadas parciais]] $\frac{\partial f}{\partial x_i}(x)$, $i = 1, \dots, m$, são o **caso particular** de derivada direcional quando $v = e_i$ é um vetor da base canônica:

$$\frac{\partial f}{\partial x_i}(x) = \frac{\partial f}{\partial e_i}(x)$$

Se $f$ é [[aula-04-funcoes-diferenciaveis#^definicao-diferenciavel|diferenciável]] no ponto $x$ com transformação linear $T: \mathbb{R}^m \to \mathbb{R}^n$, então $\frac{\partial f}{\partial v}(x)$ existe e vale $T(v)$.

---

#### bola aberta e conjunto aberto #calculo/definição/bola-aberta #calculo/definição/conjunto-aberto
^bola-aberta-e-conjunto-aberto

> **Definição.** Dados $x \in \mathbb{R}^n$ e $R > 0$, a **bola aberta** $B(x, R)$ de centro $x$ e raio $R$ é definida por:
>
> $$B(x, R) = \{ y \in \mathbb{R}^n : \|y - x\| < R \}$$

> **Definição.** Um subconjunto $U$ de $\mathbb{R}^n$ é dito **aberto** se para todo $x \in U$ existe $R > 0$ tal que $B(x, R) \subset U$.

Intuitivamente, $U$ é aberto quando, a partir de qualquer ponto de $U$, podemos nos mover um pouco em qualquer direção sem sair de $U$. Não há "borda" incluída no conjunto.

> A importância de $U$ ser aberto: para que $\frac{\partial f}{\partial v}(x)$ faça sentido, precisamos que $x + tv \in U$ para $t$ suficientemente pequeno. Isso é garantido quando $U$ é aberto.

---

#### unicidade da transformação linear #calculo/proposição/unicidade-diferencial
^unicidade-diferencial

> **Teorema.** Seja $f: U \to \mathbb{R}^n$ uma função em que $U$ é um subconjunto aberto de $\mathbb{R}^m$. Dado $x \in U$, se $f$ é [[aula-04-funcoes-diferenciaveis#^definicao-diferenciavel|diferenciável]] no ponto $x$, então a transformação linear $T: \mathbb{R}^m \to \mathbb{R}^n$ tal que
>
> $$\lim_{\Delta x \to 0} \frac{\|f(x + \Delta x) - f(x) - T(\Delta x)\|}{\|\Delta x\|} = 0 \quad (*)$$
>
> é **única**.

**Prova.** Suponha que $T_1$ e $T_2$ satisfazem a condição $(*)$. Então, para qualquer $v \in \mathbb{R}^m$:

$$T_1(v) = \frac{\partial f}{\partial v}(x) = T_2(v)$$

Como $T_1(v) = T_2(v)$ para todo $v \in \mathbb{R}^m$, concluímos que $T_1 = T_2$. $\blacksquare$

> A chave da prova: se $f$ é diferenciável com transformação $T$, então $T(v)$ coincide com a derivada direcional $\frac{\partial f}{\partial v}(x)$. Como a derivada direcional é definida por um limite (que é único quando existe), $T$ fica completamente determinada.

---

#### definição de diferencial #calculo/definição/diferencial
^definicao-diferencial

> **Definição.** Se $f: U \subset \mathbb{R}^m \to \mathbb{R}^n$ é [[aula-04-funcoes-diferenciaveis#^definicao-diferenciavel|diferenciável]] num ponto $x \in U$ (com $U$ aberto), a transformação linear $T$ (que é [[aula-05-diferencial-e-regra-da-cadeia#^unicidade-diferencial|única]]) é chamada a **diferencial** de $f$ em $x$, denotada por $df(x)$.

Temos:

$$df(x)(v) = \frac{\partial f}{\partial v}(x), \quad \forall \, v \in \mathbb{R}^m$$

Ou seja, a diferencial aplicada a um vetor $v$ dá a derivada direcional na direção $v$.

**Notação.** A [[aula-04-funcoes-diferenciaveis#^exemplo-jacobiana|matriz jacobiana]] de $f$ no ponto $x$ será denotada por $Jf(x)$:

$$Jf(x) = \begin{pmatrix} \dfrac{\partial f_1}{\partial x_1}(x) & \cdots & \dfrac{\partial f_1}{\partial x_m}(x) \\[10pt] \vdots & \ddots & \vdots \\[10pt] \dfrac{\partial f_n}{\partial x_1}(x) & \cdots & \dfrac{\partial f_n}{\partial x_m}(x) \end{pmatrix}$$

A diferencial $df(x)$ é a transformação linear; $Jf(x)$ é sua **representação matricial**. Para qualquer $v \in \mathbb{R}^m$:

$$df(x)(v) = Jf(x) \cdot v$$

---

#### casos particulares da diferencial
^casos-particulares-diferencial

##### (1) $f: U \subset \mathbb{R}^m \to \mathbb{R}$ — função escalar #calculo/definição/gradiente-como-diferencial
^gradiente-como-diferencial

Quando a saída é um escalar, a jacobiana $Jf(x)$ é uma **matriz linha** ($1 \times m$), que é exatamente o [[aula-04-funcoes-diferenciaveis#^exemplo-gradiente|gradiente]]:

$$\nabla f(x) = \left( \frac{\partial f}{\partial x_1}(x), \; \dots, \; \frac{\partial f}{\partial x_m}(x) \right)$$

Logo, se $f$ é diferenciável no ponto $x$:

$$\frac{\partial f}{\partial v}(x) = df(x)(v) = Jf(x) \cdot v = \nabla f(x) \cdot v$$

##### (2) $f: U \subset \mathbb{R} \to \mathbb{R}^n$ — curva parametrizada #calculo/definição/derivada-curva
^derivada-curva

Quando $m = 1$, pensamos em $f$ como uma [[aula-01-funções#^curvas-parametrizadas|curva parametrizada]].

Se $f$ é diferenciável em $t \in U$, então:

$$f'(t) = \lim_{\Delta t \to 0} \frac{f(t + \Delta t) - f(t)}{\Delta t} = df(t)(1) = Jf(t) \cdot 1$$

A derivada da curva é a diferencial aplicada ao escalar $1$.

---

#### derivada direcional — definição formal #calculo/definição/derivada-direcional
^derivada-direcional-formal

> **Definição.** Seja $f: U \subseteq \mathbb{R}^m \to \mathbb{R}^n$ e $x \in U$. A **derivada direcional** de $f$ em $x$ na direção $v \in \mathbb{R}^m$ é:
>
> $$\frac{\partial f}{\partial v}(x) = \lim_{t \to 0} \frac{f(x + tv) - f(x)}{t}$$
>
> quando esse limite existe.

#### derivada parcial — definição formal #calculo/definição/derivada-parcial
^derivada-parcial-formal

> **Definição.** A **derivada parcial** de $f$ em relação a $x_i$ no ponto $x$ é a derivada direcional na direção do vetor canônico $e_i$:
>
> $$\frac{\partial f}{\partial x_i}(x) = \frac{\partial f}{\partial e_i}(x) = \lim_{t \to 0} \frac{f(x + te_i) - f(x)}{t}$$

---

#### a regra da cadeia #calculo/proposição/regra-da-cadeia
^regra-da-cadeia

##### Motivação: regra da cadeia em Cálculo I
^regra-cadeia-motivacao

Em Cálculo I, se $f: \mathbb{R} \to \mathbb{R}$ e $g: \mathbb{R} \to \mathbb{R}$ são deriváveis:

$$(g \circ f)'(x) = g'(f(x)) \cdot f'(x)$$

A ideia geométrica: na física, sempre buscamos **relações entre variáveis**.

$$x \xrightarrow{f} y = f(x) \xrightarrow{g} z = g(y)$$

Uma perturbação $\Delta x$ na entrada causa:
- $\Delta y \approx f'(x) \cdot \Delta x$ (para $\Delta x$ pequeno)
- $\Delta z \approx g'(y) \cdot \Delta y$ (para $\Delta y$ pequeno)
- $\Delta z \approx g'(y) \cdot f'(x) \cdot \Delta x \implies (g \circ f)'(x) = g'(f(x)) \cdot f'(x)$

##### Caso geral: composição de funções diferenciáveis
^regra-cadeia-caso-geral

A mesma ideia funciona em dimensão maior, trocando "multiplicar por um número" por "aplicar uma transformação linear":

- $\Delta y \approx T(\Delta x)$, com $T = df(x)$ linear
- $\Delta z \approx S(\Delta y)$, com $S = dg(y) = dg(f(x))$ linear
- $\Delta z \approx S(T(\Delta x)) = (S \circ T)(\Delta x)$

Composição de transformações lineares é **multiplicação de matrizes**.

> **Regra da cadeia.** Sejam $f: U \subset \mathbb{R}^m \to \mathbb{R}^n$ e $g: V \subset \mathbb{R}^n \to \mathbb{R}^p$, com $x \in U$. Se $f$ é diferenciável em $x$ e $g$ é diferenciável em $f(x)$, então $g \circ f$ é diferenciável em $x$ e:
>
> $$d(g \circ f)(x) = dg(f(x)) \circ df(x)$$

Na linguagem de matrizes:

$$J(g \circ f)(x) = Jg(f(x)) \cdot Jf(x)$$

A jacobiana da composição é o **produto das jacobianas**.

> Note as dimensões: $Jg$ é $p \times n$, $Jf$ é $n \times m$, logo $Jg \cdot Jf$ é $p \times m$ — exatamente a dimensão da jacobiana de $g \circ f: \mathbb{R}^m \to \mathbb{R}^p$.

##### Exemplo proposto
^exemplo-regra-cadeia

$f(x, y, z) = (xy + z, \; \sin(xyz))$, com $f: \mathbb{R}^3 \to \mathbb{R}^2$.

A jacobiana é:

$$Jf(x,y,z) = \begin{pmatrix} \dfrac{\partial f_1}{\partial x} & \dfrac{\partial f_1}{\partial y} & \dfrac{\partial f_1}{\partial z} \\[10pt] \dfrac{\partial f_2}{\partial x} & \dfrac{\partial f_2}{\partial y} & \dfrac{\partial f_2}{\partial z} \end{pmatrix} = \begin{pmatrix} y & x & 1 \\[10pt] yz\cos(xyz) & xz\cos(xyz) & xy\cos(xyz) \end{pmatrix}$$

Essa é uma matriz $2 \times 3$: transforma perturbações em $\mathbb{R}^3$ (entrada) em perturbações em $\mathbb{R}^2$ (saída). Cada linha corresponde a uma componente de $f$, e cada coluna à sensibilidade em relação a uma variável.
