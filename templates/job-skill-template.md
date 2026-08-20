# [CLIENT / SKILL NAME] — Job Sheet & Governance

> **Fill-in-the-blank.** Replace every `[...]` with a real, sourced value.
> A blank you cannot fill is written **`to confirm — need X`**, never invented:
> an invented threshold is more dangerous than a missing one.
>
> One sheet per client or per skill. It is the file the agent loads *before* it acts,
> and the file a human reads to know what the agent is allowed to do.
>
> **Filled on:** [YYYY-MM-DD] · **By:** [agent / human]

---

## 1. SCOPE
- Client / entity: [e.g. Acme Group — account 1]
- Domain / ad account IDs: [e.g. MCC ID / CID]
- Owning agent: [e.g. Sentinel / Ads Performance / Dev / Client Success]
- Core objective: [e.g. hold target CPA]

## 2. READ RIGHTS VS WRITE RIGHTS
- READ (autonomous):
  * [e.g. pull 7/30/90-day spend]
  * [e.g. audit campaign structure]
- WRITE (gated):
  * Budget change: [forbidden / allowed under a +10% hard cap]
  * Bids / outbound email: [yes via PR / no without human approval]

## 3. FINANCIAL & PERFORMANCE THRESHOLDS
- Currency: [EUR / AUD / USD]
- Target CPA: [e.g. €35]
- Target ROAS: [e.g. 3.5]
- Global daily budget ceiling: [e.g. €50/day]
- Anomaly alert: [e.g. CPA > +20% over 48h -> Slack notification]

## 4. TRIGGERS
- Trigger events: [e.g. Slack alert, daily cron 08:05, inbound client email]
- Files / context to load: [e.g. rules/01_ads_rules.md]

## 5. GUARDRAILS — KNOWN TRAPS & INCIDENT HISTORY
- Absolute prohibitions:
  * [e.g. never touch an account in Standby]
  * [e.g. never email the client directly]
- Incidents not to repeat: [e.g. the 23/06 double-count incident]

---

> Rule of the sheet: a line lands in section 5 **after** something went wrong, not from imagination.
