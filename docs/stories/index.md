# Stories

Canonical implementable inventory. `what-next` and `story-loop` consume `STORY-xx.md` here. Product narrative and epics stay in `docs/mvp/`. Acceptance criteria live **only** on the story file.

A **product grill** creates new `STORY-xx` files (one batch when that topic locks). Story-loop does not. `/generate-docs` updates existing files only.

One file = one PR. Split before persist if the work would not fit.

## File format

Name: `STORY-01.md`, `STORY-02.md`, …

```markdown
# STORY-xx — Title

- Epic: cite `docs/mvp/…`
- Story: As a … I want … so that …
- Out of scope: …

## Acceptance criteria

- …

## Notes

- optional
```

## Inventory

| ID | Title | Epic |
|----|-------|------|
| — | (empty until a product grill persists stories) | — |
