# AGENTS.md — Schema do Wiki de Chinês (HSK1+)

Este arquivo governa **como o agente LLM deve operar e manter este wiki**. Leia-o completamente antes de qualquer ação no cofre. Não o modifique sem instrução explícita do usuário.

---

## 🗂️ Estrutura de Diretórios

```
d:\Chines\Chines\
│
├── AGENTS.md          ← Este arquivo. Schema e regras do wiki.
├── Bem-vindo.md       ← MOC principal (Map of Content). Gerado pelo LLM.
├── index.md           ← Índice de todas as páginas do wiki. Atualizado a cada ingestão.
├── log.md             ← Log cronológico append-only de todas as operações.
│
├── vocab\             ← Notas atômicas de vocabulário (uma por palavra/expressão)
│   ├── Lote 0\        ← O Básico (saudações, pronomes fundamentais)
│   ├── Lote 1\        ← Pronomes e Negação
│   ├── Lote 2\        ← Partículas e Perguntas
│   ├── Lote 3\        ← Identidade e Substantivos
│   ├── Lote 4\        ← Verbos de Ação
│   ├── Lote 5\        ← Números
│   ├── Lote 6\        ← Tempo e Datas
│   ├── Lote 7\        ← Família e Pessoas
│   ├── Lote 8\        ← Adjetivos e Intensidade
│   └── Lote N\        ← Lotes futuros conforme avança no HSK
│
├── wiki\              ← Páginas de síntese geradas pelo LLM
│   ├── conceitos\     ← Conceitos gramaticais (ex: tons, partículas, classificadores)
│   ├── radicais\      ← Páginas por radical chinês (ex: 女, 人, 口...)
│   ├── histórias\      ← Textos graduados HSK com análise gramatical
│   ├── temas\         ← Temas de vocabulário (ex: família, tempo, cores)
│   └── sínteses\      ← Análises, comparações, padrões descobertos
│
└── fontes\            ← Fontes brutas imutáveis (artigos, PDFs, anotações de aula)
    └── assets\        ← Imagens baixadas de fontes externas
```

> **Nota sobre a estrutura atual**: As pastas `Lote 0` a `Lote 8` existem na raiz do cofre (comportamento legado). Ao criar novas notas, use `vocab\Lote N\`. Ao referenciar notas existentes, use os caminhos atuais. Migração é opcional e incremental.

---

## 📋 Formatos de Página

### 1. Nota de Vocabulário (vocab/)

Naming: `Português - 漢字 - pinyin.md`

```markdown
---
tags: [hsk1, vocab, <categoria>]
pinyin: <pinyin com tons>
traducao: <Português>
hanzi: <漢字>
dominio: <1=HSK1, 2=HSK2, ...>
radical_principal: <radical>
tipo: <substantivo|verbo|adjetivo|advérbio|partícula|pronome|número|outro>
criado: <YYYY-MM-DD>
---

# <Português> - <漢字> - <pinyin>

## 🧩 Decomposição
* Analise os radicais que compõem o caractere.
* Link para a página do radical: [[wiki/radicais/<Radical>]]

## 🧠 Conexões Neurais
* Palavras relacionadas, compostas ou derivadas com links bidirecionais.
* Antônimos e sinônimos quando aplicável.
* Padrões gramaticais relevantes: [[wiki/conceitos/<Conceito>]]

## 💡 Mnemônica
* Uma história visual curta e criativa para fixar o caractere e o significado.

## 💬 Contexto (HSK1)
1. **Frase em 漢字.**
   * *Pinyin com tons.*
   * Tradução para Português.
2. (repetir para 2-3 frases)

## 🔗 Backlinks esperados
* (deixar vazio — o Obsidian preenche automaticamente)
```

### 2. Página de Conceito Gramatical (wiki/conceitos/)

Naming: `<Nome do Conceito>.md`

```markdown
---
tags: [conceito, gramática, hsk<N>]
criado: <YYYY-MM-DD>
fontes: [<lista de fontes que embasaram esta página>]
---

# <Nome do Conceito>

## Definição
Explicação concisa do conceito.

## Como funciona
Regras e padrões com exemplos.

## Vocabulário HSK relacionado
* Links para todas as notas de vocab que usam este conceito.

## Exceções e armadilhas
* Casos especiais, erros comuns de falantes de Português.

## Ver também
* Links para conceitos relacionados.
```

### 3. Página de Radical (wiki/radicais/)

Naming: `<漢字> - <Nome>.md` (ex: `女 - Mulher.md`)

```markdown
---
tags: [radical, componente]
radical: <漢字>
significado: <significado base>
---

# <漢字> — <Nome> (<Pinyin>)

## Significado base
...

## Palavras HSK que usam este radical
* [[vocab/...]] — significado

## Palavras compostas frequentes
...
```

### 4. Página de Síntese (wiki/sínteses/)

Naming: `<Título Descritivo>.md`

```markdown
---
tags: [síntese, <temas>]
criado: <YYYY-MM-DD>
---

# <Título>

<Conteúdo gerado pelo LLM: comparações, análises, tabelas, padrões>

## Fontes consultadas
* Links para as páginas do wiki que embasaram esta síntese.
```

### 5. Página de História / Leitura Graduada (wiki/histórias/)

Naming: `<Título PT> - <漢字 do título>.md`

```markdown
---
tags: [hsk1, leitura, historia, <temas>]
titulo_en: <Título em inglês da fonte>
fonte: "<URL da fonte>"
nivel: HSK1
criado: <YYYY-MM-DD>
palavras_novas: [<lista de hanzi novos identificados>]
---

# <Título em Português> — <漢字> — <Pinyin>

> 📖 **História curta HSK1** · Tema: <temas>.

---

## 📜 Texto Original

**<Frase em Hanzi>.** *<Pinyin com tons>.* <Tradução>.

---

## 🔑 Vocabulário da História

| Hanzi | Pinyin | Tradução | Link |
|-------|--------|----------|------|
| <hanzi> | <pinyin> | <pt> | [[wiki/vocab/Lote N/<nota>]] ou *(pendente)* |

---

## 🧠 Padrões Gramaticais em Destaque

### 1. <Nome do padrão>
> **<Frase exemplo.>** — <Explicação>
> Estrutura: ...

---

## 💡 Palavras Novas Identificadas

| Palavra | Pinyin | Status |
|---------|--------|--------|
| <hanzi> | <pinyin> | ✅ Criada: [[link]] OU ⚠️ Pendente |

---

## 🔗 Ver Também

* Links para notas de vocab relevantes e outras histórias relacionadas.
```

---

## ⚙️ Workflows Operacionais

### INGEST — Adicionar nova fonte ou novo lote de vocabulário

1. Leia a fonte (arquivo em `fontes/`, conteúdo colado, URL, etc.).
2. **Discuta** os pontos principais com o usuário antes de escrever.
3. Crie as **notas de vocab** (uma por palavra) no lote correspondente.
4. Para cada nota criada:
   - Verifique se o **radical principal** já tem página em `wiki/radicais/`. Se não, crie.
   - Verifique se algum **conceito gramatical** novo apareceu. Se sim, crie ou atualize a página em `wiki/conceitos/`.
   - Adicione links bidirecionais nas notas existentes que se relacionam.
5. Atualize `Bem-vindo.md` com o novo lote/palavras.
6. Atualize `index.md` com todas as páginas novas ou modificadas.
7. Adicione entrada em `log.md` no formato: `## [YYYY-MM-DD] ingest | <descrição>`
8. **Atualize `../README.md`** (na raiz do repositório, um nível acima do vault) com:
   - Novas páginas adicionadas em cada categoria
   - Estatísticas atualizadas (contagem de notas, cobertura HSK1)
   - Nova entrada no Changelog com data, evento e quantidade de páginas

> ⚠️ **Regra obrigatória**: Toda operação de ingest ou criação de conteúdo DEVE terminar com a atualização do `README.md`. O README é o espelho público do estado atual do wiki.

### QUERY — Responder perguntas sobre o conteúdo do wiki

1. Leia `index.md` para identificar páginas relevantes.
2. Leia as páginas identificadas.
3. Sintetize a resposta com citações para as páginas (`[[link]]`).
4. **Se a resposta for valiosa** (comparação, análise, padrão descoberto), salve-a como nova página em `wiki/sínteses/` e registre no `index.md` e no `log.md`.

### LINT — Verificação de saúde do wiki

Execute periodicamente ou quando solicitado:

1. **Órfãos**: Páginas sem nenhum link de entrada → adicione links nas páginas relacionadas ou no MOC.
2. **Contradições**: Informações conflitantes entre páginas → reconcilie e note.
3. **Radicais sem página**: Radicais mencionados em vocab mas sem página própria → crie.
4. **Conceitos mencionados sem página**: Expressões como "classificador", "partícula modal" → crie páginas.
5. **Frontmatter incompleto**: Notas sem todos os campos obrigatórios → complete.
6. **index.md desatualizado**: Verifique se todas as páginas existentes constam.
7. Registre o lint no `log.md`: `## [YYYY-MM-DD] lint | <resumo dos achados>`

### EVOLVE — Atualizar o schema

Quando o usuário pedir para mudar convenções, adicionar campos, criar novos tipos de página, etc.:
1. Atualize este `AGENTS.md` primeiro.
2. Aplique as mudanças retroativamente nas páginas existentes quando viável.
3. Registre em `log.md`: `## [YYYY-MM-DD] schema | <descrição da mudança>`

---

## 🏷️ Taxonomia de Tags

| Tag | Uso |
|-----|-----|
| `hsk1`, `hsk2`, ... | Nível HSK da palavra/conceito |
| `vocab` | Nota de vocabulário individual |
| `leitura` | Página de história / texto graduado |
| `historia` | Subtag de leitura (história curta) |
| `conceito` | Página de conceito gramatical |
| `radical` | Página de radical chinês |
| `tema` | Página temática de vocabulário |
| `síntese` | Análise ou comparação gerada |
| `gramática` | Relacionado a gramática |
| `pronome` | Tipo de palavra |
| `verbo` | Tipo de palavra |
| `substantivo` | Tipo de palavra |
| `adjetivo` | Tipo de palavra |
| `advérbio` | Tipo de palavra |
| `partícula` | Tipo de palavra |
| `número` | Tipo de palavra |
| `medida` | Classificador/medida |

---

## 📐 Convenções

- **Idioma das notas**: Português para explicações, 漢字 e Pinyin preservados.
- **Pinyin**: Sempre com diacríticos de tom (ā á ǎ à, ē é ě è, etc.). Nunca números.
- **Links**: Use `[[Nome do arquivo sem extensão]]` no estilo Obsidian Wiki Link.
- **Frontmatter**: YAML obrigatório em todas as notas de vocab. Opcional em sínteses.
- **Imutabilidade de fontes**: Nunca modifique arquivos em `fontes/`.
- **Log**: Sempre append-only. Nunca edite entradas passadas.
- **Uma palavra por nota**: Não agrupe palavras não relacionadas na mesma nota (exceto grupos lógicos como os Números do Lote 5).

---

## 🎯 Contexto do Usuário

- **Idioma nativo**: Português Brasileiro
- **Nível atual**: HSK1 (completando)
- **Próximo passo**: HSK2
- **Ferramenta**: Obsidian com Graph View ativo
- **Objetivo**: Construir base de conhecimento composta e interligada, não apenas listas de vocabulário isoladas.
- **Filosofia**: Radicais → Componentes → Palavras → Frases → Conceitos. Conexões são mais valiosas que listas.
