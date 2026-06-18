#### recordação: função inversa #calculo/definição/função-inversa
^recordacao-funcao-inversa

Uma função $f: A \to B$ possui **inversa** $f^{-1}: B \to A$ quando $f$ é [[aula-01-funções#^tipos-de-funcoes|bijetora]]. Nesse caso:

$$f^{-1}(f(x)) = x \quad \text{e} \quad f(f^{-1}(y)) = y$$

O problema: muitas funções **não são bijetoras** em seus domínios naturais. A estratégia é **restringir o domínio** para forçar injetividade.

---

#### o problema da inversão: funções não injetoras
^problema-inversao

A função $f(x) = x^2$ com $f: \mathbb{R} \to \mathbb{R}$ **não é injetora**: $f(-2) = f(2) = 4$. Então $f^{-1}(4)$ seria... $2$ ou $-2$? Não está bem definido.

A solução é **escolher um ramo**: restringir o domínio a um subconjunto onde $f$ seja injetora, e definir a inversa nesse ramo.

| Função | Domínio natural | Problema |
|---|---|---|
| $x^2$ | $\mathbb{R}$ | simétrica: $f(x) = f(-x)$ |
| $\sin(x)$ | $\mathbb{R}$ | periódica: $f(x) = f(x + 2\pi)$ |
| $\cos(x)$ | $\mathbb{R}$ | periódica e simétrica |
| $\tan(x)$ | $\mathbb{R} \setminus \{\frac{\pi}{2} + k\pi\}$ | periódica |

---

#### convenções para as inversas clássicas
^convencoes-inversas

Para cada função não injetora, existe uma **convenção padrão** de restrição de domínio que define a inversa.

##### raiz quadrada (inversa de $x^2$)

Restringimos $f(x) = x^2$ ao domínio $[0, +\infty)$, onde é injetora e crescente.

$$\sqrt{\cdot} : [0, +\infty) \to [0, +\infty), \quad \sqrt{x^2} = |x| = x \text{ (para } x \geq 0\text{)}$$

> **Convenção:** $\sqrt{a}$ é sempre $\geq 0$. A equação $x^2 = a$ tem duas soluções $\pm\sqrt{a}$, mas $\sqrt{a}$ denota apenas a positiva.

##### arco seno (inversa de $\sin$) #calculo/definição/arcsen

Restringimos $\sin$ ao intervalo $\left[-\frac{\pi}{2}, \frac{\pi}{2}\right]$, onde é injetora (estritamente crescente):

$$\arcsin: [-1, 1] \to \left[-\frac{\pi}{2}, \frac{\pi}{2}\right]$$

$$\arcsin(y) = x \iff \sin(x) = y \;\text{ com }\; x \in \left[-\frac{\pi}{2}, \frac{\pi}{2}\right]$$

**Exemplos:**
- $\arcsin(0) = 0$
- $\arcsin(1) = \frac{\pi}{2}$
- $\arcsin\!\left(\frac{1}{2}\right) = \frac{\pi}{6}$

##### arco cosseno (inversa de $\cos$) #calculo/definição/arccos

Restringimos $\cos$ ao intervalo $[0, \pi]$, onde é injetora (estritamente decrescente):

$$\arccos: [-1, 1] \to [0, \pi]$$

$$\arccos(y) = x \iff \cos(x) = y \;\text{ com }\; x \in [0, \pi]$$

**Exemplos:**
- $\arccos(1) = 0$
- $\arccos(0) = \frac{\pi}{2}$
- $\arccos(-1) = \pi$

> **Relação útil:** $\arcsin(y) + \arccos(y) = \frac{\pi}{2}$ para todo $y \in [-1, 1]$.

##### arco tangente (inversa de $\tan$) #calculo/definição/arctan

Restringimos $\tan$ ao intervalo $\left(-\frac{\pi}{2}, \frac{\pi}{2}\right)$, onde é injetora (estritamente crescente):

$$\arctan: \mathbb{R} \to \left(-\frac{\pi}{2}, \frac{\pi}{2}\right)$$

$$\arctan(y) = x \iff \tan(x) = y \;\text{ com }\; x \in \left(-\frac{\pi}{2}, \frac{\pi}{2}\right)$$

**Exemplos:**
- $\arctan(0) = 0$
- $\arctan(1) = \frac{\pi}{4}$
- $\arctan(y) \to \pm\frac{\pi}{2}$ quando $y \to \pm\infty$

##### logaritmo (inversa de $e^x$) #calculo/definição/logaritmo

A exponencial $e^x: \mathbb{R} \to (0, +\infty)$ já é bijetora (estritamente crescente), então não precisa de restrição:

$$\ln: (0, +\infty) \to \mathbb{R}$$

$$\ln(y) = x \iff e^x = y$$

##### resumo das convenções

| Função $f$ | Domínio restrito | Inversa $f^{-1}$ | Domínio de $f^{-1}$ | Imagem de $f^{-1}$ |
|---|---|---|---|---|
| $x^2$ | $[0, +\infty)$ | $\sqrt{x}$ | $[0, +\infty)$ | $[0, +\infty)$ |
| $\sin(x)$ | $\left[-\frac{\pi}{2}, \frac{\pi}{2}\right]$ | $\arcsin(x)$ | $[-1, 1]$ | $\left[-\frac{\pi}{2}, \frac{\pi}{2}\right]$ |
| $\cos(x)$ | $[0, \pi]$ | $\arccos(x)$ | $[-1, 1]$ | $[0, \pi]$ |
| $\tan(x)$ | $\left(-\frac{\pi}{2}, \frac{\pi}{2}\right)$ | $\arctan(x)$ | $\mathbb{R}$ | $\left(-\frac{\pi}{2}, \frac{\pi}{2}\right)$ |
| $e^x$ | $\mathbb{R}$ | $\ln(x)$ | $(0, +\infty)$ | $\mathbb{R}$ |

> **Princípio geral:** a escolha do ramo é uma **convenção** — poderíamos restringir $\sin$ a $\left[\frac{\pi}{2}, \frac{3\pi}{2}\right]$ e teríamos outra inversa. A convenção padrão escolhe o ramo que contém $0$ (ou o mais "simples") e preserva continuidade.

---

#### derivada da função inversa #calculo/proposição/derivada-inversa
^derivada-funcao-inversa

##### exemplo motivador: $f(x) = x^5 + x$

Considere $f: \mathbb{R} \to \mathbb{R}$, $f(x) = x^5 + x$.

$$f'(x) = 5x^4 + 1 > 0, \quad \forall \, x \in \mathbb{R}$$

Logo $f$ é **estritamente crescente** $\Rightarrow$ $f$ é **injetora**.

Além disso, $f$ é contínua e:

$$\lim_{x \to +\infty} f(x) = +\infty, \qquad \lim_{x \to -\infty} f(x) = -\infty$$

Portanto $\text{Im}\, f = \mathbb{R}$, e $f$ é **bijetora**.

Existe então a inversa $g = f^{-1}: \mathbb{R} \to \mathbb{R}$. Mas qual é a fórmula de $g$? Para calcular $g(y)$ precisaríamos resolver:

$$x^5 + x = y$$

Essa equação **não tem solução em forma fechada** — não existe fórmula algébrica para isolar $x$. Sabemos que $g(y)$ existe (unicidade garantida pela bijetividade), mas não conseguimos escrevê-la explicitamente.

> **Pergunta:** mesmo sem conhecer a fórmula de $g$, será que conseguimos calcular $g'(y)$?

##### teorema (derivada da função inversa) #calculo/teorema/derivada-inversa
^teorema-derivada-inversa

> **Teorema.** Seja $f: I \subset \mathbb{R} \to \mathbb{R}$, com $I$ intervalo, **injetora**. Então a imagem de $f$ é um intervalo $J \subset \mathbb{R}$, e existe a inversa $g = f^{-1}: J \to \mathbb{R}$.
>
> Se $f$ é derivável no ponto $x \in I$ e $f'(x) \neq 0$, então $g$ é derivável no ponto $y = f(x)$ e:
>
> $$g'(y) = \frac{1}{f'(x)}$$

Em outras palavras: a derivada da inversa é o **recíproco** da derivada da função original, avaliada no ponto correspondente.

> Note que $y = f(x) \iff x = g(y)$, então podemos reescrever como:
>
> $$g'(y) = \frac{1}{f'(g(y))}$$

##### prova (informal)
^prova-derivada-inversa

Partimos da definição de inversa:

$$g(f(x)) = x, \quad \forall \, x \in I$$

Derivando ambos os lados pela [[aula-05-diferencial-e-regra-da-cadeia#^regra-da-cadeia|regra da cadeia]]:

$$g'(f(x)) \cdot f'(x) = 1$$

Escrevendo $y = f(x)$:

$$g'(y) \cdot f'(x) = 1$$

$$\Rightarrow \quad f'(x) \neq 0 \quad \text{e} \quad g'(y) = \frac{1}{f'(x)} \qquad \blacksquare$$

> **Observação:** note que se $f'(x) = 0$, então $g'(y)$ **não existe** (não podemos dividir por zero). Geometricamente, $f'(x) = 0$ significa tangente horizontal no gráfico de $f$, o que corresponde a tangente **vertical** no gráfico de $g$ — e derivada infinita não é derivada.

> **Questão levantada em aula:** quem falou que se $f'(x) \neq 0$ então $g$ é derivável em $y = f(x)$? A conta acima **assume** que $g$ é derivável para aplicar a regra da cadeia. A prova rigorosa precisa mostrar que $g$ de fato é derivável — isso é a parte não trivial do teorema.

##### tentativa de prova formal
^tentativa-prova-formal

Queremos mostrar: $f'(x) \neq 0 \implies g$ é derivável no ponto $y$.

Pela definição de derivada:

$$g'(y) = \lim_{\Delta y \to 0} \frac{\Delta x}{\Delta y}, \quad \text{onde } \Delta x = g(y + \Delta y) - g(y)$$

Analogamente, para $f$:

$$f'(x) = \lim_{\Delta x \to 0} \frac{\Delta y}{\Delta x}, \quad \text{onde } \Delta y = f(x + \Delta x) - f(x)$$

Como $f'(x) \neq 0$:

$$\frac{\Delta x}{\Delta y} = \frac{1}{\;\dfrac{\Delta y}{\Delta x}\;}$$

e portanto:

$$g'(y) = \lim_{\Delta y \to 0} \frac{\Delta x}{\Delta y} = \frac{1}{\displaystyle\lim_{\Delta x \to 0} \frac{\Delta y}{\Delta x}} = \frac{1}{f'(x)}$$

> **Detalhe crucial:** na passagem $\Delta y \to 0 \implies \Delta x \to 0$, usamos que $g$ é **contínua** (o que é verdade: $f$ injetora e contínua num intervalo tem inversa contínua). Isso garante que quando $\Delta y \to 0$, também $\Delta x = g(y + \Delta y) - g(y) \to 0$, e o limite de $\frac{\Delta y}{\Delta x}$ coincide com $f'(x)$. $\blacksquare$

A prova acima usou que $g$ é contínua. Isso é garantido pelo seguinte resultado:

##### teorema (mais difícil): inversa de função contínua e injetora é contínua
^teorema-inversa-continua

> **Teorema.** Seja $f: I \subset \mathbb{R} \to \mathbb{R}$ **contínua** em todo o intervalo $I$, **injetora**. Seja $J = \text{Im}\, f$. Então:
>
> $$g = f^{-1}: J \to \mathbb{R} \quad \text{é contínua.}$$

(A prova deste teorema é mais difícil e não será feita aqui.)

---

##### enunciado completo: Teorema da Regra da Função Inversa
^teorema-regra-funcao-inversa

Dos dois resultados acima, segue o teorema completo:

> **Teorema (Regra da Função Inversa).** Seja $f: I \subset \mathbb{R} \to \mathbb{R}$ **contínua** e **injetora**, em que $I$ é um intervalo. Seja $g = f^{-1}: J \to \mathbb{R}$, onde $J = \text{Im}\, f$.
>
> Se $f$ é derivável em $x \in I$ e $f'(x) \neq 0$, então $g$ é derivável em $y = f(x)$ e:
>
> $$g'(y) = \frac{1}{f'(x)}$$

