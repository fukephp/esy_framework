# Cursor AI framework

Reusable git root for Cursor-driven projects: agent context, rules, skills, commands, and docs stubs.

No application code lives here. Use **scaffold-project** to copy this layout into a new sibling repo, fill `.cursor/CONTEXT.md` and `docs/`, then add your app tree when ready.

## Layout

| Path | Role |
|------|------|
| `AGENTS.md` | How agents work in this repo |
| `DESIGN.md` | Design pack index (fill when designs lock) |
| `.cursor/` | Context, rules, skills, commands, hooks |
| `docs/` | Product, architecture, stories, tasks, diagrams |
| `refs/` | Design reference packs (empty until you add them) |

## Scaffold a new project

This repo is the canonical template. Clone or keep it wherever you like; scaffold creates a **sibling** folder next to it.

### Slash command

```text
/scaffold-project my_app
```

Creates a sibling folder named `my_app` with the framework layout (no app code), runs `git init`, and leaves `CONTEXT.md` empty for you to fill.

### Skill

Ask the agent to **scaffold a project** / **new project from framework** / **bootstrap from esy_framework**, or attach the `scaffold-project` skill. Same workflow as the command — steps live in `.cursor/skills/scaffold-project/SKILL.md`.

### After scaffold

1. Open the new folder as the Cursor workspace.
2. Run **grill-me** before locking product and architecture.
3. Fill `.cursor/CONTEXT.md` and expand `docs/` as decisions lock.
4. Add application code when ready; keep docs and `.cursor/` at the git root.

Improvements to this framework only affect **new** scaffolds (no sync into old projects in v1).

## Getting started (in a project)

1. Fill `.cursor/CONTEXT.md` for the product.
2. Expand `docs/mvp/` and `docs/architecture/` as decisions lock.
3. Stress-test plans with the **grill-me** skill before building.
4. Add app code in a folder you choose; keep docs and `.cursor/` at the git root.
