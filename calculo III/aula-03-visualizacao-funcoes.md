## Transformações lineares e imagens de conjuntos #calculo/definição/imagem-de-conjunto
^imagem-de-conjunto

### Exemplo: f(x,y) = (2x, 3y)
^exemplo-imagem-linear

**Domínio (conjunto S):**

S = { (x, y) ∈ ℝ² : x² + y² ≤ 1 }  →  disco unitário (círculo de raio 1)

**Imagem f[S]:**

Aplicando f ao disco:
- x → 2x  (estica por 2 no eixo x)
- y → 3y  (estica por 3 no eixo y)

Se (X, Y) = f(x, y) = (2x, 3y), então x = X/2 e y = Y/3.

Substituindo em x² + y² ≤ 1:

$$\frac{X^2}{4} + \frac{Y^2}{9} \leq 1$$

**f[S] = elipse de centro na origem, semi-eixo 2 (horizontal) e semi-eixo 3 (vertical).**

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1.2]

% --- Disco unitário (domínio S) ---
\begin{scope}[shift={(-3.5,0)}]
  % eixos
  \draw[->] (-1.8,0) -- (1.8,0) node[right] {$x$};
  \draw[->] (0,-1.8) -- (0,1.8) node[above] {$y$};

  % disco preenchido
  \fill[blue!15] (0,0) circle (1);
  \draw[blue!70!black, thick] (0,0) circle (1);

  % marcações
  \node[below right, blue!70!black] at (0.7,-0.7) {$r=1$};
  \node[below] at (0,-2.2) {$S = \{x^2 + y^2 \leq 1\}$};
\end{scope}

% --- Seta de transformação ---
\draw[->, thick, red!70!black] (-1.2,0) -- (0.8,0)
  node[midway, above] {$f(x,y) = (2x, 3y)$};

% --- Elipse (imagem f[S]) ---
\begin{scope}[shift={(3.5,0)}]
  % eixos
  \draw[->] (-2.8,0) -- (2.8,0) node[right] {$X$};
  \draw[->] (0,-3.5) -- (0,3.5) node[above] {$Y$};

  % elipse preenchida
  \fill[red!15] (0,0) ellipse (2 and 3);
  \draw[red!70!black, thick] (0,0) ellipse (2 and 3);

  % marcações dos semi-eixos
  \draw[dashed, red!50!black] (0,0) -- (2,0) node[midway, below] {$2$};
  \draw[dashed, red!50!black] (0,0) -- (0,3) node[midway, left] {$3$};
  \node[below] at (0,-4) {$f[S] = \left\{\frac{X^2}{4} + \frac{Y^2}{9} \leq 1\right\}$};
\end{scope}

\end{tikzpicture}
\end{document}
```

## Imagem Inversa (pré-imagem) #calculo/definição/imagem-inversa
^imagem-inversa

A **imagem** $f[S]$ responde: "dado um conjunto no domínio, onde ele vai parar?"

A **imagem inversa** $f^{-1}[T]$ responde a pergunta contrária: "dado um conjunto $T$ no contradomínio, **quais pontos do domínio** são mapeados para $T$?"

$$f^{-1}[T] = \{ (x, y) \in \text{Dom}(f) : f(x,y) \in T \}$$

> **Atenção:** $f^{-1}[T]$ **não** exige que $f$ seja invertível. É apenas o conjunto de pontos que "caem" em $T$ após aplicar $f$.

### Exemplo: f(x,y) = (2x, 3y), T = elipse
^exemplo-pre-imagem

Agora o caminho é inverso. Dado $T = \left\{\frac{X^2}{4} + \frac{Y^2}{9} \leq 1\right\}$ (a elipse), queremos achar $f^{-1}[T]$.

Se $(2x, 3y) \in T$, então:

$$\frac{(2x)^2}{4} + \frac{(3y)^2}{9} \leq 1 \implies x^2 + y^2 \leq 1$$

Portanto $f^{-1}[T] = \{x^2 + y^2 \leq 1\}$ — o disco unitário. Voltamos ao $S$ original.

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1.2]

% --- Elipse (conjunto T no contradomínio) ---
\begin{scope}[shift={(-4,0)}]
  \draw[->] (-2.8,0) -- (2.8,0) node[right] {$X$};
  \draw[->] (0,-3.5) -- (0,3.5) node[above] {$Y$};

  \fill[red!15] (0,0) ellipse (2 and 3);
  \draw[red!70!black, thick] (0,0) ellipse (2 and 3);

  \draw[dashed, red!50!black] (0,0) -- (2,0) node[midway, below] {$2$};
  \draw[dashed, red!50!black] (0,0) -- (0,3) node[midway, left] {$3$};
  \node[below] at (0,-4) {$T = \left\{\frac{X^2}{4} + \frac{Y^2}{9} \leq 1\right\}$};
\end{scope}

% --- Seta inversa ---
\draw[<-, thick, blue!70!black] (-0.8,0) -- (1.2,0)
  node[midway, above] {$f^{-1}$};

% --- Disco (pré-imagem no domínio) ---
\begin{scope}[shift={(4,0)}]
  \draw[->] (-1.8,0) -- (1.8,0) node[right] {$x$};
  \draw[->] (0,-1.8) -- (0,1.8) node[above] {$y$};

  \fill[blue!15] (0,0) circle (1);
  \draw[blue!70!black, thick] (0,0) circle (1);

  \node[below right, blue!70!black] at (0.7,-0.7) {$r=1$};
  \node[below] at (0,-2.2) {$f^{-1}[T] = \{x^2 + y^2 \leq 1\}$};
\end{scope}

\end{tikzpicture}
\end{document}
```

### Imagem inversa vs. Função inversa #calculo/definição/função-inversa
^imagem-inversa-vs-funcao-inversa

É fundamental não confundir **imagem inversa** $f^{-1}[T]$ com **função inversa** $f^{-1}$.

| | Imagem inversa $f^{-1}[T]$ | Função inversa $f^{-1}$ |
|---|---|---|
| **O que é** | Um **conjunto** de pontos | Uma **função** |
| **Exige bijetora?** | Não | Sim |
| **Sempre existe?** | Sim, para qualquer $f$ | Só se $f$ for bijetora |

#### Por que a função inversa exige bijeção? #calculo/proposição/inversa-exige-bijeção
^inversa-exige-bijecao

A função inversa $f^{-1}: B \to A$ precisa **desfazer** o que $f$ fez, ou seja, $f^{-1}(f(x)) = x$. Para isso, duas coisas precisam valer (ver [[aula-01-funções#^tipos-de-funcoes|tipos de funções]]):

**1. [[aula-01-funções#^tipos-de-funcoes|Injetora]]** (cada saída vem de **uma única** entrada):

Se $f$ não for injetora, existem $a_1 \neq a_2$ com $f(a_1) = f(a_2) = b$. Então $f^{-1}(b)$ deveria retornar quem? $a_1$ ou $a_2$? Não há como escolher — $f^{-1}$ não seria função.

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1]

% --- Não injetora (problema) ---
\begin{scope}[shift={(-3.5,0)}]
  % domínio
  \draw[thick] (-1.2,-0.2) ellipse (0.8 and 2.2);
  \node[above] at (-1.2,2.3) {\small $A$};
  \fill[blue!70!black] (-1.2,1) circle (2pt) node[left] {\small $a_1$};
  \fill[blue!70!black] (-1.2,-1) circle (2pt) node[left] {\small $a_2$};

  % contradomínio
  \draw[thick] (1.2,-0.2) ellipse (0.8 and 2.2);
  \node[above] at (1.2,2.3) {\small $B$};
  \fill[red!70!black] (1.2,0) circle (2pt) node[right] {\small $b$};

  % setas f
  \draw[->, thick] (-0.5,0.8) -- (0.5,0.15);
  \draw[->, thick] (-0.5,-0.8) -- (0.5,-0.15);

  % seta inversa com ?
  \draw[<-, thick, dashed, gray] (-0.5,0) -- (0.5,0) node[midway, above] {\small \textbf{?}};

  \node[below] at (0,-3) {\small N\~ao injetora: $f^{-1}(b) = $ ?};
\end{scope}

% --- Injetora (ok) ---
\begin{scope}[shift={(3.5,0)}]
  % domínio
  \draw[thick] (-1.2,-0.2) ellipse (0.8 and 2.2);
  \node[above] at (-1.2,2.3) {\small $A$};
  \fill[blue!70!black] (-1.2,1) circle (2pt) node[left] {\small $a_1$};
  \fill[blue!70!black] (-1.2,-1) circle (2pt) node[left] {\small $a_2$};

  % contradomínio
  \draw[thick] (1.2,-0.2) ellipse (0.8 and 2.2);
  \node[above] at (1.2,2.3) {\small $B$};
  \fill[red!70!black] (1.2,1) circle (2pt) node[right] {\small $b_1$};
  \fill[red!70!black] (1.2,-1) circle (2pt) node[right] {\small $b_2$};

  % setas f
  \draw[->, thick] (-0.5,1) -- (0.5,1);
  \draw[->, thick] (-0.5,-1) -- (0.5,-1);

  \node[below] at (0,-3) {\small Injetora: sem ambiguidade};
\end{scope}

\end{tikzpicture}
\end{document}
```

**2. Sobrejetora** (todo elemento de $B$ é atingido):

Se $f$ não for sobrejetora, existe $b \in B$ que nenhum $a$ atinge. Então $f^{-1}(b)$ não teria para onde apontar — $f^{-1}$ não estaria definida em todo $B$.

**[[aula-01-funções#^tipos-de-funcoes|Injetora + Sobrejetora = Bijetora]]** → $f^{-1}$ existe como função.

#### Nosso exemplo: $f(x,y) = (2x, 3y)$ é bijetora?
^exemplo-bijetora

**Sim!**
- **Injetora:** se $(2x_1, 3y_1) = (2x_2, 3y_2)$, então $x_1 = x_2$ e $y_1 = y_2$
- **Sobrejetora:** para qualquer $(X, Y) \in \mathbb{R}^2$, basta tomar $x = X/2$ e $y = Y/3$

Portanto a **função inversa** existe:

$$f^{-1}(X, Y) = \left(\frac{X}{2}, \frac{Y}{3}\right)$$

E nesse caso, a **imagem inversa** $f^{-1}[T]$ coincide com a **aplicação da função inversa** ao conjunto $T$:

$$f^{-1}[T] = \{f^{-1}(X,Y) : (X,Y) \in T\}$$

> Quando $f$ **é** bijetora, os dois conceitos se alinham. Quando $f$ **não é** bijetora, só a imagem inversa (pré-imagem) faz sentido.

## Conjuntos de Nível #calculo/definição/conjunto-de-nível-como-pré-imagem
^conjunto-de-nivel-pre-imagem

O **[[aula-01-funções#^superficies-e-curvas-de-nivel|conjunto de nível]]** $c$ de uma função $f: A \subseteq \mathbb{R}^n \to \mathbb{R}$ nada mais é que a [[aula-03-visualizacao-funcoes#^imagem-inversa|imagem inversa]] do conjunto unitário $\{c\}$:

$$N_c(f) = f^{-1}[\{c\}] = \{(x,y) \in A : f(x,y) = c\}$$

Ou seja: é o conjunto de **todos os pontos do domínio** onde a função vale exatamente $c$.

### Exemplo: $f(x,y) = x^2 + y^2$
^exemplo-nivel-circulo

Para cada valor de $c \geq 0$:

$$N_c = \{(x,y) : x^2 + y^2 = c\} = \text{círculo de raio } \sqrt{c}$$

| $c$ | $N_c = f^{-1}[\{c\}]$ | Geometria |
|---|---|---|
| $0$ | $\{(0,0)\}$ | Ponto (origem) |
| $1$ | $x^2 + y^2 = 1$ | Círculo de raio $1$ |
| $4$ | $x^2 + y^2 = 4$ | Círculo de raio $2$ |
| $9$ | $x^2 + y^2 = 9$ | Círculo de raio $3$ |

```tikz
\usepackage{tikz}
\usepackage{amssymb}
\begin{document}
\begin{tikzpicture}

  \draw[->] (-3.5,0) -- (3.5,0) node[right] {$x$};
  \draw[->] (0,-3.5) -- (0,3.5) node[above] {$y$};

  \fill (0,0) circle (0.05);
  \node at (0.5,-0.3) {$c=0$};

  \draw[thick] (0,0) circle (1);
  \node at (1.1,0.8) {$c=1$};

  \draw[thick, dashed] (0,0) circle (2);
  \node at (1.8,1.5) {$c=4$};

  \draw[thick, dotted] (0,0) circle (3);
  \node at (2.5,2.2) {$c=9$};

  \node at (0,-4.2) {$f(x,y) = x^2 + y^2$};

  \draw[->, thick] (4.5,0) -- (5.5,0) node[midway, above] {$f$};

  \draw[->] (7,-0.5) -- (7,3.5) node[above] {$c$};
  \fill (7,0) circle (0.08) node[right] {$\quad 0$};
  \fill (7,1) circle (0.08) node[right] {$\quad 1$};
  \fill (7,2) circle (0.08) node[right] {$\quad 4$};
  \fill (7,3) circle (0.08) node[right] {$\quad 9$};
  \node at (7,-1.2) {$c \in \mathbb{R}$};

\end{tikzpicture}
\end{document}
```

Cada círculo no plano $(x,y)$ é um **conjunto de nível** — todos os pontos que a função $f$ mapeia para o mesmo valor $c$. É a pré-imagem $f^{-1}[\{c\}]$ de um único ponto no contradomínio.
