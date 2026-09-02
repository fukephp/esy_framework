# Where truth lives

How humans and agents share one map of product, architecture, and execution conventions. Agents read left-to-right priority: **CONTEXT → docs → skills/rules → app code**.

```mermaid
flowchart LR
  subgraph gitRoot["Git root (not inside app folder)"]
    subgraph docsTruth["Product & architecture truth"]
      mvp["docs/mvp/"]
      arch["docs/architecture/"]
      stories["docs/stories/"]
      diagrams["docs/diagrams/"]
    end

    subgraph cursorLayer[".cursor/ — agent operating system"]
      context["CONTEXT.md<br/>source of truth for .cursor/"]
      rules["rules/<br/>frontend · backend"]
      skills["skills/<br/>grilling · grill-me · grill-with-docs · story-loop · scaffold · …"]
      loops["loops/<br/>PLAYBOOK · maps · answer-keys"]
      commands["commands/<br/>slash workflows"]
      hooks["hooks/<br/>session injects CONTEXT"]
    end

    agents["AGENTS.md"]
    design["DESIGN.md → refs/"]
  end

  subgraph appSide["When project needs an app"]
    appRoot["App root<br/>(named in CONTEXT)<br/>commands · tests · verify"]
  end

  hooks --> context
  context --> mvp
  context --> arch
  context --> stories
  context --> skills
  context --> loops
  agents --> context
  design --> rules
  mvp --> skills
  arch --> skills
  loops --> appRoot
  skills --> appRoot

  classDef truth fill:#e8f4fc,stroke:#2a6f97,color:#222
  classDef ops fill:#f0f7f0,stroke:#3d7a4a,color:#222
  classDef app fill:#fff8e6,stroke:#b8860b,color:#222

  class mvp,arch,stories,diagrams,context truth
  class rules,skills,loops,commands,hooks,agents,design ops
  class appRoot app
```

## Priority for agents

1. Prefer `docs/mvp/` over inventing product behavior.
2. Prefer `docs/architecture/` over inventing a stack.
3. Read `.cursor/CONTEXT.md` before applying skills, rules, commands, or hooks.
4. Keep docs and `.cursor/` at the git root; run app commands from the app root named in CONTEXT.
5. Do not invent scope when docs are empty — ask or grill first.

## Artifacts called out in the lifecycle

| Artifact | Path |
|----------|------|
| Agent context | `.cursor/CONTEXT.md` |
| Domain glossary | `docs/glossary.md` (lazy; domain-modeling via grill-with-docs) |
| ADRs | `docs/adr/` (lazy; domain-modeling via grill-with-docs) |
| Stories inventory | `docs/stories/STORY-xx.md` (product grill persist) |
| Story maps | `.cursor/loops/maps/` |
| Answer keys | `.cursor/loops/answer-keys/` |
| Playbook | `.cursor/loops/PLAYBOOK.md` |
