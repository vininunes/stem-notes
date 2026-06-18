### Visualização: efeito de $\Delta x$ em $f$
^visualizacao-delta-x

Considere $f: \mathbb{R}^m \to \mathbb{R}^n$ ([[apendice-notacoes#^notacao-funcoes|notação]]). Ao perturbar $x$ por $\Delta x$, a saída muda de $f(x)$ para $f(x + \Delta x)$.

```tikz
\usepackage{tikz}
\usepackage{amssymb}

\begin{document}
\begin{tikzpicture}[scale=1]

% --- Dominio (R^m) ---
\begin{scope}[shift={(-3.5,0)}]
  \draw[thick] (-1.2,0) ellipse (1.2 and 2.5);
  \node[above] at (-1.2,2.8) {$\mathbb{R}^m$};

  \fill[blue!70!black] (-1.2,0.8) circle (2pt) node[left] {$x$};
  \fill[red!70!black] (-1.2,-0.8) circle (2pt) node[left] {$x + \Delta x$};

  \draw[->, thick, red!70!black] (-1.2,0.65) -- (-1.2,-0.65);
  \node[red!70!black, right] at (-0.9,0) {$\Delta x$};
\end{scope}

% --- Setas f ---
\draw[->, thick] (-1.8,0.6) -- (0.5,0.6) node[midway, above] {$f$};
\draw[->, thick, dashed] (-1.8,-0.6) -- (0.5,-0.6);

% --- Contradominio (R^n) ---
\begin{scope}[shift={(3.5,0)}]
  \draw[thick] (1.2,0) ellipse (1.2 and 2.5);
  \node[above] at (1.2,2.8) {$\mathbb{R}^n$};

  \fill[blue!70!black] (1.2,0.8) circle (2pt) node[right] {$f(x)$};
  \fill[red!70!black] (1.2,-0.8) circle (2pt) node[right] {$f(x + \Delta x)$};

  \draw[->, thick, red!70!black] (1.2,0.65) -- (1.2,-0.65);
  \node[red!70!black, left] at (0.9,0) {$\Delta y$};
\end{scope}

\end{tikzpicture}
\end{document}
```

Onde $\Delta y = f(x + \Delta x) - f(x)$ é a variação na saída provocada pela perturbação $\Delta x$ na entrada.

### Definição de função diferenciável
^definicao-diferenciavel

A pergunta central é: podemos **aproximar** $\Delta y$ por algo simples?

A ideia é decompor $\Delta y$ em duas partes:

$$\underbrace{f(x + \Delta x) - f(x)}_{\Delta y} = \underbrace{T(\Delta x)}_{\text{parte linear}} + \underbrace{r(\Delta x)}_{\text{resto}}$$

```tikz
\usepackage{tikz}
\usepackage{amssymb}

\begin{document}
\begin{tikzpicture}[scale=1]

% --- Contradominio (R^n) ---
\draw[thick] (0,0) ellipse (2.5 and 3);
\node[above] at (0,3.3) {$\mathbb{R}^n$};

% Ponto f(x)
\fill[blue!70!black] (-0.5,1.5) circle (2pt);
\node[left] at (-0.5,1.5) {$f(x)$};

% Ponto f(x + Δx)
\fill[red!70!black] (0.8,-1.5) circle (2pt);
\node[right] at (0.8,-1.5) {$f(x + \Delta x)$};

% Ponto intermediario: f(x) + T(Δx)
\fill[green!50!black] (0.5,-0.5) circle (2pt);
\node[right] at (0.5,-0.5) {$f(x) + T(\Delta x)$};

% Vetor T(Δx): de f(x) ate o ponto intermediario
\draw[->, thick, blue!70!black] (-0.5,1.5) -- (0.42,-0.42);
\node[left, blue!70!black] at (-0.3,0.5) {$T(\Delta x)$};

% Vetor r(Δx): do ponto intermediario ate f(x+Δx)
\draw[->, thick, gray, dashed] (0.5,-0.5) -- (0.75,-1.4);
\node[right, gray] at (1.0,-0.9) {$r(\Delta x)$};

% Vetor Δy total: de f(x) ate f(x+Δx)
\draw[->, thick, red!70!black] (-0.35,1.35) -- (0.7,-1.35);
\node[right, red!70!black] at (0.8,0.2) {$\Delta y$};

\end{tikzpicture}
\end{document}
```

> **Definição.** #calculo/definição/função-diferenciável Seja $f: U \subseteq \mathbb{R}^m \to \mathbb{R}^n$ com $U$ aberto. Dizemos que $f$ é **diferenciável** em $x \in U$ se existe uma **transformação linear** $T: \mathbb{R}^m \to \mathbb{R}^n$ tal que:
>
> $$f(x + \Delta x) = f(x) + T(\Delta x) + r(\Delta x)$$
>
> onde o resto $r(\Delta x)$ satisfaz:
>
> $$\lim_{\Delta x \to 0} \frac{r(\Delta x)}{\|\Delta x\|} = 0$$

Ou seja, o resto $r(\Delta x)$ vai a zero **mais rápido** que $\|\Delta x\|$. Equivalentemente:

$$\lim_{\Delta x \to 0} \frac{\|f(x + \Delta x) - f(x) - T(\Delta x)\|}{\|\Delta x\|} = 0$$

#### O que isso significa?
^significado-diferenciavel

- $\Delta x \in \mathbb{R}^m$ é um **vetor** — a perturbação na entrada
- $T: \mathbb{R}^m \to \mathbb{R}^n$ é uma **transformação linear** que melhor aproxima a variação de $f$
- $T(\Delta x)$ é a **parte principal** da variação — a aproximação linear de $\Delta y$
- $r(\Delta x)$ é o **erro** dessa aproximação, e ele é desprezível perto de $\|\Delta x\|$

Quando $\Delta x$ é pequeno, quase toda a variação $\Delta y$ é capturada por $T(\Delta x)$. O resto $r(\Delta x)$ é "lixo" que desaparece.

### Associação com Cálculo I
^associacao-calculo-i

No Cálculo I, para $f: \mathbb{R} \to \mathbb{R}$, a derivada é definida como:

$$f'(x) = \lim_{\Delta x \to 0} \frac{f(x + \Delta x) - f(x)}{\Delta x}$$

Se esse limite existe, podemos reescrever:

$$f(x + \Delta x) - f(x) = f'(x) \cdot \Delta x + r(\Delta x)$$

com $\dfrac{r(\Delta x)}{\Delta x} \to 0$ quando $\Delta x \to 0$.

| | Cálculo I | Cálculo III |
|---|---|---|
| **Função** | $f: \mathbb{R} \to \mathbb{R}$ | $f: \mathbb{R}^m \to \mathbb{R}^n$ |
| **Perturbação** | $\Delta x \in \mathbb{R}$ (escalar) | $\Delta x \in \mathbb{R}^m$ (vetor) |
| **Aproximação linear** | $f'(x) \cdot \Delta x$ (número $\times$ número) | $T(\Delta x)$ (transf. linear aplicada ao vetor) |
| **Quem aproxima** | $f'(x) \in \mathbb{R}$ (um número) | $T: \mathbb{R}^m \to \mathbb{R}^n$ (uma transf. linear) |
| **Condição do resto** | $\dfrac{r(\Delta x)}{\Delta x} \to 0$ | $\dfrac{r(\Delta x)}{\|\Delta x\|} \to 0$ |

A estrutura é **idêntica**:

$$\underbrace{f(x + \Delta x) - f(x)}_{\Delta y} = \underbrace{\text{(algo linear)} \cdot \Delta x}_{\text{aprox. linear}} + \underbrace{r(\Delta x)}_{\text{resto desprezível}}$$

A diferença é que no Cálculo I "algo linear" é **multiplicar por um número** $f'(x)$, e no Cálculo III é **aplicar uma transformação linear** $T$. Mas multiplicar por $f'(x)$ **é** uma transformação linear de $\mathbb{R}$ em $\mathbb{R}$ — é o caso particular $m = n = 1$.

> A derivada $f'(x)$ do Cálculo I **é** a transformação linear $T$, só que em dimensão 1 toda transformação linear é da forma $T(\Delta x) = a \cdot \Delta x$, onde $a = f'(x)$.

### Por que $T: \mathbb{R}^2 \to \mathbb{R}$ é uma matriz $1 \times 2$? #calculo/proposição/transformação-linear-é-matriz
^transformacao-linear-e-matriz

Toda transformação linear $T: \mathbb{R}^m \to \mathbb{R}^n$ é representada por uma matriz $n \times m$ (linhas = dimensão da **saída**, colunas = dimensão da **entrada**).

Para $T: \mathbb{R}^2 \to \mathbb{R}$:
- entrada $\in \mathbb{R}^2$ → **2 colunas**
- saída $\in \mathbb{R}^1$ → **1 linha**

$$T(\Delta x) = \begin{pmatrix} a & b \end{pmatrix} \begin{pmatrix} \Delta x_1 \\ \Delta x_2 \end{pmatrix} = a \cdot \Delta x_1 + b \cdot \Delta x_2$$

O resultado é um **escalar** (vetor em $\mathbb{R}^1$), como esperado.

**Exemplo concreto:** seja $f(x,y) = x^2 + y^2$ e o ponto $x = (1, 2)$.

A transformação linear que aproxima $f$ nesse ponto é:

$$T(\Delta x) = \begin{pmatrix} 2 & 4 \end{pmatrix} \begin{pmatrix} \Delta x_1 \\ \Delta x_2 \end{pmatrix} = 2 \Delta x_1 + 4 \Delta x_2$$

Conferindo: os valores $2$ e $4$ são as derivadas parciais $\frac{\partial f}{\partial x} = 2x = 2$ e $\frac{\partial f}{\partial y} = 2y = 4$ avaliadas em $(1,2)$. Essa matriz $\begin{pmatrix} 2 & 4 \end{pmatrix}$ é o **[[aula-04-funcoes-diferenciaveis#^exemplo-gradiente|gradiente]]** de $f$ no ponto — e no caso geral, é a **[[aula-04-funcoes-diferenciaveis#^exemplo-jacobiana|matriz jacobiana]]**.

| Função | Matriz de $T$ | Dimensão |
|---|---|---|
| $f: \mathbb{R} \to \mathbb{R}$ | $\begin{pmatrix} f'(x) \end{pmatrix}$ | $1 \times 1$ (um número) |
| $f: \mathbb{R}^2 \to \mathbb{R}$ | $\begin{pmatrix} \frac{\partial f}{\partial x} & \frac{\partial f}{\partial y} \end{pmatrix}$ | $1 \times 2$ (gradiente) |
| $f: \mathbb{R}^2 \to \mathbb{R}^2$ | $\begin{pmatrix} \frac{\partial f_1}{\partial x} & \frac{\partial f_1}{\partial y} \\ \frac{\partial f_2}{\partial x} & \frac{\partial f_2}{\partial y} \end{pmatrix}$ | $2 \times 2$ |
| $f: \mathbb{R}^m \to \mathbb{R}^n$ | Jacobiana | $n \times m$ |

> A dimensão da matriz sempre vem da regra: para a multiplicação $T \cdot \Delta x$ fazer sentido, a matriz $n \times m$ precisa multiplicar um vetor $m \times 1$, resultando em um vetor $n \times 1$.

### Exemplo: matriz jacobiana #calculo/definição/matriz-jacobiana
^exemplo-jacobiana

Seja $f: \mathbb{R}^2 \to \mathbb{R}^2$ definida por:

$$f(x, y) = (x^2 y, \; x + y^3)$$

Ou seja, $f$ tem duas funções componentes:
- $f_1(x,y) = x^2 y$
- $f_2(x,y) = x + y^3$

A matriz jacobiana é a matriz de todas as derivadas parciais:

$$J_f(x,y) = \begin{pmatrix} \dfrac{\partial f_1}{\partial x} & \dfrac{\partial f_1}{\partial y} \\[10pt] \dfrac{\partial f_2}{\partial x} & \dfrac{\partial f_2}{\partial y} \end{pmatrix} = \begin{pmatrix} 2xy & x^2 \\[10pt] 1 & 3y^2 \end{pmatrix}$$

**Avaliando no ponto** $(x,y) = (1, 2)$:

$$J_f(1,2) = \begin{pmatrix} 2 \cdot 1 \cdot 2 & 1^2 \\ 1 & 3 \cdot 2^2 \end{pmatrix} = \begin{pmatrix} 4 & 1 \\ 1 & 12 \end{pmatrix}$$

Essa é a transformação linear $T$ que aproxima $f$ perto de $(1,2)$. Para uma perturbação $\Delta x = (\Delta x_1, \Delta x_2)$:

$$T(\Delta x) = \begin{pmatrix} 4 & 1 \\ 1 & 12 \end{pmatrix} \begin{pmatrix} \Delta x_1 \\ \Delta x_2 \end{pmatrix} = \begin{pmatrix} 4\Delta x_1 + \Delta x_2 \\ \Delta x_1 + 12\Delta x_2 \end{pmatrix}$$

#### Verificação numérica
^verificacao-numerica-jacobiana

Tomemos $\Delta x = (0.01, \; 0.01)$ — uma perturbação pequena.

**Valor exato:**

$$f(1.01, \; 2.01) = (1.01^2 \cdot 2.01, \; 1.01 + 2.01^3) = (2.050401, \; 9.130601)$$

$$\Delta y = f(1.01, \; 2.01) - f(1, 2) = (2.050401 - 2, \; 9.130601 - 9) = (0.050401, \; 0.130601)$$

**Aproximação linear:**

$$T(\Delta x) = \begin{pmatrix} 4 \cdot 0.01 + 1 \cdot 0.01 \\ 1 \cdot 0.01 + 12 \cdot 0.01 \end{pmatrix} = \begin{pmatrix} 0.05 \\ 0.13 \end{pmatrix}$$

| | $\Delta y$ (exato) | $T(\Delta x)$ (aprox.) | $r(\Delta x)$ (resto) |
|---|---|---|---|
| componente 1 | $0.050401$ | $0.05$ | $0.000401$ |
| componente 2 | $0.130601$ | $0.13$ | $0.000601$ |

O resto $r(\Delta x)$ é da ordem de $10^{-4}$, enquanto $\|\Delta x\| \approx 0.014$. De fato $\dfrac{\|r\|}{\|\Delta x\|} \approx 0.05 \to 0$ conforme $\Delta x \to 0$.

### Contexto histórico e aplicações
^contexto-historico

#### De onde veio
^historia-derivada

O conceito de derivada em uma variável vem de **Newton** e **Leibniz** (séc. XVII), motivado por problemas de mecânica — calcular velocidades e tangentes a curvas.

A generalização para várias variáveis veio aos poucos:

- **Euler** (séc. XVIII) introduziu as **derivadas parciais**, tratando cada variável separadamente
- **Carl Gustav Jacob Jacobi** (1830s) organizou todas as derivadas parciais de uma função vetorial em uma **matriz** — a jacobiana. O contexto era substituição de variáveis em integrais múltiplas, onde o determinante da jacobiana dá o fator de escala (como $r$ em [[aula-02-sistema-de-coordenadas#^coordenadas-polares|coordenadas polares]]: $dx\,dy = r\,dr\,d\theta$)
- **Karl Weierstrass** e depois **Maurice Fréchet** (início séc. XX) formalizaram a definição moderna: diferenciável = existe uma **transformação linear** que aproxima a variação, com resto desprezível. Isso permitiu generalizar para dimensão infinita (espaços de funções)

A motivação original era sempre a mesma: **linearizar localmente** um problema não-linear. Perto de um ponto, trocar uma função complicada por algo linear torna o problema tratável.

#### Onde é aplicado hoje
^aplicacoes-modernas

**Redes neurais e deep learning** — o treinamento de uma rede neural é essencialmente calcular a jacobiana (via backpropagation) de uma função $f: \mathbb{R}^m \to \mathbb{R}^n$ com milhões de parâmetros. O gradiente descendente usa $T(\Delta x)$ para saber como ajustar os pesos.

**Robótica** — um braço robótico com $m$ juntas tem posição da mão descrita por $f: \mathbb{R}^m \to \mathbb{R}^3$. A jacobiana diz: "se eu mover a junta $i$ um pouco, quanto a mão se desloca?" — fundamental para controle de movimento.

**Computação gráfica** — mapeamento de texturas, deformação de malhas e mudanças de coordenadas usam a jacobiana para saber como áreas e ângulos se distorcem sob uma transformação.

**Otimização e economia** — encontrar mínimos/máximos de funções de várias variáveis (custos, lucros, utilidade). O gradiente (jacobiana $1 \times m$) aponta a direção de maior crescimento.

**Dinâmica de fluidos e engenharia** — equações de Navier-Stokes, deformações elásticas, transferência de calor — todas envolvem linearizar localmente campos vetoriais, que é exatamente a jacobiana.

> Em resumo: sempre que um sistema depende de **várias entradas** e produz **várias saídas**, e queremos entender como pequenas mudanças nas entradas afetam as saídas, estamos usando a jacobiana.

```chronos
# Timeline: diferenciabilidade e jacobiana
> NOTODAY
> DEFAULTVIEW 1660|1950

@ [1665~1687] #blue Newton e Leibniz
- [1665] Newton | Metodo das fluxoes: derivadas para calcular velocidades e tangentes
- [1684] Leibniz | Publica notacao dy/dx no Nova Methodus
- [1687] Principia | Newton publica leis do movimento usando calculo

@ [1730~1770] #green Euler
- [1734] Euler | Introduz derivadas parciais, tratando cada variavel separadamente
- [1755] Institutiones | Euler sistematiza o calculo em varias variaveis

@ [1830~1850] #orange Jacobi
- [1841] Jacobi | Organiza derivadas parciais na matriz jacobiana para integrais multiplas

@ [1860~1910] #purple Formalizacao moderna
- [1861] Weierstrass | Rigor na definicao de limite e continuidade
- [1906] Frechet | Define diferenciabilidade via transformacao linear + resto desprezivel

@ [1940~2020] #red Aplicacoes modernas
- [1947] Dantzig | Programacao linear e otimizacao com gradientes
- [1969] Bryson e Ho | Backpropagation: jacobianas para treinar redes neurais
- [1986] Rumelhart | Backpropagation popularizado no deep learning
```

### Exemplo: $f: \mathbb{R}^n \to \mathbb{R}$ #calculo/definição/gradiente
^exemplo-gradiente

Seja $f: \mathbb{R}^3 \to \mathbb{R}$ definida por:

$$f(x, y, z) = x^2 + yz + e^z$$

A saída é um **escalar**, então a jacobiana é uma matriz $1 \times 3$ — o **gradiente**:

$$J_f = \begin{pmatrix} \dfrac{\partial f}{\partial x} & \dfrac{\partial f}{\partial y} & \dfrac{\partial f}{\partial z} \end{pmatrix} = \begin{pmatrix} 2x & z & y + e^z \end{pmatrix}$$

**Avaliando no ponto** $(x,y,z) = (1, 2, 0)$:

$$f(1, 2, 0) = 1 + 0 + 1 = 2$$

$$J_f(1,2,0) = \begin{pmatrix} 2 & 0 & 3 \end{pmatrix}$$

A aproximação linear para uma perturbação $\Delta x = (\Delta x_1, \Delta x_2, \Delta x_3)$:

$$T(\Delta x) = \begin{pmatrix} 2 & 0 & 3 \end{pmatrix} \begin{pmatrix} \Delta x_1 \\ \Delta x_2 \\ \Delta x_3 \end{pmatrix} = 2\Delta x_1 + 0 \cdot \Delta x_2 + 3\Delta x_3$$

Note que $\dfrac{\partial f}{\partial y}(1,2,0) = 0$. Isso significa que, perto de $(1,2,0)$, pequenas variações em $y$ **quase não afetam** $f$. A função é mais sensível a $z$ (peso $3$) e a $x$ (peso $2$).

#### Verificação numérica
^verificacao-numerica-gradiente

Tomemos $\Delta x = (0.01, \; 0.01, \; 0.01)$.

**Valor exato:**

$$f(1.01, \; 2.01, \; 0.01) = 1.01^2 + 2.01 \cdot 0.01 + e^{0.01} = 1.0201 + 0.0201 + 1.01005 = 2.05025$$

$$\Delta y = 2.05025 - 2 = 0.05025$$

**Aproximação linear:**

$$T(\Delta x) = 2 \cdot 0.01 + 0 \cdot 0.01 + 3 \cdot 0.01 = 0.05$$

| $\Delta y$ (exato) | $T(\Delta x)$ (aprox.) | $r(\Delta x)$ (resto) |
|---|---|---|
| $0.05025$ | $0.05$ | $0.00025$ |

O resto é da ordem de $10^{-4}$, desprezível frente a $\|\Delta x\| \approx 0.017$.
