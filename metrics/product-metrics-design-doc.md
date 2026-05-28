# JioBharatIQ — Product Metrics Design

**Document version:** v1.0
**Last updated:** 2026-05-11
**Author:** Sridhar
**Status:** Working draft · Internal · Reliance Intelligence

---

## Table of Contents

1. [Purpose and Audience](#1-purpose-and-audience)
2. [Method — Output-Backward Tree](#2-method--output-backward-tree)
3. [Activity Units](#3-activity-units)
4. [The Paired Product L0 — North Star](#4-the-paired-product-l0--north-star)
5. [L1 Decomposition — Causal vs Mathematical](#5-l1-decomposition--causal-vs-mathematical)
6. [The 7 Layers](#6-the-7-layers)
   - 6.1 [Layer 1 — The User Loop](#61-layer-1--the-user-loop)
   - 6.2 [Layer 2 — The Personalization](#62-layer-2--the-personalization)
   - 6.3 [Layer 3 — The Conversation](#63-layer-3--the-conversation)
   - 6.4 [Layer 4 — The Task Delivery](#64-layer-4--the-task-delivery)
   - 6.5 [Layer 5 — The Quality](#65-layer-5--the-quality)
   - 6.6 [Layer 6 — The Platform](#66-layer-6--the-platform)
   - 6.7 [Layer 7 — The Partners](#67-layer-7--the-partners)
7. [Cross-Cutting Attributes](#7-cross-cutting-attributes)
8. [Bharat — Parallel Strategic Frame](#8-bharat--parallel-strategic-frame)
9. [Out of the Product Tree](#9-out-of-the-product-tree)
10. [Change Management and Governance](#10-change-management-and-governance)
11. [Instrumentation and Data Interaction](#11-instrumentation-and-data-interaction)
12. [Metrics-Design Audit](#12-metrics-design-audit)
13. [Design Choices Defended](#13-design-choices-defended)
14. [Future Scope](#14-future-scope)
15. [Glossary](#15-glossary)
16. [References and Companion Files](#16-references-and-companion-files)

---

## 1. Purpose and Audience

### 1.1 Purpose

This document defines the **Product Metrics framework** for JioBharatIQ (JBIQ). It establishes:

- What the product is measured by (the L0 north star and its decomposition)
- How layers of the product map to user-experienced outcomes
- The cross-cutting attributes by which every metric must be sliceable
- Where qualitative or strategic resonance metrics live (Bharat framework, parallel)
- Where non-product metrics belong (parallel tracks, not in this tree)
- The change-management and governance discipline that keeps the framework alive

### 1.2 Audience

| Audience | What to read |
|---|---|
| **Leadership** (Naroo, Rushabh) | §1–4, §6 layer L0s, §8 (Bharat), §13 (design choices) |
| **Pod owners** (Sridhar, Anmol, Karan, Bharat, Vinay, Sushant) | Full document, especially §6 for owned layer |
| **Engineering** | §11 (instrumentation), §10 (change management), §6 layer L1/L2 |
| **Analytics / Data** | §7 (attributes), §11, §10 |
| **GTM / Comms** | §9 (parallel tracks, especially Customer Lifecycle), §7 (cohorts) |
| **Cross-pod reviewers** | §2 (method), §12 (audit), §13 (design choices) |

### 1.3 What This Document Defines vs Does Not

| Does define | Does not define |
|---|---|
| The canonical metric tree (what metrics exist) | Specific numeric targets at FnF / Beta / GA — see `product-context.md` |
| The relationship between metrics (L0 → L1 → L2) | Instrumentation implementation details — see engineering specs |
| Cross-cutting attributes (the slicing dimensions) | Dashboard layouts — owned by Data pod |
| Governance for changing metrics | Specific pod execution plans |
| Out-of-tree parallel tracks (overview) | Detailed GTM / Operations metrics — see `non-product-metrics.md` |

---

## 2. Method — Output-Backward Tree

### 2.1 The Principle

The metrics tree is **output-backward**. It starts from outcomes (what the product is meant to deliver) and decomposes toward inputs (what teams can move). Every metric in the tree must trace backward to a Product L0 — if it can't, it doesn't belong.

This is in contrast to **input-forward** thinking, which starts from activities (what teams ship) and hopes outcomes follow. Input-forward is the right framing for operations and engineering management — *not* for product metrics. Operations metrics live in the parallel non-product-metrics tracks (§9).

### 2.2 The Three Levels

Every layer of the tree has three levels:

| Level | What it is | Direction |
|---|---|---|
| **L0** | The single primary metric — the outcome that defines whether the layer is doing its job | Outcome |
| **L1** | Primary drivers — sub-outcomes or components that compose / cause L0 | Causal step backward |
| **L2** | Leading indicators · inputs · diagnostics — the signals and levers used to understand L1 movements | Input layer |

The discipline: every metric must answer **one of three questions** working backward from outcome:
1. *Did the product work?* (L0)
2. *What sub-outcome or driver moved?* (L1)
3. *What input or signal explains the L1 movement?* (L2)

### 2.3 Layer Organisation — User-Experience-First

The 7 layers are organised around **questions a user would actually ask of the product**, not internal pod taxonomy. Each layer is named for the user-experience question it addresses:

| Layer | User question |
|---|---|
| 1 — The User Loop | Did the user come back? |
| 2 — The Personalization | Did it feel made for me? |
| 3 — The Conversation | Did talking to it feel natural? |
| 4 — The Task Delivery | Did the AI do what I asked? |
| 5 — The Quality | Was the answer right? |
| 6 — The Platform | Did it work when I needed it? |
| 7 — The Partners | Scale path — supplier of Layers 4–5 |

Internal taxonomy (Core / Vertical / Signature Experience) is not a layer — it lives as cross-cuts (§7) and as Group G qualification within Layer 1.

### 2.4 What the Product Promises (the Three Claims)

Every metric in the tree must trace back to one of three claims the product makes:

1. **Knows you** — language, context, history
2. **Knows what you need right now** — proactive, situational
3. **Does the work** — completes tasks, doesn't suggest

Operationally:
> *The product is working when a user opens JBIQ, gets something done, comes back tomorrow without being pushed, and the next session starts smarter than the last. Repeat across 1.4B Indians, 12 languages, 12 domains.*

---

## 3. Activity Units

All units anchored at the **monthly level** for consistency. Daily snapshots (DAU, DQU) are derived from these monthly bases when needed for the L0 stickiness ratio — they are not primary units.

| Unit | Definition | Role |
|---|---|---|
| **MAU** | Users who opened the app in last 30 days (rolling) | Funnel diagnostic only — opened ≠ engaged |
| **MQU** | Users who sent ≥1 query in last 30 days (rolling) | **The activity unit · L0 denominator.** Anchors engagement and retention metrics. |
| **MTU** | Users who completed ≥1 useful task in last 30 days (rolling) | **Monthly value-delivered unit** — captures value, not just engagement |

**Note on daily snapshots:** Active Habit Rate (L0) = `Organic DQU ÷ MQU` is a daily-stickiness ratio computed from these monthly bases — daily querying user counts are derived from MQU on a per-day basis.

**Per-query views** are used for outcome-quality measurement:

```
Query → Resolved (Task Resolution Rate)
Resolved → Satisfied (User Satisfaction Rate)
Useful Task Rate = Resolved × Satisfied  (per-query)
```

---

## 4. The Paired Product L0 — North Star

A single number is too lossy for a product whose promise is "loop AND work." The Product L0 is a **paired north star** — both metrics must move together for the product to be working.

### 4.1 The Pair

| | Metric | Definition | What it tests |
|---|---|---|---|
| **Loop** | **Active Habit Rate** | Organic DQU ÷ MQU — daily-stickiness ratio anchored on querying users, push-attributed returns *excluded* | Did the product earn the user, or did push pay for the visit? *(P7 — Build for the loop, not the visit.)* |
| **Work** | **Useful Task Rate** | % of queries that resolved AND user signaled value | Did the AI actually deliver something useful? |

### 4.2 Composite Rollup

For one-number reporting (never a substitute for the pair):

```
Compounding Habit Index = Active Habit Rate × Useful Task Rate
```

A 40% Active Habit × 80% Useful Task = 32% Compounding Habit Index.

### 4.3 Why Paired

A single L0 is gameable:
- *Active Habit Rate alone* — push spam can drive returns at the cost of meaningful value
- *Useful Task Rate alone* — could be high among a tiny loyal base, while the product fails at scale

The pair forces alignment on both: *did users come back* AND *did they get value when they did*. No movement on one without movement on the other.

### 4.4 Why Not MAU/DAU

MAU/DAU are reach metrics, gameable by paid acquisition and notification spam. They go at Layer 1 L2 (funnel diagnostic) and in the parallel Growth track — not at L0. The Product L0 must be hostile to vanity.

---

## 5. L1 Decomposition — Causal vs Mathematical

L0 → L1 relationships are of two types. The tree honestly distinguishes which case is which:

### 5.1 Mathematical Decomposition

L1 metrics compose to L0 via a strict identity (multiplication or AND). Examples:

- **Useful Task Rate** = `Intent × Routing × Execution × Production Quality Floor × User Satisfaction` (multiplicative)
- **Production Quality Floor** = `% passing all critical eval dimensions` (AND)
- **Reliability-Adjusted Availability** = `% seconds up AND within latency SLO AND below crash threshold` (AND)

For mathematically composed L0s: you can attribute *exactly* how much each L1 moved L0. Sum of L1 contributions = L0 movement.

### 5.2 Causal Decomposition

L1 metrics are drivers that influence L0 but don't compose to it numerically (different denominators or time scales). Examples:

- **Active Habit Rate** drivers: Activation × Retention × Loop Self-Sufficiency × Engagement Depth × Personalization Lift × Virality (causal, not multiplicative — drivers sit at different denominators)
- **Task Resolution Rate** sub-causals: Per-skill accuracy, Per-domain completion (drivers, not strict components)

For causally decomposed L0s: you can identify which L1 *correlates* with L0 movement, but precise attribution requires controlled experiments (A/B). Without experiments, attribution is correlational.

### 5.3 Implications

| If L0 → L1 is mathematical | If L0 → L1 is causal |
|---|---|
| Attribute exactly how each L1 moved L0 | Identify which L1 likely drove L0 movement |
| Forecast L0 = forecast each L1 and compose | Need experiments to attribute precisely |
| Set L1 targets that mathematically guarantee L0 target | Set L1 targets as necessary-but-not-sufficient |

The framework documents which type each L0 belongs to (see audit, §12).

---

## 6. The 7 Layers

### 6.1 Layer 1 — The User Loop

**Question:** *Did the user come back?*

**L0:** **Active Habit Rate** = `Organic DQU ÷ MQU` *(this IS the product L0)*

**L1 — 8 groups:**

#### Group A — Activation (entry to the loop, with window)

| Metric | Why |
|---|---|
| Activation Rate | % of installs that fire ≥1 query within D7 window. Quality of the query lives in Useful Task Rate, not here. |
| First-session activation rate | First query on Day 0 |
| Delayed activation rate | First query post-session-1, within D7 window |
| Time-to-Activation | Median, p90 hours from install to first query |
| Activation rate by session-number-when-activated | Activation curve diagnostic |

#### Group B — Engagement (depth + frequency + time)

| Metric | Why |
|---|---|
| Queries per DQU per day | Per-user depth |
| Sessions per DQU per day | Per-user frequency |
| Avg session duration (median, p95) | Time spent — paired with completion to interpret |
| Total time spent per DQU per day | Aggregate engagement time |
| Multi-query session rate | % sessions with ≥2 queries |
| Multi-session day rate | % DQU with ≥2 sessions in a day |
| Active days per week | Avg days/week with ≥1 query (per MQU) |
| Power-user rate | % of DAU with ≥X queries |
| Queries per MQU per month | Monthly-level engagement intensity |
| Total query / session volume per day | Operational scale (non-unique) |

#### Group C — Retention curve

| Metric | Why |
|---|---|
| D1 organic return rate | Activation-depth signal — did the first session land? |
| D7 organic return rate | Week-1 habit signal |
| D30 organic return rate | Month-1 habit signal |
| D90 organic return rate | Long-term loyalty signal |

#### Group D — Loop quality (Organic vs Inorganic)

| Metric | Why |
|---|---|
| Organic Returning Users | Returns without push attribution — the loop working |
| Inorganic Returning Users (push-attributed) | Returns triggered by PN / WA tap — comms working |
| Loop Self-Sufficiency = Organic ÷ Total returns | What share of returns are unprompted |
| Push-attributed Return Rate | 1 − Loop Self-Sufficiency |
| Habit Formation Rate | % of Inorganic → Organic within 60d |

#### Group E — Sentiment + value

| Metric | Why |
|---|---|
| NPS | Will the user recommend? |
| User Satisfaction Rate | Per-query behavioural + explicit signals |
| Surface time-to-meaningful (p95) | Did the entry surface earn the next tap? |

#### Group F — Loop expansion

| Metric | Why |
|---|---|
| Experience discovery rate | % of users who used ≥2 named experiences in week 1 |
| Vertical breadth | Avg distinct domains used per active user (D7) |
| Cross-domain engagement rate | % users using ≥2 domains in a session |

#### Group G — Experience metrics (filter: Generic vs Signature)

Three sub-groups: **G.1** Per-experience metrics applies to all experiences. **G.2** Signature qualification benchmarks define what counts as Signature. **G.3** Signature vs Non-Signature deltas validate the designation. **G.4** Catalog velocity tracks how fast new experiences ship.

| Sub-group | Key metrics |
|---|---|
| G.1 Per-experience | Attempt Rate · Completion Rate · 24-hour Return · D7/D30 Stickiness · Avg Turns · Cohort Penetration · In-context NPS |
| G.2 Qualification | Proprietary data binding (binary) · Loop-forming threshold · Cultural irreplaceability · Composite Qualification Score (0–3, only 3/3 qualifies) |
| G.3 Delta validators | D7 Retention Delta · Completion Delta · Stickiness Delta · Per-Cohort Pull Delta · NPS Delta · Per-Domain Coverage Delta · Time-to-Resolution Delta |
| G.4 Catalog velocity | New experiences live/month · New Signature Experiences live/month · Time idea → live · % new experiences clearing D7 within 30 days |

#### Group H — Outcome value delivered to user (aspirational at GA, per Mesh)

| Metric | Why |
|---|---|
| Time saved per user per day (estimated) | Per Mesh GA aspirational: 30–60 min/user/day. Estimated per task type. |
| Money saved per user per month (estimated) | Per Mesh GA aspirational: ₹500–2,000/user/month. Driven by deal-finding, mandi timing, GST/scheme advice. |
| Money earned per user per month (estimated) | Income-driven use cases — jobs, commerce, financial timing |
| User-reported value (survey) | Weekly self-reported quantification |
| Substitution rate | % of tasks where JBIQ replaced another app/service/call — "completes things vs points elsewhere" |
| Value Ribbon surface engagement | % of users viewing the cumulative ₹-saved / time-saved widget |
| Per-domain value attribution | Time/money saved per domain — different value profiles |

**L2 — Diagnostics:**

| Metric | Why |
|---|---|
| Pre-activation funnel | Install → DAU → DQU → Activation rates |
| Onboarding completion, time-to-first-query, drop-off step | Where the funnel leaks |
| Curve diagnostics (D1→D7, D7→D30, D30→D90 drop-offs) | Where retention leaks |
| Behavioural satisfaction signals | Rephrase, Re-ask, Response dwell time |
| At-risk % (no query for X+ days in Retention) | Pre-churn warning |
| Cohort Variance (max − min Active Habit across A–E) | Bharat-resonance diagnostic |
| Per-cohort Layer 1 metrics | All Layer 1 metrics sliced by Cohort A–E |
| Comms-layer effectiveness | PN / WA open rate, post-click action rate |
| NPS verbatim themes, free-text sentiment | Where is the love and the hate |
| FGD / diary findings | Qualitative feed-in |
| Trust signal events | Shared output, advocacy actions |

### 6.2 Layer 2 — The Personalization

**Question:** *Did it feel made for me?*

**L0:** **Personalization Resonance Rate** = `% of returning sessions where (a) personalization fired, (b) was correct, AND (c) the user signaled value`

This is one of the 5 Key Bets per the Mesh ("N=1 personalisation"). The L0 is a three-clause AND — captures user-perceived "knows me," not just memory accuracy.

**L1 — Drivers:**

| Driver | Definition |
|---|---|
| Memory-driven (Context-Driven Value Rate) | Memory retrieved + applied + user did not re-explain |
| Surface-driven (Widget / tile tap rate) | Taps ÷ impressions on home widgets, tiles, suggestions, recommendations |
| Language-driven | Correct-language session rate (no manual selection) |
| Identity-driven | JioID pre-load rate |
| Adaptive engagement | Next-prompt suggestion match rate · time-of-day relevance |
| N=1 Retention Lift (validation) | D30(memory active) − D30(no-memory cohort) — periodic causal validation |

**L2 — Diagnostics:**

Memory capture / retrieval precision and recall · Re-explanation rate (direct test of "knows you") · Hallucinated facts per audit · Cross-language recall rate · Memory-trust signal events (Saved Kundali, etc.) · Per-widget-position tap rate.

### 6.3 Layer 3 — The Conversation

**Question:** *Did talking to it feel natural?*

**L0:** **Multi-turn Coherence Rate** = `% of multi-turn sessions where context held across all turns AND modality switches succeeded`

The conversation surface is unified voice + text + image. Voice gets the most detailed sub-tree because it's one of the 5 Key Bets per the Mesh, but text and image are first-class.

**L1 — by modality and cross-modal:**

| Sub-area | Key metrics |
|---|---|
| Voice path (Key Bet) | Voice Primary User Share · Initiation · Stickiness · Fallback Rate · ASR WER · Code-mix Completion · Voice Intent Accuracy · E2E Voice Latency p95 · Barge-in · VAD F1 · TTS Naturalness (MOS) · TTS Playback Completion · Voice Carry-Through · Misunderstanding Recovery |
| Text path | Text Query Latency · Text Completion · Multi-turn rate · Suggested-prompt usage |
| Image path | Image Upload Success · Vision Accuracy · Image-to-Task Completion |
| Cross-modal | Multi-turn Coherence · Modality Switch Success · Turn-Taking Quality |

**L2:** Noise-ASR retention (kitchen, market, traffic) · Per-network-type voice latency · Per-device-tier voice metrics · Audio Replay Rate · Mic Permission Grant Rate.

### 6.4 Layer 4 — The Task Delivery

**Question:** *Did the AI do what I asked?*

**L0:** **Task Resolution Rate** (system-side: task reached a resolved state)

This is the system-side contribution to Useful Task Rate. The user-satisfaction half lives in Layer 1.

**L1 — Accuracy + Speed:**

| Dimension | Metrics |
|---|---|
| Accuracy | Intent Classification Accuracy · Routing Accuracy (right skill, first try) · Execution Success Rate · Multi-step Task Success Rate |
| Speed | TTFT p95 · E2E Latency p95 |

**L2:** Per-skill accuracy · Per-domain task completion · Confirmation-bypass rate (must = 0 for irreversible actions) · Per-network and per-device-tier latency.

### 6.5 Layer 5 — The Quality

**Question:** *Was the answer right?*

**L0:** **Production Quality Floor** = `% of production responses passing all critical eval dimensions (relevance, accuracy, safety, language)`

Critical: this measures quality in **production**, not just in offline eval sets (avoiding the eval-tautology trap).

**L1 — Quality dimensions:**

Eval pass rate (offline golden) · Hallucination rate · Guardrail block rate (adversarial) · Drift (online vs offline golden, ≤10pp) · CI/CD eval gating coverage · Brand-voice adherence · Language authenticity.

**L2:** Per-language eval score · Red-team violation count · New grader velocity · Eval misses that reached users.

### 6.6 Layer 6 — The Platform

**Question:** *Did it work when I needed it?*

**L0:** **Reliability-Adjusted Availability** = `% of seconds platform is up AND within latency SLO AND below crash threshold`

Uptime alone doesn't capture usability. The L0 combines availability + latency + stability.

**L1 — Components:**

Service uptime % · Latency SLO compliance (voice / agentic / dashboard) · Crash rate per 100 sessions · Scale headroom under load · PR-to-production velocity.

**L2:** Per-service availability · Per-region latency · Self-serve service setup time · Incident detect → ack time.

### 6.7 Layer 7 — The Partners

**Question:** *Scale path — supplier of capacity to Layers 4–5*

**L0:** **% of skills served by partners** (everyday intent or Signature Experience — both count)

Partners ship skills that core engineering can't ship at cadence — irrespective of skill class.

**L1:**

Partner-built skills live in production · Self-serve onboarding compliance gate time · New skills shipped/month autonomously · External partners live in production.

**L2:** Per-partner skill share · Per-partner-skill task completion rate · Manual intervention steps per onboarding.

---

## 7. Cross-Cutting Attributes

Every L0 / L1 in the tree must be sliceable by these. Every metric reported should carry the dimensions it was sliced by.

| # | Attribute | Values | Especially relevant for |
|---|---|---|---|
| 1 | **Cohort A–E** | 5 user cohorts per `jbiq_user_cohort_gtm__v1.docx` (encapsulates language, device, geography, segment) | Bharat (BPC), Active Habit, NPS, Useful Task |
| 2 | **Loop type** | Daily · Task · Life | Active Habit per loop type, per-experience retention |
| 3 | **Domain** | 12 daily-life domains | Useful Task Rate per domain, per-domain quality |
| 4 | **Experience type** | Vertical · Signature · Generic chat | Group G filter |
| 5 | **Modality** | Voice · Text · Image | Voice Primary User Share, modality switch success |
| 6 | **Language** | 12 Indian languages | ASR WER, Production Quality, NPS, brand-voice |
| 7 | **Device tier** | Low-end · Mid-end · Flagship | Latency, crash rate, voice abandonment |
| 8 | **Network type** | 4G · 3G · 2G | Voice latency, task completion |
| 9 | **Surface** | Home · Persona page · Suggestion tile · Widget · Deep link · Notification | Surface time-to-meaningful, widget tap rate |
| 10 | **Time horizon** | D1 · D7 · D30 · D90 | Retention curve, cohort analysis |
| 11 | **Acquisition channel** | Jio retail · MyJio · JioFiber · Organic · Paid · Referral | Per-channel D7 organic return |
| 12 | **Session depth** | Single-turn · Multi-turn (≥3) · Extended (≥5) | Multi-turn Coherence, Engagement |
| 13 | **Time of day** | Morning · Day · Evening · Night | Adaptive engagement, Personalization |
| 14 | **Day of week** | Weekday · Weekend | Engagement frequency, weekend-specific use cases |
| 15 | **Region** | Urban · Tier-2 · Tier-3 · Rural | Per-region latency, Bharat composite |
| 16 | **Skill class** | 1P · 2P · 3P · Generic chat | Partner skill share, per-partner task completion |

---

## 8. Bharat — Parallel Strategic Frame

Bharat is **not a layer of the product tree** — it's a parallel strategic frame, reviewed alongside it. Inherits product metrics sliced by Cohort A–E and adds qualitative resonance signals.

### 8.1 Why Parallel, Not a Layer

The cohort cuts on Active Habit Rate ARE the behavioural resonance test — *if Cohort D users return organically, the product is resonating*. A separate "Bharat layer" would double-count what the cohort cut already shows.

But some resonance signals are inherently qualitative and Bharat-specific — *"feels native vs translated,"* persona-fit, cultural relevance — and can't sit in always-on product instrumentation. These live in the Bharat framework, reviewed quarterly.

### 8.2 Structure

| Section | Content |
|---|---|
| Section 1 — Per-Cohort Product Health | Inherits Product Tree metrics sliced by Cohort A–E. Cohort Score per cohort. **Cohort Variance** (max − min) as the diagnostic. |
| Section 2 — Bharat-Specific Resonance | New metrics not in Product Tree: "Feels native vs translated" surveys · Persona-fit · Cultural relevance · Bharat user-pattern signals (shared-device, family-as-unit, micro-loops) · Brand-voice cross-language audit |

### 8.3 BPC — Bharat Persona Composite

```
BPC = weighted average of Cohort Score across Cohorts A–E
Cohort Variance = max(Cohort Score) − min(Cohort Score)
```

If BPC is healthy on average but Cohort D is failing, the strategic bet is broken for the deepest users. Cohort Variance is itself the diagnostic.

### 8.4 Detailed Framework

See `bharat-metrics.md` for full Section 1 and Section 2 with all metrics and methodology.

---

## 9. Out of the Product Tree

Real, measurable, important — but they're **infrastructure, GTM, or operations**, not product-quality measures of whether the AI works for users.

### 9.1 The Parallel Tracks

| Track | Owner | What it covers |
|---|---|---|
| **Growth** | GTM/Marketing | Acquisition · CAC · Channel mix |
| **Distribution** | GTM | Channels · Partnerships · Distribution-derived cohorts |
| **Business / Monetization** | Biz + GTM | ARPU · LTV · Subscription (post-GA) |
| **Customer Lifecycle** | Sridhar + Comms | 8 user-journey stages · Habit Formation Rate · per-campaign attribution |
| **Data** | Vinay | Insight Velocity · Dashboards · Instrumentation · Self-serve analytics |
| **A/B Experimentation** | Vinay | Causal validation · Experiment velocity |
| **Unit Economics** | Engineering + Finance | Tokens/user · Cost/query · Cost/MAU |

### 9.2 Interfaces to the Product Tree

| Track | Interface |
|---|---|
| Growth | GTM produces installs → consumed by Activation Rate (Layer 1 L1). Product earns advocacy → flows back via Virality. |
| Customer Lifecycle | Push-attributed Return Rate (Layer 1 L1) — the product-tree side. Lifecycle-stage transitions live in the parallel track. |
| Data | Every L0/L1 in product tree depends on Data being live. |
| A/B | Validates that L0 / L1 movements were caused by specific changes (vs correlation). |
| Unit Economics | Every product metric has a unit-economics shadow — paired with cost-per-user/query. |

### 9.3 Detailed Tracks

See `non-product-metrics.md` for full metric lists per track.

---

## 10. Change Management and Governance

### 10.1 Change Types

| Type | Risk | Process |
|---|---|---|
| **New metric (additive)** | Low | PR to metrics-tree + dbt model. Pod owner + Sridhar approve. Live in 1–2 days. |
| **New event (additive)** | Low | Pod adds to typed event schema. Vinay reviews data-layer impact. |
| **Definition change to existing metric** | **High** | **Versioning + deprecation** required. Metric Council review. |
| **Event schema change (rename / remove)** | Medium | Migration window: both names emit ≥30 days. Schema registry tracks. |
| **Cohort definition changes** | **High** | Re-baseline 30 days back. All cohort cuts re-computed. Change date flagged. |
| **Threshold change (e.g., Signature qualification)** | Medium | Re-compute SE catalog. Some experiences may demote. Quarterly review confirms. |

### 10.2 Versioning Pattern (for definition changes)

```
v1 of metric (deprecated 2026-08-01, removed 2026-11-01)
v2 of metric (current, since 2026-08-01)

Both compute in parallel during transition.
Dashboards explicitly label which version they show.
Historical reports include the cutover date.
```

### 10.3 The Metric Council

4-person review for material changes (definition, cohort, threshold). Meets monthly or on-demand:

| Member | Role |
|---|---|
| Sridhar | Owns metrics-tree.md as canon |
| Vinay (Data) | Owns data layer feasibility |
| Karan (Evals) | Quality lens |
| Leadership rep | Strategic alignment |

### 10.4 Change Request Workflow

1. **Proposal** — PR to metrics-tree.md with what's changing, why, who's impacted, migration plan
2. **Pod-owner review** — Layer owner sign-off
3. **Data-layer review** — Vinay confirms instrumentation feasibility
4. **Council review** — Only for material changes
5. **Implementation** — PR ships metrics-tree update + dbt model + event schema + dashboard wiring + changelog entry
6. **Validation** — Within 48h: events firing? numbers populating?

### 10.5 Observability for Instrumentation Itself

Alert when:
- A defined event stops firing for >1 hour
- A new event fires that doesn't have a schema
- A required property is missing (>0.5% rate)
- Cross-source join fails (>0.5% rate on user_id / session_id)
- dbt model fails to refresh on schedule
- A dashboard metric changes definition without council approval

---

## 11. Instrumentation and Data Interaction

### 11.1 The 5-Layer Instrumentation Chain

| Layer | Owner | What lives here |
|---|---|---|
| 1. Definition | Sridhar (metrics-tree.md as canon) | Every metric has ONE definition |
| 2. Event taxonomy | Each pod for their layer | Events as typed schemas (TypeScript / protobuf), CI-enforced |
| 3. Pipelines | Vinay (Data pod) | Spanner · GA4 · Langfuse · CleverTap · New Relic · GrowthBook — joined in Databricks |
| 4. Computation | Vinay + each layer owner | dbt models — metric computation as code, versioned with metrics-tree.md |
| 5. Surfaces | Vinay | Dashboards · Self-serve query · NL interface |

**Principle:** metric-as-code. PRs that change a metric require updates in both `metrics-tree.md` and the dbt repo.

### 11.2 Three Surfaces for Data Interaction

| Surface | Tool | Audience | SLO |
|---|---|---|---|
| Pre-built dashboards | Mode / Tableau / native | Leadership, daily standup | Open in ≤10 sec |
| Self-serve query | Hex / Mode Visual Explorer / Databricks SQL | PMs, analysts, designers | New view in ≤2 min |
| Natural language layer | Internal MetricsBot | Anyone | Answer in ≤1 min |

### 11.3 MetricsBot — Internal NL Data Interaction

An internal AI copilot for analytics, built using JBIQ's own AI stack:

- Understands metric definitions (grounded in metrics-tree.md)
- Generates SQL against Databricks
- Suggests the right cut (cohort, language, time horizon)
- Handles drill-downs and anomaly detection
- Distinguishes correlational from causal attribution

When metric definitions change, MetricsBot re-grounds; old definitions remain queryable with a "deprecated since X" warning.

---

## 12. Metrics-Design Audit

| Principle | Pass? | Note |
|---|---|---|
| Layers organised by user experience, not internal pods | ✓ | Each layer answers a user-question |
| L1 decomposes L0 | Partial ✓ | Useful Task Rate is clean math. Active Habit Rate is causal — explicit in §5. |
| Each metric Actionable | Mostly ✓ | Some observational (NPS, virality, FGD) — flagged in their layer |
| Each metric Measurable today | ⚠ | 16 P0 instrumentation gaps tracked in FnF metrics workbook |
| Leading vs lagging distinct | ✓ | L2 mostly leading, L1 mostly lagging |
| No vanity metrics at the top | ✓ | DAU at Layer 1 L2 (funnel diagnostic). Growth, Data, A/B, Unit Economics all out of tree. |
| Each metric has causal link to L0 | ✓ | Output-backward enforces this |
| Not double-counted across layers | ✓ | Task Resolution lives once (Layer 4); appears elsewhere only as a factor |
| Activity unit appropriate | ✓ | DQU not DAU; monthly units (MAU/MQU/MTU) primary |
| Bharat resonance has a home | ✓ | Cohort A–E cross-cut + Cohort Variance at Layer 1 L2 + parallel `bharat-metrics.md` |
| Personalization elevated | ✓ | Layer 2 with own L0 — not buried in Memory |
| Conversation unified | ✓ | Layer 3 covers voice + text + image |
| Memory L0 operationally viable | ✓ | Context-Driven Value Rate (always-on); N=1 lift at L1 for periodic causal validation |
| Per-experience metrics consistently leveled | ✓ | Group G has clear per-experience + qualification + delta + velocity structure |
| Causal validation has a home | ⚠ | A/B in capability track; currently blocked at FnF |

---

## 13. Design Choices Defended

### 13.1 Paired L0, Not Single

Choosing one of {Active Habit, Useful Task} would compromise the product. A high single-metric org can hit it by failing the other half. The pair forces both.

### 13.2 DQU as the Activity Unit, Not DAU

For an AI assistant, "opened the app" is a vanity floor. DQU (sent ≥1 query) anchors L0 in real engagement. DAU is kept at Layer 1 L2 as a funnel diagnostic — the DAU→DQU rate surfaces friction. (Now reframed at month level: MAU/MQU/MTU as primary units, daily derived for L0 ratio.)

### 13.3 Memory L0 = Context-Driven Value Rate, Not D30 Retention Lift

The retention-lift formulation requires a holdout cohort with memory disabled — deliberately giving some users a worse product. Context-Driven Value Rate measures memory delivering value directly (three-clause AND on retrieval, application, no re-explanation). Loses the causal A/B claim, gains operational viability and direct measurement. N=1 Retention Lift retained at L1 as periodic validation.

### 13.4 Cohort A–E as Cross-Cut, Bharat as Parallel Framework — Not a Separate Layer

The cohort cuts on Active Habit Rate ARE the behavioural resonance test. A "Bharat composite" layer was double-counting. Soft, qualitative resonance metrics live in `bharat-metrics.md` as a parallel periodic framework. Cohort Variance (max − min Active Habit across A–E) is kept at Layer 1 L2.

### 13.5 Layers Organised by User Experience, Not Internal Pod Taxonomy

The user doesn't experience "Vertical Experience" or "Signature Experience" — they experience "did it work, did it know me, did it talk well." Organising layers around user-experienced concepts forces metrics to test what users actually feel, not what teams ship. Internal taxonomy lives as cross-cuts.

### 13.6 Personalization Elevated to Its Own Layer

N=1 personalization is one of the 5 Key Bets. Burying it inside Memory + scattering it across User obscured a strategic bet. Layer 2 with **Personalization Resonance Rate** as L0 makes the bet visible and movable.

### 13.7 Output-Backward, Not Input-Forward

The tree starts from outcomes and decomposes toward inputs (§2.1). Input-forward (vanity metrics: queries shipped, PNs sent, dashboards built) lives in operations, not the product tree.

---

## 14. Future Scope

Things that would belong in the tree but are out of scope at the current product stage:

- **Revenue / monetisation metrics** — explicitly out per Product Mesh ("no advertising, transactions, subscriptions at GA"). Becomes a layer post-monetization.
- **Family / multi-user account metrics** — Personalisation says "family profiles" is a post-launch direction.
- **Offline / on-device intelligence** — same, post-launch.
- **Cost per session as a product L1** — currently in Unit Economics (out of tree); may need a paired surface once monetization activates.

---

## 15. Glossary

| Term | Definition |
|---|---|
| **L0** | The single primary metric for a layer; the north-star test |
| **L1** | Primary drivers / components that decompose the L0 |
| **L2** | Leading indicators and diagnostics |
| **DAU / DQU** | Daily Active / Daily Querying Users — daily snapshots derived from MAU / MQU |
| **MAU / MQU / MTU** | Monthly Active / Querying / Task Users — the primary monthly units |
| **NPS** | Net Promoter Score |
| **D1 / D7 / D30 / D90** | Day 1 / 7 / 30 / 90 organic return rate |
| **SE** | Signature Experience — Vertical Experience that passes 3 quality checks |
| **L0–L3 (SE)** | Maturity ladder for vertical experiences: L0 basic, L1 better, L2 differentiated, L3 signature |
| **BPC** | Bharat Persona Composite — weighted average across Cohorts A–E |
| **Cohort A–E** | 5 user cohorts per `jbiq_user_cohort_gtm__v1.docx` |
| **P7** | Principle 7: "Build for the loop, not the visit" |
| **ASR / TTS** | Automatic Speech Recognition / Text-to-Speech |
| **WER** | Word Error Rate — ASR accuracy (lower better) |
| **VAD** | Voice Activity Detection |
| **MOS** | Mean Opinion Score — TTS naturalness 1–5 |
| **TTFT** | Time to First Token |
| **E2E** | End-to-End latency |
| **p50 / p95** | 50th / 95th percentile latency |
| **SLO** | Service Level Objective |
| **CI/CD** | Continuous Integration / Continuous Deployment |
| **PN / WA** | Push Notification / WhatsApp |
| **CAC / LTV / ARPU** | Cost of Acquisition / Lifetime Value / Average Revenue Per User |
| **1P / 2P / 3P** | First / Second / Third party |
| **LLM / SLM** | Large / Small Language Model |
| **MCP** | Model Context Protocol — partner integration standard |
| **FnF** | Friends and Family — pre-Beta program |
| **GA** | General Availability — public launch |
| **OCP** | Omni Central Profile — intelligence layer |
| **UCP** | User Central Profile — one input into OCP |
| **FGD** | Focus Group Discussion |
| **pp** | Percentage points (95% → 85% = 10pp) |
| **JioID** | Reliance Jio user identity |

---

## 16. References and Companion Files

### 16.1 Source Documents (saloni's OneDrive — `01 Product/`)

- `JBIQ Product Mesh.docx` (March 2026) — North Star, Success definition, 7 GA metrics with targets, 3 Loops (Daily/Task/Life), 10 Signature Experiences, 5 Key Bets, scope boundaries
- `Product Layers/JBIQ Product Layers.pptx` (March 2026) — Layer stack (Experience / Intelligence / Systems), FnF pod ownership
- `Product Milestones/JBIQ Goals — GA Pod Cascade.md` (May 2026) — 10 org goals × 10 pods × Beta + GA targets
- `JBIQ_FnF_Metrics_Working.xlsx` — FnF dashboard with ~150 metrics across 8 sections, plus 16 instrumentation gaps
- `User Lifecycle/JBIQ_User_Lifecycle_Framework_v1.0.docx` — 8-stage lifecycle, Habit Formation Rate
- `User Lifecycle/JBIQ_CT_WA_Instrumentation_Spec_v1.0_1.docx` — 14 CleverTap events, 9 user properties, campaign config map
- `jbiq_user_cohort_gtm__v1.docx` — canonical cohort definitions A through E
- `Bharat Concept Note.docx` — Soul, 6 Character traits, 4 Indian Pillars

### 16.2 Companion Files (same folder)

| File | Purpose |
|---|---|
| `metrics-tree.md` | The canonical Product Metrics tree (working canon, terse and scannable) |
| `product-context.md` | Context wrapper — ties Mesh + Goals + FnF + ownership and operational state |
| `bharat-metrics.md` | Bharat resonance framework (per-cohort product health + qualitative resonance) |
| `non-product-metrics.md` | Parallel tracks outside the product tree |
| `product-metrics-overview.html` | Interactive overview with sidebar navigation and collapsible sections |
| `product-metrics-design-doc.md` | **This document** — the formal write-up |

---

*End of document · v1.0 · 2026-05-11 · Sridhar*
