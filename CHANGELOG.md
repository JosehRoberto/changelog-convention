# Changelog

> Convenção: a própria skill (`SKILL.md`). Ordem **cronológica decrescente**;
> não misturar séries de numeração sem a **nota + divisor**.

## [Unreleased]

### Documentação (09/10/2026) — Descrição harness-agnóstica no README

- **README:** primeira linha passou de "Skill do OpenCode" para "Skill no padrão **Agent Skills**", refletindo o suporte a OpenCode, Claude Code e OpenClaude.

### Documentação (09/10/2026) — Guia de instalação multi-harness e multi-SO

- **README:** seção "Instalação" expandida — escopo **global × local do projeto**, locais por **harness** (OpenCode, Claude Code, OpenClaude) e por **SO** (GNU/Linux, macOS, Windows/WSL/nativo), com exemplos de symlink e cópia.

## [1.0.0] - 2026-10-09

### Adicionado — Skill `changelog-convention`

- **SKILL.md:** estrutura do arquivo, ordem cronológica, versionamento por eras, formato das entradas, tipos padronizados, regras FAZER/NÃO FAZER e manutenção.
- **templates/CHANGELOG.template.md:** modelo para copiar em projetos novos.
- **README.md:** instalação (symlink/cópia) e resumo da convenção.
- **CHANGELOG.md:** este arquivo.
- **Arquivos:** `SKILL.md`, `templates/CHANGELOG.template.md`, `README.md`, `CHANGELOG.md`.

## Legenda

- **Adicionado** — novas funcionalidades
- **Alterado** — mudanças em funcionalidades existentes
- **Corrigido** — correções de bugs
- **Removido** — funcionalidades removidas
- **Segurança** — correções de vulnerabilidades
- **Obsoleto** — funcionalidades marcadas para remoção futura
