# Agent Harness & Loop Kit

Fill-in-the-blank canvases for designing an AI agent, the loop that runs it, and the sheet that scopes it to one real account — **without writing code**.

The first two are based on Addy Osmani's [Agent Harness Engineering](https://addyosmani.com/blog/agent-harness-engineering/) and [Loop Engineering](https://addyosmani.com/blog/loop-engineering/). The essays explain the ideas; this repo turns them into boxes you fill in on a Tuesday afternoon. The third is ours, and it starts where the essays stop: the day the agent is real and the money is someone else's.

**No install. No account. No code.**

---

## The canvases

**Use it now: [solernicolas041.github.io/agent-harness-kit/canvas/](https://solernicolas041.github.io/agent-harness-kit/canvas/)**

Or open [`canvas/index.html`](canvas/index.html) locally — double-click the file, that's it. Works offline.

- Type straight into the boxes; your text saves in that browser
- **Show a filled example** fills both canvases with a worked example so you can see what "done" looks like
- **Print / Save as PDF** gives you one A3 landscape sheet per canvas, ready for a pen

Prefer plain text? The same two canvases live as Markdown in [`templates/`](templates/).

```
CANVAS 01 — THE HARNESS          what the agent reads, may touch, may never do
  1 Prompting   2 Tools   3 Infrastructure   4 Knowledge
  5 Context     6 Loop
  7 Guardrails — what it can never do
  ↻ The Ratchet — mistakes turned into rules

CANVAS 02 — THE LOOP             what makes it run without you
  1 Trigger     2 State   3 Isolation        4 Skills
  5 Maker & Checker        6 Connectors
  7 Human gate — the part that never automates
  ↻ One lap, on paper, before you build anything
```

---

## The job sheet

**Use it now: [solernicolas041.github.io/agent-harness-kit/job-sheet/](https://solernicolas041.github.io/agent-harness-kit/job-sheet/)**

Or open [`job-sheet/index.html`](job-sheet/index.html) locally. Same boxes, same print sheet, its own page and its own link — so you can hand it to someone without handing over the whole kit.

The two canvases above are filled in **once per agent**. This one is filled in **once per account**, and it answers the question that costs money when nobody wrote the answer down: *what is this agent allowed to touch here?*

```
THE JOB SHEET                    what it may touch on ONE account, with real money
  1 Scope       2 Read rights
  3 Write rights — every one of them gated      4 Thresholds
  5 Triggers
  6 Guardrails — and the scars they came from
  ? The blanks you could not fill
```

Two rules make it worth filling in:

- **A read right is a habit. A write right is a decision.** Box 3 makes you name the gate for each one — who approves it, and the hard ceiling per operation. A ceiling is not an approval; you need both.
- **A blank is a finding, not a formatting problem.** Box 7 is where a number you don't have gets written down as missing, never guessed. An invented threshold is more dangerous than an absent one, because the agent will act on it.

Box 6 stays empty on day one. A guardrail is written *after* an incident, not from imagination — otherwise you invent the wrong walls and miss the real one.

Markdown twin: [`templates/job-skill-template.md`](templates/job-skill-template.md).

---

## Start here

| Step | File | Time |
|---|---|---|
| 1. Read the method | [`GUIDE.md`](GUIDE.md) | 10 min |
| 2. Design the harness | [`canvas/index.html`](canvas/index.html), Canvas 01 | 30 min |
| 3. Draw it | [`diagrams/harness-anatomy.mmd`](diagrams/harness-anatomy.mmd) → paste into [mermaid.live](https://mermaid.live) | 10 min |

> Only the `.mmd` files are diagram source. The canvases in `templates/` are Markdown worksheets — mermaid.live will reject them.

| 4. Run it by hand ten times | — | a week |
| 5. Design the loop | [`canvas/index.html`](canvas/index.html), Canvas 02 | 30 min |
| 6. See it done | [`examples/filled-loop-canvas.md`](examples/filled-loop-canvas.md) | 5 min |
| 7. Scope it to one account | [`job-sheet/index.html`](job-sheet/index.html) | 20 min |

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
canvas/index.html               the two canvases, fillable and printable
job-sheet/index.html            the per-account sheet, fillable and printable
GUIDE.md                        the method, six steps, no code
templates/
  harness-canvas.md             7 sections - what the agent reads, uses, and may never do
  loop-canvas.md                7 sections - what makes it run without you
  job-skill-template.md         5 sections - what it may touch on one client account
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
3. **Memory lives on disk.** The model starts every run with no recollection of the last one. If it isn't in a file, it didn't happen.

---

## Credits

The ideas here are Addy Osmani's, from [Agent Harness Engineering](https://addyosmani.com/blog/agent-harness-engineering/) and [Loop Engineering](https://addyosmani.com/blog/loop-engineering/). **Read those first** — they are the source, and they are better than this summary of them.

This repo is an independent work: the canvas format, the questions in each box, the worked example and the wording are ours. Where we quote him, the quote is marked and credited. See [CREDITS.md](CREDITS.md).

Not affiliated with, sponsored by, or endorsed by Addy Osmani.

## License

Our material is MIT — take it, fork it, fill it in. Addy Osmani's essays are his and are not covered by this licence.
