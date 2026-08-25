---
version: stub
name: Design index
description: Index for visual design packs. Read the matching pack before UI work — do not mix packs.
---

## Overview

Add one folder per locked design under `refs/`:

| Design | Scope | Spec |
|--------|--------|------|
| **Design N** | Describe surface (e.g. marketing site, product app) | `refs/design-N/DESIGN.md` + any image refs in the same folder |

**Do not mix designs.** Product UX still wins via `docs/mvp/` and `.cursor/rules/frontend/` when it conflicts with visual taste.

## Which file to read

- Building against a locked pack → open that pack’s `DESIGN.md` (and refs).
- No pack yet → use `docs/mvp/` UI goals (when written) and `.cursor/rules/frontend/`.
- Unsure → read this index first, then open the matching source.

## Status

- No design packs yet. Create `refs/design-1/` (and later packs) when a look is locked.
