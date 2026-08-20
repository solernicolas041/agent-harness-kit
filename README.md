# Agent Harness & Loop Kit

Fill-in-the-blank templates for designing an AI agent harness and the loop that runs it — **without writing code**.

Based on Addy Osmani's [Agent Harness Engineering](https://addyosmani.com/blog/agent-harness-engineering/) and [Loop Engineering](https://addyosmani.com/blog/loop-engineering/). The essays explain the ideas; this repo turns them into blanks you can fill on a Tuesday afternoon.

**No install. No account. No code.** Markdown files and Mermaid diagrams that GitHub draws for you.

---

## Start here

| Step | File | Time |
|---|---|---|
| 1. Read the method | [`GUIDE.md`](GUIDE.md) | 10 min |
| 2. Design the harness | [`templates/harness-canvas.md`](templates/harness-canvas.md) | 30 min |
| 3. Draw it | [`diagrams/harness-anatomy.mmd`](diagrams/harness-anatomy.mmd) → paste into [mermaid.live](https://mermaid.live) | 10 min |

> Only the `.mmd` files are diagram source. The canvases in `templates/` are Markdown worksheets — mermaid.live will reject them.

| 4. Run it by hand ten times | — | a week |
| 5. Design the loop | [`templates/loop-canvas.md`](templates/loop-canvas.md) | 30 min |
| 6. See it done | [`examples/filled-loop-canvas.md`](examples/filled-loop-canvas.md) | 5 min |

Step 4 is not optional and not a formality. The rules that make a harness work are the ones you write *after* watching it fail.

---

## What a loop looks like

```mermaid
flowchart TB
    T["TRIGGER<br/>runs every: ______"]
    R["READ STATE<br/>memory file: ______"]
    S["SCAN<br/>where it looks: ______"]
    D{"ANYTHING FOUND?"}
    Z["ARCHIVE<br/>log the quiet run"]
    I["ISOLATE<br/>separate copy: ______"]
    M["MAKER<br/>agent that does the work: ______"]
    C["CHECKER<br/>DIFFERENT agent that reviews: ______"]
    V{"CHECKER APPROVES?"}
    A["ACT<br/>real-world action: ______"]
    H["HUMAN INBOX<br/>where you review it: ______"]
    W["WRITE STATE<br/>saved for next lap: ______"]

    T --> R --> S --> D
    D -->|no| Z --> W
    D -->|yes| I --> M --> C --> V
    V -->|no| M
    V -->|yes| A --> H --> W
    W -.->|"next lap"| T

    classDef step fill:#eeeeee,stroke:#9e9e9e,stroke-dasharray:5 3,color:#424242
    classDef human fill:#fff3cd,stroke:#f57f17,stroke-width:2px,color:#e65100
    classDef guard fill:#cceeff,stroke:#0277bd,stroke-width:2px,color:#01579b
    class T,R,S,I,M,A,Z,W step
    class H human
    class C,D,V guard
```

Every `______` is yours to fill. Grey = a step you configure. Blue = a gate that stops bad work. Amber = the part that never automates.

---

## The maker never grades itself

```mermaid
flowchart TB
    subgraph BAD["WRONG - one agent does everything"]
        direction TB
        B1["Agent writes the work"] --> B2["Same agent says 'looks good'"] --> B3["Ships<br/>nobody caught the mistake"]
    end
    subgraph GOOD["RIGHT - the maker never grades itself"]
        direction TB
        G1["MAKER agent<br/>only writes"] --> G2["CHECKER agent<br/>fresh context, only reviews<br/>tries to REFUTE the work"]
        G2 -->|"finds a problem"| G1
        G2 -->|"clean"| G3["HUMAN<br/>reads it before it counts"]
    end
    BAD ~~~ GOOD
    classDef bad fill:#ffd6d6,stroke:#c62828,stroke-width:2px,color:#b71c1c
    classDef good fill:#d4f8d4,stroke:#2e7d32,stroke-width:2px,color:#1b5e20
    classDef human fill:#fff3cd,stroke:#f57f17,stroke-width:2px,color:#e65100
    class B1,B2,B3 bad
    class G1,G2 good
    class G3 human
```

---

## What's in the box

```
GUIDE.md                        the method, six steps, no code
templates/
  harness-canvas.md             7 sections - what the agent reads, uses, and may never do
  loop-canvas.md                7 sections - what makes it run without you
  AGENTS.md.template            the rules file, capped at 60 lines
  state.md.template             the memory that survives between runs
diagrams/
  harness-anatomy.mmd           blank, fill and paste into mermaid.live
  loop-cycle.mmd                blank
  maker-checker.mmd             ready to use
examples/
  filled-loop-canvas.md         one boring loop, filled end to end
```

---

## Three rules that carry the rest

1. **A rule is earned, never invented.** Every line in your rules file traces to something that actually went wrong. Delete the rest.
2. **The maker never grades itself.** One agent works, a different one — fresh, with no memory of the first — tries to prove it wrong.
3. **Memory lives on disk.** The model forgets everything between runs. If it isn't in a file, it didn't happen.

---

## License

MIT. Take it, fork it, fill it in.
