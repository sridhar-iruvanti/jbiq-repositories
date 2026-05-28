# JioBharatIQ — Non-Product Metrics

*Parallel metrics tracks that sit **outside** the Product Metrics Tree (`metrics-tree.md`). Real, measurable, important — but they're infrastructure, GTM, operations, or strategic content management, not product-quality measures of whether the AI works for users.*

*Owner: Sridhar (cross-track view) · Last updated: 2026-05-10*

---

## Why these are not in the Product Tree

A product metric measures whether the product **delivered value to the user**. The metrics here measure:

- Whether we acquired users (**Growth**)
- Whether we can run the business sustainably (**Unit Economics**)
- Whether we can measure (**Data**)
- Whether we can validate causally (**A/B Experimentation**)
- Whether we can ship content (**Vertical Portfolio Management**)
- Whether comms moves the lifecycle (**Customer Lifecycle**)
- Whether we generate revenue (**Business / Monetization**, post-GA)

All necessary for the product to exist and grow — but not measures of the product itself.

---

## Track 1 — Growth (GTM)

*Acquisition, CAC, channel mix, paid attribution. Owned by GTM/Marketing.*

| Metric | Definition |
|---|---|
| New users acquired per month | Total new installs across all channels |
| Activated New Users / Month | Installs that fire ≥1 query within 7 days (the quality-adjusted view) |
| CAC | Cost of Acquisition per user |
| Channel mix | % of acquisitions per channel |
| Per-channel D7 organic return | Cohort retention sliced by acquisition channel — separates real users from vanity installs |
| Per-channel CAC | Acquisition cost per channel |
| Attribution coverage | % of installs with attributable source |
| Referral attribution rate | % of new installs from in-app referrals (product-earned, flagged here for completeness) |

**Interface to Product Tree:**
- GTM produces installs → consumed by **Activation Rate** (Layer 1 L1)
- Product earns advocacy → **Virality, Active Share Rate, Referral Attribution Rate** (Layer 1, components of Active Habit Rate) flow back to GTM

---

## Track 2 — Distribution (GTM)

*Channels through which users reach the product — Jio retail, MyJio, JioFiber, organic search, paid acquisition, referral. Owned by GTM.*

| Metric | Definition |
|---|---|
| Channel install volume | Per-channel new users |
| Channel cohort distribution | Which Cohort A–E each channel produces |
| Distribution partnership outcomes | Effectiveness of bundle / retail / OEM deals |
| Distribution-driven activation rate | % of channel users who activate |

**Interface:** The **Cohort A–E** cross-cut in the product tree slices every metric by distribution-derived cohort segments without owning the channels themselves.

---

## Track 3 — Business / Monetization (post-GA)

*Revenue, transactions, subscriptions. Out of scope at GA per the Mesh ("no advertising, transactions, subscriptions at GA"). Activates post-GA. Track structure exists; metrics activate when monetization launches.*

| Metric | When it activates |
|---|---|
| ARPU (Average Revenue Per User) | Post-monetization |
| Per-feature monetization conversion | Post-monetization |
| Transaction volume per user | Post-monetization |
| Subscription conversion rate | Post-monetization |
| Subscription churn rate | Post-monetization |
| LTV (Lifetime Value) | Post-monetization |
| LTV/CAC ratio | Post-monetization |
| Ad revenue per user (if ads ship) | Post-monetization, if applicable |

**Status:** Inactive at GA. No interface to Product Tree until monetization is live.

---

## Track 4 — Customer Lifecycle

*Per `JBIQ_User_Lifecycle_Framework_v1.0.docx` (April 2026). Eight stages defined by intent signals (not days). The lifecycle is a user-journey framework — comms is one mechanism for moving users through stages, but the lifecycle itself is broader (covers product surfaces, comms, and behavioural transitions). Owned by Sridhar.*

### Lifecycle stages and their metrics

| Stage | Definition | Key metrics |
|---|---|---|
| **Onboarding** | First home page load → tooltips dismissed or first query sent | Onboarding completion %, time to first query, drop-off point |
| **Activation** | First query response received | Activation rate, D1 return rate, DQU, first query modality |
| **Engagement** | Y* queries across 2+ sessions; multiple session, multiple query types | WAU, DQU, queries per session, multi-turn rate, modality mix, feature breadth |
| **Retention (Prompted)** | Returns consistently in response to PN/WA — channel-dependent habit | MAU, DAU/MAU, DQU, at-risk %, query length trend |
| **Retention (Organic)** | Returns on own intent without any prompt — habit formed | MAU, DAU/MAU, DQU, **Habit Formation Rate**, query length trend |
| **Re-engagement** | App installed; no query for X+ days | Reactivation rate, sessions post-nudge, DQU recovery, PN vs WA response rate |
| **Uninstalled** | User has removed the app — PN channel lost | Re-install rate, WA open rate, WA response rate, stage at uninstall |
| **Winback** | Re-install after prior uninstall — prior context exists | D14 re-retention, time to exit, DQU recovery, multi-turn rate |
| **Advocacy** (outcome layer, not sequential) | Satisfaction signal fired — high multi-turn, repeated daily use | Rating submitted rate, referral shared rate |

### Habit Formation Rate

```
Habit Formation Rate = % of Prompted-stage users who become Organic-stage within 60 days
```

**The KPI for whether comms is working long-term.** A consistently low rate signals the *product loop* needs strengthening, not more comms.

### Comms-effectiveness metrics (CleverTap + WA)

Per `JBIQ_CT_WA_Instrumentation_Spec_v1.0_1.docx` — 14 events, 9 user properties, 11 campaign configs.

| Metric | Definition |
|---|---|
| PN delivered, opened, post-click action rate by stage and campaign | Per-campaign push effectiveness |
| WA delivered, opened, response rate | Per-campaign WhatsApp effectiveness |
| Per-campaign nudge effectiveness | Completed action within 24hr ÷ delivered |
| Stage transition rates | % moving from Prompted → Organic, etc. |
| Frequency cap hit rate | Users hitting daily/weekly PN/WA caps |

### Interface to Product Tree

- **Push-attributed Return Rate** (Layer 1 L1) — the product-tree side: returns triggered by comms
- **Loop Self-Sufficiency** (Layer 1 L1) — Organic ÷ Total returns; high value = product working without comms support
- Comms-only metrics (per-campaign open rates, stage-transition rates) live here, not in the product tree

---

## Track 5 — Data (Foundation Capability)

*Instrumentation, dashboards, joins, freshness, self-serve analytics. Owned by Vinay (Data + Reporting pod).*

| Metric | Definition |
|---|---|
| Insight Velocity | Median time question raised → answer found (target: ≤1 min self-serve, ≤1 day for new instrumentation) |
| Dashboard coverage % | % of L1 metrics in `metrics-tree.md` with a live dashboard openable in ≤10s |
| Cross-source join freshness | Time to join Spanner / GA4 / Langfuse / GrowthBook / New Relic / CleverTap on user_id and session_id (target: ≤15min Beta, ≤5min GA) |
| Instrumentation velocity | Days to add a new event to any consumer |
| Self-serve analytics adoption | % of teams creating dashboards without data engineer |
| Data engineer involvement count for product Qs | Should trend → 0 |
| Per-source uptime | Where instrumentation breaks |
| Open instrumentation gap count | Backlog signal |

### Status as of FnF (May 2026)

**16 P0 / P1 instrumentation gaps tracked in `JBIQ_FnF_Metrics_Working.xlsx`.** Must close before Wave 1 (May 15). Critical gaps include:
- Task Completion Rate (no completion signal defined — blocks Layer 4 L0)
- Re-explanation rate (NLP detection not built — blocks Layer 2 L2)
- Language param missing from all Firebase events (blocks per-language slicing)
- trace_id missing from prompt_submitted (#1 instrumentation gap — blocks turn-level join)
- Family cohort identification (blocks Cohort A–E classification — Open Q1)
- Channel attribution tagging (blocks per-channel cuts — Open Q2)

**Interface:** Every L0 / L1 in the product tree depends on Data being live. If Data fails, product metrics are not measurable.

---

## Track 6 — A/B Experimentation (Foundation Capability)

*Causal inference engine — validates that product metric movements were caused by specific changes. Owned by Vinay (Experimentation pod).*

| Metric | Definition |
|---|---|
| Experiment velocity | # of experiments shipped per month |
| Time-to-significance | Days from experiment start to actionable result |
| Experiment coverage | % of changes shipped through A/B vs ship-and-watch |
| Holdout-cohort discipline | % of high-risk changes with clean control group |
| Variant-assignment integrity | Leakage rate, randomisation quality |
| Per-team experiment cadence | Are pods using experiments? |

### Distinct from Eval CI/CD (Layer 5 in product tree)

| | When | What it does | Where it lives |
|---|---|---|---|
| **Eval CI/CD** | Pre-deploy | Offline quality gate — every merge runs evals before shipping | Layer 5 (Quality) L1 |
| **A/B experiment** | Post-deploy | Online causal validation — split traffic, measure delta | Here (capability track) |
| **Production Quality Floor** | Always-on | Production truth on shipped responses | Layer 5 (Quality) L0 |

### Status at FnF

**Blocked.** GrowthBook not cleared by InfoSec; no client-side instrumentation. **All FnF metric movements during Wave 1 are correlational, not causal.** P1 instrumentation gap.

---

## Track 7 — Unit Economics (Operations)

*Cost of serving the product. Owned by Engineering + Finance.*

| Metric | Definition |
|---|---|
| Tokens consumed per user per day | LLM input + output tokens |
| Cost per query | Compute + model + orchestration overhead per query |
| Cost per task | Queries × turns × routing overhead |
| Cost per active user per month | Running cost ÷ MQU |
| LLM model-mix cost ratio | Premium model usage as a cost driver |
| Voice pipeline cost | ASR + TTS per voice query |
| Per-domain cost-per-task | Which domains are most expensive? |
| Per-language cost | Regional language costs (some languages more expensive due to model mix) |
| Cost per 1M MAU | Marginal scale economics |

### Interface to Product Tree

Every product metric has a **unit-economics shadow**:
- Active Habit Rate ↑ + Cost-per-user flat = product winning sustainably
- Active Habit Rate ↑ + Cost-per-user explodes = unsustainable victory
- Useful Task Rate ↑ + Cost-per-task flat = quality scaling
- Useful Task Rate ↑ + Cost-per-task ↑ = expensive quality

Track them paired but don't put unit economics IN the product tree. *The product earns engagement; the operations layer pays for it.*

---

## How to use this doc

| Audience | Tracks they care about |
|---|---|
| **Sridhar / Core Experience** | Track 4 (Customer Lifecycle) — own pod's adjacency · Track 5 (Data) status |
| **GTM / Marketing** | Tracks 1, 2 · Track 3 (post-GA) |
| **Engineering / Vinay** | Tracks 5 (Data), 6 (A/B), 7 (Unit Economics) |
| **Leadership** | Cross-track view — looked at in totality alongside Product Tree to see whether the product is being measured, validated, served, and made sustainable as a system |

---

## Open questions across tracks

| # | Question | Track | Owner |
|---|---|---|---|
| N1 | Activated New Users / Month threshold definition | Track 1 (Growth) | Sridhar + GTM |
| N2 | Channel attribution tagging at registration | Track 2 (Distribution) | Registration flow team |
| N3 | Customer Lifecycle X/Y thresholds — calibrate from FnF cohort data | Track 4 (Lifecycle) | Sridhar + Vinay (post-Wave 1) |
| N4 | A/B unblock — InfoSec clearance for GrowthBook | Track 6 (A/B) | Vinay + InfoSec |
| N5 | Cost-per-query baseline before Wave 1 | Track 7 (Unit Economics) | Engineering |
| N6 | 16 instrumentation gaps to close before Wave 1 | Track 5 (Data) | Vinay + App eng |

---

## References

**Source docs (saloni's OneDrive `01 Product/`):**
- `JBIQ_FnF_Metrics_Working.xlsx` — FnF dashboard with full instrumentation gap list
- `JBIQ_User_Lifecycle_Framework_v1.0.docx` — Customer Lifecycle Framework (8 stages)
- `JBIQ_CT_WA_Instrumentation_Spec_v1.0_1.docx` — Comms instrumentation
- `JBIQ_CLM_Strategy_Working - V3.docx` — CLM strategy v3
- `jbiq_user_cohort_gtm__v1.docx` — GTM cohort definitions (A through E)
- `Product Milestones/JBIQ Goals — GA Pod Cascade.md` — pod-level cascaded targets

**Companion files in this folder:**
- `metrics-tree.md` — **the** Product Metrics tree (always-on, user-experience layers)
- `product-context.md` — Product Metrics context / synthesis (ties Mesh + Goals + FnF + tree)
- `bharat-metrics.md` — Bharat resonance framework (parallel, periodic, qualitative)
