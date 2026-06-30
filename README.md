# scripts

Personal global scripts. This directory is on `PATH` (added via `~/.zshrc`), so
any executable file dropped here becomes a global command.

## gcm — AI git commit message

Analyzes the **staged** changes in the current git repo, asks DeepSeek to write a
[Conventional Commits](https://www.conventionalcommits.org/) message (English),
previews it for confirmation, and commits.

### Setup

```sh
cp .env.example .env
# edit .env and set DEEPSEEK_API_KEY
```

`.env` lives next to the `gcm` script and is gitignored.

| Variable           | Required | Default             |
| ------------------ | -------- | ------------------- |
| `DEEPSEEK_API_KEY` | yes      | —                   |
| `DEEPSEEK_MODEL`   | no       | `deepseek-v4-flash` |

### Usage

```sh
git add -p          # stage what you want to commit
gcm                 # generate → preview → confirm → commit
```

At the prompt:

- `y` — commit the message
- `e` — edit it in `$EDITOR` (falls back to `vi`)
- `r` — regenerate
- `n` — abort

### Requirements

- Node.js 18+ (uses the built-in `fetch`; zero dependencies)
- `git`
