# Cursor CLI tools (fewer tokens, faster agents)

Tools that shrink shell/context noise and keep Cursor agents lean.

## RTK

[rtk-ai/rtk](https://github.com/rtk-ai/rtk) — compresses shell command output before it reaches the agent.

```bash
brew install rtk
rtk init -g --agent cursor   # global Cursor preToolUse hook → ~/.cursor/hooks.json runs `rtk hook cursor`
rtk gain                     # measure savings
```

## Ponytail

[DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail) (MIT) — rule/skill that pushes minimal code and terse replies.

Official Cursor install (hooks):

```bash
git clone https://github.com/DietrichGebert/ponytail
node ponytail/scripts/cursor-hooks.js install
```

Or paste a short Ponytail rule into Cursor User Rules. Use **hooks or rule, not both**.

## Fast CLI toolkit

| Tool | Purpose | Repo |
|------|---------|------|
| `rg` (ripgrep) | Fast recursive search | [BurntSushi/ripgrep](https://github.com/BurntSushi/ripgrep) |
| `fd` | Fast file finder (`find` replacement) | [sharkdp/fd](https://github.com/sharkdp/fd) |
| `jq` | JSON query/filter | [jqlang/jq](https://github.com/jqlang/jq) |
| `yq` | YAML/XML/TOML query (jq-like) | [mikefarah/yq](https://github.com/mikefarah/yq) |
| `ast-grep` | Structural code search and edits | [ast-grep/ast-grep](https://github.com/ast-grep/ast-grep) |
| `gh` | GitHub PRs, issues, CI from the terminal | [cli/cli](https://github.com/cli/cli) |
| `difft` (difftastic) | Structural / syntax-aware diffs | [Wilfred/difftastic](https://github.com/Wilfred/difftastic) |
| `tokei` | Fast lines-of-code / repo overview | [XAMPPRocky/tokei](https://github.com/XAMPPRocky/tokei) |

```bash
brew install ripgrep fd jq yq ast-grep gh difftastic tokei
gh auth login   # once
```

## Agent rule text

Shell: prefer `rg` over grep, `fd` over find, `jq`/`yq` to extract only needed fields, `ast-grep` for structural code search/edits, `gh` for GitHub PRs/issues/CI, `tokei` for repo overview. Keep output small: filter, use `| head`, `--quiet`, failures-only test flags; never dump whole large files or logs.
