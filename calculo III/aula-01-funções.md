#### tipos de funções #calculo/definição/injetora #calculo/definição/sobrejetora #calculo/definição/bijetora
^tipos-de-funcoes

- **Injetora**: elementos distintos do domínio são levados a elementos distintos do contradomínio. Graficamente, qualquer reta horizontal corta a curva **no máximo uma vez**. Se cortar duas vezes, a função não é injetora
- **Sobrejetora**: todo elemento do contradomínio é imagem de pelo menos um elemento do domínio. A imagem da função coincide com o contradomínio
- **Bijetora**: é injetora e sobrejetora ao mesmo tempo. Possui [[aula-03-visualizacao-funcoes#^inversa-exige-bijecao|inversa]]

#### superfícies de nível e curvas de nível #calculo/definição/conjunto-de-nível
^superficies-e-curvas-de-nivel

Dado $f: \mathbb{R}^{n} \to \mathbb{R}$ e uma constante $c \in \mathbb{R}$, o **conjunto de nível** $c$ de $f$ é:

$$
\{ (x_{1}, \dots, x_{n}) \in \mathbb{R}^{n} \mid f(x_{1}, \dots, x_{n}) = c \}
$$

- Para $f: \mathbb{R}^{2} \to \mathbb{R}$, os conjuntos de nível são **curvas de nível** (curvas no plano)
- Para $f: \mathbb{R}^{3} \to \mathbb{R}$, os conjuntos de nível são **superfícies de nível** (superfícies no espaço)
- O conjunto de nível pode ser **vazio** (ex: $x^{2} + y^{2} = -1$ não tem solução)

O gráfico de $f: \mathbb{R}^{2} \to \mathbb{R}$ é uma superfície em $\mathbb{R}^{3}$. As curvas de nível são como "fatias horizontais" desse gráfico — uma ferramenta de visualização.

#### curvas parametrizadas #calculo/definição/curva-parametrizada
^curvas-parametrizadas

Uma **curva parametrizada** é uma função $\alpha: I \subseteq \mathbb{R} \to \mathbb{R}^{n}$ onde o parâmetro $t$ representa o tempo. A imagem de $\alpha$ descreve a trajetória e $\alpha(t)$ é a posição no instante $t$.

#### objetivo do curso
^objetivo-do-curso

Estudar funções de $\mathbb{R}^{n}$ em $\mathbb{R}^{m}$ ([[apendice-notacoes#^notacao-funcoes|notação]]) — funções não lineares:
- [[aula-04-funcoes-diferenciaveis#^definicao-diferenciavel|Diferenciabilidade]] dessas funções
- [[aula-04-funcoes-diferenciaveis#^exemplo-jacobiana|Matriz jacobiana]]
