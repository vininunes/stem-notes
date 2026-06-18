Colocar algo em um sistema de coordenadas significa **associar pontos a números**, o que seriam as **coordenadas do ponto**.

## Coordenadas Cartesianas #calculo/definição/coordenadas-cartesianas
^coordenadas-cartesianas

Cada ponto $P$ no plano é representado por um par ordenado $(x, y)$, onde:
- $x$ = distância horizontal (ao eixo $y$)
- $y$ = distância vertical (ao eixo $x$)

No espaço, um ponto é representado por uma tripla $(x, y, z)$.

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1.2]
  % eixos
  \draw[->] (-0.5,0) -- (4,0) node[right] {$x$};
  \draw[->] (0,-0.5) -- (0,3.5) node[above] {$y$};

  % ponto
  \fill[red!70!black] (2.5,2) circle (2pt) node[above right] {$P = (x_0, y_0)$};

  % projeções
  \draw[dashed, gray] (2.5,0) node[below] {$x_0$} -- (2.5,2);
  \draw[dashed, gray] (0,2) node[left] {$y_0$} -- (2.5,2);
\end{tikzpicture}
\end{document}
```


## Coordenadas Polares #calculo/definição/coordenadas-polares
^coordenadas-polares

Cada ponto $P$ no plano é representado por $(\rho, \theta)$, onde:
- $\rho$ = distância do ponto à origem
- $\theta$ = ângulo medido a partir do eixo $x$ positivo (sentido anti-horário)

**Conversão para cartesianas:**

$$x = \rho \cos\theta, \quad y = \rho \sin\theta$$

**Conversão para polares:**

$$\rho = \sqrt{x^2 + y^2}, \quad \theta = \arctan\left(\frac{y}{x}\right)$$

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1.5]
  % eixos
  \draw[->] (-0.5,0) -- (4,0) node[right] {$x$};
  \draw[->] (0,-0.5) -- (0,3.5) node[above] {$y$};

  % ponto P
  \coordinate (O) at (0,0);
  \coordinate (P) at (3,2);

  % linha rho (da origem ao ponto)
  \draw[thick, blue!70!black] (O) -- (P) node[midway, above left] {$\rho$};

  % ponto
  \fill[red!70!black] (P) circle (2pt) node[above right] {$P = (\rho, \theta)$};

  % arco do ângulo theta
  \draw[thick, red!70!black] (0.8,0) arc[start angle=0, end angle=33.69, radius=0.8];
  \node[red!70!black] at (1.1,0.25) {$\theta$};

  % projeções
  \draw[dashed, gray] (3,0) node[below] {$\rho\cos\theta$} -- (P);
  \draw[dashed, gray] (0,2) node[left] {$\rho\sin\theta$} -- (P);
\end{tikzpicture}
\end{document}
```

Ou seja, uma coordenada cartesiana $(x, y)$ equivale a uma coordenada polar da seguinte forma:

$$(x, y) = (\rho\cos\theta,\; \rho\sin\theta)$$

### Observações importantes
^polares-observacoes

- $\rho \geq 0$ (distância é sempre não-negativa)
- $\theta$ não é único: $(\rho, \theta)$ e $(\rho, \theta + 2\pi)$ representam o **mesmo ponto**
- A origem tem $\rho = 0$ e $\theta$ pode ser qualquer valor

### Restringindo as variáveis
^polares-restringindo-variaveis

É possível colocar **limites nas variáveis** para descrever regiões específicas:

$$\rho \in [0, 1], \quad \theta \in [0, 2\pi]$$

Isso descreve o **disco unitário** completo (todos os pontos com distância até 1 da origem, varrendo todos os ângulos).

Variando os limites, descrevemos diferentes regiões:

| $\rho$ | $\theta$ | Região |
|---|---|---|
| $[0, 1]$ | $[0, 2\pi]$ | Disco unitário completo |
| $\{1\}$ | $[0, 2\pi]$ | Circunferência unitária (borda) |
| $[0, 1]$ | $[0, \pi]$ | Meia-lua superior |
| $[0, 1]$ | $[0, \pi/2]$ | Quarto de disco (1° quadrante) |

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1.1]

% --- 1) Disco unitário completo ---
\begin{scope}[shift={(-4.5,4)}]
  \draw[->] (-1.6,0) -- (1.6,0) node[right] {\tiny $x$};
  \draw[->] (0,-1.6) -- (0,1.6) node[above] {\tiny $y$};
  \fill[blue!20] (0,0) circle (1);
  \draw[blue!70!black, thick] (0,0) circle (1);
  \node[below] at (0,-2) {\small $\rho \in [0,1],\; \theta \in [0,2\pi]$};
  \node[above] at (0,1.8) {\small \textbf{Disco completo}};
\end{scope}

% --- 2) Circunferência unitária ---
\begin{scope}[shift={(1.5,4)}]
  \draw[->] (-1.6,0) -- (1.6,0) node[right] {\tiny $x$};
  \draw[->] (0,-1.6) -- (0,1.6) node[above] {\tiny $y$};
  \draw[red!70!black, very thick] (0,0) circle (1);
  \node[below] at (0,-2) {\small $\rho = 1,\; \theta \in [0,2\pi]$};
  \node[above] at (0,1.8) {\small \textbf{Circunfer\^encia}};
\end{scope}

% --- 3) Meia-lua superior ---
\begin{scope}[shift={(-4.5,-1.5)}]
  \draw[->] (-1.6,0) -- (1.6,0) node[right] {\tiny $x$};
  \draw[->] (0,-1.6) -- (0,1.6) node[above] {\tiny $y$};
  \fill[green!20] (0,0) -- (1,0) arc[start angle=0, end angle=180, radius=1] -- cycle;
  \draw[green!50!black, thick] (1,0) arc[start angle=0, end angle=180, radius=1];
  \draw[green!50!black, thick] (-1,0) -- (1,0);
  \node[below] at (0,-2) {\small $\rho \in [0,1],\; \theta \in [0,\pi]$};
  \node[above] at (0,1.8) {\small \textbf{Meia-lua superior}};
\end{scope}

% --- 4) Quarto de disco (1° quadrante) ---
\begin{scope}[shift={(1.5,-1.5)}]
  \draw[->] (-1.6,0) -- (1.6,0) node[right] {\tiny $x$};
  \draw[->] (0,-1.6) -- (0,1.6) node[above] {\tiny $y$};
  \fill[orange!20] (0,0) -- (1,0) arc[start angle=0, end angle=90, radius=1] -- cycle;
  \draw[orange!70!black, thick] (1,0) arc[start angle=0, end angle=90, radius=1];
  \draw[orange!70!black, thick] (0,0) -- (1,0);
  \draw[orange!70!black, thick] (0,0) -- (0,1);
  \node[below] at (0,-2) {\small $\rho \in [0,1],\; \theta \in [0,\pi/2]$};
  \node[above] at (0,1.8) {\small \textbf{Quarto de disco}};
\end{scope}

\end{tikzpicture}
\end{document}
```

### Exemplo: círculo em polares
^exemplo-circulo-polares

O círculo $x^2 + y^2 = r^2$ em coordenadas polares se torna simplesmente:

$$\rho = r$$

Pois $x^2 + y^2 = (\rho\cos\theta)^2 + (\rho\sin\theta)^2 = \rho^2(\cos^2\theta + \sin^2\theta) = \rho^2$

### Associação entre coordenadas polares e cartesianas
^associacao-polares-cartesianas

Um mesmo ponto $P$ pode ser descrito nos dois sistemas simultaneamente:

$$P = (x, y) = (\rho\cos\theta,\; \rho\sin\theta)$$

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1.8]

  % eixos
  \draw[->] (-0.5,0) -- (4.2,0) node[right] {$x$};
  \draw[->] (0,-0.5) -- (0,3.2) node[above] {$y$};

  % coordenadas do ponto
  \coordinate (O) at (0,0);
  \coordinate (P) at (3,2);

  % triângulo retângulo
  \draw[gray!50, thin] (3,0) -- (3,2);

  % projeções cartesianas (x, y)
  \draw[dashed, blue!60, thick] (3,0) -- (P);
  \draw[dashed, blue!60, thick] (0,2) -- (P);

  % labels x e y nos eixos
  \draw[blue!70!black, thick] (0,-0.1) -- (0,-0.2);
  \draw[blue!70!black, thick] (3,-0.1) -- (3,-0.2);
  \node[blue!70!black, below] at (1.5,-0.2) {$x = \rho\cos\theta$};

  \draw[blue!70!black, thick] (-0.1,0) -- (-0.2,0);
  \draw[blue!70!black, thick] (-0.1,2) -- (-0.2,2);
  \node[blue!70!black, left] at (-0.2,1) {$y = \rho\sin\theta$};

  % rho (linha da origem ao ponto)
  \draw[red!70!black, very thick] (O) -- (P)
    node[midway, above left] {$\rho = \sqrt{x^2 + y^2}$};

  % arco theta
  \draw[red!70!black, thick] (0.7,0) arc (0:33.69:0.7);
  \node[red!70!black] at (0.95,0.22) {$\theta$};

  % ângulo reto
  \draw[gray!60] (2.75,0) -- (2.75,0.25) -- (3,0.25);

  % ponto P
  \fill[black] (P) circle (2pt);
  \node[above right] at (P) {$P = (x,y) = (\rho, \theta)$};

  % marcações nos eixos
  \fill[blue!70!black] (3,0) circle (1.5pt);
  \fill[blue!70!black] (0,2) circle (1.5pt);

\end{tikzpicture}
\end{document}
```

Resumindo a associação:

| Cartesiana → Polar | Polar → Cartesiana |
|---|---|
| $\rho = \sqrt{x^2 + y^2}$ | $x = \rho\cos\theta$ |
| $\theta = \arctan\left(\frac{y}{x}\right)$ | $y = \rho\sin\theta$ |

O triângulo retângulo formado pelas projeções é a chave: os **catetos** são $x$ e $y$ (cartesianas), a **hipotenusa** é $\rho$ e o **ângulo** na origem é $\theta$ (polares).

#### Exemplo 1: Círculo $\rho = 1$
^exemplo-circulo-rho-1

No plano $(\rho, \theta)$: uma **linha horizontal** em $\rho = 1$.
No plano $(x, y)$: um **círculo** de raio 1.

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1]

% --- Plano (rho, theta) ---
\begin{scope}[shift={(-4.5,0)}]
  \draw[->] (-0.5,0) -- (4.5,0) node[right] {$\theta$};
  \draw[->] (0,-0.5) -- (0,2.5) node[above] {$\rho$};

  % linha rho = 1
  \draw[red!70!black, very thick] (0,1) -- (4,1);

  % marcações no eixo theta
  \node[below] at (0,0) {\tiny $0$};
  \node[below] at (2,0) {\tiny $\pi$};
  \node[below] at (4,0) {\tiny $2\pi$};

  % marcação no eixo rho
  \draw[thin] (-0.1,1) -- (0.1,1);
  \node[left] at (-0.1,1) {\tiny $1$};

  \node[below] at (2,-1) {\small Plano $(\rho, \theta)$};
  \node[red!70!black, above] at (2,1.1) {\small $\rho = 1$};
\end{scope}

% --- Seta ---
\draw[->, thick] (-0.2,0) -- (1.2,0) node[midway, above] {\small $f$};

% --- Plano (x, y) ---
\begin{scope}[shift={(4,0)}]
  \draw[->] (-2.2,0) -- (2.2,0) node[right] {$x$};
  \draw[->] (0,-2.2) -- (0,2.2) node[above] {$y$};

  % círculo
  \draw[red!70!black, very thick] (0,0) circle (1.5);

  % marcações
  \draw[thin] (1.5,-0.1) -- (1.5,0.1);
  \node[below] at (1.5,-0.15) {\tiny $1$};
  \draw[thin] (-0.1,1.5) -- (0.1,1.5);
  \node[left] at (-0.15,1.5) {\tiny $1$};

  \node[below] at (0,-2.8) {\small Plano $(x, y)$};
  \node[red!70!black] at (1.8,1.5) {\small $x^2+y^2=1$};
\end{scope}

\end{tikzpicture}
\end{document}
```

#### Exemplo 2: Reta $\theta = \pi/4$
^exemplo-reta-theta

No plano $(\rho, \theta)$: uma **linha vertical** em $\theta = \pi/4$.
No plano $(x, y)$: uma **reta** passando pela origem com inclinação de $45°$.

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1]

% --- Plano (rho, theta) ---
\begin{scope}[shift={(-4.5,0)}]
  \draw[->] (-0.5,0) -- (4.5,0) node[right] {$\theta$};
  \draw[->] (0,-0.5) -- (0,2.5) node[above] {$\rho$};

  % linha theta = pi/4
  \draw[blue!70!black, very thick] (1,0) -- (1,2.2);

  % marcações no eixo theta
  \node[below] at (0,0) {\tiny $0$};
  \node[below] at (1,0) {\tiny $\frac{\pi}{4}$};
  \node[below] at (2,0) {\tiny $\pi$};
  \node[below] at (4,0) {\tiny $2\pi$};

  \node[below] at (2,-1) {\small Plano $(\rho, \theta)$};
  \node[blue!70!black, right] at (1.1,1.8) {\small $\theta = \frac{\pi}{4}$};
\end{scope}

% --- Seta ---
\draw[->, thick] (-0.2,0) -- (1.2,0) node[midway, above] {\small $f$};

% --- Plano (x, y) ---
\begin{scope}[shift={(4,0)}]
  \draw[->] (-2.2,0) -- (2.2,0) node[right] {$x$};
  \draw[->] (0,-2.2) -- (0,2.2) node[above] {$y$};

  % reta y = x
  \draw[blue!70!black, very thick] (-1.8,-1.8) -- (1.8,1.8);

  \node[below] at (0,-2.8) {\small Plano $(x, y)$};
  \node[blue!70!black, above left] at (-1.2,-1.2) {\small $y = x$};
\end{scope}

\end{tikzpicture}
\end{document}
```

#### Exemplo 3: Retângulo $\rho \in [0,1],\; \theta \in [0, \pi/2]$
^exemplo-retangulo-quarto-disco

No plano $(\rho, \theta)$: um **retângulo**.
No plano $(x, y)$: um **quarto de disco**.

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1]

% --- Plano (rho, theta) ---
\begin{scope}[shift={(-4.5,0)}]
  \draw[->] (-0.5,0) -- (4.5,0) node[right] {$\theta$};
  \draw[->] (0,-0.5) -- (0,2.5) node[above] {$\rho$};

  % retângulo preenchido
  \fill[orange!20] (0,0) rectangle (1.5,1.5);
  \draw[orange!70!black, very thick] (0,0) rectangle (1.5,1.5);

  % marcações
  \node[below] at (0,0) {\tiny $0$};
  \node[below] at (1.5,0) {\tiny $\frac{\pi}{2}$};
  \node[below] at (3,0) {\tiny $\pi$};
  \node[below] at (4,0) {\tiny $2\pi$};
  \draw[thin] (-0.1,1.5) -- (0.1,1.5);
  \node[left] at (-0.1,1.5) {\tiny $1$};

  \node[below] at (2,-1) {\small Plano $(\rho, \theta)$};
\end{scope}

% --- Seta ---
\draw[->, thick] (-0.2,0) -- (1.2,0) node[midway, above] {\small $f$};

% --- Plano (x, y) ---
\begin{scope}[shift={(4,0)}]
  \draw[->] (-2.2,0) -- (2.2,0) node[right] {$x$};
  \draw[->] (0,-2.2) -- (0,2.2) node[above] {$y$};

  % quarto de disco
  \fill[orange!20] (0,0) -- (1.5,0) arc (0:90:1.5) -- cycle;
  \draw[orange!70!black, very thick] (1.5,0) arc (0:90:1.5);
  \draw[orange!70!black, very thick] (0,0) -- (1.5,0);
  \draw[orange!70!black, very thick] (0,0) -- (0,1.5);

  % marcações
  \draw[thin] (1.5,-0.1) -- (1.5,0.1);
  \node[below] at (1.5,-0.15) {\tiny $1$};
  \draw[thin] (-0.1,1.5) -- (0.1,1.5);
  \node[left] at (-0.15,1.5) {\tiny $1$};

  \node[below] at (0,-2.8) {\small Plano $(x, y)$};
\end{scope}

\end{tikzpicture}
\end{document}
```

#### Exemplo 4: Espiral $\rho = \theta$ (Espiral de Arquimedes)
^exemplo-espiral-arquimedes

No plano $(\rho, \theta)$: uma **reta** diagonal ($\rho = \theta$, como $y = x$).
No plano $(x, y)$: uma **espiral** que se afasta da origem à medida que $\theta$ cresce.

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1]

% --- Plano (rho, theta) ---
\begin{scope}[shift={(-4.5,0)}]
  \draw[->] (-0.5,0) -- (4.5,0) node[right] {$\theta$};
  \draw[->] (0,-0.5) -- (0,4) node[above] {$\rho$};

  % reta rho = theta
  \draw[purple!70!black, very thick] (0,0) -- (3.5,3.5);

  % marcações no eixo theta
  \node[below] at (0,0) {\tiny $0$};
  \node[below] at (1.57,0) {\tiny $\frac{\pi}{2}$};
  \node[below] at (3.14,0) {\tiny $\pi$};

  % marcações no eixo rho
  \draw[thin] (-0.1,1.57) -- (0.1,1.57);
  \node[left] at (-0.1,1.57) {\tiny $\frac{\pi}{2}$};
  \draw[thin] (-0.1,3.14) -- (0.1,3.14);
  \node[left] at (-0.1,3.14) {\tiny $\pi$};

  \node[below] at (2,-1) {\small Plano $(\rho, \theta)$};
  \node[purple!70!black, above left] at (3,3.2) {\small $\rho = \theta$};
\end{scope}

% --- Seta ---
\draw[->, thick] (-0.2,0) -- (1.2,0) node[midway, above] {\small $f$};

% --- Plano (x, y) ---
\begin{scope}[shift={(4.5,0)}]
  \draw[->] (-3.5,0) -- (3.5,0) node[right] {$x$};
  \draw[->] (0,-3.5) -- (0,3.5) node[above] {$y$};

  % espiral de Arquimedes: rho = theta
  % pontos: (theta*cos(theta), theta*sin(theta)) para theta de 0 a 2pi
  % escalada por 0.45 para caber
  \draw[purple!70!black, very thick]
    (0,0)
    \foreach \t in {0.1,0.2,...,6.28} {
      -- ({\t*cos(\t r)*0.45}, {\t*sin(\t r)*0.45})
    };

  % marcação de direção
  \fill[purple!70!black] ({6.28*cos(6.28 r)*0.45}, {6.28*sin(6.28 r)*0.45}) circle (2pt);
  \node[purple!70!black, right] at ({6.28*cos(6.28 r)*0.45+0.1}, {6.28*sin(6.28 r)*0.45+0.2}) {\small $\theta = 2\pi$};

  \fill[purple!70!black] ({3.14*cos(3.14 r)*0.45}, {3.14*sin(3.14 r)*0.45}) circle (2pt);
  \node[purple!70!black, above left] at ({3.14*cos(3.14 r)*0.45}, {3.14*sin(3.14 r)*0.45}) {\small $\theta = \pi$};

  \node[below] at (0,-4) {\small Plano $(x, y)$};
\end{scope}

\end{tikzpicture}
\end{document}
```

A cada volta completa ($2\pi$), a espiral se afasta mais $2\pi$ unidades da origem — pois $\rho$ cresce linearmente com $\theta$.

### Aplicação: do globo ao plano (Projeção de Mercator)
^projecao-mercator

Um exemplo clássico dessa associação entre sistemas de coordenadas é a **Projeção de Mercator** — como representamos a Terra (esfera) em um mapa plano (retângulo).

Na esfera, cada ponto é descrito por **coordenadas esféricas**:
- $\lambda$ = longitude (ângulo horizontal, como $\theta$)
- $\varphi$ = latitude (ângulo vertical)

No mapa plano, precisamos de **coordenadas cartesianas** $(x, y)$.

A projeção de Mercator faz essa conversão:

$$x = \lambda$$
$$y = \ln\left(\tan\left(\frac{\pi}{4} + \frac{\varphi}{2}\right)\right)$$

Ou seja, é uma [[apendice-notacoes#^notacao-funcoes|função]] $f(\lambda, \varphi) = (x, y)$ que transforma coordenadas angulares (esféricas) em coordenadas planas ([[aula-02-sistema-de-coordenadas#^coordenadas-cartesianas|cartesianas]]) — exatamente o tipo de transformação que estamos estudando.

```tikz
\usepackage{tikz}

\begin{document}
\begin{tikzpicture}[scale=1]

% --- Globo (esfera) ---
\begin{scope}[shift={(-3.5,0)}]
  % esfera
  \draw[thick] (0,0) circle (2);
  \draw[gray!50] (0,0) ellipse (2 and 0.6);

  % linhas de latitude
  \draw[blue!40, thin] (0,0.8) ellipse (1.83 and 0.5);
  \draw[blue!40, thin] (0,-0.8) ellipse (1.83 and 0.5);

  % linhas de longitude
  \draw[red!40, thin] (0,-2) arc (-90:90:0.6 and 2);
  \draw[red!40, thin] (0,-2) arc (-90:90:-0.6 and 2);

  % ponto
  \fill[black] (1.2,1.1) circle (2pt);
  \node[above right] at (1.2,1.1) {\small $(\lambda, \varphi)$};

  % labels
  \node[red!60!black, left] at (-0.8,1.5) {\tiny $\lambda$};
  \node[blue!60!black, right] at (1.9,0.8) {\tiny $\varphi$};

  \node[below] at (0,-2.7) {\small \textbf{Globo}};
  \node[below] at (0,-3.2) {\small (coord. esf\'ericas)};
\end{scope}

% --- Seta ---
\draw[->, thick] (-0.8,0) -- (0.8,0) node[midway, above] {\small Mercator};

% --- Mapa plano ---
\begin{scope}[shift={(3.5,0)}]
  % retângulo do mapa
  \draw[thick] (-2.2,-1.8) rectangle (2.2,1.8);

  % grid latitude (horizontal)
  \draw[blue!40, thin] (-2.2,-0.9) -- (2.2,-0.9);
  \draw[blue!40, thin] (-2.2,0) -- (2.2,0);
  \draw[blue!40, thin] (-2.2,0.9) -- (2.2,0.9);

  % grid longitude (vertical)
  \draw[red!40, thin] (-1.1,-1.8) -- (-1.1,1.8);
  \draw[red!40, thin] (0,-1.8) -- (0,1.8);
  \draw[red!40, thin] (1.1,-1.8) -- (1.1,1.8);

  % ponto
  \fill[black] (1.1,1.2) circle (2pt);
  \node[above right] at (1.1,1.2) {\small $(x, y)$};

  \node[below] at (0,-2.7) {\small \textbf{Mapa plano}};
  \node[below] at (0,-3.2) {\small (coord. cartesianas)};
\end{scope}

\end{tikzpicture}
\end{document}
```

**Consequência:** os meridianos (longitude, vermelho) viram linhas verticais e os paralelos (latitude, azul) viram linhas horizontais. Regiões perto dos polos ficam **distorcidas** (esticadas) porque a função $\ln(\tan(...))$ cresce muito quando $\varphi \to \pm 90°$ — por isso a Groenlândia parece enorme no mapa, mas na realidade é menor que a África.

## Coordenadas Cilíndricas #calculo/definição/coordenadas-cilíndricas
^coordenadas-cilindricas

As coordenadas cilíndricas são a extensão natural das [[aula-02-sistema-de-coordenadas#^coordenadas-polares|coordenadas polares]] para o espaço 3D: usamos $(\rho, \theta)$ no plano $xy$ e adicionamos a altura $z$.

Um ponto $P$ no espaço é representado por $(\rho, \theta, z)$, onde:
- $\rho$ = distância do ponto ao **eixo** $z$ (não à origem!)
- $\theta$ = ângulo no plano $xy$, medido a partir do eixo $x$ positivo
- $z$ = altura (mesma do cartesiano)

**Conversão para cartesianas:**

$$x = \rho\cos\theta, \quad y = \rho\sin\theta, \quad z = z$$

**Conversão para cilíndricas:**

$$\rho = \sqrt{x^2 + y^2}, \quad \theta = \arctan\left(\frac{y}{x}\right), \quad z = z$$

> Note que $z$ não muda — a única diferença em relação às polares é a adição da coordenada $z$.

```tikz
\usepackage{tikz}
\usepackage{amssymb}
\begin{document}
\begin{tikzpicture}[scale=1.3]

  % eixos 3D (projeção oblíqua)
  \draw[->] (0,0) -- (-1.5,-1) node[below] {$x$};
  \draw[->] (0,0) -- (4,0) node[right] {$y$};
  \draw[->] (0,0) -- (0,4) node[above] {$z$};

  % ponto P
  \coordinate (P) at (2,3);
  \coordinate (Pxy) at (2,0);

  % projeção no plano xy
  \draw[dashed, gray] (P) -- (Pxy);
  \draw[dashed, gray] (0,0) -- (Pxy);

  % rho no plano xy
  \draw[thick] (0,0) -- (Pxy) node[midway, below] {$\rho$};

  % z vertical
  \draw[thick] (Pxy) -- (P) node[midway, right] {$z$};

  % arco theta
  \draw[thick] (-0.4,-0.27) arc (214:360:0.5);
  \node at (0.5,-0.4) {$\theta$};

  % ponto
  \fill (P) circle (0.06) node[above right] {$P = (\rho, \theta, z)$};
  \fill (Pxy) circle (0.04);

\end{tikzpicture}
\end{document}
```

### Quando usar cilíndricas?
^quando-usar-cilindricas

Sempre que o problema tiver **simetria em torno de um eixo** (geralmente o eixo $z$). Exemplos:

| Superfície | Cartesiana | Cilíndrica |
|---|---|---|
| Cilindro | $x^2 + y^2 = r^2$ | $\rho = r$ |
| Cone | $z = \sqrt{x^2 + y^2}$ | $z = \rho$ |
| Paraboloide | $z = x^2 + y^2$ | $z = \rho^2$ |

### Limites das variáveis
^cilindricas-limites-variaveis

$$\rho \geq 0, \quad \theta \in [0, 2\pi], \quad z \in \mathbb{R}$$

Para descrever um **cilindro sólido** de raio $R$ e altura $h$:

$$\rho \in [0, R], \quad \theta \in [0, 2\pi], \quad z \in [0, h]$$

Isso é um **retângulo** no espaço $(\rho, \theta, z)$ que vira um cilindro no espaço $(x, y, z)$ — a mesma ideia do retângulo polar que virava um quarto de disco, agora em 3D.

```tikz
\usepackage{tikz}
\usepackage{amssymb}
\begin{document}
\begin{tikzpicture}[scale=1.2]

  % eixos 3D
  \draw[->] (0,0) -- (-2,-1.2) node[below] {$x$};
  \draw[->] (0,0) -- (3.5,0) node[right] {$y$};
  \draw[->] (0,0) -- (0,5) node[above] {$z$};

  % elipse inferior (base do cilindro) - parte de trás
  \draw[dashed, gray] (-1.5,0) arc (180:360:1.5 and 0.5);

  % corpo do cilindro - linhas laterais
  \draw[thick] (-1.5,0) -- (-1.5,3.5);
  \draw[thick] (1.5,0) -- (1.5,3.5);

  % elipse inferior (base) - parte da frente
  \draw[thick] (-1.5,0) arc (180:0:1.5 and 0.5);

  % elipse superior (topo do cilindro)
  \draw[thick] (-1.5,3.5) arc (180:360:1.5 and 0.5);
  \draw[thick] (-1.5,3.5) arc (180:0:1.5 and 0.5);

  % rho (raio)
  \draw[dashed] (0,0) -- (1.5,0) node[midway, below] {$R$};

  % h (altura)
  \draw[<->] (2.2,0) -- (2.2,3.5) node[midway, right] {$h$};

  % labels
  \node at (0,-1.5) {$\rho \in [0, R]$};
  \node at (0,-2.1) {$\theta \in [0, 2\pi]$};
  \node at (0,-2.7) {$z \in [0, h]$};

\end{tikzpicture}
\end{document}
```
