# Agent 04 — Weekly Health Check
**Scope:** All 10 L1 groups · L0 · North Star
**Time budget:** 20–30 minutes
**Input:** Whatever numbers you have — rough, partial, or complete

---

## What This Agent Does

You paste what you have. It tells you what's alarming, what to watch, and what to fix this week.

It works with incomplete data. It flags when a metric is missing rather than estimating. It never confuses correlation with causation (A/B is blocked at FnF).

---

## How to Use It

Paste your numbers in any format — a table, a standup note, a screenshot description, a dashboard read. Include what you have, skip what you don't.

The agent will:
1. Audit what's reliable vs missing vs estimated
2. Map every number to an L1 group
3. Score each group Red / Amber / Green
4. Call out the top 3 things alarming
5. Give one specific action per alarm

---

## The Scoring Logic

| Status | Criteria |
|---|---|
| 🔴 Red | Below target AND trending wrong OR gate at risk |
| 🟡 Amber | Below target but stable OR at target but declining |
| 🟢 Green | At or above target AND stable or improving |
| ⚫ No data | Metric not instrumented or not available this week |

---

## The 10 L1 Groups — What to Check Each Week

| # | L1 Group | Key metric to paste | Gate / target |
|---|---|---|---|
| 1 | Activation | First-session task rate · Onboarding completion | 40%+ · 80%+ |
| 2 | Engagement | Sessions/DEU/day · Tasks/DEU/day | Year 1: 2 sessions/day |
| 3 | Retention | D7 organic return rate | FnF gate: 15%+ |
| 4 | Loop Self-Sufficiency | Organic DEU ÷ Total DEU | Increasing |
| 5 | Push-attributed Return | Push DEU ÷ Total DEU | Decreasing |
| 6 | Habit Formation Rate | % push users → organic in 60d | Increasing |
| 7 | Organic Active Habit Rate | Organic DEU ÷ MEU | GA: 25%+ |
| 8 | Sentiment + Advocacy | NPS · Satisfaction rate | FnF: NPS 50+ |
| 9 | Expansion | Experience discovery rate | 50%+ in week 1 |
| 10 | Experience (G) | Top SE completion + D7 return | No domain below 70% sat |

---

## FnF Gate Metrics — Always Check These First

These are non-negotiable. If any gate is at risk, everything else is secondary.

| Gate metric | Target | If missed |
|---|---|---|
| D3 organic return (W1) | ≥22% | Escalate immediately |
| D7 organic return | ≥15% | Wave 2 blocked |
| DAU/MAU at D30 | ≥30% | Beta readiness at risk |
| NPS at D7 + D21 | ≥50 | Quality intervention needed |
| Crash rate | <1% per 100 sessions | Stop ship |
| p95 latency | <2,000ms | Platform pod action |

---

## Cohort Variance — Always Report

For any metric you have, cut by cohort if available.
Report: **max value − min value across Cohort A–E.**

High variance (>15pp on D7 return) = winning unevenly. Probably Cohort D/E failing.
This is not a footnote — it is the primary strategic diagnostic.

---

## What to Do With Missing Data

If a metric is missing, say so explicitly:

| Scenario | Response |
|---|---|
| No task completion signal | "CE-3 unmeasurable this week — task completion event not instrumented. Action: Vinay to add completion signal before Wave 2." |
| No cohort cuts available | "Cohort Variance not reportable — cohort classification not live. Headline metrics may be masking a failing cohort." |
| No D7 data yet (too early) | "D7 gate not yet reportable — Day 7 not reached for this wave cohort. D3 proxy: [number]." |

Never estimate without flagging. Never skip a missing gap without naming it as a risk.

---

## Output Format — Every Week

```
JBIQ Core UX — Weekly Health
Week of: [date]
Data reliability: [what's instrumented vs estimated]

GATE STATUS
[🔴/🟡/🟢] D7 Organic Return: X% vs 15% target
[🔴/🟡/🟢] NPS: X vs 50 target
[🔴/🟡/🟢] Crash rate: X% vs <1% target

L0
[🔴/🟡/🟢] Active Habit Rate (DEU÷MEU): X%

L1 SNAPSHOT
[🔴/🟡/🟢] Activation: ...
[🔴/🟡/🟢] Retention: ...
[🔴/🟡/🟢] Loop Self-Sufficiency: ...
[🟡] Engagement: no data this week ⚫
...

COHORT VARIANCE
D7 return: Cohort A X% — Cohort D X% — Variance: Xpp [🔴 if >15pp]

TOP 3 ALARMS THIS WEEK
1. [metric] at [number] — [why alarming] — [one action]
2. ...
3. ...

WHAT'S WORKING
1. ...

INSTRUMENTATION GAPS OPEN
- [gap] blocks [metric] — owner: [name]
```
