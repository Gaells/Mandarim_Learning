# 📋 Log do Wiki — Chinês (HSK1+)

> Arquivo **append-only**. Nunca edite entradas existentes.
> Formato das entradas: `## [YYYY-MM-DD] <tipo> | <descrição>`
> Tipos válidos: `ingest`, `query`, `lint`, `schema`, `síntese`

---

## [2026-05-02] schema | Inicialização do LLM Wiki

**Operação**: Criação da estrutura base do LLM Wiki para o cofre de Chinês HSK1.

**Arquivos criados**:
- `AGENTS.md` — Schema completo com workflows, formatos de página, taxonomia de tags e convenções.
- `index.md` — Índice inicial com as 41 notas de vocab existentes (Lotes 0–8) catalogadas.
- `log.md` — Este arquivo.

**Estado inicial do wiki**:
- 41 notas de vocabulário distribuídas em 9 lotes (Lote 0 a Lote 8).
- 0 páginas de conceitos gramaticais.
- 0 páginas de radicais.
- 0 páginas de síntese.
- `Bem-vindo.md` existente (MOC central) mantido sem alteração.

**Pendências identificadas**:
- Criar páginas de radicais para os principais radicais presentes no vocab HSK1 (女, 人/亻, 口, 日, etc.).
- Criar páginas de conceitos gramaticais (tons, partículas, negação, estrutura SVO).
- Verificar se todas as notas de vocab têm frontmatter completo conforme novo schema.
- Migração opcional das pastas `Lote N` para `vocab/Lote N/` (não urgente).

---

## [2026-05-02] ingest | Criação das primeiras páginas wiki (conceitos e radicais)

**Páginas criadas**:
- `wiki/conceitos/Os Quatro Tons do Mandarim.md` — Explica os 4 tons + tom neutro, sandhi tonal, com links para todo o vocab HSK1 organizado por tom.
- `wiki/radicais/女 - Mulher.md` — Radical 女, aparece em 好, 她, 妈妈.
- `fontes/README.md` — Instruções para a pasta de fontes brutas.

**Próximos radicais prioritários**: 人/亻 (aparece em 你, 他, 们, 人), 口 (aparece em 吃, 吗, 呢), 日 (aparece em 日, 明天).

---


---


## [2026-05-02] ingest | Compilacao completa fontes wiki (Lote 9 + Sinteses + Radicais)

**Operacao**: Compilacao de todos os arquivos de fonte para o wiki seguindo o schema do AGENTS.md.

**Fontes processadas**:
- fontes/Lista de vocabulario HSK 1.md - lista oficial de 150 palavras
- fontes/Lote 0-8/*.md - 41 notas de vocabulario existentes

**Paginas wiki criadas**:
- Lote 0-8: 41 notas recompiladas com schema completo
- Lote 9: 56 novas notas de vocab da lista oficial HSK1
- Radicais: 2 novas paginas (Pessoa 人, Boca 口)
- Sinteses: 2 novas paginas (Familia 电, Particulas Modais)

**Estatisticas**: 93 paginas wiki | 97 notas de vocab (65% HSK1) | 3 radicais | 2 sinteses | 1 conceito

**Pendentes (~53 palavras)**: 爱, 杯子, 本, 点, 东西, 都, 儿子, 个, 汉语, 号, 后面, 几, 块, 了, 里, 没关系, 认识, 睡觉, 太, 天气, 同学, 喂, 些, 先生, 一点儿, 衣服, 椅子, 怎么, 怎么样, 字, 住, 桌子, 坐, 做, 分钟, 钱, 岁...

**Proximas acoes**: Lint | Lote 9 continuacao | Conceito: Negacao 不没 | Radical 日

---
