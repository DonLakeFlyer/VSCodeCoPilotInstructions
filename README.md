# VSCodeCoPilotInstructions

Personal GitHub Copilot custom instructions, shared across machines.

Copilot loads personal (user-level) instructions from `~/.copilot/instructions`.
That folder is not synced by VS Code Settings Sync, so this repo holds the files
and `~/.copilot/instructions` is a symlink to the repo's `instructions/` folder.

## Layout

```text
instructions/                       # symlink target for ~/.copilot/instructions
  my-preferences.instructions.md    # feature workflow, commit, PR, and code style preferences
  test-policy.instructions.md       # test levels, reproduce-first bug fixes, coverage reporting
```

Only the `instructions/` folder is linked, so the rest of the repo (this README,
`.git/`) stays out of the folder Copilot scans.

## Setup on a new machine

### macOS / Linux

```bash
git clone https://github.com/DonLakeFlyer/VSCodeCoPilotInstructions.git ~/repos/VSCodeCoPilotInstructions

# Back up any existing instructions first, then replace the folder with a symlink
[ -d ~/.copilot/instructions ] && [ ! -L ~/.copilot/instructions ] && mv ~/.copilot/instructions ~/.copilot/instructions.bak
mkdir -p ~/.copilot
ln -s ~/repos/VSCodeCoPilotInstructions/instructions ~/.copilot/instructions
```

Verify:

```bash
ls -la ~/.copilot/instructions   # should show: instructions -> .../VSCodeCoPilotInstructions/instructions
```

### Windows (PowerShell)

Creating a symlink requires Developer Mode or an elevated shell.

```powershell
git clone https://github.com/DonLakeFlyer/VSCodeCoPilotInstructions.git "$HOME\repos\VSCodeCoPilotInstructions"

if (Test-Path "$HOME\.copilot\instructions") { Rename-Item "$HOME\.copilot\instructions" instructions.bak }
New-Item -ItemType Directory -Force "$HOME\.copilot" | Out-Null
New-Item -ItemType SymbolicLink -Path "$HOME\.copilot\instructions" -Target "$HOME\repos\VSCodeCoPilotInstructions\instructions"
```

## Updating

Edit files in `instructions/` (directly or through `~/.copilot/instructions`,
which is the same folder), then commit and push. On other machines, `git pull`.
Changes apply to new chat sessions.

## Adding instructions

- Files must be named `*.instructions.md` and placed in `instructions/`
  (subfolders are fine; the folder is searched recursively).
- Use frontmatter to control when they apply, for example:

  ```markdown
  ---
  description: "When to use these instructions"
  applyTo: "**"
  ---
  ```

## Which sessions use these

`~/.copilot/instructions` is read by the **Copilot** harness (the Copilot
Session Target in VS Code, Copilot CLI, and the Copilot app). Other harnesses
look elsewhere:

| Session Target | Personal instructions location |
| -------------- | ------------------------------ |
| Copilot        | `~/.copilot/instructions`      |
| Claude         | `~/.claude/rules`              |
| Local          | VS Code profile storage        |

See [Use custom instructions in VS Code](https://code.visualstudio.com/docs/agent-customization/custom-instructions).
