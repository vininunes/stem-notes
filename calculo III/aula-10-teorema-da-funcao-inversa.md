#### o teorema da função inversa como resultado central #calculo/teorema/funcao-inversa-central
^teorema-funcao-inversa-central

O professor destacou que o [[aula-09-diferenciabilidade#^teorema-funcao-inversa|Teorema da Função Inversa]] é o resultado principal e **substitui** vários teoremas menores vistos nas aulas anteriores. Na prática, podemos usar diretamente o TFI em vez desses resultados parciais:

| Resultado anterior | Por que o TFI torna dispensável |
|---|---|
| [[aula-09-diferenciabilidade#^recordacao-jacobiana-inversa\|Jacobiana da inversa]] (aula 9) | Assume que $g = f^{-1}$ é contínua e $f$ é bijetora. O TFI **já garante** continuidade (e $C^1$) da inversa local |
| [[aula-09-diferenciabilidade#^teorema-bijecao-abertos\|Bijeção contínua entre abertos]] (aula 9) | Usado para garantir que $f^{-1}$ é contínua. O TFI inclui isso como consequência |
| [[aula-09-diferenciabilidade#^problema-injetividade\|Injetividade global]] (aula 9) | O TFI não exige injetividade global — basta $\det Jf(x_0) \neq 0$ para obter inversibilidade **local** |

> **Resumo:** para usar os resultados anteriores, precisávamos verificar separadamente que $f$ era bijetora, que $f^{-1}$ era contínua, e que $Jf$ era inversível. O TFI exige apenas que $f \in C^1$ e $\det Jf(x_0) \neq 0$, e **entrega tudo de uma vez**: bijetividade local, abertura da imagem, $g \in C^1$, e $Jg(y) = (Jf(x))^{-1}$.

---

#### enunciado: Teorema da Função Inversa #calculo/teorema/funcao-inversa
^enunciado-tfi

> **Teorema da Função Inversa.** Seja $f: U \subset \mathbb{R}^n \to \mathbb{R}^n$ de classe $C^1$, com $U$ aberto. Seja $x_0 \in U$ tal que $\det Jf(x_0) \neq 0$. Então:
>
> 1. Existem abertos $V \subset U$ com $x_0 \in V$ e $W \subset \mathbb{R}^n$ com $f(x_0) \in W$ tais que $f\big|_V: V \to W$ é **bijetora**
> 2. A inversa $g = (f\big|_V)^{-1}: W \to V$ é de **classe $C^1$**
> 3. Para todo $y = f(x) \in W$:
>
> $$Jg(y) = \big(Jf(x)\big)^{-1}$$

> **Hipóteses (checklist):**
> - $f$ definida num aberto $U \subset \mathbb{R}^n$ com valores em $\mathbb{R}^n$ (mesma dimensão no domínio e contradomínio)
> - $f \in C^1(U)$ (derivadas parciais existem e são contínuas)
> - $\det Jf(x_0) \neq 0$ no ponto de interesse

> **O que o teorema entrega:**
> - Inversibilidade **local** (não precisa verificar injetividade global)
> - A inversa é automaticamente $C^1$ (não precisa provar continuidade separadamente)
> - Fórmula explícita para a jacobiana da inversa

---

#### exemplo: $f(x, y) = (e^x \cos y,\; e^x \sin y)$ #calculo/exemplo/tfi-exponencial
^exemplo-tfi-exponencial

Considere $f: \mathbb{R}^2 \to \mathbb{R}^2$ definida por:

$$f(x, y) = (e^x \cos y,\; e^x \sin y)$$

##### passo 1: verificar que $f \in C^1$

As componentes $f_1 = e^x \cos y$ e $f_2 = e^x \sin y$ são composições de exponenciais e trigonométricas, portanto $C^\infty$. Em particular, $f \in C^1$. $\checkmark$

##### passo 2: calcular a jacobiana

$$Jf(x, y) = \begin{pmatrix} \dfrac{\partial f_1}{\partial x} & \dfrac{\partial f_1}{\partial y} \\[6pt] \dfrac{\partial f_2}{\partial x} & \dfrac{\partial f_2}{\partial y} \end{pmatrix} = \begin{pmatrix} e^x \cos y & -e^x \sin y \\ e^x \sin y & e^x \cos y \end{pmatrix}$$

##### passo 3: calcular o determinante

$$\det Jf(x, y) = e^x \cos y \cdot e^x \cos y - (-e^x \sin y) \cdot e^x \sin y$$

$$= e^{2x}\cos^2 y + e^{2x}\sin^2 y = e^{2x} > 0 \quad \forall\, (x, y) \in \mathbb{R}^2$$

O determinante **nunca se anula**, então o TFI se aplica em **qualquer** ponto $(x_0, y_0)$. $\checkmark$

##### passo 4: aplicar o TFI

Para qualquer $(x_0, y_0)$, existem vizinhanças abertas $V$ de $(x_0, y_0)$ e $W$ de $f(x_0, y_0)$ tais que $f\big|_V: V \to W$ é bijetora com inversa $g \in C^1$.

##### passo 5: calcular $Jg$

$$Jg(u, v) = \big(Jf(x, y)\big)^{-1} = \frac{1}{e^{2x}} \begin{pmatrix} e^x \cos y & e^x \sin y \\ -e^x \sin y & e^x \cos y \end{pmatrix} = \begin{pmatrix} \dfrac{\cos y}{e^x} & \dfrac{\sin y}{e^x} \\[6pt] -\dfrac{\sin y}{e^x} & \dfrac{\cos y}{e^x} \end{pmatrix}$$

onde $(u, v) = f(x, y) = (e^x \cos y,\; e^x \sin y)$.

> **Observação:** note que $u^2 + v^2 = e^{2x}$, então $e^x = \sqrt{u^2 + v^2}$. Além disso, $\cos y = \frac{u}{e^x} = \frac{u}{\sqrt{u^2+v^2}}$ e $\sin y = \frac{v}{\sqrt{u^2+v^2}}$. Substituindo, podemos escrever $Jg$ puramente em termos de $(u,v)$:
>
> $$Jg(u,v) = \frac{1}{u^2+v^2}\begin{pmatrix} u & v \\ -v & u \end{pmatrix}$$
>
> Isso confirma que $g$ está bem definida desde que $(u,v) \neq (0,0)$, ou seja, fora da origem — coerente com $e^x > 0$.

> **Por que este exemplo é esclarecedor?** A função $f$ **não é globalmente injetora** (pois $f(x, y) = f(x, y + 2\pi)$), mas o TFI garante inversibilidade local em qualquer ponto sem precisar verificar isso. Além disso, o determinante nunca se anula, então o teorema se aplica em todo o domínio — cada ponto tem sua própria vizinhança onde $f$ é invertível.

---

#### contexto histórico #calculo/contexto/tfi-historia
^contexto-historico-tfi

O Teorema da Função Inversa foi desenvolvido ao longo do século XIX, com contribuições centrais de **Augustin-Louis Cauchy** (que provou versões para funções analíticas complexas) e **Ulisse Dini** (que formulou e provou a versão geral para $\mathbb{R}^n$ com hipóteses de $C^1$, por volta de 1870). Por isso, em muitos textos europeus, o teorema aparece como **Teorema de Dini**.

A motivação original era um problema prático recorrente na matemática e na física: dada uma relação entre variáveis expressa por equações (não necessariamente resolúveis explicitamente), **quando podemos "inverter" essas equações** e tratar algumas variáveis como funções das outras?

---

#### aplicação: robótica e cinemática inversa #calculo/exemplo/aplicacao-robotica
^aplicacao-robotica

Um braço robótico com duas juntas rotativas tem ângulos $(\theta_1, \theta_2)$ que controlam a posição $(x, y)$ da ponta do braço. A relação é dada pela **cinemática direta**:

$$f(\theta_1, \theta_2) = \begin{pmatrix} l_1\cos\theta_1 + l_2\cos(\theta_1 + \theta_2) \\ l_1\sin\theta_1 + l_2\sin(\theta_1 + \theta_2) \end{pmatrix} = \begin{pmatrix} x \\ y \end{pmatrix}$$

onde $l_1, l_2$ são os comprimentos dos elos.

##### o problema: cinemática inversa

O engenheiro quer o contrário: dado um ponto-alvo $(x_0, y_0)$, **quais ângulos** $(\theta_1, \theta_2)$ levam a ponta até lá? Isso é a **cinemática inversa** — ou seja, calcular $f^{-1}$.

O problema é que:
- $f$ **não é globalmente injetora** (diferentes configurações de ângulos podem alcançar o mesmo ponto — "cotovelo para cima" vs. "cotovelo para baixo")
- **Não existe fórmula fechada** simples para $f^{-1}$ em geral

##### como o TFI resolve

A jacobiana de $f$ é:

$$Jf(\theta_1, \theta_2) = \begin{pmatrix} -l_1\sin\theta_1 - l_2\sin(\theta_1+\theta_2) & -l_2\sin(\theta_1+\theta_2) \\ l_1\cos\theta_1 + l_2\cos(\theta_1+\theta_2) & l_2\cos(\theta_1+\theta_2) \end{pmatrix}$$

$$\det Jf = l_1 l_2 \sin\theta_2$$

O TFI garante: se $\sin\theta_2 \neq 0$ (ou seja, o braço não está totalmente esticado nem dobrado sobre si mesmo), então **localmente** existe uma função $g(x,y) = (\theta_1, \theta_2)$ de classe $C^1$ que resolve o problema. Além disso:

$$Jg(x,y) = \big(Jf(\theta_1, \theta_2)\big)^{-1}$$

Isso permite ao controlador do robô calcular como **pequenas mudanças** na posição-alvo se traduzem em ajustes nos ângulos, sem precisar resolver o sistema inteiro a cada instante.

> **Na prática:** controladores robóticos usam exatamente a jacobiana inversa para fazer controle em tempo real — a cada ciclo, multiplicam o erro de posição $\Delta(x,y)$ pela jacobiana inversa para obter a correção $\Delta(\theta_1, \theta_2)$. O TFI é o que **garante** que essa estratégia funciona (desde que $\sin\theta_2 \neq 0$).

> **Quando falha:** $\det Jf = 0$ quando $\theta_2 = 0$ ou $\theta_2 = \pi$ — são as chamadas **singularidades** do manipulador. Fisicamente, o braço está completamente esticado ou dobrado, e perde um grau de liberdade. O TFI prevê exatamente isso: nessas configurações, a inversão local não é garantida.

---

#### difeomorfismo #calculo/definição/difeomorfismo
^definicao-difeomorfismo

> **Definição.** Sejam $U, V \subset \mathbb{R}^n$ abertos. Uma função $f: U \to V$ é um **difeomorfismo** quando:
>
> 1. $f$ é **bijetora**
> 2. $f$ é de classe $C^1$
> 3. $f^{-1}: V \to U$ é de classe $C^1$

Em palavras: $f$ é uma bijeção "suave" com inversa também "suave". Difeomorfismo é para o cálculo diferencial o que **isomorfismo** é para álgebra linear — uma equivalência que preserva toda a estrutura relevante (neste caso, a estrutura diferenciável).

> Se $f$ e $f^{-1}$ são de classe $C^k$ (não apenas $C^1$), dizemos que $f$ é um **difeomorfismo de classe $C^k$**.

##### difeomorfismo local

> **Definição.** Uma função $f: U \to \mathbb{R}^n$ é um **difeomorfismo local** em $x_0 \in U$ quando existem vizinhanças abertas $V$ de $x_0$ e $W$ de $f(x_0)$ tais que $f\big|_V: V \to W$ é um difeomorfismo.

---

#### relação entre difeomorfismo e o TFI #calculo/proposição/tfi-difeomorfismo
^relacao-tfi-difeomorfismo

O Teorema da Função Inversa pode ser reformulado de maneira mais elegante usando a linguagem de difeomorfismo:

> **TFI (reformulação).** Seja $f: U \subset \mathbb{R}^n \to \mathbb{R}^n$ de classe $C^1$ com $\det Jf(x_0) \neq 0$. Então $f$ é um **difeomorfismo local** em $x_0$.

Essa é exatamente a mesma afirmação do [[aula-10-teorema-da-funcao-inversa#^enunciado-tfi|enunciado anterior]], mas condensada: o TFI diz que a condição $\det Jf(x_0) \neq 0$ é **suficiente** para garantir que $f$ se comporta como um difeomorfismo numa vizinhança do ponto.

##### por que difeomorfismo importa

| Conceito | Preserva | Exemplo |
|---|---|---|
| Homeomorfismo ($f$ e $f^{-1}$ contínuas) | topologia (abertos, conexidade) | dobrar uma folha de papel |
| Difeomorfismo ($f$ e $f^{-1}$ são $C^1$) | topologia **e** estrutura diferencial (tangentes, jacobianas) | mudança de coordenadas |
| Isomorfismo linear | estrutura de espaço vetorial | mudança de base |

O difeomorfismo é a noção certa de "dois abertos são essencialmente iguais do ponto de vista do cálculo". Se $f: U \to V$ é um difeomorfismo, tudo que sabemos fazer em $U$ (derivar, integrar, resolver EDOs) pode ser **transportado** para $V$ e vice-versa.

> **Conexão com mudança de coordenadas:** quando passamos de coordenadas cartesianas $(x, y)$ para polares $(\rho, \theta)$, estamos usando um difeomorfismo (local). O TFI garante que essa mudança é válida sempre que $\rho \neq 0$ — exatamente onde $\det Jf = \rho \neq 0$. É por isso que coordenadas polares "falham" na origem.

---

#### exemplo: $f(x, y) = (x^2 - y^2,\; 2xy)$ #calculo/exemplo/tfi-quadrado-complexo
^exemplo-quadrado-complexo

Considere $f: \mathbb{R}^2 \to \mathbb{R}^2$ definida por:

$$f(x, y) = (x^2 - y^2,\; 2xy)$$

> **Interpretação:** essa é a função "elevar ao quadrado" nos números complexos. Se $z = x + iy$, então $z^2 = (x^2 - y^2) + i(2xy)$, ou seja, $f$ corresponde a $z \mapsto z^2$.

##### jacobiana e determinante

$$Jf(x, y) = \begin{pmatrix} 2x & -2y \\ 2y & 2x \end{pmatrix}$$

$$\det Jf(x, y) = (2x)(2x) - (-2y)(2y) = 4x^2 + 4y^2 = 4(x^2 + y^2)$$

##### caso 1: $(x, y) \neq (0, 0)$ — TFI se aplica

Se $(x, y) \neq (0, 0)$, então $x^2 + y^2 > 0$, logo $\det Jf = 4(x^2 + y^2) > 0$.

Como $f \in C^1$ (componentes são polinômios) e $\det Jf \neq 0$, o TFI garante que $f$ é um **difeomorfismo local** em qualquer ponto fora da origem.

A jacobiana da inversa é:

$$Jg(u, v) = (Jf(x, y))^{-1} = \frac{1}{4(x^2 + y^2)} \begin{pmatrix} 2x & 2y \\ -2y & 2x \end{pmatrix} = \frac{1}{2(x^2+y^2)} \begin{pmatrix} x & y \\ -y & x \end{pmatrix}$$

##### caso 2: $(x, y) = (0, 0)$ — TFI não se aplica

Na origem, $\det Jf(0, 0) = 4(0 + 0) = 0$. O TFI **não garante** inversibilidade local.

E de fato, $f$ **não é localmente injetora** na origem. Para ver isso, basta notar que:

$$f(x, y) = f(-x, -y) \quad \forall\, (x, y)$$

pois $((-x)^2 - (-y)^2,\; 2(-x)(-y)) = (x^2 - y^2,\; 2xy)$.

Então qualquer vizinhança de $(0,0)$ contém pares distintos $(x,y)$ e $(-x,-y)$ com a mesma imagem — $f$ é $2$ para $1$ perto da origem.

> **Geometricamente:** $z \mapsto z^2$ "dobra" o plano — ângulos são duplicados e módulos são elevados ao quadrado. Na origem ($z = 0$), essa "dobra" colapsa direções distintas numa só, destruindo a injetividade.

##### resumo dos casos

| Ponto | $\det Jf$ | TFI aplica? | $f$ localmente injetora? |
|---|---|---|---|
| $(x,y) \neq (0,0)$ | $4(x^2+y^2) > 0$ | sim | sim (difeomorfismo local) |
| $(0,0)$ | $0$ | não | não ($f(x,y) = f(-x,-y)$) |

> **Observação importante:** o TFI dá condição **suficiente**, não necessária. Quando $\det Jf = 0$, o teorema não diz nada — a função **pode ou não** ser localmente inversível. Neste exemplo, de fato não é. Mas existem funções com $\det Jf = 0$ num ponto que ainda são localmente injetoras (ex: $f(x) = x^3$ em $\mathbb{R}$, com $f'(0) = 0$ mas $f$ injetora).

---

