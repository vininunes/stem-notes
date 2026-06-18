#### motivação: quando uma equação define uma função? #calculo/motivação/funcao-implicita
^motivacao-funcao-implicita

Considere a equação do círculo:

$$x^2 + y^2 = 1$$

Isso **não** define $y$ como função de $x$ globalmente — para cada $x \in (-1, 1)$, existem **dois** valores de $y$: $+\sqrt{1 - x^2}$ e $-\sqrt{1 - x^2}$.

Mas **localmente** (perto de um ponto do círculo que não seja $(1, 0)$ ou $(-1, 0)$), conseguimos escrever $y = g(x)$ para alguma função $g$ de classe $C^1$.

> **Pergunta geral:** dada uma equação $F(x, y) = 0$, quando podemos "isolar" $y$ como função de $x$, pelo menos localmente? E se tivermos um sistema $F(x_1, \ldots, x_n, y_1, \ldots, y_m) = 0$?

O [[aula-10-teorema-da-funcao-inversa#^enunciado-tfi|TFI]] responde quando podemos inverter $f$ localmente. O **Teorema da Função Implícita** (TFImp) responde quando podemos resolver equações $F = 0$ localmente — e na verdade é **consequência** do TFI.

---

#### enunciado: Teorema da Função Implícita #calculo/teorema/funcao-implicita
^enunciado-tfimplicita

> **Teorema da Função Implícita.** Seja $F: U \subset \mathbb{R}^n \times \mathbb{R}^m \to \mathbb{R}^m$ de classe $C^1$, com $U$ aberto. Seja $(x_0, y_0) \in U$ tal que:
>
> - $F(x_0, y_0) = 0$
> - A matriz $\dfrac{\partial F}{\partial y}(x_0, y_0) \in M_{m \times m}(\mathbb{R})$ é **inversível** (i.e., $\det \dfrac{\partial F}{\partial y}(x_0, y_0) \neq 0$)
>
> Então:
>
> 1. Existem abertos $V \subset \mathbb{R}^n$ com $x_0 \in V$ e $W \subset \mathbb{R}^m$ com $y_0 \in W$ tais que, para cada $x \in V$, existe **único** $y = g(x) \in W$ com $F(x, g(x)) = 0$
> 2. A função $g: V \to W$ assim definida é de **classe $C^1$**
> 3. A jacobiana de $g$ é dada por:
>
> $$Jg(x) = -\left(\frac{\partial F}{\partial y}(x, g(x))\right)^{-1} \cdot \frac{\partial F}{\partial x}(x, g(x))$$

Aqui, as variáveis são separadas em dois grupos:
- $x = (x_1, \ldots, x_n) \in \mathbb{R}^n$ — as variáveis **livres** (parâmetros)
- $y = (y_1, \ldots, y_m) \in \mathbb{R}^m$ — as variáveis que queremos **isolar**

E a jacobiana de $F$ se decompõe em dois blocos:

$$JF(x, y) = \begin{pmatrix} \dfrac{\partial F}{\partial x} & \dfrac{\partial F}{\partial y} \end{pmatrix}$$

onde $\dfrac{\partial F}{\partial x}$ é $m \times n$ e $\dfrac{\partial F}{\partial y}$ é $m \times m$.

> **Hipóteses (checklist):**
> - $F: U \subset \mathbb{R}^{n+m} \to \mathbb{R}^m$ de classe $C^1$
> - $(x_0, y_0) \in U$ com $F(x_0, y_0) = 0$ (ponto na "superfície" de nível)
> - $\det \dfrac{\partial F}{\partial y}(x_0, y_0) \neq 0$ (a parte da jacobiana relativa às variáveis que queremos isolar é inversível)

> **O que o teorema entrega:**
> - **Existência local** de $g$: perto de $(x_0, y_0)$, a equação $F = 0$ define $y$ como função de $x$
> - **Unicidade local**: o $y$ é único (na vizinhança $W$)
> - $g \in C^1$ automaticamente
> - **Fórmula** para $Jg$ sem precisar encontrar $g$ explicitamente

---

#### comparação: TFI vs. TFImp #calculo/proposição/comparacao-tfi-tfimplicita
^comparacao-tfi-tfimplicita

| | TFI | TFImp |
|---|---|---|
| **Pergunta** | Quando $f$ é localmente inversível? | Quando $F(x,y) = 0$ define $y = g(x)$ localmente? |
| **Função** | $f: \mathbb{R}^n \to \mathbb{R}^n$ | $F: \mathbb{R}^{n+m} \to \mathbb{R}^m$ |
| **Hipótese-chave** | $\det Jf(x_0) \neq 0$ | $\det \dfrac{\partial F}{\partial y}(x_0, y_0) \neq 0$ |
| **Entrega** | $f^{-1}$ local, $C^1$ | $g$ local com $F(x, g(x)) = 0$, $C^1$ |
| **Fórmula** | $Jg = (Jf)^{-1}$ | $Jg = -\left(\dfrac{\partial F}{\partial y}\right)^{-1}\dfrac{\partial F}{\partial x}$ |

> **Relação:** o TFImp é **consequência** do TFI. A ideia da prova é definir uma função auxiliar $\Phi(x, y) = (x, F(x, y))$ e aplicar o TFI a $\Phi$. Se $\det \frac{\partial F}{\partial y} \neq 0$, então $\det J\Phi \neq 0$, e a inversão local de $\Phi$ permite extrair $y = g(x)$.

---

#### de onde vem a fórmula de $Jg$ #calculo/proposição/formula-jg-implicita
^formula-jg-implicita

A fórmula sai da **regra da cadeia**. Sabemos que $F(x, g(x)) = 0$ para todo $x \in V$. Derivando ambos os lados em relação a $x$:

$$\frac{d}{dx}\big[F(x, g(x))\big] = 0$$

Pela regra da cadeia:

$$\frac{\partial F}{\partial x} + \frac{\partial F}{\partial y} \cdot Jg(x) = 0$$

Isolando $Jg$:

$$\frac{\partial F}{\partial y} \cdot Jg(x) = -\frac{\partial F}{\partial x}$$

$$\boxed{Jg(x) = -\left(\frac{\partial F}{\partial y}\right)^{-1} \cdot \frac{\partial F}{\partial x}}$$

> Note que precisamos de $\frac{\partial F}{\partial y}$ inversível para poder isolar $Jg$ — exatamente a hipótese do teorema.

---

#### exemplo 1: círculo $x^2 + y^2 = 1$ #calculo/exemplo/tfimplicita-circulo
^exemplo-circulo

Seja $F(x, y) = x^2 + y^2 - 1$. Queremos saber quando $F(x,y) = 0$ define $y = g(x)$ localmente.

##### passo 1: verificar $F \in C^1$

$F$ é polinomial, logo $C^\infty$. $\checkmark$

##### passo 2: escolher um ponto com $F(x_0, y_0) = 0$

Tomemos $(x_0, y_0) = (0, 1)$. De fato, $0^2 + 1^2 - 1 = 0$. $\checkmark$

##### passo 3: calcular $\frac{\partial F}{\partial y}$

$$\frac{\partial F}{\partial y}(x, y) = 2y$$

No ponto: $\frac{\partial F}{\partial y}(0, 1) = 2 \neq 0$. $\checkmark$

##### passo 4: conclusão

O TFImp garante que, numa vizinhança de $x_0 = 0$, existe uma única função $g \in C^1$ com $g(0) = 1$ e $F(x, g(x)) = 0$, ou seja:

$$x^2 + g(x)^2 = 1$$

(Neste caso sabemos que $g(x) = \sqrt{1 - x^2}$, mas o teorema garante existência **mesmo quando não há fórmula explícita**.)

##### passo 5: calcular $g'(x)$ pela fórmula

$$g'(x) = -\frac{\partial F / \partial x}{\partial F / \partial y} = -\frac{2x}{2y} = -\frac{x}{y}$$

No ponto $(0, 1)$: $g'(0) = 0$. (Coerente: o topo do círculo tem tangente horizontal.)

##### quando falha?

Nos pontos $(\pm 1, 0)$: $\frac{\partial F}{\partial y} = 2 \cdot 0 = 0$. O TFImp **não se aplica**.

Geometricamente, nesses pontos a tangente ao círculo é **vertical** — $y$ não pode ser escrito como função de $x$ (a curva "volta sobre si mesma").

> **Observação:** nos mesmos pontos, podemos trocar os papéis e perguntar se $x = h(y)$. Temos $\frac{\partial F}{\partial x}(1, 0) = 2 \neq 0$, então o TFImp garante que **$x$ é função de $y$** perto de $(1, 0)$. A escolha de quem é "variável livre" e quem é "variável dependente" é nossa.

---

#### exemplo 2: sistema de equações #calculo/exemplo/tfimplicita-sistema
^exemplo-sistema

Seja $F: \mathbb{R}^4 \to \mathbb{R}^2$ definida por:

$$F(x_1, x_2, y_1, y_2) = \begin{pmatrix} x_1 y_1 + x_2 y_2 - 1 \\ x_1^2 + y_1^2 + y_2^2 - 3 \end{pmatrix}$$

Queremos: perto do ponto $(x_1, x_2, y_1, y_2) = (1, 0, 1, 1)$, o sistema $F = 0$ define $(y_1, y_2)$ como função de $(x_1, x_2)$?

Aqui $n = 2$ (variáveis livres $x_1, x_2$) e $m = 2$ (variáveis a isolar $y_1, y_2$).

##### passo 1: verificar que $F(1, 0, 1, 1) = 0$

$$F(1, 0, 1, 1) = \begin{pmatrix} 1 \cdot 1 + 0 \cdot 1 - 1 \\ 1^2 + 1^2 + 1^2 - 3 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix} \checkmark$$

##### passo 2: calcular $\frac{\partial F}{\partial y}$

$$\frac{\partial F}{\partial (y_1, y_2)} = \begin{pmatrix} \dfrac{\partial F_1}{\partial y_1} & \dfrac{\partial F_1}{\partial y_2} \\[6pt] \dfrac{\partial F_2}{\partial y_1} & \dfrac{\partial F_2}{\partial y_2} \end{pmatrix} = \begin{pmatrix} x_1 & x_2 \\ 2y_1 & 2y_2 \end{pmatrix}$$

No ponto $(1, 0, 1, 1)$:

$$\frac{\partial F}{\partial y}(1, 0, 1, 1) = \begin{pmatrix} 1 & 0 \\ 2 & 2 \end{pmatrix}$$

$$\det = 1 \cdot 2 - 0 \cdot 2 = 2 \neq 0 \checkmark$$

##### passo 3: conclusão

O TFImp garante: existem vizinhanças de $(x_1, x_2) = (1, 0)$ e de $(y_1, y_2) = (1, 1)$ tais que o sistema define uma única função $g: \mathbb{R}^2 \to \mathbb{R}^2$ de classe $C^1$ com:

$$g(1, 0) = (1, 1) \quad \text{e} \quad F(x_1, x_2, g(x_1, x_2)) = 0$$

##### passo 4: calcular $Jg$

Precisamos de $\frac{\partial F}{\partial x}$:

$$\frac{\partial F}{\partial (x_1, x_2)} = \begin{pmatrix} y_1 & y_2 \\ 2x_1 & 0 \end{pmatrix}$$

No ponto:

$$\frac{\partial F}{\partial x}(1, 0, 1, 1) = \begin{pmatrix} 1 & 1 \\ 2 & 0 \end{pmatrix}$$

Pela fórmula:

$$Jg(1, 0) = -\begin{pmatrix} 1 & 0 \\ 2 & 2 \end{pmatrix}^{-1} \begin{pmatrix} 1 & 1 \\ 2 & 0 \end{pmatrix} = -\frac{1}{2}\begin{pmatrix} 2 & 0 \\ -2 & 1 \end{pmatrix}\begin{pmatrix} 1 & 1 \\ 2 & 0 \end{pmatrix}$$

$$= -\frac{1}{2}\begin{pmatrix} 2 & 2 \\ 0 & -2 \end{pmatrix} = \begin{pmatrix} -1 & -1 \\ 0 & 1 \end{pmatrix}$$

> **Interpretação:** sem resolver o sistema, sabemos por exemplo que $\frac{\partial y_1}{\partial x_1} = -1$ e $\frac{\partial y_2}{\partial x_2} = 1$ no ponto. Se $x_1$ aumenta um pouco, $y_1$ diminui na mesma proporção.

---

#### contexto histórico #calculo/contexto/tfimplicita-historia
^contexto-historico-tfimplicita

O Teorema da Função Implícita tem origem no trabalho de **Augustin-Louis Cauchy** (década de 1830), que provou versões para funções analíticas. A formulação rigorosa em $\mathbb{R}^n$ é atribuída a **Ulisse Dini** (por volta de 1877–1878), que demonstrou o resultado com hipóteses de $C^1$ — o mesmo matemático por trás do [[aula-10-teorema-da-funcao-inversa#^contexto-historico-tfi|TFI]]. Em muitos textos italianos e franceses, o TFImp é chamado de **Teorema de Dini**.

A motivação histórica veio da **geometria algébrica** e da **mecânica analítica**: equações como $F(x, y) = 0$ descrevem curvas no plano, e os matemáticos precisavam saber quando essas curvas podiam ser localmente parametrizadas — ou seja, quando $y$ podia ser escrito como função de $x$. **Lagrange** e **Euler** já usavam essa ideia implicitamente no século XVIII ao estudar vínculos mecânicos, mas sem a formalização que Dini trouxe.

> **Curiosidade:** o TFI e o TFImp são logicamente equivalentes — cada um pode ser deduzido do outro. Dini os provou essencialmente juntos.

---

#### aplicação: equilíbrio econômico (oferta e demanda) #calculo/exemplo/aplicacao-economia
^aplicacao-economia

Em economia, o **preço de equilíbrio** $p$ e a **quantidade de equilíbrio** $q$ de um mercado são determinados pela igualdade entre oferta e demanda:

$$F(\alpha, \beta, p, q) = \begin{pmatrix} D(\alpha, p) - q \\ S(\beta, p) - q \end{pmatrix} = 0$$

onde:
- $D(\alpha, p)$ = demanda (depende do preço $p$ e de um parâmetro externo $\alpha$, como renda do consumidor)
- $S(\beta, p)$ = oferta (depende do preço $p$ e de um parâmetro $\beta$, como custo de produção)

O sistema $F = 0$ diz que $q = D(\alpha, p) = S(\beta, p)$ — oferta iguala demanda.

##### o que o TFImp garante

Se $\det \frac{\partial F}{\partial (p, q)} \neq 0$ num ponto de equilíbrio, então **localmente** existem funções $C^1$:

$$p = p(\alpha, \beta), \qquad q = q(\alpha, \beta)$$

Ou seja, preço e quantidade de equilíbrio dependem suavemente dos parâmetros externos. Além disso, a fórmula do TFImp dá:

$$\frac{\partial p}{\partial \alpha}, \quad \frac{\partial p}{\partial \beta}, \quad \frac{\partial q}{\partial \alpha}, \quad \frac{\partial q}{\partial \beta}$$

sem precisar resolver o sistema explicitamente.

> **Na prática:** isso é a base da **estática comparativa** em microeconomia — analisar como mudanças em parâmetros (renda, impostos, custos) afetam o equilíbrio, usando apenas derivadas parciais do sistema. Quando economistas escrevem "$\frac{\partial p}{\partial \alpha} > 0$" (aumento de renda aumenta o preço), a **existência** dessa derivada é garantida pelo TFImp.

> **Quando falha:** se $\det \frac{\partial F}{\partial (p,q)} = 0$, estamos numa **bifurcação** — pequenas mudanças nos parâmetros podem causar saltos descontínuos no equilíbrio (ex: colapso de mercado, transição de fase). O TFImp prevê exatamente onde a análise linear deixa de funcionar.

---

#### aplicação: termodinâmica (equação de estado) #calculo/exemplo/aplicacao-termodinamica
^aplicacao-termodinamica

A equação de estado de um gás relaciona pressão $P$, volume $V$ e temperatura $T$. Para um **gás ideal**:

$$F(P, V, T) = PV - nRT = 0$$

Aqui é fácil isolar qualquer variável ($P = \frac{nRT}{V}$, etc.). Mas para gases reais, a equação de **van der Waals** é:

$$F(P, V, T) = \left(P + \frac{a}{V^2}\right)(V - b) - RT = 0$$

onde $a, b$ são constantes do gás. Isolar $V = g(P, T)$ explicitamente é **impossível** (equação cúbica em $V$).

##### como o TFImp ajuda

Temos $\frac{\partial F}{\partial V} = -\frac{2a}{V^3}(V - b) + P + \frac{a}{V^2}$. Se $\frac{\partial F}{\partial V} \neq 0$ num ponto $(P_0, V_0, T_0)$ com $F = 0$, o TFImp garante:

- Existe localmente $V = g(P, T)$ de classe $C^1$
- Podemos calcular como o volume responde a mudanças de pressão e temperatura:

$$\frac{\partial V}{\partial T} = -\frac{\partial F / \partial T}{\partial F / \partial V} = \frac{R}{\frac{\partial F}{\partial V}}$$

> **Na prática:** coeficientes termodinâmicos como o **coeficiente de dilatação** $\alpha = \frac{1}{V}\frac{\partial V}{\partial T}$ e a **compressibilidade** $\kappa = -\frac{1}{V}\frac{\partial V}{\partial P}$ são calculados exatamente assim — derivando implicitamente a equação de estado, sem precisar isolá-la.

> **Quando falha:** no **ponto crítico** do gás ($P_c, V_c, T_c$), temos $\frac{\partial F}{\partial V} = 0$ — o TFImp não se aplica. Fisicamente, isso corresponde à transição líquido-gás, onde $V$ deixa de ser função suave de $(P, T)$ e ocorre descontinuidade (mudança de fase).

---
