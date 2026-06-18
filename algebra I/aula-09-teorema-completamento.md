#### motivação: por que a base precisa de mais um teorema
^motivacao-completamento

Na aula passada definimos [[aula-08-dependencia-independencia-linear#^base|base]] como um conjunto que é, ao mesmo tempo, [[aula-08-dependencia-independencia-linear#^independencia-linear|LI]] e [[aula-08-dependencia-independencia-linear#^subespaco-gerado|gerador]]. Mas ficaram duas perguntas em aberto:

1. Será que **todo** espaço vetorial (de dimensão finita) tem base? E será que **sempre** dá pra construir uma a partir de um conjunto LI que já temos em mãos?
2. Será que duas bases do mesmo espaço têm **o mesmo número** de elementos? (Sem isso, falar em "dimensão" não faz sentido.)

> O **teorema do completamento** responde a primeira pergunta e é a ferramenta que, na sequência, responde a segunda. Ele é a ponte que **formaliza** a noção de base e abre caminho para a **dimensão**.

---

#### teorema do completamento de base #algebra/teorema/completamento-base
^completamento-base

Seja $V$ um espaço vetorial de dimensão finita e seja $\{v_1, \dots, v_k\}$ um conjunto **LI** de $V$. Então existem vetores $w_1, \dots, w_m \in V$ (possivelmente nenhum) tais que

$$\{v_1, \dots, v_k, w_1, \dots, w_m\}$$

é uma **base** de $V$.

> Em palavras: **todo conjunto LI pode ser completado até virar uma base**. A gente acrescenta vetores até passar a gerar tudo, sem nunca estragar a independência.

**Ideia da prova (construtiva):**

- Se $\{v_1, \dots, v_k\}$ já gera $V$, ele já é base — acabou ($m = 0$).
- Se **não** gera, existe $w_1 \in V$ que **não** está em $[\{v_1, \dots, v_k\}]$. Acrescentando esse $w_1$, o conjunto $\{v_1, \dots, v_k, w_1\}$ continua LI.
- Repete-se o processo. Como $V$ tem dimensão finita, ele **para** depois de um número finito de passos, e o conjunto obtido é LI **e** gerador, ou seja, base. $\blacksquare$

> O ponto fino é o "continua LI": se $w_1 \notin [\{v_1,\dots,v_k\}]$, então $w_1$ **não** é combinação linear dos $v_i$, e por isso nenhum vetor do novo conjunto vira combinação dos outros — é a [[aula-08-dependencia-independencia-linear#^caracterizacao-LD|caracterização da dependência]] usada ao contrário.

---

#### o resultado-irmão: refinar um conjunto gerador #algebra/proposição/refinamento-gerador
^refinamento-gerador

O completamento age **adicionando** vetores a um conjunto LI. Existe a versão simétrica, que age **removendo** vetores de um conjunto gerador:

> Se $S$ é um conjunto **gerador** de $V$, então é possível **retirar** os vetores redundantes de $S$ até sobrar uma **base** de $V$.

Juntos, os dois resultados dizem que a base está "no meio do caminho": é o conjunto LI grande o suficiente pra gerar, e o conjunto gerador pequeno o suficiente pra ser LI.

| Ponto de partida | Operação | Chega em |
|---|---|---|
| Conjunto **LI** (talvez pequeno) | **acrescentar** vetores | base |
| Conjunto **gerador** (talvez com excesso) | **remover** redundâncias | base |

> Consequência imediata: **todo espaço vetorial de dimensão finita tem base** (parta de qualquer gerador finito e refine; ou parta do conjunto vazio / de um vetor não-nulo e complete).

---

#### lema da troca (de Steinitz) #algebra/teorema/lema-troca
^lema-troca

A engrenagem por trás de tudo. Se $\{v_1, \dots, v_k\}$ é **LI** e $\{u_1, \dots, u_n\}$ **gera** $V$, então:

$$k \le n.$$

> Ou seja: **um conjunto LI nunca tem mais elementos que um conjunto gerador**. A prova troca, um a um, os $u_i$ pelos $v_j$ mantendo a propriedade de gerar — daí o nome "troca".

---

#### consequência central: a dimensão está bem definida #algebra/teorema/invariancia-dimensao
^invariancia-dimensao

Sejam $\mathcal{B} = \{v_1, \dots, v_k\}$ e $\mathcal{C} = \{u_1, \dots, u_n\}$ **duas bases** de $V$. Aplicando o [[#^lema-troca|lema da troca]] nos dois sentidos:

- $\mathcal{B}$ é LI e $\mathcal{C}$ gera $\Rightarrow k \le n$;
- $\mathcal{C}$ é LI e $\mathcal{B}$ gera $\Rightarrow n \le k$.

Logo $k = n$. **Todas as bases de $V$ têm o mesmo número de elementos.**

> Esse número comum é a **dimensão** de $V$, escrita $\dim V$. É exatamente o "próximo passo" prometido no fim da [[aula-08-dependencia-independencia-linear#^base|aula 08]], agora **justificado**: a definição de dimensão só faz sentido porque este teorema garante que o número não depende da base escolhida.

---

#### corolários úteis (atalhos pra prova) #algebra/corolário/corolarios-dimensao
^corolarios-dimensao

Seja $\dim V = n$. Então:

1. Todo conjunto **LI** tem **no máximo** $n$ elementos.
2. Todo conjunto **gerador** tem **no mínimo** $n$ elementos.
3. Um conjunto LI com **exatamente** $n$ elementos **já é base** (não precisa checar que gera).
4. Um conjunto gerador com **exatamente** $n$ elementos **já é base** (não precisa checar que é LI).

> Os itens 3 e 4 são os que mais economizam trabalho: quando você já sabe a dimensão, verificar **uma** das duas propriedades em um conjunto de tamanho $n$ basta.

---

> **Próximo passo:** com a dimensão bem definida, a próxima aula entra de cabeça em **bases** — coordenadas de um vetor numa base, mudança de base e o cálculo da dimensão de subespaços. *(a ver na aula 10)*
