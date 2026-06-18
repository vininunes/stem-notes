# stem-notes

Anotações de estudo de matemática, escritas em [Obsidian](https://obsidian.md/) e versionadas com git.

## Por que este repositório existe

Este é um cofre (*vault*) do Obsidian com as notas das disciplinas que estou cursando.
Os objetivos são:

- **Centralizar e organizar** o conteúdo das aulas em um único lugar, em formato de texto puro (Markdown + LaTeX).
- **Versionar o histórico de estudo** — acompanhar a evolução das notas ao longo do semestre via git.
- **Aproveitar o grafo de conhecimento do Obsidian** — links internos (`[[...]]`), blocos referenciáveis (`^id`) e tags hierárquicas conectam definições, teoremas e exemplos entre as disciplinas.
- **Servir de material de revisão** — uma base consultável e pesquisável para provas e listas de exercícios.

## Disciplinas

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

## Comandos do Claude (skills)

O repositório inclui comandos personalizados do [Claude Code](https://claude.com/claude-code) em
`.claude/commands/`. Eles automatizam tarefas recorrentes de estudo, sempre seguindo o padrão de
escrita do cofre. Use-os como *slash commands* (`/nome`) ao abrir o Claude Code nesta pasta.

| Comando | O que faz |
|---|---|
| **`/pdf-to-notes <disciplina> <pdf>`** | Lê um PDF de aula (inclusive manuscrito) como imagem e o transforma em uma nota `aula-NN-tema.md` no padrão do cofre — headers, tags, blocos referenciáveis, links internos, LaTeX e provas completas. Se existir um *preview* da aula, gera um `aula-NN-diff-preview.md` comparando previsto × real e apaga o PDF ao final. |
| **`/course-summary <disciplina>`** | Lê todas as aulas em ordem e gera um `resumo.md` com axiomas e definições, resultados importantes (com a ideia das provas), o que já é possível demonstrar, contraexemplos e a progressão lógica do curso. |
| **`/next-class-preview <disciplina>`** | A partir do conteúdo já coberto, simula a próxima aula (conexão com a anterior, novos conceitos, resultados prováveis, exercícios típicos e perguntas para pensar) e salva como `aula-NN-preview.md`. |
| **`/monitor <disciplina>`** | Entra em modo monitor/tutor: carrega aulas, `resumo.md`, `padroes-de-demonstracao.md` e listas, e responde dúvidas fundamentado nas notas — guiando com dicas antes da solução e usando matemática em texto puro (sem LaTeX), legível no terminal. |

## Convenções de escrita

- **Markdown + LaTeX** para a matemática (`$...$` e `$$...$$`).
- **Tags hierárquicas** identificam o tipo de conteúdo, ex.: `#analise/definição/corpo`, `#calculo/definição/injetora`.
- **Blocos referenciáveis** (`^id-do-bloco`) permitem citar trechos específicos a partir de outras notas.
- **Links internos** (`[[aula-02-sistemas-lineares#^representacao-matricial|matricial]]`) conectam ideias entre aulas e disciplinas.
- Os arquivos são nomeados como `aula-NN-assunto.md`.

## Como usar

Abra a pasta como um cofre no Obsidian para navegar pelo grafo, seguir os links e usar a busca. Os arquivos `.md` também são legíveis em qualquer editor de texto.
