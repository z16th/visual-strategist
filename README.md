# Visual Strategist

A Claude Code agent that defines a product's visual language and keeps it coherent as the product grows: icons, type, colour, layout and motion. It critiques screens and assets, proposes coded design options, runs value sweeps and writes visual language specs.

This repo is a Claude Code plugin marketplace with two plugins:

| Plugin | What it adds |
| --- | --- |
| `visual-strategist` | The `visual-strategist:strategist` agent and the `visual-strategist:option-boards` skill |
| `core-strategist` | The `core-strategist:method` skill: discovery, critique, coded options, specs, decision logs and handoffs. `visual-strategist` depends on it |

## Install for yourself

```bash
claude plugin marketplace add z16th/visual-strategist
claude plugin install visual-strategist@z16th
```

This also installs `core-strategist`.

## Offer it to everyone working in a project

Add this to the project's `.claude/settings.json`. Claude Code offers to install the plugins when someone trusts the folder.

```json
{
  "extraKnownMarketplaces": {
    "z16th": {
      "source": { "source": "github", "repo": "z16th/visual-strategist" }
    }
  },
  "enabledPlugins": {
    "core-strategist@z16th": true,
    "visual-strategist@z16th": true
  }
}
```

To keep a project on a known version, tag a release here and add `"ref": "<tag>"` to the source.

## Use it

- **As a subagent:** ask Claude to use the visual strategist, or name `visual-strategist:strategist`.
- **As the main agent:** in any folder, create `.claude/settings.json` containing `{ "agent": "visual-strategist:strategist" }` and start Claude Code there.

## Project details stay in the project

This repo has no details about any project, and should stay that way. Each project keeps its facts, decisions and visual spec in its own brief, a skill named `<project>-brief` at `<project-repo>/.claude/skills/<project>-brief/SKILL.md`. If a project has no brief yet, the strategist runs discovery and writes one there.

The agent also keeps its own memory on each machine, at user scope. That memory never comes from or goes to this repo.

If a lesson from a project is worth adding here, write it so it applies to any product: no project names, paths, examples or languages.

## What it works with

- **Doop**, the shared design canvas, for option boards. Connect its MCP server to Claude Code. Without it, the strategist can still critique, preview options in chat and write specs.
- **A headless Chromium** (optional), such as Playwright's `chrome-headless-shell`, to screenshot labs outside Doop.
