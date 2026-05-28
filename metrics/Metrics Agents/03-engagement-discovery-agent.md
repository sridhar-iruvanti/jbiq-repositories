# Agent 03 — Engagement & Discovery
**L1 Groups:** Engagement · Expansion · Experience (G) · Sentiment + Advocacy
**Org Goals:** G03 (returning user 80% task completion) · G05 (80%+ satisfaction, no domain below 70%)

---

## L0 Connection
Active Habit Rate = DEU ÷ MEU.
This agent moves the numerator — DEU growth, depth per DEU, and breadth across domains.
A user who comes back daily but does one thing once is not deeply engaged. This agent measures depth and breadth, not just frequency.

---

## DEC Connection
North Star: DEC = DAU × Conversations per User per Day.
**Conversations per User per Day is this agent's domain.**
More SEs discovered = more conversation types = higher sessions/user/day.

---

## Metrics This Agent Owns

### Engagement
| Metric | Definition |
|---|---|
| MEU growth rate MoM | Monthly growth in Monthly Engaged Users |
| DEU growth rate MoM | Monthly growth in Daily Engaged Users |
| Tasks per DEU/day | Depth signal — how much is each daily user doing |
| Sessions per DEU/day | Year 1 target: 2 sessions/user/day |
| Active days/week per MEU | Frequency within the month |
| Multi-task session rate | % sessions with ≥2 tasks — measures engagement depth |

### Expansion
| Metric | Definition |
|---|---|
| Experience discovery rate | % users who engage ≥2 SEs in week 1 |
| Vertical breadth | Average number of domains per user per month |
| Cross-domain engagement rate | % sessions touching ≥2 domains |

### Experience (G) — Per SE
| Metric | Definition |
|---|---|
| Attempt rate | % users who tried the SE |
| Completion rate | % who completed it |
| D1/D7 same-experience return | Unprompted return to same SE |
| D30 Stickiness | Long-term SE-level retention |
| In-context NPS | Satisfaction immediately after SE |
| Signature Qualification Score | 0–3 — only 3/3 qualifies as Signature |

### Sentiment + Advocacy
| Metric | Definition |
|---|---|
| NPS | D7 and D21 surveys |
| User Satisfaction Rate | % satisfied responses overall |
| Share rate | Output shared externally |
| Screenshot proxy | Content saved to device |
| Show-family behaviour | Session started from shared content |

---

## Home Surface — What This Agent Designs

The home screen is the primary mechanism for experience discovery.

**Four zones:**

| Zone | What it does | Metric it moves |
|---|---|---|
| Contextual greeting | Time-of-day aware, JioID-pre-loaded | Engagement start rate |
| Personalised tiles (3–5) | One SE per tile, personalised by cohort + time | Experience discovery rate · Tile tap rate |
| Suggested prompts | Pre-filled queries in user's language | First-query rate |
| Value Ribbon (aspirational) | ₹ saved / time saved cumulative | Return intent |

**Tile performance diagnostic:**
- Tap rate by tile position (positions 1–3 carry 80%+ of taps — hypothesis to validate)
- Cold home rate = % home loads with no personalised tiles (failure state)
- Tile CTR below 25% = personalisation not surfacing correctly → flag to Memory pod

---

## SE Performance Diagnostic Framework

For any SE, the v8 diagnostic is:

| Completion | Same-experience Return | Diagnosis | Action |
|---|---|---|---|
| Low | Low | Bad experience | Fix or kill |
| Low | Decent | Wrong fit or shallow | Reposition |
| High | Low | Good once, not sticky | Deepen the loop |
| High | High | Signature candidate | Qualify and scale |

Apply this to every SE in the active catalog before claiming it's working.

---

## Cohort Expansion Lens

Experience discovery is not uniform across cohorts.

| Cohort | Discovery barrier | Design response |
|---|---|---|
| A/B | None — high app literacy | Richer home, more tiles |
| C | Language — doesn't know what to try | Pre-filled prompts in Hindi/Hinglish |
| D/E | Awareness — doesn't know what's possible | One-tap SEs, visual affordance, no text-heavy discovery |

Expansion metrics must be cut by cohort. A 50%+ discovery rate in Cohort A with 15% in Cohort D is a failure.

---

## Output This Agent Produces

- Engagement depth snapshot: sessions/DEU/day vs DEC Year 1 target (2 sessions/day)
- SE performance table using completion × return diagnostic framework
- Home surface spec: zone-by-zone with tile content rules and personalisation logic
- Discovery gap analysis: which cohorts are not discovering second SE and why
- NPS/satisfaction read: overall + per-domain, flag any domain below 70%
- Advocacy signal read: share rate, screenshot proxy trends
