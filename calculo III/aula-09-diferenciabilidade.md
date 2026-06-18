#### recordação: diferenciabilidade e jacobiana da inversa #calculo/proposição/jacobiana-inversa
^recordacao-jacobiana-inversa

O professor provou um teorema que relaciona diferenciabilidade de uma função com a de sua inversa:

> **Teorema.** Sejam $f: U \to V$ diferenciável em $x \in U$ com $Jf(x)$ inversível, e $g = f^{-1}$ contínua em $y = f(x)$. Então:
>
> $g$ é diferenciável em $y$ e $Jg(y) = \big(Jf(x)\big)^{-1}$

---

#### teorema (difícil): bijeção contínua entre abertos #calculo/teorema/bijecao-abertos
^teorema-bijecao-abertos

> **Teorema.** Seja $f: U \to V$ bijetora e contínua, com $U \subset \mathbb{R}^n$, $V \subset \mathbb{R}^n$ abertos. Então $m = n$ e $f^{-1}: V \to U$ é contínua.

##### conclusão (combinando os dois resultados)

> **Teorema.** Seja $f: U \to V$ bijetora e contínua, com $U \subset \mathbb{R}^n$, $V \subset \mathbb{R}^n$ abertos. Se $f$ é diferenciável em $x \in U$ e $Jf(x)$ é inversível, então $g = f^{-1}$ é diferenciável em $y = f(x)$ e:
>
> $$Jg(y) = \big(Jf(x)\big)^{-1}$$

---

#### o problema da injetividade em várias variáveis
^problema-injetividade

Para funções de uma variável, conseguimos verificar se $f$ é injetora em todo o domínio (por exemplo, checando se $f' > 0$). Para funções de várias variáveis, **não conseguimos** garantir injetividade global com facilidade.

A ideia é: **perto do ponto** onde calculamos a jacobiana e ela é inversível, a função é localmente injetora. Isso motiva o **teorema da função inversa**.

---

#### funções de classe $C^1$ #calculo/definição/classe-c1
^definicao-classe-c1

> **Definição.** Uma função $f: U \subset \mathbb{R}^n \to \mathbb{R}^m$ é de **classe $C^1$** (ou $f \in C^1(U)$) quando todas as derivadas parciais $\frac{\partial f_i}{\partial x_j}$ existem e são **contínuas** em $U$.

---

#### teorema da função inversa #calculo/teorema/funcao-inversa
^teorema-funcao-inversa

> **Teorema da Função Inversa.** Seja $f: U \subset \mathbb{R}^n \to \mathbb{R}^n$ de classe $C^1$, com $U$ aberto. Se $Jf(x_0)$ é inversível (ou seja, $\det Jf(x_0) \neq 0$), então:
>
> 1. Existe uma vizinhança aberta $V$ de $x_0$ tal que $f\big|_V: V \to f(V)$ é **bijetora**
> 2. $f(V)$ é aberto
> 3. A inversa $g = (f\big|_V)^{-1}: f(V) \to V$ é de classe $C^1$
> 4. $Jg(y) = \big(Jf(x)\big)^{-1}$ para $y = f(x)$

Em outras palavras: se a jacobiana é inversível num ponto, então $f$ é **localmente inversível** numa vizinhança desse ponto, mesmo que não seja globalmente injetora.

> O diagrama do teorema: temos um aberto $U$ com um ponto $x$, e a função $f$ leva uma vizinhança $V \subset U$ de $x$ bijetivamente em $f(V)$, uma vizinhança aberta de $y = f(x)$.

---

#### exemplo: coordenadas polares #calculo/exemplo/coordenadas-polares
^exemplo-coordenadas-polares

Considere $f: \mathbb{R}^2 \to \mathbb{R}^2$ definida por:

$$f(\rho, \theta) = (\rho \cos\theta,\; \rho \sin\theta)$$

##### $f$ não é injetora (globalmente)

A função $f$ **não é injetora** em todo $\mathbb{R}^2$:

- $f(\rho, \theta) = f(\rho, \theta + 2k\pi)$ para todo $k \in \mathbb{Z}$ (periodicidade em $\theta$)
- $f(\rho, \theta) = f(-\rho, \theta + \pi)$ (trocar sinal de $\rho$ e somar $\pi$)

##### jacobiana de $f$

$$Jf(\rho, \theta) = \begin{pmatrix} \cos\theta & -\rho\sin\theta \\ \sin\theta & \rho\cos\theta \end{pmatrix}$$

$$\det\big(Jf(\rho, \theta)\big) = \rho\cos^2\theta + \rho\sin^2\theta = \rho$$

Logo $\det Jf \neq 0$ quando $\rho \neq 0$.

##### $f$ é $C^1$ e localmente inversível

Como $f$ é $C^1$ (as derivadas parciais são funções trigonométricas, contínuas), e $\det Jf(\rho, \theta) = \rho \neq 0$ para $\rho \neq 0$, o [[aula-09-diferenciabilidade#^teorema-funcao-inversa|teorema da função inversa]] garante que $f$ é **localmente inversível** em qualquer ponto com $\rho \neq 0$.

Por exemplo, restringindo ao aberto $U = \{(\rho, \theta) : \rho > 0,\; 0 < \theta < \pi\}$, a função $f\big|_U$ é injetora.

##### jacobiana da inversa

Seja $g = (f\big|_U)^{-1}: f(U) \to \mathbb{R}^2$. Pelo teorema:

$$Jg(x, y) = \big(Jf(\rho, \theta)\big)^{-1} = \begin{pmatrix} \cos\theta & -\rho\sin\theta \\ \sin\theta & \rho\cos\theta \end{pmatrix}^{-1}$$

Invertendo (usando que $\det = \rho$), onde $(x, y) = f(\rho, \theta)$:

$$Jg(x, y) = \frac{1}{\rho} \begin{pmatrix} \rho\cos\theta & \rho\sin\theta \\ -\sin\theta & \cos\theta \end{pmatrix} = \begin{pmatrix} \cos\theta & \sin\theta \\ -\dfrac{\sin\theta}{\rho} & \dfrac{\cos\theta}{\rho} \end{pmatrix}$$
