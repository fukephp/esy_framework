# Framework lifecycle

How work moves from a new project through clarity gates to one story → one PR.

Use this diagram in decks (screenshot Mermaid) or keep it as the editable source of truth.

```mermaid
flowchart TD
  start([esy_framework template]) --> scaffold["/scaffold-project<br/>sibling repo"]
  scaffold --> open[Open new folder as workspace]
  open --> lock["Fill CONTEXT.md<br/>+ docs/mvp + docs/architecture<br/>as decisions lock"]
  lock --> pick[Pick one story]
  pick --> fog{Fog gate}
  fog -->|non-trivial| map["Wayfinder-lite map<br/>.cursor/loops/maps/"]
  fog -->|sharp path| grill
  map --> grill["grill-me<br/>one decision at a time"]
  grill --> key["Compile answer key<br/>.cursor/loops/answer-keys/"]
  key --> approve{You approve key?}
  approve -->|no| grill
  approve -->|yes| verify{App root + verify<br/>commands ready?}

  verify -->|yes| loop["story-loop<br/>Cloud Agent brief"]
  loop --> impl["Implement → verify<br/>iteration cap"]
  impl --> pr[Open PR]
  pr --> bugbot[Bugbot on PR]
  bugbot --> merge([You merge])

  verify -.->|not yet| planOnly["Plan-gate only<br/>map / answer key<br/>no coding loop yet"]
  planOnly -.-> lock

  classDef artifact fill:#f5f5f5,stroke:#666,color:#222
  classDef gate fill:#fff8e6,stroke:#b8860b,color:#222
  classDef main fill:#e8f4fc,stroke:#2a6f97,color:#222
  classDef dashed fill:#fafafa,stroke:#999,stroke-dasharray: 5 5,color:#444

  class lock,map,key artifact
  class fog,approve,verify gate
  class scaffold,grill,loop,impl,pr,bugbot main
  class planOnly dashed
```

## Reading the main path

1. Scaffold a sibling project from this template.
2. Lock product/architecture truth before inventing behavior or stack.
3. Clear fog (optional map) and grill open decisions.
4. Approve a pass/fail answer key.
5. When verify exists: story-loop → PR → Bugbot → you merge.

## Dashed branch

If the app root or verify runners are not ready, stop at map/answer key (plan-gate only). Do not run a coding loop that invents “done.”
