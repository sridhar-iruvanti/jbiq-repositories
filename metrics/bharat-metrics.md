# JioBharatIQ — Bharat Metrics Framework

*Parallel framework to the Product Metrics tree. Reviewed in totality, periodically. Not part of the always-on product tree.*

*Owner: Sridhar · Last updated: 2026-05-10*

---

## What this framework is — and what it isn't

**It is:** A parallel view that combines **Product Metrics sliced by Cohort A–E** with **Bharat-specific qualitative resonance metrics** (the soft stuff that doesn't fit in always-on product instrumentation).

**It is not:** A separate layer of the product tree. The behavioural resonance test — *"are users in each cohort coming back organically?"* — is already captured by Active Habit Rate sliced by Cohort A–E. That's a cross-cut in the product tree, not a separate metric.

**Why the framework exists:** Some resonance signals are inherently qualitative, periodic, and Bharat-specific — *"feels native or translated?"*, persona-fit feel, cultural relevance. These can't sit in always-on instrumentation. They belong in a separate framework reviewed quarterly.

**The product is working for a cohort when:**
- The cohort's Active Habit Rate is healthy (behavioural resonance — measured in product tree)
- The cohort's qualitative resonance signals say it feels native (cultural resonance — measured here)

Both must hold.

---

## How this connects to the Product Metrics tree

```
PRODUCT METRICS TREE                   BHARAT METRICS FRAMEWORK
(canonical, always-on)                 (this doc, periodic)
─────────────                          ─────────────
                                       
Layer 1: The User Loop                 Section 1: Per-Cohort Product Health
Layer 2: The Personalization             (inherits from Product Tree, sliced by A–E)
Layer 3: The Conversation                See §1 below.
Layer 4: The Task Delivery             
Layer 5: The Quality                   Section 2: Bharat-Specific Resonance
Layer 6: The Platform                    (NEW metrics not in Product Tree —
Layer 7: The Partners                     qualitative, periodic, cohort-specific)
                                         See §2 below.
Cross-cut: Cohort A–E                  
applies to all metrics                 Reviewed in totality, quarterly.
```

---

## Section 1 — Per-Cohort Product Health (inherited)

**Cohort definitions:** A through E, per `jbiq_user_cohort_gtm__v1.docx`. Each cohort encapsulates language, device tier, geography, and segment attributes. Cohort definitions are deliberately not unpacked here — the GTM doc is the single source of truth.

For each cohort A–E, track the Product Tree metrics filtered to that cohort:

| Metric | Source layer in Product Tree | Per-cohort question |
|---|---|---|
| Active Habit Rate (Organic DQU ÷ MQU) | Layer 1 L0 | Are users in this cohort returning organically? |
| Useful Task Rate | Product L0 | When this cohort uses JBIQ, does the AI deliver? |
| Personalization Resonance Rate | Layer 2 L0 | Does it feel made for this cohort? |
| Multi-turn Coherence Rate | Layer 3 L0 | Do conversations work for this cohort? |
| Task Resolution Rate | Layer 4 L0 | Does the orchestrator serve this cohort? |
| Production Quality Floor | Layer 5 L0 | Is response quality holding up for this cohort? |
| Reliability-Adjusted Availability | Layer 6 L0 | Is the platform serving this cohort reliably? |
| NPS | Layer 1 L1 | Does this cohort recommend it? |
| First-session activation rate | Layer 1 L1 | Did the cohort get value on first visit? |
| D7, D30, D90 organic return rate | Layer 1 L1 | Retention curve per cohort |
| Voice Primary User Share | Layer 3 L1 | Is voice the primary mode for this cohort? |

**The Cohort Score (per cohort) is a weighted composite of these.** Same template across cohorts; weights tuned to reflect what matters for each cohort (e.g., voice metrics weighted higher for voice-primary cohorts).

### The diagnostic — Cohort Variance

```
Cohort Variance = max(Cohort Score across A–E) − min(Cohort Score across A–E)
```

If Cohort Variance is high, the product is winning unevenly. Even a healthy *average* across cohorts can hide one cohort failing.

This metric is **also kept at Layer 1 L2 of the product tree** so leadership reviewing the tree alone catches it.

---

## Section 2 — Bharat-Specific Resonance Metrics (new, qualitative, periodic)

These metrics are **not in the product tree** because they're survey-based, qualitative, or require linguistic deep-dive. They live here, reviewed quarterly.

### A — Cultural & linguistic resonance

| Metric | How measured | Cadence |
|---|---|---|
| **"Feels native vs translated" score** per language | Native-speaker blind eval — rate AI responses in their language for native-feel on a 1–5 scale | Quarterly per language |
| **Code-mix authenticity** (Hinglish, Tanglish, Gujlish, etc.) | Native-speaker eval — does code-mix feel like how Indians actually speak, or stilted? | Quarterly per language pair |
| **Cultural relevance rating** | Survey on cultural moments handling — festival awareness, idiom usage, regional nuance, religious sensitivity | Quarterly |
| **Regional idiom usage rate** | NLP scan of AI responses for region-correct idioms (target language ≥ X% rate) | Monthly |

### B — Persona-fit / "made for me" signals

| Metric | How measured | Cadence |
|---|---|---|
| **Persona-fit score per cohort** | Survey item: *"Felt like a friend / felt like a tool / felt foreign"* — collected per cohort | Quarterly |
| **"It understands me" score** | Survey item: *"How well does JBIQ understand who you are?"* on a 1–5 scale per cohort | Quarterly |
| **"Made for users like me" agreement rate** | Survey item: *"This product feels made for someone like me"* (agree/disagree) per cohort | Quarterly |

### C — Bharat user-pattern signals (qualitative deep-dive)

| Metric | How measured | Cadence |
|---|---|---|
| **Shared-device handling quality** | Diary-study observation: are family members getting context-correct responses without confusion? | Quarterly |
| **Family-as-unit relevance** | Qualitative: are household-relevant intents (homework, panchang, schemes-for-parents) surfacing for the right cohorts? | Quarterly |
| **Micro-loop satisfaction** (≤60s, ≤90s sessions) | FGD: do users in micro-loop cohorts feel the product values their time? | Quarterly |
| **Trust in low-end-device experience** | FGD with low-end users: does it feel like the product is built for their device, or like a degraded version? | Quarterly |

### D — Brand-voice + tone (cross-language deep-dive)

| Metric | How measured | Cadence |
|---|---|---|
| **Brand-voice character traits adherence** (cross-language) | Audit of AI responses against the 6 character traits (`CLAUDE.md` brand voice doc): *Never Behind · Seedha Baat Pyaar Se · No Dead Ends · Infinite Patience · Celebrates Small Wins · Honest About Limits* | Quarterly per language |
| **Sycophancy rate** ("Great question!" or padding) | NLP scan — should trend → 0 in all languages | Monthly |
| **"Translated feel" detection** | Linguist rating — does the AI sound like English-translated-to-Hindi, or natively Hindi? | Quarterly per language |

### E — Cohort qualitative deep-dive (FGD + diary)

| Output | Cadence | Owner |
|---|---|---|
| Top 5 promoter and detractor themes per cohort A–E | Quarterly | Research + Sridhar |
| Diary-study findings per cohort | Quarterly | Research |
| Cross-cohort comparison: which cohorts are most/least served, and why | Quarterly synthesis | Sridhar |

---

## How to use this framework

### Quarterly review (in totality)
- Walk the full per-cohort scorecard (Section 1) — surface which cohorts are clicking
- Walk the Bharat-specific resonance metrics (Section 2) — surface where the product feels native vs translated
- **The integrative question:** *Which cohorts are we serving well behaviourally AND resonance-wise?*

### Decision rule for cohort bets
- High Active Habit + high Persona-fit = doubling down
- High Active Habit + low Persona-fit = users are stuck (no alternative); resonance work needed
- Low Active Habit + high Persona-fit = small loyal base; expand carefully
- Low Active Habit + low Persona-fit = the bet is failing; investigate before scaling

### Where this connects to product decisions
- Any feature that improves headlines but degrades any cohort's resonance is **net negative** — Bharat is the strategic moat
- Any feature that *increases Cohort Variance* (helps Cohort A but not D) is suspect — even if absolute headlines move up
- Quarterly Bharat review feeds back into Layer 5 (brand-voice, language authenticity at L1) and Layer 1 (NPS verbatim themes at L2)

---

## On user-level cohort identification

Every user is assigned to one of cohorts A–E based on signals (language, device tier, geography, behaviour). This is:
- Standard product analytics — most consumer apps do this
- Algorithmic — rules-based assignment from Day 0 signals, refined by behaviour over time
- Owned by the Data layer (Vinay), per definitions in the GTM cohort doc
- Not a manual decision per user — automated classification

The cost: real but standard one-time eng work. The benefit: every product metric in the tree becomes sliceable by cohort, and this Bharat framework becomes operable.

---

## Open questions

| # | Question | Decision needed from |
|---|---|---|
| B1 | Cohort Score component weights — how to weight Active Habit, Useful Task, Personalization, NPS, voice signals within each cohort? | Sridhar + Vinay |
| B2 | Cohort weights for any composite — equal across A–E, or weighted by population / strategic importance? | Sridhar + leadership |
| B3 | Cohort definitions — refer to `jbiq_user_cohort_gtm__v1.docx`; if cohorts evolve, who owns re-baselining of this framework? | Sridhar + GTM |
| B4 | "Translated vs native" rating — calibration across native speakers per language; agreement threshold? | Research + Quality |
| B5 | Persona-fit survey — minimum sample size per cohort for statistical validity? | Research |
| B6 | FGD / diary cadence — quarterly across all 5 cohorts feasible? | Research |
| B7 | NPS verbatim NLP classification — feeds Section 2 themes; instrumentation needed | Vinay |
| B8 | Code-mix authenticity instrumentation per language pair | Anmol (Voice) |

---

## References

**Source docs:**
- `jbiq_user_cohort_gtm__v1.docx` (April 29, 2026) — **canonical cohort definitions A through E**, 491M subscribers
- `Bharat Concept Note.docx` (April 2026) — Soul, 6 Character traits, 4 Indian Pillars (the philosophy basis)
- `JBIQ Product Mesh.docx` — "Bharat-first UX" listed as one of 5 Key Bets
- `~/Desktop/claudespace/CLAUDE.md` — brand voice standard
- `jbiq-domain-persona-matrix.md` — anchor persona definitions (Arjun, Priya, Ramesh, Sunita, Raju) — illustrative archetypes, not the cohort taxonomy

**Companion:**
- `~/Desktop/claudespace/metrics/Product metrics/metrics-tree.md` — main metrics tree (always-on, this framework inherits from it)
- `~/Desktop/claudespace/metrics/Product metrics/product-context.md` — product metrics context / synthesis
- `~/Desktop/claudespace/metrics/Product metrics/non-product-metrics.md` — parallel tracks (Growth · Data · A/B · Unit Economics · Customer Lifecycle · etc.)
