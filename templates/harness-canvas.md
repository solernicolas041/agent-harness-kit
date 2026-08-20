# Harness Canvas

> Fill every blank. A blank you cannot fill is a gap in your harness, not a formatting problem.
> Rule: you only add a line here **after** something went wrong. Do not pre-fill from imagination.

**Agent name:** ______
**One job it does:** ______
**Date:** ______

---

## 1 · Prompting — what the agent is told every time

| Question | Your answer |
|---|---|
| File holding the rules | ______ (`AGENTS.md`, `CLAUDE.md`, …) |
| How many lines is it? | ______ / 60 max |
| Three rules that earned their place | 1. ______  2. ______  3. ______ |
| A rule you deleted because it never fired | ______ |

> Test: read the file out loud in under 60 seconds. If you can't, it's too long.

## 2 · Tools — what it is allowed to touch

| Tool / connector | What it does | Why the agent needs it |
|---|---|---|
| ______ | ______ | ______ |
| ______ | ______ | ______ |
| ______ | ______ | ______ |

**Count:** ______ tools.
> "Ten focused tools outperform fifty overlapping ones because the model can hold the menu in its head." — Addy Osmani, *Agent Harness Engineering*
**Removed because it confused the agent:** ______

## 3 · Infrastructure — where it works

| Question | Your answer |
|---|---|
| Working folder | ______ |
| Can it undo its own damage? (version control) | ______ |
| What it must never reach | ______ |
| Where risky commands run instead of your machine | ______ |

## 4 · Knowledge — what it knows without being told

| Question | Your answer |
|---|---|
| File where project facts live | ______ |
| Who adds to it, when | ______ |
| A fact you were tired of repeating | ______ |

## 5 · Context — what happens when it fills up

| Question | Your answer |
|---|---|
| What gets summarised first | ______ |
| Where big outputs get parked instead of staying in the conversation | ______ |
| The one file that must survive a full reset | ______ |

## 6 · Loop — when and how it runs

| Question | Your answer |
|---|---|
| Trigger | ______ |
| Done means | ______ |
| Give-up condition | ______ |

> Detail this on the **Loop Canvas**.

## 7 · Guardrails — what it can never do

| Blocked action | What happens instead |
|---|---|
| ______ | ______ |
| ______ | ______ |

| Automatic check before "done" | Passing looks like |
|---|---|
| ______ | ______ |

> "success is silent, failures are verbose." — Addy Osmani, *Agent Harness Engineering*
>
> If your guardrails congratulate you on every run, you'll stop reading them.

---

## The Ratchet — mistakes turned into rules

*"The ratchet" is Osmani's term for this; see [CREDITS](../CREDITS.md).*

| Date | What went wrong | The rule it became | Where the rule lives |
|---|---|---|---|
| ______ | ______ | ______ | ______ |
| ______ | ______ | ______ | ______ |

> This table is the whole method. A harness gets good by accumulating scars, not by being designed well on day one.
