# Agent instructions

This git root is the Cursor/docs workspace. Application code is not part of this framework layout — add an app folder only when a real project needs one.

## Layout

- `docs/` — product (`docs/mvp/`), architecture (`docs/architecture/`), stories (`docs/stories/`), diagrams; lazy `docs/glossary.md` and `docs/adr/` from domain-modeling (via grill-with-docs)
- `.cursor/` — rules, skills, commands, hooks
- `refs/` — design packs when locked
- `AGENTS.md` — this file
- `DESIGN.md` — design index

Do not put docs, rules, or skills inside an application folder. Do not invent product behavior or stack when `docs/` is empty — ask or grill first.

## Working directory

- Git, and edits to `docs/` / `.cursor/` / this file: run from the git root.
- When a project adds application code, run app commands (`composer`, `npm`, `docker compose`, tests) from that app folder — not the git root unless the project says otherwise.

## Product and architecture

Read `.cursor/CONTEXT.md`. Prefer `docs/mvp/` and `docs/architecture/` over inventing behavior or stack.

## Plans and designs

Before locking a plan or design, prefer **grilling** over guessing:

- **grilling** (`.cursor/skills/grilling/`) — default interview engine (rounds/frontier); auto before locking a plan
- **grill-me** (`.cursor/skills/grill-me/`, `/grill-me`) — user-invoked; no app code, or a throwaway interview; persist at end of topic (mvp, `docs/stories/STORY-xx.md`, architecture, CONTEXT as decided)
- **grill-with-docs** (`.cursor/skills/grill-with-docs/`, `/grill-with-docs`) — user-invoked when application code exists; glossary + ADRs as terms/decisions lock via domain-modeling; product/stories end-batch. Do not treat `.cursor/CONTEXT.md` as a glossary.

## Story loops

For one story from `docs/stories/` → one PR with an approved answer key, use **story-loop** (`.cursor/skills/story-loop/`, `/story-loop`) and `.cursor/loops/PLAYBOOK.md`. Runtime is Hybrid: Local default; Cloud on `unattended`. Coding loops need an app root with verify commands named in CONTEXT. Story-loop consumes `STORY-xx` files; it does not create them.

## New projects from this framework

To copy this layout into a sibling folder under `Projects/`, use the **scaffold-project** skill or `/scaffold-project <name>`. See `README.md` and `.cursor/skills/scaffold-project/SKILL.md`.

## Improving this template

Edit `esy_framework` directly when you want better defaults for future projects. New scaffolds pick up those changes. To propagate allowlisted Cursor defaults into an already-scaffolded sibling, use **sync-framework** (`.cursor/skills/sync-framework/`, `/sync-framework <name>`). Do not invent a separate “improve framework” skill — edit this repo, then sync.
