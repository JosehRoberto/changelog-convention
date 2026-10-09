# changelog-convention

Skill no padrão **[Agent Skills](https://agentskills.io)** com a **convenção para manter arquivos `CHANGELOG.md`** nos projetos deste computador: histórico cronológico, sem duplicatas e sem ambiguidade de numeração. Compatível com **OpenCode**, **Claude Code** e **OpenClaude** (e outros harnesses que suportam o padrão).

## Conteúdo

| Arquivo | Descrição |
|---|---|
| `SKILL.md` | A convenção (estrutura, ordem, versionamento por eras, formato das entradas, tipos, regras FAZER/NÃO FAZER, manutenção). |
| `templates/CHANGELOG.template.md` | Modelo para copiar em projetos novos. |

## Instalação

A skill segue o padrão **[Agent Skills](https://agentskills.io)** (`SKILL.md` com frontmatter `name`/`description`), então funciona em vários harnesses. Escolha o **escopo** e o **harness**.

### Escopo: global × local do projeto

- **Global (na máquina):** vale para **todos os seus projetos**; não é versionado no projeto.
- **Local do projeto:** fica dentro do repositório e é **compartilhado com o time** (comite a pasta da skill).
- **Recomendado aqui:** instalar **global via symlink** para este repositório (fonte única) — editar no repo reflete no harness.

Uma skill é uma pasta com `SKILL.md` (e arquivos de apoio, como `templates/`).

### OpenCode

Locais de descoberta (docs oficiais `opencode.ai/docs/skills`):

| Escopo | Caminho |
|---|---|
| Projeto (OpenCode) | `.opencode/skills/<name>/SKILL.md` |
| Global (OpenCode) | `~/.config/opencode/skills/<name>/SKILL.md` |
| Projeto (Claude-compat) | `.claude/skills/<name>/SKILL.md` |
| Global (Claude-compat) | `~/.claude/skills/<name>/SKILL.md` |
| Projeto (agent-compat) | `.agents/skills/<name>/SKILL.md` |
| Global (agent-compat) | `~/.agents/skills/<name>/SKILL.md` |

Global (symlink, recomendado):

```bash
ln -sfn ~/projetos/changelog-convention \
        ~/.config/opencode/skills/changelog-convention
```

Local do projeto (cópia, para comitar):

```bash
mkdir -p .opencode/skills
cp -r ~/projetos/changelog-convention .opencode/skills/changelog-convention
```

### Claude Code

| Escopo | Caminho |
|---|---|
| Pessoal (global) | `~/.claude/skills/<name>/SKILL.md` |
| Projeto | `.claude/skills/<name>/SKILL.md` (comitar para o time) |
| Enterprise | `.claude/skills/` no diretório de *managed settings* |
| Plugin | `<plugin>/skills/<name>/SKILL.md` |

Pessoal (symlink):

```bash
ln -sfn ~/projetos/changelog-convention \
        ~/.claude/skills/changelog-convention
```

Projeto (cópia): `cp -r ~/projetos/changelog-convention .claude/skills/changelog-convention`

### OpenClaude

[OpenClaude](https://openclaude.gitlawb.com/) é um harness open-source derivado do Claude Code. Guarda a própria config em `~/.openclaude` (ou `OPENCLAUDE_CONFIG_DIR`) e **não lê** `~/.claude` nem `.claude/`.

| Escopo | Caminho |
|---|---|
| Usuário (global) | `~/.openclaude/skills/<name>/SKILL.md` |
| Projeto | `.openclaude/skills/<name>/SKILL.md` |

Instalação pelo próprio CLI:

```bash
openclaude skills install ~/projetos/changelog-convention --global   # usuário
openclaude skills install ~/projetos/changelog-convention            # projeto
```

Verificação: `openclaude skills list`.

### Por sistema operacional

**GNU/Linux e macOS** — use os caminhos acima; prefira **symlink**:

```bash
# troque o destino conforme o harness:
ln -sfn ~/projetos/changelog-convention ~/.config/opencode/skills/changelog-convention   # OpenCode
ln -sfn ~/projetos/changelog-convention ~/.claude/skills/changelog-convention            # Claude Code
ln -sfn ~/projetos/changelog-convention ~/.openclaude/skills/changelog-convention        # OpenClaude
```

**Windows** — duas opções:

1. **WSL (recomendado):** rode o harness dentro do WSL e use os caminhos Linux acima (o `~` é o home do WSL).
2. **Nativo:** copie a pasta (symlink exige privilégio). Caminhos:

   | Harness | Caminho |
   |---|---|
   | OpenCode | `%USERPROFILE%\.config\opencode\skills\changelog-convention` |
   | Claude Code | `%USERPROFILE%\.claude\skills\changelog-convention` |
   | OpenClaude | `%USERPROFILE%\.openclaude\skills\changelog-convention` |

   Symlink nativo (habilite o **Modo de Desenvolvedor**), em CMD:

   ```bat
   mklink /D "%USERPROFILE%\.config\opencode\skills\changelog-convention" "%USERPROFILE%\projetos\changelog-convention"
   ```

   ou em PowerShell:

   ```powershell
   New-Item -ItemType SymbolicLink -Path "$env:USERPROFILE\.config\opencode\skills\changelog-convention" -Target "$env:USERPROFILE\projetos\changelog-convention"
   ```

> **Dica:** `~/.agents/skills/` (global) e `.agents/skills/` (projeto) são lidos pelo OpenCode no padrão *agent-compatible* — um local neutro entre harnesses.

## Uso

A skill é aplicada automaticamente quando o assunto é criar/revisar um `CHANGELOG.md` (em qualquer projeto). Este projeto segue a própria convenção — ver [`CHANGELOG.md`](CHANGELOG.md).

## Convenção aplicada (resumo)

- `## [Unreleased]` no topo; `## [x.y.z] - AAAA-MM-DD` em ordem **decrescente**.
- Entradas: `### vX.Y (DD/MM/AAAA) — Título` (marco) ou `### <Tipo> (DD/MM/AAAA) — Título` (pontual).
- Tipos: Adicionado, Alterado, Corrigido, Removido, Segurança, Obsoleto, Documentação, Validado em produção, Resolvido.
- **Eras de versionamento**: nunca misturar séries; separar com nota + divisor `## Histórico legado (...)`.
