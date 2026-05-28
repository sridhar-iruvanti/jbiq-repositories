# Instrumentation Gap Registry
Living document. Update as gaps close.
Every agent checks this before reporting a metric as reliable.

---

## How to Read This

| Status | Meaning |
|---|---|
| 🔴 Blocked | Metric completely unmeasurable |
| 🟡 Partial | Metric estimated or available for some cohorts only |
| 🟢 Live | Metric instrumented and reliable |

---

## P0 Gaps — Blocking Core Metrics

| # | Gap | Metric blocked | L1 Group | Owner | Status | Notes |
|---|---|---|---|---|---|---|
| 1 | Task completion signal undefined | First-session task rate · Useful Task Rate | Activation | Product + Langfuse | 🔴 Blocked | No completion event defined anywhere in the stack |
| 2 | trace_id missing from prompt_submitted | Multi-turn coherence rate · Session join | Engagement | App + Orchestrator | 🔴 Blocked | Cannot join prompt events to session |
| 3 | session_start/end timestamps | Session duration · Onboarding time | Activation | App + Firebase | 🔴 Blocked | CE-2 unmeasurable without this |
| 4 | Language param missing from events | Per-language cuts on all metrics | All | App instrumentation | 🔴 Blocked | Cannot slice any metric by language |
| 5 | agents_used ≥2 derived metric | Experience discovery rate · Magic number hypothesis | Expansion | Databricks | 🔴 Blocked | Cannot measure CE-4 or validate magic number |
| 6 | Cohort classification not live | Cohort Variance (A–E) | All | Registration flow | 🔴 Blocked | All headline metrics may be masking cohort failures |
| 7 | Channel attribution tagging | Per-channel activation/retention cuts | Activation · Retention | Registration flow | 🔴 Blocked | Cannot separate Jio retail vs organic |
| 8 | Per-step onboarding events | Drop-off step identification | Activation | App instrumentation | 🔴 Blocked | Know funnel drops but not where |
| 9 | Modality field on session events | Voice vs text vs image splits | Engagement | App + Firebase | 🟡 Partial | Available on some events, not all |
| 10 | GrowthBook A/B | Causal attribution for any metric | All | InfoSec gate | 🔴 Blocked | All FnF movements are correlational |

---

## What to Say When a Gap Blocks Analysis

Template for every agent to use:

> "[Metric name] is not reportable this week — [gap description] is not yet instrumented.
> This means [what we can't know].
> Action needed: [specific fix] · Owner: [name] · Priority: P0"

---

## Closed Gaps (update as they resolve)

| # | Gap | Closed date | Notes |
|---|---|---|---|
| — | — | — | None closed yet |

---

## How This Connects to FnF Analysis

All FnF movements are correlational until GrowthBook clears InfoSec gate.
Never claim causation. Always say:
- "X metric moved when Y happened" ✓
- "Y caused X to move" ✗ (not until A/B is live)
