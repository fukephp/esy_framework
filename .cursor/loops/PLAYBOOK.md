# Story-loop playbook

Loop Engineering means: clear fog, approve a pass/fail answer key, let a Cloud Agent implement and verify on a branch with a hard iteration cap, run Bugbot on the PR, then you merge.

This is **not** an unattended gauntlet that builds the whole MVP from a vague prompt.

## Project fields (fill in CONTEXT when locked)

| Field | Role |
|-------|------|
| Stories source | Path to the stories doc or folder (`docs/mvp/…` or `docs/stories/…`) |
| App root | Folder where app commands and verify runners live |
| Domain triggers | Extra fog-gate topics (e.g. auth, payments, new user-facing surface). **Empty by default** until the project locks them |

## Wayfinder-lite (plan gate only)

Foggy stories use a **light story map** (Destination, Decisions so far, Open decisions, Not yet specified, Out of scope) before the answer key. That borrows Wayfinder’s fog discipline without Matt Pocock’s full skill, issue-tracker maps, claiming, or research/prototype ticket types.

- Maps: `.cursor/loops/maps/` (template: `MAP_TEMPLATE.md`)
- Keys: `.cursor/loops/answer-keys/` (template: `ANSWER_KEY_TEMPLATE.md`)

## When to loop vs prompt

**Loop** when all of these are true:

- Work is **one story** (or a thin vertical slice of one story) → one PR
- Product fog is cleared (map compiled or sharp-path grill; answer key approved)
- An **approved** answer key exists under `.cursor/loops/answer-keys/`
- The app root named in CONTEXT has a real local verify runner (tests and/or typecheck/lint the agent can fail)

**Prompt turn-by-turn** when:

- Scaffolding the app, or the app root is still a placeholder / unset
- Product or architecture decisions are still open (stay on the map / grill)
- The task is one-off, exploratory, or not machine-verifiable
- You would need the agent to invent “quality” without a pass/fail key

## Contract (locked)

| Decision | Choice |
|----------|--------|
| Job | Ship features with less babysitting |
| Stop rule | You approve answer key → machine gates → you review PR |
| Unit of work | One story → one PR |
| Ready when | App root + local verify commands exist |
| Runtime | Cloud Agent (or Automation) on a feature branch |
| Answer key | Per-story markdown under `.cursor/loops/answer-keys/` |
| Hard stop | 5–8 implement→verify cycles, then escalate |
| Plan gate | Fog check → optional map → compile key → you approve → Cloud Agent |
| Checker | Bugbot on the PR (no second unattended critic loop) |

## Fog gate

Use a story map when fog is **non-trivial**:

- More than **3** open decisions, **or**
- Story touches any item in the project’s **domain trigger list** (CONTEXT / this playbook; empty until filled)

Otherwise skip the map: short grill → draft answer key directly.

## Compile rule

Compile map → answer key only when **all** of these are true:

1. **Not yet specified** is empty
2. **Open decisions** are empty (all moved into Decisions so far)
3. **You explicitly OK** compiling the key

Then set map Status to `compiled`. Do not invent pass/fail checks for leftover fog.

## Flow

1. Pick a story from the stories source named in CONTEXT.
2. Apply the **fog gate**. If non-trivial: create/update `.cursor/loops/maps/STORY-xx.md` from `MAP_TEMPLATE.md`.
3. Grill **one open decision at a time** (grill-me style); update the map. Graduate fog into open decisions only when the question is sharp.
4. When fog and opens are clear, get your OK → **compile** `.cursor/loops/answer-keys/STORY-xx.md` from Decisions so far + Out of scope + verify placeholders. (Sharp path: draft the key without a map.)
5. **You approve** the answer key (Status `approved`; every check concrete).
6. Use the `story-loop` skill to emit a Cloud Agent brief (branch, key path, cap, verify commands).
7. Cloud Agent implements against the key; runs verify from the app root; retries while under the iteration cap.
8. On pass: open a PR. On cap / stuck: open a draft or blocked PR with what failed — do not burn more cycles.
9. Run Bugbot on the PR.
10. You review and merge.

## Gates

1. **Plan gate** — fog cleared (map or sharp path); answer key approved by you; agent does not invent the key mid-run.
2. **Machine gate** — every verify command in the answer key exits 0.
3. **Checker gate** — Bugbot on the PR (lightweight second opinion).
4. **Merge gate** — you review and merge.

## Hard stop

- Default iteration cap: **5–8** implement→verify cycles.
- If the **same failure** repeats twice with no meaningful progress, stop early and escalate.
- Escalation = leave a PR (or draft) titled/blocked with the failing check, last commands, and what a human must decide. Do not continue the loop.

## Out of scope

- Unattended whole-MVP or multi-epic gauntlet
- Coding loops before the app root has a real verify runner
- Docs-only “loops” that check markdown checklists with no runnable app
- A second long unattended critic agent (Bugbot + human review is enough for story PRs)
- Porting Claude Code `/goal` or viral gauntlet prompts verbatim
- Full Wayfinder (issue-tracker maps, ticket claiming, research/prototype labels)

## Related

- Map template: `.cursor/loops/MAP_TEMPLATE.md`
- Maps: `.cursor/loops/maps/`
- Answer key template: `.cursor/loops/ANSWER_KEY_TEMPLATE.md`
- Keys: `.cursor/loops/answer-keys/`
- Skill: `.cursor/skills/story-loop/SKILL.md`
- Product constraints while implementing: `.cursor/skills/custom-feature-skills/SKILL.md`
- Tests command: `.cursor/commands/run-tests.md`
- Grill-me: `.cursor/skills/grill-me/SKILL.md`
