<div align="center">

# 🀄 Mandarim Wiki — LLM-Powered Knowledge Base

**Uma base de conhecimento pessoal para aprendizado de Mandarim, construída e mantida por LLMs usando o padrão LLM Wiki.**

[![Obsidian](https://img.shields.io/badge/Obsidian-7C3AED?style=for-the-badge&logo=obsidian&logoColor=white)](https://obsidian.md)
[![Nível](https://img.shields.io/badge/Nível-HSK1%20→%20HSK2-red?style=for-the-badge)](https://www.chinesetest.cn)
[![Notas](https://img.shields.io/badge/Notas%20Wiki-105%2B-brightgreen?style=for-the-badge)]()
[![Histórias](https://img.shields.io/badge/Histórias%20HSK1-5-orange?style=for-the-badge)]()
[![Licença](https://img.shields.io/badge/licença-MIT-blue?style=for-the-badge)]()

[Ver o Wiki](#-estrutura-do-wiki) · [Começar a usar](#-como-usar) · [Adaptar para outro idioma](#-adaptando-para-outro-idioma)

</div>

---

## 📖 O que é este projeto?

Este repositório implementa o padrão **LLM Wiki** aplicado ao aprendizado de Mandarim (foco inicial: HSK1).

Em vez de uma simples coleção de flashcards, é uma **base de conhecimento viva**:

- 📝 **Notas atômicas** — uma nota por palavra, com decomposição de radicais, mnemônicas e exemplos
- 🕸️ **Grafo interligado** — cada nota referencia radicais, conceitos gramaticais e palavras relacionadas
- 🤖 **Mantida por LLMs** — você traz as fontes e faz perguntas; o agente escreve, atualiza e cross-referencia
- 📈 **Composta** — a base fica mais rica a cada sessão, sem precisar redescobrir o que já foi aprendido

> **Conceito base**: [LLM Wiki Pattern](https://github.com/tobi/llm-wiki) — em vez de RAG (retrieval na hora da query), o LLM constrói e mantém um wiki persistente. O conhecimento é compilado uma vez e fica lá, crescendo.

---

## 🗂️ Estrutura do Projeto

```
📁 Chines/                          ← Vault do Obsidian
│
├── 📄 AGENTS.md                    ← Schema do wiki (leia antes de tudo)
├── 📄 Bem-vindo.md                 ← MOC principal (Map of Content)
├── 📄 index.md                     ← Índice de todas as páginas
├── 📄 log.md                       ← Log cronológico append-only
│
├── 📁 wiki/                        ← Gerado e mantido pelo LLM
│   ├── 📁 vocab/
│   │   ├── 📁 Lote 0/              ← O Básico (你好, 我, 是)
│   │   ├── 📁 Lote 1/              ← Pronomes e Negação (他, 她, 们, 不)
│   │   ├── 📁 Lote 2/              ← Partículas (吗, 呢, 的, 什么)
│   │   ├── 📁 Lote 3/              ← Identidade (人, 老师, 学生, 中国)
│   │   ├── 📁 Lote 4/              ← Verbos (有, 在, 吃, 去)
│   │   ├── 📁 Lote 5/              ← Números (零到百)
│   │   ├── 📁 Lote 6/              ← Tempo (月, 日, 今天, 明天)
│   │   ├── 📁 Lote 7/              ← Família (妈妈, 爸爸, 朋友)
│   │   ├── 📁 Lote 8/              ← Adjetivos (很, 大, 小, 好)
│   │   └── 📁 Lote 9/              ← Complementar HSK1 + Histórias (62 palavras)
│   ├── 📁 histórias/               ← Textos graduados com análise gramatical
│   ├── 📁 conceitos/               ← Gramática (tons, partículas, SVO...)
│   ├── 📁 radicais/                ← Por radical (女, 人/亻, 口...)
│   └── 📁 sínteses/                ← Análises e comparações geradas
│
└── 📁 fontes/                      ← Fontes brutas IMUTÁVEIS
    ├── 📁 Lote 0-9/                ← Notas originais por lote
    ├── 📄 Lista HSK1 oficial.md    ← Fonte primária da lista
    └── 📄 *.md                     ← Histórias e leituras graduadas (chinesehskreading.com)
```

### Contagem atual

| Categoria | Quantidade |
|-----------|-----------|
| Notas de vocabulário | 102+ |
| Histórias de leitura | 5 (HSK1) |
| Conceitos gramaticais | 5 (Tons, Partículas, SVO, Negação, Posse) |
| Páginas de radicais | 4 (女, 人/亻, 口, 日) |
| Sínteses temáticas | 3 (Família 电, Partículas, Classificadores) |
| **Total de páginas wiki** | **110+** |
| Cobertura HSK1 (150 palavras) | ~68% |

---

## 🧱 Anatomia de uma Nota

Cada nota de vocabulário segue um schema consistente:

```markdown
---
tags: [hsk1, vocab, verbo]
pinyin: chī
traducao: Comer
hanzi: 吃
dominio: 1
radical_principal: 口
tipo: verbo
criado: 2026-05-02
---

# Comer - 吃 - chī

## 🧩 Decomposição
* [[wiki/radicais/口 - Boca]] (口) + 乞 (implorar)

## 🧠 Conexões Neurais
* **Par**: Beber - 喝 | **Composto**: 吃饭 (fazer refeição)
* **Adjetivo**: 好吃 (delicioso) | **Negação**: 不吃

## 💡 Mnemônica
"A boca (口) que implora (乞) por comida."

## 💬 Contexto (HSK1)
1. **我吃苹果。** — *Wǒ chī píngguǒ.* — Eu como maçã.
```

---

## 📖 Anatomia de uma Página de História

Além das notas de vocabulário, o wiki compila **histórias de leitura graduada** com análise integrada:

```markdown
---
tags: [hsk1, leitura, historia, animais]
titulo_en: I am a cat
fonte: "https://chinesehskreading.com/hsk1/short/i-am-a-cat/"
nivel: HSK1
criado: 2026-05-02
palavras_novas: [猫, 叫, 喜欢, 狗, 再见, 睡觉]
---

# Eu Sou um Gato — 我是一只猫

## 📜 Texto Original
**我叫小猫。** · *Wǒ jiào Xiǎo Māo.* · Meu nome é Xiao Mao.

## 🔑 Vocabulário da História
| Hanzi | Pinyin | Tradução | Link |
|-------|--------|----------|------|
| 猫 | māo | Gato | [[wiki/vocab/Lote 9/Gato - 猫 - māo]] |

## 🧠 Padrões Gramaticais em Destaque
### 1. Classificador 只 para animais
> **我是一只猫。** — Estrutura: 一 + 只 + [animal]

## 💡 Palavras Novas Identificadas
| Palavra | Status |
|---------|--------|
| 睡觉 | ⚠️ Pendente — criar nota vocab |
```

---

## ⚙️ Como Usar

### Pré-requisitos

- [Obsidian](https://obsidian.md/) (gratuito)
- Um agente LLM com acesso ao sistema de arquivos:
  - [Claude Code](https://claude.ai/code) ✅ (recomendado)
  - [OpenAI Codex](https://openai.com) ✅
  - [Antigravity](https://antigravity.dev) ✅
  - Qualquer LLM com acesso a ferramentas de arquivo

---

### Passo 1 — Clone e abra no Obsidian

```bash
git clone https://github.com/seu-usuario/mandarim-wiki.git
```

1. Abra o Obsidian
2. "Open folder as vault" → selecione a pasta `Chines/`
3. Ative o **Graph View** para ver as conexões

---

### Passo 2 — Leia o schema (AGENTS.md)

Antes de pedir qualquer coisa ao LLM, compartilhe o arquivo `AGENTS.md` com ele. Esse arquivo define:

- Estrutura de diretórios
- Formato de cada tipo de página
- Workflows: `ingest`, `query`, `lint`, `evolve`
- Taxonomia de tags e convenções

```
"Leia o arquivo AGENTS.md deste repositório antes de qualquer operação."
```

---

### Passo 3 — Adicionar uma fonte (INGEST)

```
"Ingest o arquivo fontes/minha-aula-2026-05-10.md seguindo o AGENTS.md"
```

O LLM vai:
1. Ler o arquivo fonte
2. Criar/atualizar notas de vocabulário em `wiki/vocab/`
3. Para histórias: criar página em `wiki/histórias/` com texto, vocab e análise gramatical
4. Verificar e atualizar páginas de radicais em `wiki/radicais/`
5. Criar sínteses quando padrões relevantes emergirem
6. Atualizar `index.md`, `log.md` e **`README.md`**

---

### Passo 4 — Fazer perguntas (QUERY)

```
"Quais palavras HSK1 usam o radical 口? Crie uma síntese."
"Compare 不 e 没 — quando usar cada um?"
"Liste todos os verbos de movimento que já aprendi."
```

Se a resposta for valiosa, peça para salvar:

```
"Salve esta análise em wiki/sínteses/ e atualize o index.md"
```

---

### Passo 5 — Manutenção (LINT)

Periodicamente:

```
"Execute um lint do wiki: procure páginas órfãs, links quebrados,
radicais mencionados sem página própria e frontmatter incompleto."
```

---

## 🔄 Fluxo de Trabalho Recomendado

```
┌──────────────────────────────────────────────────────────┐
│                    VOCÊ (curador)                        │
│  • Traz fontes (artigos, listas, anotações)              │
│  • Faz perguntas e dirige a análise                      │
│  • Decide o que vale preservar                           │
└─────────────────────┬────────────────────────────────────┘
                      │ instrui
                      ▼
┌──────────────────────────────────────────────────────────┐
│                   LLM (mantenedor)                       │
│  • Lê AGENTS.md (schema)                                 │
│  • Consulta index.md (navegação)                         │
│  • Escreve/atualiza páginas wiki                         │
│  • Mantém cross-references e log                         │
└─────────────────────┬────────────────────────────────────┘
                      │ escreve em
                      ▼
┌──────────────────────────────────────────────────────────┐
│                    WIKI (artefato)                       │
│  • Vocabulário com radicais e mnemônicas                 │
│  • Conceitos gramaticais interligados                    │
│  • Sínteses de análises e comparações                    │
│  • Fica mais rico a cada sessão                          │
└──────────────────────────────────────────────────────────┘
```

---

## 🌍 Adaptando para Outro Idioma

Este projeto pode ser adaptado para **qualquer idioma** ou **domínio de conhecimento**. As peças que precisam mudar:

### 1. Schema (AGENTS.md)

Edite as seções:
- **Estrutura de Diretórios** — renomeie `Lote N` para o que fizer sentido (capítulos, temas, níveis...)
- **Formato de Página** — remova campos específicos (pinyin, hanzi) e adicione os relevantes
- **Taxonomia de Tags** — adapte para o novo domínio
- **Contexto do Usuário** — atualize idioma, nível e objetivo

### 2. Tipo de Nota (exemplos)

**Japonês**: campos `kanji`, `kana`, `romaji`, `jlpt_level`  
**Francês/Espanhol**: campos `género`, `conjugação`, `nível_cef`  
**Programação**: campos `linguagem`, `complexidade`, `caso_de_uso`  
**Medicina**: campos `sistema`, `especialidade`, `mecanismo`

### 3. Estrutura de Lotes

Substitua os Lotes por qualquer organização que faça sentido:
- Capítulos de um livro
- Módulos de um curso
- Sprints de estudo
- Temas (cores, família, trabalho...)

---

## 🛠️ Dicas de Configuração do Obsidian

### Plugins recomendados

| Plugin | Uso |
|--------|-----|
| **Graph View** (nativo) | Visualizar conexões entre notas |
| **Templates** (nativo) | Criar notas de vocab com o schema |
| **Dataview** | Queries sobre frontmatter (listar por tag, tipo...) |
| **Obsidian Web Clipper** | Converter artigos da web em Markdown |

### Configurações úteis

- **Files & Links → Attachment folder path**: `fontes/assets` (para imagens)
- **Graph View → Filters**: exclua `index.md` e `log.md` para ver só o conteúdo
- **Hotkeys**: mapeie "Open graph view" para acesso rápido

---

## 📋 Referência Rápida de Comandos ao LLM

```bash
# Processar uma fonte nova (vocab, lista, aula)
"Ingest fontes/[arquivo.md] seguindo o AGENTS.md"

# Processar histórias de leitura
"Compile os arquivos adicionados em fontes/ para o wiki — são histórias em Mandarim"

# Perguntar algo
"Quais palavras HSK1 pertencem ao radical 人?"

# Salvar resposta valiosa
"Salve esta análise como síntese e registre no log"

# Verificar saúde do wiki
"Execute um lint completo do wiki"

# Adicionar novo lote de vocabulário
"Crie o Lote 10 com as palavras: [lista]"

# Criar conceito gramatical
"Crie uma página de conceito sobre [tópico] em wiki/conceitos/"

# Ver progresso
"Leia o index.md e me dê um resumo do estado atual do wiki"

# [OBRIGATÓRIO após qualquer geração de conteúdo]
"Atualize o README.md com as novas páginas e estatísticas geradas"
```

---

## 📅 Changelog

| Data | Evento | Páginas |
|------|--------|--------|
| 2026-05-02 | Início do projeto — Lotes 0–8 migrados | 41 notas |
| 2026-05-02 | Compilação completa HSK1 — Lote 9 + radicais + sínteses | +56 notas, +2 sínteses, +3 radicais |
| 2026-05-02 | Histórias de leitura HSK1 (5 textos) + vocab emergente | +5 histórias, +5 notas, +1 síntese |
| 2026-05-05 | Criação de conceitos e radicais pendentes | +4 conceitos, +1 radical |

---

## 📚 Referências e Inspirações

- [LLM Wiki Pattern](https://github.com/tobi/llm-wiki) — o padrão conceitual que este projeto implementa
- [Obsidian](https://obsidian.md) — o "IDE" do wiki
- [HSK Academy](https://hsk.academy/pt/hsk-1-vocabulary-list) — fonte da lista oficial HSK1
- [Chinese HSK Reading](https://chinesehskreading.com) — histórias de leitura graduada gratuitas
- [Vannevar Bush — As We May Think (1945)](https://www.theatlantic.com/magazine/archive/1945/07/as-we-may-think/303881/) — a inspiração original para bases de conhecimento pessoais e associativas

---

## 📄 Licença

MIT — sinta-se livre para clonar, adaptar e usar para o seu próprio aprendizado.

---

<div align="center">

**HSK1 em progresso**

*"A parte tediosa de manter uma base de conhecimento não é a leitura ou o pensamento — é a contabilidade. LLMs não se cansam, não esquecem de atualizar uma referência cruzada."*

</div>
