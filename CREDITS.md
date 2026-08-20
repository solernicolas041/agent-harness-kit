# Credits

## The ideas are not ours

This repo is a set of worksheets built on two essays by **Addy Osmani**:

- [Agent Harness Engineering](https://addyosmani.com/blog/agent-harness-engineering/) — where the seven parts of a harness, the ratchet, and the anti-patterns come from
- [Loop Engineering](https://addyosmani.com/blog/loop-engineering/) — where the loop components, the maker/checker separation, and state-on-disk come from

**Read the originals first.** They explain the reasoning; these canvases only give you somewhere to write your answers down. If you have time for one or the other, read Osmani.

Nothing here is affiliated with, sponsored by, or endorsed by Addy Osmani. He has not reviewed this.

## What is ours

- The canvas format and layout — the grid of boxes, what goes next to what
- The question written in each box, and the prompts under it
- The worked example (a blog link-rot loop)
- The six-step guide, the checklist, and the diagrams
- All wording, except the quotations listed below

## What we quote directly

Osmani's essays carry a copyright notice and no reuse licence, so we quote sparingly and always with attribution. These are the only direct quotations in this repo:

| Quote | Source | Where we use it |
|---|---|---|
| "Ten focused tools outperform fifty overlapping ones because the model can hold the menu in its head." | Agent Harness Engineering | `templates/harness-canvas.md` §2 |
| "success is silent, failures are verbose." | Agent Harness Engineering | `templates/harness-canvas.md` §7 |
| "the model forgets everything between runs so the memory has to be on disk and not in the context." | Loop Engineering | `templates/loop-canvas.md` §2 |
| "A loop running unattended is also a loop making mistakes unattended." | Loop Engineering | `GUIDE.md`, `canvas/index.html` |
| "Build the loop. But build it like someone who intends to stay the engineer, not just the person who presses go." | Loop Engineering | `GUIDE.md`, `canvas/index.html` |

We also borrow two of his terms: **the ratchet** (a mistake becoming a permanent rule) and the **maker/checker** framing for sub-agents. Both are credited where they appear.

## If you are Addy Osmani

If any of this oversteps — the quotations, the terminology, the framing, or the existence of this repo — open an issue or email us and we will change or remove it, no argument.

## Licence

Our material is MIT (see [LICENSE](LICENSE)). The essays remain the property of their author.
