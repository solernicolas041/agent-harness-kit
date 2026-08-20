# Loop Canvas — FILLED EXAMPLE

> A deliberately boring, non-technical loop: **keeping a personal blog's links from rotting.**
> Copy the shape, not the content.

**Loop name:** link-rot patrol
**It exists so that I stop doing:** clicking through 200 old posts every few months
**Date:** 2026-08-19

---

## 1 · Trigger

| Question | Answer |
|---|---|
| It runs | every Monday, 7am |
| The instruction it receives | "Check every external link in `/posts`. List the ones that no longer load." |
| It stops when | every post has been checked once this week |
| Longest it may run | 20 minutes |

## 2 · State

| Question | Answer |
|---|---|
| Memory file | `state.md` at the repo root |
| What it records | posts already checked, dead links found, links already fixed |
| What it must never record | nothing sensitive here — it's a public blog |
| Who reads it besides the agent | me, Monday morning, 30 seconds |

## 3 · Isolation

| Question | Answer |
|---|---|
| Each run works on its own copy of | the blog repo, on a branch named `linkrot/<date>` |
| Two runs at once would collide over | `state.md` |
| Cleanup after a run | branch deleted once merged or rejected |

## 4 · Skills

| Skill file | What it saves you from re-explaining |
|---|---|
| `skills/blog-conventions.md` | posts are Markdown, links live in `[text](url)`, archive links are fine when dead |
| `skills/replacement-policy.md` | dead link → find an archive.org snapshot first, only then delete |

**Question the agent keeps getting wrong:** it deleted dead links instead of archiving them → **skill that fixes it:** `replacement-policy.md`

## 5 · Connectors

| Connector | Action it can take | Reversible? |
|---|---|---|
| GitHub | open a pull request | yes |
| GitHub | merge to the live site | no |

> Anything **no** needs a human. Human: **me** — I merge, the loop never does.

## 6 · Maker / Checker

| Role | Who | Instructions | Must NOT see |
|---|---|---|---|
| Maker | agent "fixer" | replace dead links per `replacement-policy.md` | — |
| Checker | agent "auditor", fresh session | open every replacement URL, confirm it loads and the content matches the old link text | the maker's reasoning |

**Checker's job in one sentence:** try to prove the replacement links are wrong or unrelated.
**If they disagree twice:** leave the link untouched, flag it in the inbox.

## 7 · Human gate

| Question | Answer |
|---|---|
| Where finished work lands | a pull request titled "link rot — week of X" |
| Expires unreviewed after | 14 days, then auto-closed |
| Never automatic | merging, deleting a post, editing anything outside `/posts` |
| How I find out it broke | no PR and no "all clean" note by Monday noon = it broke |

---

## One-lap dry run

1. Trigger fires Monday 7am
2. Reads state, learns 140 of 200 posts were checked last week
3. Scans the remaining 60 posts, finds 4 dead links
4. Opens branch `linkrot/2026-08-19`
5. Maker swaps 4 dead links for archive.org snapshots
6. Checker opens all 4, rejects 1 (snapshot is a 404 page)
7. Opens a PR with the 3 good fixes, notes the 4th as unresolved
8. Lands in my inbox as a GitHub PR
9. Writes to state: 200/200 checked, 1 link unresolved

**Where does this break first?** archive.org rate-limits and the checker calls good links dead.
**Cost of one lap:** a few cents of tokens, 2 minutes of my Monday.
