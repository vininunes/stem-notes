# stem-notes

Anotações de estudo de matemática, escritas em [Obsidian](https://obsidian.md/) e versionadas com git.

## Por que este repositório existe

Este é um cofre (*vault*) do Obsidian com as notas das disciplinas que estou cursando.
Os objetivos são:

- **Centralizar e organizar** o conteúdo das aulas em um único lugar, em formato de texto puro (Markdown + LaTeX).
- **Versionar o histórico de estudo** — acompanhar a evolução das notas ao longo do semestre via git.
- **Aproveitar o grafo de conhecimento do Obsidian** — links internos (`[[...]]`), blocos referenciáveis (`^id`) e tags hierárquicas conectam definições, teoremas e exemplos entre as disciplinas.
- **Servir de material de revisão** — uma base consultável e pesquisável para provas e listas de exercícios.

## Disciplinas ("skills")

Cada pasta é uma disciplina, com as aulas em Markdown e as listas de exercícios em PDF.

### 📐 álgebra I
Álgebra linear introdutória.
- Escalonamento e sistemas lineares
- Matrizes e propriedades do produto
- Forma escalonada reduzida, matriz inversa e algoritmo de Gauss
- Espaços vetoriais, dependência/independência linear
- Teorema do completamento

### 📊 análise aplicada
Fundamentos de análise real.
- Números reais como corpo ordenado completo
- Corpos ordenados, naturais e indução
- Inteiros, racionais e o segundo princípio de indução
- Axiomas de Peano e boa ordenação
- Intervalos, limitação e propriedade arquimediana
- Supremo, completeza e a existência de √2
- Sequências
- `padroes-de-demonstracao.md` — referência dos padrões de demonstração

### ∫ cálculo III
Cálculo de funções de várias variáveis.
- Funções, sistemas de coordenadas e visualização
- Funções diferenciáveis, diferencial e regra da cadeia
- Derivadas de produtos e função inversa
- Teorema da função inversa e teorema da função implícita
- Apêndices da disciplina e de notações

## Convenções de escrita

- **Markdown + LaTeX** para a matemática (`$...$` e `$$...$$`).
- **Tags hierárquicas** identificam o tipo de conteúdo, ex.: `#analise/definição/corpo`, `#calculo/definição/injetora`.
- **Blocos referenciáveis** (`^id-do-bloco`) permitem citar trechos específicos a partir de outras notas.
- **Links internos** (`[[aula-02-sistemas-lineares#^representacao-matricial|matricial]]`) conectam ideias entre aulas e disciplinas.
- Os arquivos são nomeados como `aula-NN-assunto.md`.

## Como usar

Abra a pasta como um cofre no Obsidian para navegar pelo grafo, seguir os links e usar a busca. Os arquivos `.md` também são legíveis em qualquer editor de texto.
