## Conjuntos e espaços
^conjuntos-e-espacos

| Notação | Significado |
|---|---|
| $\mathbb{R}$ | Conjunto dos números reais |
| $\mathbb{R}^2$ | Plano — pares $(x, y)$ |
| $\mathbb{R}^3$ | Espaço — triplas $(x, y, z)$ |
| $\mathbb{R}^n$ | Espaço $n$-dimensional |
| $\in$ | "pertence a" — ex: $(x,y) \in \mathbb{R}^2$ |
| $\subseteq$ | "está contido em" — ex: $S \subseteq \mathbb{R}^2$ |
| $\{x : P(x)\}$ | Conjunto dos $x$ que satisfazem a propriedade $P$ |

## Funções
^notacao-funcoes

| Notação | Significado |
|---|---|
| $f: A \to B$ | Função de $A$ (domínio) em $B$ (contradomínio) |
| $f(x, y)$ | Valor de $f$ aplicada ao **ponto** $(x, y)$ |
| $f[S]$ | **[[aula-03-visualizacao-funcoes#^imagem-de-conjunto\|Imagem]]** do **conjunto** $S$ por $f$ — todos os resultados de aplicar $f$ a cada ponto de $S$: $f[S] = \{f(x) : x \in S\}$ |
| $f^{-1}[T]$ | **[[aula-03-visualizacao-funcoes#^imagem-inversa\|Imagem inversa]]** (pré-imagem) do conjunto $T$ — todos os pontos do domínio que $f$ mapeia para $T$: $f^{-1}[T] = \{x : f(x) \in T\}$ |
| $f^{-1}$ | **[[aula-03-visualizacao-funcoes#^inversa-exige-bijecao\|Função inversa]]** (só existe se $f$ for bijetora) |
| $N_c(f)$ | **[[aula-01-funções#^superficies-e-curvas-de-nivel\|Conjunto de nível]]** $c$ — equivale a $f^{-1}[\{c\}]$ |

## Coordenadas
^notacao-coordenadas

| Notação | Significado |
|---|---|
| $(x, y)$ | [[aula-02-sistema-de-coordenadas#^coordenadas-cartesianas\|Coordenadas cartesianas]] no plano |
| $(x, y, z)$ | [[aula-02-sistema-de-coordenadas#^coordenadas-cartesianas\|Coordenadas cartesianas]] no espaço |
| $(\rho, \theta)$ | [[aula-02-sistema-de-coordenadas#^coordenadas-polares\|Coordenadas polares]] — distância e ângulo |
| $(\rho, \theta, z)$ | [[aula-02-sistema-de-coordenadas#^coordenadas-cilindricas\|Coordenadas cilíndricas]] — polares + altura |

## Topologia
^notacao-topologia

| Notação | Significado |
|---|---|
| $B(x, R)$ | [[aula-05-diferencial-e-regra-da-cadeia#^bola-aberta-e-conjunto-aberto\|Bola aberta]] de centro $x$ e raio $R$: $\{y \in \mathbb{R}^n : \|y - x\| < R\}$ |
| $U$ aberto | [[aula-05-diferencial-e-regra-da-cadeia#^bola-aberta-e-conjunto-aberto\|Conjunto aberto]]: $\forall x \in U, \exists R > 0$ tal que $B(x,R) \subset U$ |
| $\|x\|$ | Norma (comprimento) do vetor $x$ |

## Diferenciabilidade
^notacao-diferenciabilidade

| Notação | Significado |
|---|---|
| $\dfrac{\partial f}{\partial x_i}(x)$ | [[aula-05-diferencial-e-regra-da-cadeia#^derivada-parcial-formal\|Derivada parcial]] de $f$ em relação a $x_i$ no ponto $x$ |
| $\dfrac{\partial f}{\partial v}(x)$ | [[aula-05-diferencial-e-regra-da-cadeia#^derivada-direcional-formal\|Derivada direcional]] de $f$ na direção $v$ no ponto $x$ |
| $df(x)$ | [[aula-05-diferencial-e-regra-da-cadeia#^definicao-diferencial\|Diferencial]] de $f$ em $x$ — a transformação linear que aproxima $f$ |
| $Jf(x)$ | [[aula-05-diferencial-e-regra-da-cadeia#^definicao-diferencial\|Matriz jacobiana]] de $f$ em $x$ — representação matricial de $df(x)$ |
| $\nabla f(x)$ | [[aula-05-diferencial-e-regra-da-cadeia#^gradiente-como-diferencial\|Gradiente]] de $f$ em $x$ — caso $f: \mathbb{R}^m \to \mathbb{R}$ (jacobiana é matriz linha) |
| $f'(t)$ | [[aula-05-diferencial-e-regra-da-cadeia#^derivada-curva\|Derivada de curva]] — caso $f: \mathbb{R} \to \mathbb{R}^n$ |
| $\det Jf(x)$ | Determinante da jacobiana — mede se $f$ preserva/inverte orientação e por quanto "estica" volumes localmente |
| $(Jf(x))^{-1}$ | Inversa da matriz jacobiana — é a [[aula-10-teorema-da-funcao-inversa#^enunciado-tfi\|jacobiana da função inversa]]: $Jg(y) = (Jf(x))^{-1}$ |
| $f\big\|_V$ | Restrição de $f$ ao subconjunto $V$ do domínio |

## Regras de cálculo
^notacao-regras-calculo

| Notação | Significado |
|---|---|
| $J(g \circ f)(x) = Jg(f(x)) \cdot Jf(x)$ | [[aula-06-regra-da-cadeia-e-funcao-diferenciavel#^prova-regra-da-cadeia\|Regra da cadeia]] — jacobiana da composição é produto das jacobianas |
| $(f \circ \gamma)'(t) = Jf(\gamma(t)) \cdot \gamma'(t)$ | [[aula-06-regra-da-cadeia-e-funcao-diferenciavel#^derivada-ao-longo-de-curva\|Derivada ao longo de curva]] — consequência da regra da cadeia |
| $Jg(y) = (Jf(x))^{-1}$ | [[aula-10-teorema-da-funcao-inversa#^enunciado-tfi\|Regra da função inversa]] — jacobiana da inversa é a inversa da jacobiana |

## Propriedades de funções
^propriedades-de-funcoes

| Notação | Significado |
|---|---|
| [[aula-01-funções#^tipos-de-funcoes\|Injetora]] | $f(a_1) = f(a_2) \implies a_1 = a_2$ — cada saída vem de uma única entrada |
| [[aula-01-funções#^tipos-de-funcoes\|Sobrejetora]] | Para todo $b \in B$, existe $a \in A$ com $f(a) = b$ — todo elemento de $B$ é atingido |
| [[aula-01-funções#^tipos-de-funcoes\|Bijetora]] | Injetora + Sobrejetora — [[aula-03-visualizacao-funcoes#^inversa-exige-bijecao\|$f^{-1}$ existe como função]] |
| [[aula-04-funcoes-diferenciaveis#^definicao-diferenciavel\|Diferenciável]] | Existe transformação linear $T$ com resto desprezível: $f(x+\Delta x) = f(x) + T(\Delta x) + r(\Delta x)$ |
| [[aula-09-diferenciabilidade#^definicao-classe-c1\|Classe $C^1$]] | Todas as derivadas parciais existem e são **contínuas** — notação: $f \in C^1(U)$ |
| [[aula-10-teorema-da-funcao-inversa#^definicao-difeomorfismo\|Difeomorfismo]] | Bijeção $C^1$ com inversa $C^1$ — equivalência entre abertos do ponto de vista diferencial |
| [[aula-10-teorema-da-funcao-inversa#^relacao-tfi-difeomorfismo\|Difeomorfismo local]] | $f$ é difeomorfismo quando restrita a uma vizinhança do ponto |

## Siglas e abreviações
^siglas

| Sigla | Significado |
|---|---|
| EDO | **Equação Diferencial Ordinária** — equação que relaciona uma função de uma variável com suas derivadas. Ex: $y' = f(t, y)$ |
| EDP | **Equação Diferencial Parcial** — envolve derivadas parciais de funções de várias variáveis |
| TFI | **[[aula-10-teorema-da-funcao-inversa#^enunciado-tfi\|Teorema da Função Inversa]]** |
| TVI | **Teorema do Valor Intermediário** — se $f$ é contínua em $[a,b]$, assume todos os valores entre $f(a)$ e $f(b)$ |
| TFC | **Teorema Fundamental do Cálculo** |
| $C^k$ | Função de **classe $C^k$** — derivadas parciais até ordem $k$ existem e são contínuas |
| $\text{Im}\, f$ | **Imagem** de $f$ — conjunto de todos os valores que $f$ assume |
| $\det A$ | **Determinante** da matriz $A$ |
| $\nabla f$ | **Gradiente** de $f$ (nabla) — vetor das derivadas parciais |
| $Jf$ | **Matriz jacobiana** de $f$ |
| $f\big\|_V$ | **Restrição** de $f$ ao subconjunto $V$ |

---

> **Cobertura:** este apêndice cobre notações introduzidas da **aula-01** até a **aula-10**. Atualizar a partir da aula-11.
