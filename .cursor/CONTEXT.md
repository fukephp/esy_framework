# Project — agent context

This file is the source of truth for everything under `.cursor/`. Read it before applying rules, skills, commands, or hooks. Product scope lives in `docs/mvp/`. Target architecture lives in `docs/architecture/`. Fill this file when the project locks product and stack decisions. See `AGENTS.md`.

## Product (fill when locked)

- One-paragraph product summary
- Who uses it; core flows
- Explicit non-goals for the current phase

Prefer `docs/mvp/` over inventing behavior.

## Architecture (fill when locked)

- Short stack summary (link out to `docs/architecture/`)
- **App root** — folder where application commands and verify runners live (add when the project needs one; no default name in the framework)
- **Stories source** — path to stories (`docs/mvp/…` or `docs/stories/…`) used by story-loop
- **Domain triggers** — fog-gate topics for story-loop (e.g. auth, payments, new user-facing surface). Leave empty until locked; then list them here

Do not invent a different stack. Do not scaffold app code unless the user asks.

## Folder map

| Path | Role |
|------|------|
| `docs/mvp/` | Product scope |
| `docs/architecture/` | Stack and system design |
| `docs/stories/` | User stories |
| `docs/tasks/` | Implementation tasks |
| `docs/diagrams/` | Diagrams |
| `docs/glossary.md` | Domain glossary (lazy; grill-with-docs). Not `.cursor/CONTEXT.md`. |
| `docs/adr/` | ADRs (lazy; grill-with-docs) |
| `DESIGN.md` | Index of design packs under `refs/` |
| `refs/` | Design packs (empty until locked) |
| `rules/frontend/` | UI conventions when frontend files are in play |
| `rules/backend/` | API and data conventions when backend files are in play |
| `hooks/` | Scripts wired in `hooks.json` (session injects this file) |
| `skills/grill-me/` | Relentless interview of a plan or design; writes nothing — default when there is no app code |
| `skills/grill-with-docs/` | Same interview against a codebase; writes `docs/glossary.md` + `docs/adr/` as terms/decisions lock |
| `skills/scaffold-project/` | Copy this framework into a new sibling project under `Projects/` |
| `skills/sync-framework/` | Propagate allowlisted Cursor defaults into one existing sibling (`/sync-framework`) |
| `skills/story-loop/` | Story-sized Loop Engineering: answer key → Hybrid implement → Bugbot |
| `skills/custom-feature-skills/` | How to add a feature against epics/stories |
| `skills/deploy-staging/` | How to ship to staging |
| `skills/tailwindcss/` | Tailwind utility-first UI |
| `skills/design-first-ui-prompting/` | Spec-driven UI prompts |
| `skills/landing-page/` | Marketing landing pages |
| `skills/pricing-page/` | Marketing pricing pages |
| `skills/build-awwwards-quality-sites/` | Marketing polish |
| `loops/` | Story-loop playbook, Wayfinder-lite maps, answer-key templates, and per-story keys |
| `commands/` | Slash workflows (`/generate-docs`, `/run-tests`, `/scaffold-project`, `/sync-framework`, `/story-loop`, `/grill-with-docs`) |

## How to follow this file

1. Prefer `docs/mvp/` over inventing product behavior.
2. Prefer `docs/architecture/` over inventing a stack.
3. Do not expand scope into later phases unless the user asks.
4. Update this file when a locked product or architecture decision lands.
5. Before UI work, read root `DESIGN.md`, then the matching pack under `refs/` if it exists.
6. Before locking a plan or design: **grill-me** when there is no app code (writes nothing). **grill-with-docs** (`/grill-with-docs`) when application code exists — same interview, writes glossary + ADRs.
7. To bootstrap a new sibling project from this framework, use **scaffold-project** or `/scaffold-project`. To propagate allowlisted defaults into an existing sibling, use **sync-framework** or `/sync-framework <name>`.
8. Use MengTo UI skills when the user asks for Tailwind, design-first prompting, landing, pricing, or marketing polish. Do not scaffold a marketing site unless asked.
9. Story loops: use `skills/story-loop/` and `loops/PLAYBOOK.md` for one story → one PR. Runtime is Hybrid: Local default; Cloud on `unattended` (short paste, no `briefs/` folder). Coding loops need an app root with real verify commands; until then use plan-gate only (map / answer key). Fill stories source, app root, and domain triggers above when locked. Prefer grill-me while product fog is open and there is no app code; prefer grill-with-docs once a codebase exists. UI stories: embed desktop + mobile screenshots in the PR description (see playbook **PR visual evidence**).
