# Agent instructions

This git root is the Cursor/docs workspace. Application code is not part of this framework layout — add an app folder only when a real project needs one.

## Layout

- `docs/` — product (`docs/mvp/`) and architecture (`docs/architecture/`); also stories, tasks, diagrams
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

Before locking a plan or design, use the **grill-me** skill (`.cursor/skills/grill-me/`) until shared understanding. Prefer grilling over guessing.

## Story loops

For one story → one PR with an answer key and Cloud Agent brief, use **story-loop** (`.cursor/skills/story-loop/`, `/story-loop`) and `.cursor/loops/PLAYBOOK.md`. Coding loops need an app root with verify commands named in CONTEXT.

## New projects from this framework

To copy this layout into a sibling folder under `Projects/`, use the **scaffold-project** skill or `/scaffold-project <name>`. See `README.md` and `.cursor/skills/scaffold-project/SKILL.md`.

## Improving this template

Edit `esy_framework` directly when you want better defaults for future projects. New scaffolds pick up those changes. Do not sync framework updates into already-scaffolded projects (v1). Do not invent a separate “improve framework” skill.
