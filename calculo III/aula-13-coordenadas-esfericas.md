#### motivação: integrais triplas e simetria esférica #calculo/motivação/coordenadas-esfericas
^motivacao-coordenadas-esfericas

A integral dupla da [[aula-12-integral-dupla-fubini#^definicao-integral-dupla|aula 12]] estende-se naturalmente para três variáveis: a **integral tripla** $\iiint_W f\,dV$ mede, por exemplo, a massa de um sólido $W \subset \mathbb{R}^3$ com densidade $f(x, y, z)$. A definição é a mesma — somas de Riemann sobre pequenos paralelepípedos $\Delta V = \Delta x\,\Delta y\,\Delta z$ — e [[aula-12-integral-dupla-fubini#^teorema-fubini|Fubini]] continua valendo, agora com **três** integrais iteradas.

O problema: muitos sólidos importantes (bolas, cascas, cones) têm **simetria esférica**, e descrevê-los em coordenadas cartesianas gera limites de integração horríveis (com raízes duplas). Assim como as [[aula-12-integral-dupla-fubini#^mudanca-polares|coordenadas polares]] transformaram o disco num retângulo, as **coordenadas esféricas** transformam a bola num paralelepípedo.

> **Pergunta:** qual é a mudança de variáveis $T(\rho, \theta, \varphi) = (x, y, z)$ adaptada à simetria radial, e qual é o seu jacobiano (o análogo do $\rho$ das polares)?

---

#### mudança de variáveis em $\mathbb{R}^3$ #calculo/teorema/mudanca-variaveis-3d
^mudanca-variaveis-3d

O [[aula-12-integral-dupla-fubini#^teorema-mudanca-variaveis|teorema de mudança de variáveis]] vale igual em $\mathbb{R}^3$: para um difeomorfismo $T: W^* \to W$ de classe $C^1$ com $\det JT \neq 0$,

$$\iiint_W f(x, y, z)\, dx\,dy\,dz = \iiint_{W^*} f\big(T(u, v, w)\big)\,\left|\det JT\right|\,du\,dv\,dw$$

O fator $\left|\det JT\right|$ continua sendo o jacobiano — agora um determinante $3 \times 3$ — e mede como $T$ distorce **volumes** localmente, exatamente a interpretação de [[apendice-notacoes#^notacao-diferenciabilidade|$\det Jf$]] vista na [[aula-10-teorema-da-funcao-inversa#^enunciado-tfi|aula 10]].

> **Lembrete (cilíndricas):** o caminho mais curto entre polares e esféricas são as [[aula-02-sistema-de-coordenadas#^coordenadas-cilindricas|coordenadas cilíndricas]] $(\rho, \theta, z)$, que são "polares no plano $xy$ + altura $z$". Seu jacobiano é $\left|\det JT\right| = \rho$ (o mesmo das polares, pois $z$ entra trivialmente), dando $dV = \rho\,d\rho\,d\theta\,dz$.

---

#### definição: coordenadas esféricas #calculo/definição/coordenadas-esfericas
^definicao-coordenadas-esfericas

Localizamos um ponto $P = (x, y, z)$ por três grandezas:

| Coordenada | Significado | Intervalo |
|---|---|---|
| $\rho$ | **distância** de $P$ à origem ($\rho = \|P\|$) | $\rho \geq 0$ |
| $\varphi$ | **ângulo polar** (colatitude): ângulo entre o eixo $z^+$ e o vetor $\vec{OP}$ | $0 \leq \varphi \leq \pi$ |
| $\theta$ | **ângulo azimutal**: o mesmo $\theta$ das polares, medido no plano $xy$ a partir do eixo $x^+$ | $0 \leq \theta < 2\pi$ |

As fórmulas de conversão $T(\rho, \theta, \varphi) = (x, y, z)$ são:

$$\boxed{\;x = \rho \sin\varphi \cos\theta, \qquad y = \rho \sin\varphi \sin\theta, \qquad z = \rho \cos\varphi\;}$$

> **Como deduzir:** a projeção de $P$ no plano $xy$ tem comprimento $r = \rho\sin\varphi$ (cateto oposto a $\varphi$) e altura $z = \rho\cos\varphi$ (cateto adjacente). Aí aplicamos as polares **no plano** a esse $r$: $x = r\cos\theta$, $y = r\sin\theta$. Substituindo $r = \rho\sin\varphi$, saem as três fórmulas.

A relação inversa fundamental é:

$$\rho = \sqrt{x^2 + y^2 + z^2}, \qquad \cos\varphi = \frac{z}{\rho}, \qquad \tan\theta = \frac{y}{x}$$

> **Convenção (atenção!):** aqui $\varphi$ é o ângulo a partir do eixo $z$ e $\theta$ é o azimutal — convenção comum em **matemática** (e a usada em geografia, onde $\varphi$ relaciona-se à latitude). Em **física** os papéis de $\theta$ e $\varphi$ costumam ser **trocados**. Ao consultar tabelas, confira sempre qual letra é qual ângulo.

---

#### superfícies coordenadas #calculo/proposição/superficies-esfericas
^superficies-esfericas

Fixar cada coordenada gera uma superfície simples — é o que torna a bola um "retângulo" nessas coordenadas:

- $\rho = \text{const}$ → **esfera** centrada na origem
- $\varphi = \text{const}$ → **cone** com vértice na origem e eixo $z$ (e $\varphi = \frac{\pi}{2}$ dá o plano $xy$)
- $\theta = \text{const}$ → **semiplano** vertical contendo o eixo $z$

> Por isso uma bola $\{x^2+y^2+z^2 \leq R^2\}$ vira o paralelepípedo $W^* = [0, R] \times [0, 2\pi) \times [0, \pi]$ em $(\rho, \theta, \varphi)$ — limites todos constantes.

---

#### o jacobiano das esféricas #calculo/proposição/jacobiano-esfericas
^jacobiano-esfericas

Calculamos $\det JT$ com $T(\rho, \theta, \varphi) = (\rho\sin\varphi\cos\theta,\ \rho\sin\varphi\sin\theta,\ \rho\cos\varphi)$. A jacobiana (colunas: derivadas em $\rho$, $\theta$, $\varphi$):

$$JT = \begin{pmatrix}
\sin\varphi\cos\theta & -\rho\sin\varphi\sin\theta & \rho\cos\varphi\cos\theta \\
\sin\varphi\sin\theta & \rho\sin\varphi\cos\theta & \rho\cos\varphi\sin\theta \\
\cos\varphi & 0 & -\rho\sin\varphi
\end{pmatrix}$$

Expandindo pela **terceira linha** (que tem um zero, facilitando):

$$\det JT = \cos\varphi \cdot M_{31} - 0 + (-\rho\sin\varphi)\cdot M_{33}$$

Calculando os menores:

$$M_{31} = \begin{vmatrix} -\rho\sin\varphi\sin\theta & \rho\cos\varphi\cos\theta \\ \rho\sin\varphi\cos\theta & \rho\cos\varphi\sin\theta \end{vmatrix} = -\rho^2\sin\varphi\cos\varphi$$

$$M_{33} = \begin{vmatrix} \sin\varphi\cos\theta & -\rho\sin\varphi\sin\theta \\ \sin\varphi\sin\theta & \rho\sin\varphi\cos\theta \end{vmatrix} = \rho\sin^2\varphi$$

Logo:

$$\det JT = \cos\varphi\,(-\rho^2\sin\varphi\cos\varphi) - \rho\sin\varphi\,(\rho\sin^2\varphi) = -\rho^2\sin\varphi\,(\cos^2\varphi + \sin^2\varphi) = -\rho^2\sin\varphi$$

Como $0 \leq \varphi \leq \pi$ implica $\sin\varphi \geq 0$, temos:

$$\boxed{\;\left|\det JT\right| = \rho^2 \sin\varphi\;}$$

> **Sinal:** o determinante deu negativo porque a ordem $(\rho, \theta, \varphi)$ inverte a orientação; o que importa na fórmula de integração é o **módulo**, sempre $\rho^2\sin\varphi$.

---

#### o elemento de volume #calculo/definição/elemento-volume-esferico
^elemento-volume-esferico

Substituindo o jacobiano na fórmula de mudança de variáveis, o elemento de volume em coordenadas esféricas é:

$$\boxed{\;dV = \rho^2 \sin\varphi\, d\rho\, d\varphi\, d\theta\;}$$

e portanto:

$$\iiint_W f(x,y,z)\, dV = \iiint_{W^*} f(\rho\sin\varphi\cos\theta,\, \rho\sin\varphi\sin\theta,\, \rho\cos\varphi)\;\rho^2\sin\varphi\; d\rho\, d\varphi\, d\theta$$

> **Intuição geométrica:** uma "caixa esférica" infinitesimal tem arestas $d\rho$ (radial), $\rho\,d\varphi$ (arco no meridiano) e $\rho\sin\varphi\,d\theta$ (arco no paralelo, cujo raio é $\rho\sin\varphi$). O volume é o produto: $d\rho \cdot \rho\,d\varphi \cdot \rho\sin\varphi\,d\theta = \rho^2\sin\varphi\,d\rho\,d\varphi\,d\theta$. O fator $\rho^2$ aparece porque cascas distantes têm mais volume; o $\sin\varphi$ porque os paralelos encolhem perto dos polos.

> **Erro clássico:** esquecer o $\rho^2\sin\varphi$ (análogo a esquecer o $\rho$ das polares). Sem ele, a integral está simplesmente errada.

---

#### exemplo: volume da bola #calculo/exemplo/volume-esfera
^exemplo-volume-esfera

Calcular o volume da bola $W = \{x^2 + y^2 + z^2 \leq R^2\}$ usando $\text{Vol}(W) = \iiint_W 1\, dV$.

Em esféricas, $W^* = \{0 \leq \rho \leq R,\ 0 \leq \varphi \leq \pi,\ 0 \leq \theta \leq 2\pi\}$ e o integrando é $1 \cdot \rho^2\sin\varphi$:

$$\text{Vol}(W) = \int_0^{2\pi}\!\!\int_0^{\pi}\!\!\int_0^{R} \rho^2 \sin\varphi\; d\rho\, d\varphi\, d\theta$$

Como o domínio é um "retângulo" e o integrando **fatora**, separamos as três integrais:

$$= \underbrace{\left(\int_0^{2\pi} d\theta\right)}_{2\pi} \underbrace{\left(\int_0^{\pi} \sin\varphi\, d\varphi\right)}_{[-\cos\varphi]_0^\pi\, =\, 2} \underbrace{\left(\int_0^{R} \rho^2\, d\rho\right)}_{R^3/3} = 2\pi \cdot 2 \cdot \frac{R^3}{3} = \boxed{\frac{4}{3}\pi R^3}$$

> Reobtivemos a fórmula clássica do volume da esfera. Em cartesianas, isso exigiria $\int\int\int$ com limites $\pm\sqrt{R^2 - x^2 - y^2}$ — comparativamente intratável.

---

#### quando usar cada sistema #calculo/proposição/quando-usar-coordenadas
^quando-usar-coordenadas

| Sistema | Elemento de volume | Use quando há simetria... |
|---|---|---|
| Cartesianas $(x,y,z)$ | $dx\,dy\,dz$ | retangular / caixas |
| [[aula-02-sistema-de-coordenadas#^coordenadas-cilindricas\|Cilíndricas]] $(\rho,\theta,z)$ | $\rho\, d\rho\,d\theta\,dz$ | axial (cilindros, em torno de um eixo) |
| Esféricas $(\rho,\theta,\varphi)$ | $\rho^2\sin\varphi\, d\rho\,d\varphi\,d\theta$ | radial (bolas, cones, cascas) |

> **Regra de bolso:** olhe o **domínio** e o **integrando**. Se ambos ficam simples ($x^2+y^2+z^2 \to \rho^2$, esfera $\to$ limite constante), a mudança vale a pena. A escolha das coordenadas é a decisão mais importante numa integral tripla — uma boa escolha transforma um cálculo impossível num trivial.

---

#### contexto histórico #calculo/contexto/coordenadas-esfericas-historia
^contexto-historico-esfericas

As coordenadas esféricas remontam à **astronomia** e à **geografia** antigas — latitude, longitude e distância radial são essencialmente coordenadas esféricas sobre a Terra. Sua formalização no cálculo, com o jacobiano $\rho^2\sin\varphi$, vem do trabalho de **Euler** e **Lagrange** no século XVIII, e foi sistematizada por **Jacobi** (de quem vem o nome jacobiano) ao estudar mudanças de variáveis em integrais múltiplas.

> **Onde aparecem:** são onipresentes em **física** — campos gravitacional e elétrico de fontes pontuais (que dependem só de $\rho$), o átomo de hidrogênio em mecânica quântica, e qualquer problema com simetria central. A escolha de coordenadas adaptadas à simetria é o que torna esses cálculos viáveis.

---

> **Próximos passos:** consolidar **integrais triplas** em regiões gerais (limites variáveis nos três níveis) e aplicar os três sistemas de coordenadas a problemas de massa, centro de massa e momento de inércia (tópicos 5–7 do [[apendice-disciplina#^programa|programa]]). Depois, partir para **integrais de linha e de superfície** (tópico 8).
