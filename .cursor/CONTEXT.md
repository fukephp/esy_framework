# Project — agent context

This file is the source of truth for everything under `.cursor/`. Read it before applying rules, skills, commands, or hooks. Product scope lives in `docs/mvp/`. Target architecture lives in `docs/architecture/`. Fill this file when the project locks product and stack decisions. See `AGENTS.md`.

## Product (fill when locked)

- One-paragraph product summary
- Who uses it; core flows
- Explicit non-goals for the current phase

Prefer `docs/mvp/` over inventing behavior.

## Architecture (fill when locked)

- Short stack summary (link out to `docs/architecture/`)
- Where application code will live (add a folder when the project needs one)

Do not invent a different stack. Do not scaffold app code unless the user asks.

## Folder map

| Path | Role |
|------|------|
| `docs/mvp/` | Product scope |
| `docs/architecture/` | Stack and system design |
| `docs/stories/` | User stories |
| `docs/tasks/` | Implementation tasks |
| `docs/diagrams/` | Diagrams |
| `DESIGN.md` | Index of design packs under `refs/` |
| `refs/` | Design packs (empty until locked) |
| `rules/frontend/` | UI conventions when frontend files are in play |
| `rules/backend/` | API and data conventions when backend files are in play |
| `hooks/` | Scripts wired in `hooks.json` (session injects this file) |
| `skills/grill-me/` | Relentless interview of a plan or design until shared understanding — default before locking plans |
| `skills/scaffold-project/` | Copy this framework into a new sibling project under `Projects/` |
| `skills/custom-feature-skills/` | How to add a feature against epics/stories |
| `skills/deploy-staging/` | How to ship to staging |
| `skills/tailwindcss/` | Tailwind utility-first UI |
| `skills/design-first-ui-prompting/` | Spec-driven UI prompts |
| `skills/landing-page/` | Marketing landing pages |
| `skills/pricing-page/` | Marketing pricing pages |
| `skills/build-awwwards-quality-sites/` | Marketing polish |
| `commands/` | Slash workflows (`/generate-docs`, `/run-tests`, `/scaffold-project`) |

## How to follow this file

1. Prefer `docs/mvp/` over inventing product behavior.
2. Prefer `docs/architecture/` over inventing a stack.
3. Do not expand scope into later phases unless the user asks.
4. Update this file when a locked product or architecture decision lands.
5. Before UI work, read root `DESIGN.md`, then the matching pack under `refs/` if it exists.
6. Before locking a plan or design, use **grill-me**.
7. To bootstrap a new sibling project from this framework, use **scaffold-project** or `/scaffold-project`.
8. Use MengTo UI skills when the user asks for Tailwind, design-first prompting, landing, pricing, or marketing polish. Do not scaffold a marketing site unless asked.
