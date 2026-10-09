---
name: changelog-convention
description: Convenção para manter arquivos CHANGELOG.md neste computador — estrutura, ordem cronológica, versionamento por eras, formato das entradas, tipos padronizados e template. Use sempre que criar, revisar ou atualizar um CHANGELOG.md (em qualquer projeto), ou ao definir o changelog de um projeto novo.
---

# Skill: changelog-convention

> Padrão adotado nos projetos deste computador para manter o `CHANGELOG.md`.
> Objetivo: histórico **cronológico**, **sem duplicatas** e **sem ambiguidade de numeração**.
> Idioma: **português brasileiro (pt-BR)**.

## 1. Estrutura do arquivo

- `## [Unreleased]` no **topo** — log da série atual (trabalho em andamento/recém-concluído).
- `## [x.y.z] - AAAA-MM-DD` para cada release/série, em ordem **decrescente**.
- `### …` para as entradas dentro de cada seção.
- `## Legenda` no final (lista dos tipos).
- **Ordem:** sempre a mais recente primeiro (decrescente por data).

## 2. Versionamento por "eras" (regra de ouro)

Quando a numeração do projeto sofrer **reset** (migração, renomeação de repositório,
mudança de esquema), **não misture** as séries. Separe com **nota + divisor**,
imediatamente antes do bloco antigo:

```markdown
---

> **Nota de versionamento.** O `[Unreleased]` e `[x.y.z]` (mês/ano) formam a **série atual** do projeto `<nome>`. Os blocos abaixo — `[a.b.c]` → `[d.e.f]`, com data **até AAAA-MM-DD** — são o **histórico legado** da numeração anterior à migração.

## Histórico legado (pré-<marco> — até AAAA-MM-DD)
```

Isso evita o erro clássico de "2.x de setembro aparecer depois de 1.x de outubro".

## 3. Formato das entradas

Duas formas (ambas com `— Título` e, quando aplicável, a data `(DD/MM/AAAA)`):

- **Marco de versão** (entrega relevante): `### vX.Y (DD/MM/AAAA) — Título`
- **Mudança pontual**: `### <Tipo> (DD/MM/AAAA) — Título`

**Tipos padronizados:** `Adicionado`, `Alterado`, `Corrigido`, `Removido`,
`Segurança`, `Obsoleto`, `Documentação`, `Validado em produção`, `Resolvido`.

## 4. Corpo da entrada

- Bullets no formato `- **Rótulo:** descrição.`
- Incluir `- **Arquivos:** ...` quando fizer sentido.
- Incluir `- **Testes:** +N. Suíte em **M**.` (atualiza a contagem total da suíte).
- Referenciar `docs/`, issues e PRs quando útil.

## 5. Regras — FAZER / NÃO FAZER

**FAZER**
- Ordem cronológica decrescente.
- Uma entrada por unidade lógica de trabalho.
- Atualizar a contagem de testes ao final das entradas de código.
- Registrar a **causa-raiz** nas correções.
- Permitir `docs:` como commit separado do código.

**NÃO FAZER**
- ❌ Duplicar blocos/seções (ex.: dois `### vX.Y.z` iguais).
- ❌ Deixar "Em investigação" após resolver (mudar para `Resolvido`).
- ❌ Misturar séries de numeração sem a nota + divisor.
- ❌ Reordenar/reestruturar de forma a perder conteúdo.
- ❌ Expor segredos (tokens, senhas) no CHANGELOG.

## 6. Manutenção

1. Antes de editar: backup (`cp CHANGELOG.md backup/CHANGELOG_<ts>.bak`).
2. Adicionar a entrada no `[Unreleased]` (ou na seção de release correspondente).
3. Não mover entradas antigas sem motivo.
4. Commit do tipo `docs:`.

## 7. Template

Modelo pronto em `templates/CHANGELOG.template.md` — copie para `CHANGELOG.md` ao
iniciar um projeto novo e substitua os marcadores `<...>`.
