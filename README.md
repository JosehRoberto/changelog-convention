# changelog-convention

Skill do [OpenCode](https://opencode.ai) com a **convenção para manter arquivos `CHANGELOG.md`** nos projetos deste computador: histórico cronológico, sem duplicatas e sem ambiguidade de numeração.

## Conteúdo

| Arquivo | Descrição |
|---|---|
| `SKILL.md` | A convenção (estrutura, ordem, versionamento por eras, formato das entradas, tipos, regras FAZER/NÃO FAZER, manutenção). |
| `templates/CHANGELOG.template.md` | Modelo para copiar em projetos novos. |

## Instalação (OpenCode)

O OpenCode descobre skills em `~/.config/opencode/skills/`. Recomenda-se **symlink** para manter este repositório como fonte única:

```bash
ln -sfn ~/projetos/changelog-convention \
        ~/.config/opencode/skills/changelog-convention
```

Alternativa (cópia):

```bash
cp -r ~/projetos/changelog-convention \
      ~/.config/opencode/skills/changelog-convention
```

## Uso

A skill é aplicada automaticamente quando o assunto é criar/revisar um `CHANGELOG.md` (em qualquer projeto). Este projeto segue a própria convenção — ver [`CHANGELOG.md`](CHANGELOG.md).

## Convenção aplicada (resumo)

- `## [Unreleased]` no topo; `## [x.y.z] - AAAA-MM-DD` em ordem **decrescente**.
- Entradas: `### vX.Y (DD/MM/AAAA) — Título` (marco) ou `### <Tipo> (DD/MM/AAAA) — Título` (pontual).
- Tipos: Adicionado, Alterado, Corrigido, Removido, Segurança, Obsoleto, Documentação, Validado em produção, Resolvido.
- **Eras de versionamento**: nunca misturar séries; separar com nota + divisor `## Histórico legado (...)`.
