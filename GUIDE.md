# The Guide

Written for someone who has never written code. You will not write any here either.
You will answer questions on paper. The answers *are* the harness.

Two ideas, in order:

- A **harness** is everything around the AI: the rules it reads, the tools it may use, the things it may never do. The AI is the engine; the harness is the car. You are the harness.
- A **loop** is what makes the harness run without you typing anything. It's the difference between owning a car and owning a bus route.

Build the harness first. A loop around a bad harness just makes mistakes faster.

---

## Step 1 — Write down one job. One.

Not "help me with my work". One job, with a beginning and an end, that you do repeatedly and resent.

> Good: "Every Monday, check my blog for links that no longer work."
> Bad: "Manage my content."

Write it in this shape:

**Every ______ , look at ______ , and if you find ______ , do ______ , then tell me.**

If you can't fill that sentence, you don't have a loop yet. You have a wish.

## Step 2 — Fill the Harness Canvas

Open `templates/harness-canvas.md`. Seven sections, one page.

Some blanks you'll fill instantly. Some you'll stare at. **The ones you stare at are the point** — they're the parts of the job that only exist in your head, and the AI cannot read your head.

Two blanks matter more than the rest:

- **§7 What it can never do.** Write the thing that would actually hurt if it happened. Sending an email to a client. Deleting a file. Spending money. Everything you write here becomes a wall.
- **§1 Three rules that earned their place.** Leave these empty on day one. Genuinely empty. You have not made the mistakes yet.

> **The 60-line rule.** Your rules file stays under 60 lines. Not a style preference — past that, the AI starts skimming, and a rule that gets skimmed is worse than no rule, because you think you're protected.

## Step 3 — Draw it

Open `diagrams/harness-anatomy.mmd` in any text editor. It's a blank picture written as words. Replace each `______`, paste it into <https://mermaid.live>, and it draws itself. Free, no account.

Colour the boxes as you go:

- **green** — you have this, it works
- **red** — you don't have this, and you know it
- **grey** — you don't need it yet

Most people's first drawing is mostly grey with two red boxes. That's a correct first drawing. The red boxes are your build list.

## Step 4 — Run it by hand, ten times

Do not automate yet.

Ten times, by hand, ask the AI to do the job with your rules file in front of it. Each time it does something wrong, **do not fix that one output**. Add one line to the rules file so it can't happen again. Log it in the Ratchet table at the bottom of the canvas.

This is the whole method:

> **A mistake is only allowed to happen once. The second time, it's your fault for not writing the rule.**

Around run seven or eight the corrections dry up. That's your signal. Not before.

## Step 5 — Fill the Loop Canvas

Open `templates/loop-canvas.md`. Now you're wrapping the working harness in something that runs on its own.

Three sections people skip, and the skip is always what breaks:

**§2 State — the memory file.** The AI remembers nothing between runs. Nothing. Every Monday it wakes up with amnesia. So the memory has to be a file on disk that it reads first and writes last. Without it, your loop redoes the same work forever and never finishes anything.

**§6 Maker / Checker — two agents, not one.** An AI asked to grade its own work will pass itself. Every time. So one agent does the work and a *second* one, starting fresh, tries to prove the first one wrong. See `diagrams/maker-checker.mmd`. This costs more. It is the single line item worth paying for.

**§7 Human gate.** The loop proposes; you decide. Write down explicitly which actions are never automatic. Then write down how you'd find out if the loop died quietly — because a loop that stops running looks exactly like a loop with nothing to report.

## Step 6 — Dry run on paper

Bottom of the Loop Canvas, nine numbered lines. Walk one full lap in writing before anything is built.

Then answer the last question honestly: **where does this break first?** You already know. Everyone does. Write it down and build the guard for it now, not after.

---

## The six ways this goes wrong

| Failure | What it looks like | The fix |
|---|---|---|
| **Stops early** | Announces "done" with half the work missing | Write down what "done" means, testably, before it starts |
| **Grades itself** | Everything it produces is "excellent" | Separate checker agent, fresh context |
| **Forgets** | Redoes Monday's work every Monday | Memory file on disk |
| **Drowns** | Good for ten minutes, incoherent by minute forty | Park big outputs in files, keep the conversation short |
| **Too many tools** | Confused, picks the wrong one | Cut to ten. Ten focused beats fifty overlapping |
| **You stop reading** | Everything looks fine and you have no idea what changed | Read the output. This one never automates |

That last row is the real one. A loop running unattended is a loop making mistakes unattended.

---

## What "finished" looks like

- [ ] Harness Canvas: every blank filled or deliberately struck out
- [ ] Rules file under 60 lines, every line traceable to a real incident
- [ ] Ratchet table has at least three entries — proof you ran it by hand first
- [ ] Loop Canvas filled, including the paper dry run
- [ ] A memory file the loop reads first and writes last
- [ ] Maker and checker are different agents
- [ ] A written list of things that are never automatic
- [ ] You know how you'd notice the loop dying in silence

Eight boxes. No code.

---

## Where this comes from

- Addy Osmani — [Agent Harness Engineering](https://addyosmani.com/blog/agent-harness-engineering/)
- Addy Osmani — [Loop Engineering](https://addyosmani.com/blog/loop-engineering/)

The canvases are those two essays turned into blanks. Credit theirs; the blanks are the contribution.

> Build the loop. Stay the engineer.
