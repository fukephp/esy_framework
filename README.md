# Cursor AI framework

Reusable git root for Cursor-driven projects: agent context, rules, skills, commands, and docs stubs.

No application code lives here. Use **scaffold-project** to copy this layout into a new sibling repo, fill `.cursor/CONTEXT.md` and `docs/`, then add your app tree when ready.

## Layout

| Path | Role |
|------|------|
| `AGENTS.md` | How agents work in this repo |
| `DESIGN.md` | Design pack index (fill when designs lock) |
| `.cursor/` | Context, rules, skills, commands, hooks, loops |
| `docs/` | Product, architecture, stories, diagrams |
| `refs/` | Design reference packs (empty until you add them) |

## How it works (diagrams)

| Diagram | File |
|---------|------|
| Lifecycle: once per project (scaffold → lock including persist stories) then once per story (draft key → you approve → story-loop / plan-gate → PR) | [docs/diagrams/lifecycle.md](docs/diagrams/lifecycle.md) |
| Truth map: where docs and `.cursor/` sit relative to the app | [docs/diagrams/truth-map.md](docs/diagrams/truth-map.md) |

Index: [docs/diagrams/index.md](docs/diagrams/index.md). Mermaid is the source; screenshot for slides.

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
2. Run **grill-me** before locking product and architecture (no app code yet). A finished product grill persists `docs/mvp/` and `docs/stories/STORY-xx.md`.
3. Fill `.cursor/CONTEXT.md` (app root and domain triggers when ready). Stories source is `docs/stories/`.
4. Add application code when ready; keep docs and `.cursor/` at the git root. After that, use **grill-with-docs** / `/grill-with-docs` so glossary, ADRs, and product/stories persist land on disk.
5. When shipping one story with an answer key, use **story-loop** / `/story-loop` (see `.cursor/loops/PLAYBOOK.md`).

## Improving this template

Change `esy_framework` here when you want better structure for the next scaffold. New projects get the update on scaffold. To push allowlisted Cursor defaults into an existing sibling project:

```text
/sync-framework esyres_project
```

See `.cursor/skills/sync-framework/SKILL.md` (overwrite allowlist + summary; one name per run; does not touch CONTEXT, product docs, or story keys).

## Getting started (in a project)

1. Fill `.cursor/CONTEXT.md` for the product.
2. Expand `docs/mvp/` and `docs/architecture/` as decisions lock (numbered docs when decisions lock — not pre-created empty files). Product grill persist also writes `docs/stories/STORY-xx.md`.
3. Stress-test plans with **grill-me** (no code; persist at end of topic) or **grill-with-docs** (codebase; glossary/ADRs as they lock; product/stories end-batch).
4. Add app code in a folder you choose; keep docs and `.cursor/` at the git root.
5. Use **story-loop** for one story → one PR once verify commands exist.
