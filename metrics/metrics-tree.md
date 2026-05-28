# JioBharatIQ — Product Metrics Tree

*Owner: Sridhar · v8 · Last updated: 2026-05-20 · Internal · Reliance Intelligence*

---

## Product Promise

The product is working when a user opens JBIQ, gets something done, comes back tomorrow without being pushed, and the next session starts smarter than the last. Repeat that across 1.4B Indians, in 12 languages, across 12 domains.

**Three claims:**
- **Knows you** — language, context, history
- **Knows what you need right now** — proactive, situational
- **Does the work** — completes tasks, doesn't suggest

---

## Design Principle

Every metric is derivable. L0 is the outcome. L1 is what drives it. L2 is where you look when L1 moves. Complexity lives at the bottom, not the top.

**Direction:** Layers 1–5 are user-backwards — defined from what the user experienced, not what the system produced. Layer 6 is system-backwards. Layer 7 is org-backwards.

---

## Activity Units

| Unit | Definition | Role |
|---|---|---|
| **MAU** | Opened app in last 30 days | Funnel diagnostic only — opened ≠ engaged |
| **MEU** | Query OR audio/video ≥10s in last 30 days (MQU ∪ MCU) | Primary engaged base · L0 denominator |
| **MQU** | ≥1 query sent in last 30 days. MQU ⊂ MEU | Query-depth analytics |
| **MCU** | ≥1 audio/video ≥10s in last 30 days. MCU ⊂ MEU | Content analytics |
| **DEU** | Daily Engaged Users — daily snapshot of MEU | Numerator of Active Habit Rate |

**Useful Task** — a task that resolved AND the user signaled value. ALL of: no rephrase within 60s · no thumbs-down · no restart. Plus ≥1 positive: conversation continued · domain return within 24h · explicit thumbs-up.

**A query is a task.** A task is not always a single query — one user intent can span multiple queries.

---

## North Star — Paired

Both must move together. Neither alone is sufficient.

| | Metric | Definition |
|---|---|---|
| **Loop** | **Active Habit Rate** | DEU ÷ MEU — all returns included. Push vs organic qualified at L1. |
| **Work** | **Useful Task Rate** | % tasks resolved AND user signaled value |

**Composite:** Compounding Habit Index = Active Habit Rate × Useful Task Rate · One-number reporting only.

---

## Org Goals → Metrics Tree

| Goal | Cluster | Metric home |
|---|---|---|
| G03 | Consumer Outcome | Layer 4 L0 — Task Completion Rate |
| G04 | Consumer Outcome | Layer 1 L0 — Active Habit Rate |
| G05 | Consumer Outcome | Layer 5 L0 — Response Satisfaction Rate |
| G06 | Platform Capability | Layer 3 L1 — ASR WER per language |
| G07 | Platform Capability | Layer 5 L1 + Layer 6 L1 |
| G08 | Scale Readiness | Layer 7 L0 + L1 |
| G09 | Scale Readiness | Layer 1 Group G — Catalog velocity |
| G01 | Market Reach | GTM track — out of product metrics tree |
| G02 | Market Reach | Layer 1 Group G — Experience objectives |

---

## Layer Objectives

| # | Layer | Objective | L0 | Direction |
|---|---|---|---|---|
| 1 | User Loop | Users return on their own, without being pushed | Active Habit Rate | User-backwards |
| 2 | Personalisation | Every session feels tailored to that specific user | Personalisation Resonance Rate | User-backwards |
| 3 | Conversation | Talking to JBIQ feels as natural as talking to a person | Multi-turn Coherence Rate | User-backwards |
| 4 | Task Delivery | The AI completes what the user came to get done | Task Completion Rate | User-backwards |
| 5 | Quality | Every response is accurate, safe, and sounds native | Response Satisfaction Rate | User-backwards |
| 6 | Platform | Available and fast whenever a user shows up | Reliability-Adjusted Availability | System-backwards |
| 7 | Partners | The catalog grows beyond what core engineering can build | Partner Skill Coverage | Org-backwards |

---

## Layer 1 — User Loop

**L0:** Active Habit Rate = DEU ÷ MEU · All returns included. Push vs organic qualified at L1.

| Group | L1 Metrics |
|---|---|
| Activation | Activation Rate · Onboarding completion rate · First-session task rate · Delayed activation rate · Time-to-first-task |
| Engagement | MEU growth rate (MoM) · DEU growth rate (MoM) · Tasks per DEU/day · Sessions per DEU/day · Avg session duration · Multi-task session rate · Active days/week |
| Retention | D1 / D7 / D30 / D90 organic return rate |
| Loop Self-Sufficiency | Organic DEU ÷ Total DEU — what share of daily returns are unprompted |
| Push-attributed Return Rate | Push DEU ÷ Total DEU — what share is comms pulling in |
| Habit Formation Rate | % push-prompted users → organic within 60d |
| Organic Active Habit Rate | Organic DEU ÷ MEU — push-excluded pull signal · quality lens on L0 |
| Sentiment | NPS · User Satisfaction Rate · Surface time-to-meaningful p95 |
| Advocacy | Share rate · Screenshot proxy · Show-family behaviour |
| Expansion | Experience discovery rate · Vertical breadth · Cross-domain engagement rate |
| Experience (G) — Per-experience | Attempt rate · Completion rate · D1/D3/D7 same-experience return rate (unprompted) · D30 Stickiness · Cohort Penetration · In-context NPS |
| Experience (G) — Signature | Signature Qualification Score (0–3, only 3/3 qualifies) · D7 Retention Delta · Completion Delta · NPS Delta vs Generic |
| Experience (G) — Catalog | New experiences live/month · Time idea→live · % clearing D7 threshold in 30d |

**L2 Diagnostics:**

| Group | Diagnostics |
|---|---|
| User buckets | MAU / MEU / MQU / MCU counts · MEU growth rate (MoM) · DEU growth rate (MoM) |
| Drop-off | Per-experience: completion paired with same-experience return · Low completion + low return = bad experience · Low completion + decent return = wrong fit |
| Onboarding | Onboarding time (median, p90) · Drop-off step · Per-device + per-network completion |
| Cohort | Cohort Variance = max(Active Habit Rate) − min across A–E |
| Signals | Rephrase rate · Re-ask rate · At-risk % · PN/WA open + post-click · History-to-query conversion rate |

---

## Layer 2 — Personalisation

**L0:** Personalisation Resonance Rate = % sessions where product demonstrated it knew the user · At least ONE of: correct language auto-served · prior context applied without re-explanation · personalised surface element engaged · proactive suggestion accepted

| Group | L1 Metrics |
|---|---|
| Identity | Warm start rate · Cold start rate · Cold→warm transition rate (D7) |
| Memory | Context carry-through rate = % returning sessions where prior context applied without re-explanation |
| Surface relevance | Personalised surface engagement rate |
| Anticipation | Proactive suggestion acceptance rate · Time-of-day relevance rate |
| Language | Correct-language session rate · Cross-language continuity rate |
| Validation | N=1 Retention Lift = D30(on) − D30(off cohort) · Periodic |

**L2 Diagnostics:**

| Group | Diagnostics |
|---|---|
| UCP | UCP parameter coverage · UCP utilisation ratio · Signal freshness (≤15 min) |
| Identity | JioID context load rate · Language auto-detect accuracy |
| Memory | Memory capture/retrieval precision + recall · Hallucinated facts per audit · Re-explanation rate · Users with 6+ memories stored |
| Surface | Tile tap rate by position · Cold home rate · Inference latency p95 ≤50ms |

---

## Layer 3 — Conversation

**L0:** Multi-turn Coherence Rate = % multi-turn sessions where context held AND modality switches succeeded

| Group | L1 Metrics |
|---|---|
| Voice | Voice Primary User Share · ASR WER per language · E2E Voice Latency p95 ≤1.5s · Barge-in ≤300ms · TTS Naturalness MOS · Voice Carry-Through · Misunderstanding Recovery Rate |
| Text | Text Query Latency · Text Completion Rate · Suggested-prompt usage rate |
| Image | Image Upload Success · Vision Accuracy · Image-to-Task Completion |
| Cross-modal | Modality Switch Success · Turn-Taking Quality |

**L2 Diagnostics:** Noise-ASR retention · Per-network latency (4G/3G/2G) · Per-device-tier voice metrics · Mic Permission Grant Rate · Voice Abandonment Rate · Audio Replay Rate

---

## Layer 4 — Task Delivery

**L0:** Task Completion Rate = % of tasks that reached a resolved state

| Group | L1 Metrics |
|---|---|
| Split | First-time user task completion rate · Returning user task completion rate |
| Qualified | Qualified Task Rate = % completed tasks where user felt the problem was solved |
| Accuracy | Intent Classification Accuracy · Routing Accuracy · Execution Success Rate · Multi-step Task Success Rate |
| Speed | TTFT p95 · E2E Latency p95 |

**L2 Diagnostics:** Per-skill completion · Per-domain completion · Confirmation-bypass rate (must = 0) · Task failure recovery rate · Post-failure abandonment rate · Per-network latency · Per-device-tier latency

---

## Layer 5 — Quality

**L0:** Response Satisfaction Rate = % of chats where user was satisfied · Reported overall AND per domain. Overall valid only when all domains above minimum floor.

| Group | L1 Metrics |
|---|---|
| System gate | Production Quality Floor = % responses passing all eval dimensions (relevance, accuracy, safety, language) · Per-domain Response Satisfaction Rate |
| Quality | Eval pass rate · Hallucination rate · Guardrail block rate · Drift online vs offline ≤10pp · CI/CD eval gating coverage |
| Authenticity | Brand-voice adherence · Language authenticity (native-speaker blind eval per language) |

**L2 Diagnostics:** Per-language eval score · Per-language satisfaction rate · Satisfaction gap by domain · Eval misses that reached users · Red-team violation count

---

## Layer 6 — Platform

**L0:** Reliability-Adjusted Availability = % of seconds up AND within latency SLO AND below crash threshold

| Group | L1 Metrics |
|---|---|
| Components | Service uptime % · Latency SLO compliance (voice ≤1.5s / agentic ≤700ms) · Crash rate per 100 sessions · Scale headroom ≥30% at 100K concurrent · PR-to-production velocity ≤2h |

**L2 Diagnostics:** Per-service availability · Per-region latency · Incident detect→ack time

---

## Layer 7 — Partners

**L0:** Partner Skill Coverage = % of skills served by partners

| Group | L1 Metrics |
|---|---|
| Ecosystem | Partner-built skills in production · Self-serve onboarding rate · Onboarding gate time ≤7d · New skills/month autonomous · External partners live |

**L2 Diagnostics:** Per-partner skill share · Per-partner task completion rate · Manual steps per onboarding (must → 0)

---

## Cross-Cutting Attributes

Every L0 and L1 sliceable by all of these.

| # | Attribute | Values |
|---|---|---|
| 1 | Cohort A–E | 5 cohorts per jbiq_user_cohort_gtm__v1.docx |
| 2 | Language | Hindi · English · Tamil · Telugu · Gujarati · Bengali · Marathi · Kannada · Malayalam · Punjabi · Odia · Assamese |
| 3 | Use Cases | Astrology · Spirituality · News · Entertainment · Career · Daily Assistant (directional — grows as verticals ship) |
| 4 | Modality | Voice · Text · Image |
| 5 | Device tier | Low-end · Mid-end · Flagship |
| 6 | Network type | 4G · 3G · 2G |
| 7 | Region | Urban · Tier-2 · Tier-3 · Rural |
| 8 | User type | First-time · Returning |
| 9 | Experience type | Signature · Vertical · Generic chat · Qualifier: 3/3 benchmarks required |
| 10 | Session depth | Single-turn · Multi-turn (≥3) · Extended (≥5) |
| 11 | Time horizon | D1 · D7 · D30 · D90 |
| 12 | Acquisition channel | Jio retail · MyJio · JioFiber · Organic · Paid · Referral |
| 13 | Loop type | Daily · Task · Life |
| 14 | Task type | Query (text/voice/image) · Structured skill action |
| 15 | Surface | Home · Persona page · Widget · Deep link · Notification · History · Settings |

---

## Out of Product Metrics Tree

Real, measurable, important — not measures of whether the product is working for users.

| Track | What it covers |
|---|---|
| Growth / Distribution | Acquisition, CAC, channel mix. GTM produces installs → consumed by Activation Rate (Layer 1 L1). |
| A/B Experimentation | Causal inference engine. Currently blocked at FnF (GrowthBook InfoSec gate). All FnF movements are correlational. |
| Unit Economics | Tokens/user, cost/query, cost/task. The product earns engagement; the operations layer pays for it. |
| Data / Instrumentation | Insight velocity, dashboard coverage, join freshness. |
| Vertical Portfolio | SE count at maturity levels, idea→live velocity. Informs what to build — not whether the product works today. |
| Customer Lifecycle | 8 user-journey stages, per-campaign attribution. Push-attributed Return Rate (Layer 1 L1) is the product-tree interface. |

---

## Glossary

| Term | Definition |
|---|---|
| L0 | The single primary metric for a layer — the outcome. One per layer. |
| L1 | Primary drivers of L0. What pod leads own and optimise. |
| L2 | Diagnostics — where you look when L1 moves. Never in a leadership review. |
| MAU | Monthly Active Users — opened app in last 30 days. |
| MEU | Monthly Engaged Users — query OR audio/video ≥10s. Primary engaged base. |
| MQU | Monthly Query Users — ≥1 query sent. MQU ⊂ MEU. |
| MCU | Monthly Content Users — ≥1 audio/video ≥10s. MCU ⊂ MEU. |
| DEU | Daily Engaged Users — daily snapshot of MEU. |
| Active Habit Rate | DEU ÷ MEU — all returns. Push vs organic at L1. |
| Organic Active Habit Rate | Organic DEU ÷ MEU — push-excluded pull signal. L1 quality lens. |
| Loop Self-Sufficiency | Organic DEU ÷ Total DEU. What share of returns are unprompted. |
| Habit Formation Rate | % push-prompted users who become organic within 60d. |
| Useful Task Rate | % tasks resolved AND user signaled value. Product Work L0. |
| Task Completion Rate | % tasks reaching a resolved state. Layer 4 L0. |
| Qualified Task Rate | % completed tasks where user felt problem was solved. Layer 4 L1. |
| Personalisation Resonance Rate | % sessions where product demonstrated it knew the user. |
| Warm start | Correct language served AND ≥1 UCP attribute applied AND JioID loaded. |
| UCP | User Central Profile — attributes from JioID and session behaviour. |
| Cohort Variance | max(Active Habit Rate across A–E) − min. High = winning unevenly. |
| Signature Experience | Passes all 3 benchmarks — proprietary data + loop-forming + cultural irreplaceability. 3/3 only. |
| ASR / WER | Automatic Speech Recognition / Word Error Rate (lower is better). |
| TTS / MOS | Text-to-Speech / Mean Opinion Score (naturalness, 1–5). |
| TTFT / p95 | Time to First Token / 95th percentile latency. |
| FnF / GA | Friends and Family (pre-Beta) / General Availability (public launch). |
| pp | Percentage points. |

---

## Companion Files

- `product-context.md` — product metrics context, ownership, operational state
- `bharat-metrics.md` — Bharat resonance framework, per-cohort metrics, qualitative resonance
- `non-product-metrics.md` — parallel tracks outside the product tree
