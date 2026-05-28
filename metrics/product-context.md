# JioBharatIQ — Product Metrics Context

*Owner: Sridhar · Status: Synthesis · Last updated: 2026-05-10*

*This file is the **context wrapper** around the metrics work — it ties the canonical source docs (Product Mesh, Goals GA, FnF Dashboard, Lifecycle Framework) together with current ownership, milestones, and operational state. The actual product metrics tree lives in `metrics-tree.md`. The Bharat resonance framework lives in `bharat-metrics.md`. Non-product metrics tracks (Growth, Data, A/B, Unit Economics, Customer Lifecycle, etc.) live in `non-product-metrics.md`.*

---

## The crystallised view

**The metrics framework already exists.** It is not one document — it is four, layered, by altitude:

1. **Vision / Mission / Success** — `JBIQ Product Mesh.docx` (Mar 2026, GA-defining)
2. **Org goals (10) cascaded to Pods (10), with Beta + GA targets** — `JBIQ Goals — GA Pod Cascade.md` + `JBIQ_Goals_GA.docx` (May 8, 2026, draft v0.5, awaiting Rushabh + Naroo review)
3. **Lifecycle framework (8 stages) + comms triggers** — `JBIQ_User_Lifecycle_Framework_v1.0.docx` (Apr 2026, Sridhar's)
4. **Operational surface (FnF dashboard, 8 sections, ~150 metrics, instrumented across 6 systems)** — `JBIQ_FnF_Metrics_Working.xlsx` (Apr 2026)

**The work for this folder is not to draft a new framework — it is to:**
- Crystallise the single operational North Star
- Map every metric to a layer + owner
- Track instrumentation gaps blocking May 15 FnF wave 1
- Calibrate provisional thresholds (X*, Y*) from FnF cohort data

---

## 1. Vision and Success (from Product Mesh)

> **Vision:** Democratize intelligence for 1.4 billion Indians — making AI abundant, affordable, and accessible to every Indian, in every language, across every domain of daily life.
>
> **Success:** "When users say 'my day just works better' without thinking about the technology."

**Underlying principle (P7):** *Build for the loop, not the visit.* The measure of a product working is organic return without push.

---

## 2. The Operational North Star

Of the 10 org goals, **Goal 4 is the operational North Star** — it is the only goal that directly tests P7 at scale, and it captures both the core promise (the product works) and the loop principle (it works without being pushed).

### Goal 4 — Consumer Outcomes
| Milestone | Target |
|---|---|
| **Beta (by June 30, 2026)** | 25–30% of monthly users return **daily without a push trigger** AND 70%+ of tasks initiated are **resolved** |
| **GA (within 60 days of launch)** | 40%+ return daily without push AND 80%+ tasks resolved |

**Why this and not MAU:** Goal 1 (1M MAU at GA) is the *reach* outcome; it can be hit with paid acquisition and push spam without the product working. Goal 4 measures whether the loop works.

**Composite framing (FnF dashboard's "Engagement North Star"):** `DAU × Sessions/User` — combines reach and depth in one number.

---

## 3. The 10 Org Goals (cascaded targets)

From `JBIQ Goals — GA Pod Cascade.md` (May 8, 2026, draft v0.5).

| # | Cluster | Beta (June 30, 2026) | GA (within 60 days) |
|---|---|---|---|
| **1** | Market Reach | 50K+ Reliance/Jio employee MAU | **1M+ MAU within 90 days** |
| **2** | Market Reach | 10+ signature experiences across 3+ domains, D7 ≥25%, ≥1 at L3 | 15+ across 5+ domains, D7 ≥40% |
| **3** | Consumer Outcomes | 30%+ first-session task completion | 40%+ first-session task completion |
| **4** | **Consumer Outcomes** | **25–30% organic daily return + 70%+ task resolution** | **40%+ organic daily return + 80%+ task resolution** |
| **5** | Platform Capability | 8+ languages at parity with benchmark WER | 12+ languages beating benchmark by 5%+ |
| **6** | Platform Capability | 95%+ eval pass · stable at 25K concurrent | 99%+ eval pass · stable at 100K concurrent |
| **7** | Scale Readiness | 3+ Jio partners powering ≥25% queries | 5+ partners powering ≥40% |
| **8** | Scale Readiness | 1+ new SE/month, partner-built or autonomous | 2+ new SE/month, autonomous |
| **9** | Scale Readiness | 3+ external partners live, ≤7-day compliance | 5+ external partners, 3+ new/month |
| **10** | AI-Native Org | 70%+ org using AI tooling | 100% org using AI tooling |

---

## 4. Pod Cascade — Who Owns What

Layered by floor (per Product Layers + Pod Cascade). **Sridhar is sole owner of Core Experience.**

### Top Floor — Experience
| Pod | Owner | Owns | Supports |
|---|---|---|---|
| **Core Experience** | **Sridhar** | Goal 4 (return rate) | 1, 2, 3 |
| **Vertical Experience** | **Sridhar** | Goal 2 | 4, 8 |
| Partner Experience | Sushant | Goals 7, 8, 9 | 2 |

### Middle Floor — Capability
| Pod | Owner | Owns | Supports |
|---|---|---|---|
| Agentic Orchestration | Bharat | Goal 3, Goal 4 (task resolution) | 6 |
| Speech / Voice | Anmol | Goal 5 | 4 |
| Memory / Personalisation | Karan | — | 3, 4 |

### Bottom Floor — Foundation
| Pod | Owner | Owns | Supports |
|---|---|---|---|
| Data | Vinay | — | All 10 |
| DevOps | (TBC) | Goal 6 (capacity) | All |
| Evals + Trust | Karan | Goal 6 (quality) | All |

### Cross-cutting
| Pod | Owner | Owns |
|---|---|---|
| Business / GTM | (TBC) | Goal 1 |
| AI-Native Org | All pods | Goal 10 |

---

## 5. Core Experience — My Pod's Six Beta-to-GA Commitments

These are mine to deliver. Pulled verbatim from the Pod Cascade.

| Goal | Beta target | GA target |
|---|---|---|
| First-session activation | 50%+ first-time users issue ≥1 query | 70%+ |
| **Organic daily return** | **25–30% of monthly users return daily without push** | **40%+** |
| Experience discovery | 40%+ discover ≥2 SEs in first week | 60%+ |
| Satisfaction (NPS) | NPS ≥30 (≥30% survey response) | NPS ≥50 |
| Homepage performance | ≤3s p95 at 25K concurrent | ≤2s p95 at 100K concurrent |
| D7 retention signal | Top 3 driver experiences + top 3 drop-offs identified by Beta exit | D7 retention ↑ ≥5pp over Beta baseline |

---

## 6. Lifecycle Framework (8 stages, drives comms)

From `JBIQ_User_Lifecycle_Framework_v1.0.docx` (Apr 2026, mine). Stages are defined by **intent signals**, not days. Day markers are intervention windows.

```
Onboarding → Activation → Engagement → Retention(Prompted) → Retention(Organic)
                                                 │                  │
                                                 ↓                  ↓
                                            Re-engagement ← Uninstalled → Winback
                                                                            │
                                                                            ↓
                                                                       Advocacy (outcome layer)
```

**Critical metric — Habit Formation Rate:** % of Prompted users who become Organic within 60 days. *A consistently low rate signals the product loop needs strengthening, not more comms.* This is the single best integrative health signal for P7.

**Companion engineering brief:** `JBIQ_CT_WA_Instrumentation_Spec_v1.0_1.docx` — 14 CleverTap events, 9 user properties, 11 campaign configs. Pre-FnF instrumentation checklist defined.

---

## 7. FnF Operational Dashboard (May 15 – June 12, 2026)

From `JBIQ_FnF_Metrics_Working.xlsx`. Two waves (May 15, May 29). Target: 3,000–4,000 active users across waves.

### Eight sections, ~150 metrics
| | Section | What it measures |
|---|---|---|
| A | Top of Funnel | Reach → Acquisition → Onboarding → Activation |
| B | Engagement | Sessions, Depth, Breadth (incl. **Engagement North Star = DAU × Sessions/User**) |
| C | Retention & Lifecycle | Cohort returns (D1/D3/D7/D14/D21), inactive thresholds |
| D | User Profiling | Cohort, Modality, Language, Device, Permissions |
| E | **Persona / Vertical FnF Marquee** | 19 personas/tools — Attempt %, Completion %, 24hr Return |
| F | Quality, Performance, Ops | Thumbs up/down, NPS, eval scores, hallucination, latency, crash, uptime |
| G | Voice Performance | Voice session %, abandonment, ASR WER |
| H | Campaigns & Nudges | PN/WA delivery, CTR, post-click action |

### FnF gate metrics
- **D3 organic return ≥22% (W1) / ≥18% (W2)** — primary early signal
- **D7 return ≥15%** — gate for Wave 2 open (May 22)
- **DAU/MAU ≥30% at D30** (no Alpha baseline)
- **NPS ≥50** at D7 + D21 surveys (≥80% completion target)
- **Crash rate <1% per 100 sessions**
- **p95 latency <2,000ms** (Alpha p90 was 26s — hard requirement to beat)
- **AI resolution rate ≥99%**

### Magic number hypothesis (FnF activation)
**"3 tasks, 2 domains, 7 days"** — % of D7 users with 3+ flows ≥40% predicts D7 organic return. Validating this in FnF.

### 19 FnF personas/tools tracked individually
**Personas:** Cricket Companion · Rashifal/Kundali · Devotion (Aarti/Sankalp/Mandir/Sandesh) · Interview Prep · English Learning · Microlearning · Govt Exam Prep · Daily News Reader · Fact Check Shield · Market Pulse · Apna Dost · Saheli · Jaankaar Bhaiya · Subah Ka Saathi
**Tools:** Create Image · Edit Image · Email/Message Writer · Analyse Document · Translate

Each tracked: Attempt Rate %, Completion Rate %, 24hr Return % (P0 priority on first two, P1 on third).

---

## 8. Instrumentation Stack

Six systems, joined on `user_id` and `session_id`. Per Goal 7 (Data): all sources must be joined within 15 min at Beta, 5 min at GA.

| System | Role |
|---|---|
| **Firebase / GA4** | Mobile events (app launch, prompts, taps, permissions, crashes) |
| **Langfuse** | LLM traces, eval scores, hallucination, ASR/TTS performance |
| **Databricks** | Joined event/user data, cohort analytics, retention curves |
| **CleverTap** | Lifecycle campaigns, PN/WA delivery, segmentation |
| **New Relic** | Backend latency, error rate, uptime |
| **Crashlytics** | Mobile crash and ANR monitoring |
| (GrowthBook) | Experimentation — *blocked at FnF, InfoSec gating* |

**Goal 7 (Data, Vinay):** Every metric in this doc has a live dashboard openable in ≤10s by Beta exit. Self-serve analytics: any team member creates a dashboard in <2 min.

---

## 9. Critical Instrumentation Gaps — Block FnF May 15

From the FnF Metrics xlsx "Instrumentation Gaps" sheet. **All P0 must be resolved before Wave 1 opens.**

| Metric | Gap | Owner |
|---|---|---|
| Avg Session Duration | session_start/end timestamps not in Firebase | App + Firebase |
| Task Completion Rate | No completion signal defined | Product + Langfuse |
| First-Try Success / Rephrase Rate | Rephrase detection not built | Langfuse |
| Language on prompt_submitted | Language param missing from all Firebase events | App instrumentation |
| Turn-level join (trace_id) | trace_id missing — **#1 instrumentation gap** | App + orchestrator |
| Mid-Session Drop-Off Rate | No session-end event for abandoned sessions | Firebase |
| Feature Penetration | agents_used ≥2 derived metric not built | Databricks |
| **Family cohort identification** | No referral link — cannot flag family vs employee | Registration flow (**Open Q1**) |
| **Channel attribution tagging** | Source channel not captured at allow-list registration | Registration flow (**Open Q2**) |
| Push campaign → session join | push_notification_tapped event not built | App + CleverTap ETL |

P1 gaps (can defer): Time to Activation, City Tier/State/City, Age/Gender, Persona ID on events, Domain field rename, Fallback to English Rate, GrowthBook variant assignment.

---

## 10. Open Questions (status as of 2026-05-09)

| # | Question | Decision needed from |
|---|---|---|
| Q1 | Family cohort identification at registration — referral link mechanic? | Sridhar + Registration flow team |
| Q2 | Channel attribution tagging — how is source captured at allow-list? | Sridhar + GTM |
| Q3 | Calibrate X* (day) and Y* (query) thresholds in lifecycle framework from FnF cohort data | Sridhar + Vinay (after Wave 1) |
| Q4 | Loop-level reporting (Daily / Task / Life cuts per Product Mesh) — does the data layer support this from Wave 1? | Vinay |
| Q5 | Speech / Voice pod owner — not named in Pod Cascade | Naroo |
| Q6 | DevOps pod owner + Business/GTM pod owner — not named | Naroo |
| Q7 | "Bharat Pulse" dashboard — referenced in concept note as the always-on Sridhar/Analytics view; design and cadence not specified | Sridhar + Vinay |
| Q8 | Goals GA doc is awaiting Rushabh + Naroo review (draft v0.5, May 8) — when does it lock? | Naroo |

---

## 11. Where this leaves Core Experience for the next 6 weeks

**Wave 1 opens May 15.** My focus before that:

1. **Close P0 instrumentation gaps** (or accept degraded view) — coordinate with Vinay, Karan, App eng
2. **Resolve Q1 (family cohort) and Q2 (channel attribution)** — registration flow change
3. **Define task completion signal** with Bharat + Karan — currently undefined, blocks M3 and Goal 4
4. **Confirm magic number hypothesis instrumentation** — % users with 3+ flows by D7 needs `agents_used ≥ 2 per session` derived metric
5. **Lock NPS survey mechanics** — D7 + D21, ≥80% completion, ≥30% response

**During Wave 1 (May 15 – May 22):**
- Watch D3 organic return and D7 return as gate metrics for Wave 2 open
- Identify top 3 driver SEs and top 3 drop-off points (per Goal 6 scale-readiness for Core Experience)

**Between FnF and Beta exit (June 30):**
- Calibrate X*/Y* thresholds in lifecycle framework
- Diagnose any gap on Goal 4 (organic daily return) — is it onboarding, discovery, or engagement loop?

---

## 12. References

**Source docs (saloni's OneDrive — `01 Product/`):**
- `JBIQ Product Mesh.docx` (Mar 2026) — Vision, Success, 7 GA metrics, 3 Loops (Daily/Task/Life), 10 Signature Experiences, 5 Key Bets, scope boundaries
- `Product Layers/JBIQ Product Layers.pptx` (Mar 2026) — Layer stack (Experiences/Intelligence/Systems), pod ownership
- `Product Milestones/JBIQ Goals — GA Pod Cascade.md` (May 8, 2026, v0.5) — 10 org goals × 10 pods × Beta+GA targets
- `Product Milestones/JBIQ_Goals_GA.docx` (May 9, 2026) — Same content in docx form
- `JBIQ_FnF_Metrics_Working.xlsx` (Apr 2026) — FnF dashboard, ~150 metrics across 8 sections + instrumentation gaps
- `User Lifecycle/JBIQ_User_Lifecycle_Framework_v1.0.docx` (Apr 2026) — 8-stage lifecycle, comms triggers, Habit Formation Rate
- `User Lifecycle/JBIQ_CT_WA_Instrumentation_Spec_v1.0_1.docx` (Apr 2026) — 14 events, 9 properties, campaign config map
- `JBIQ GA Launch PRFAQ.docx` (May 2026) — Public framing for GA launch
- `JBIQ_CLM_Strategy_Working - V3.docx` (Apr 26, 2026) — CLM strategy v3 (not yet integrated into this doc)

**In claudespace:**
- `JBIQ_Onboarding_Full_Doc.md` — onboarding success metrics (feeds first-session activation)
- `JBIQ Experience Decks/06-hooks-loops/DECK_BRIEF.md` — PLG framework (Hooks/Loops/Growth)
- `JBIQ Experience Decks/decisions/jbiq-chat-log.md` — architectural decisions, dropped S8 metrics slide context
