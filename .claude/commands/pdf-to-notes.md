Transforme um PDF de anotações de aula em uma nota estruturada no padrão do vault.

**Argumentos:** `$ARGUMENTS` no formato `<disciplina> <caminho-do-pdf>` (ex: `analise aplicada analise aplicada/Aula04.pdf`).

## Instruções

1. **Leia o PDF como imagem** — use a ferramenta Read com o caminho do PDF. Leia todas as páginas (o Read renderiza cada página como imagem). Interprete a caligrafia/texto manuscrito com atenção.

2. **Leia as aulas anteriores** da disciplina (arquivos `aula-*.md`) para entender:
   - O estilo de formatação (headers, tags, block references `^`)
   - A notação e convenções usadas
   - Onde o conteúdo parou (para manter continuidade)
   - As tags Obsidian já utilizadas (ex: `#analise/definição/...`, `#algebra/proposição/...`)

3. **Identifique o número da aula** — se houver um `aula-XX-preview.md`, esta é a aula XX. Caso contrário, use o próximo número após a última aula existente.

4. **Gere a nota de aula** seguindo o padrão:
   - Use headers `####` para cada conceito/seção
   - Adicione tags Obsidian (`#disciplina/tipo/nome`) nos headers relevantes
   - Adicione block references (`^nome-do-bloco`) para permitir links entre notas
   - Use links internos do Obsidian (`[[aula-XX-nome#^bloco|texto]]`) para referenciar conceitos de aulas anteriores
   - Formate matemática em LaTeX (`$...$` e `$$...$$`)
   - Inclua provas completas quando presentes no PDF
   - Preserve exemplos, contraexemplos e observações do professor
   - Use `>` blockquotes para observações e notas importantes

5. **Salve a nota** como `aula-XX-<tema-principal>.md` na pasta da disciplina.

6. **Se existir um preview** (`aula-XX-preview.md`), gere também um arquivo `aula-XX-diff-preview.md` com uma tabela comparando:
   - O que o preview acertou
   - O que o preview previa mas não apareceu
   - O que apareceu na aula mas não estava no preview
   - Um resumo das diferenças

7. **Delete o PDF** após gerar a nota.

## Dicas para leitura de PDFs manuscritos

- Preste atenção em símbolos matemáticos manuscritos: $\in$, $\implies$, $\iff$, $\forall$, $\exists$, $\subseteq$
- Setas e chaves agrupam condições (ex: definições com múltiplas cláusulas)
- Sublinhados e caixas indicam resultados importantes
- Texto entre aspas ou com "ex:" indica exemplos
- "Obs:" ou "Cuidado:" indicam observações do professor
