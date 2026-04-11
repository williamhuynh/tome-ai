# ToME Review Draft
*Generated: 2026-04-10 | Covering: 2026-04-06 to 2026-04-10 | Mode: Draft (not applied)*

---

## Data Sufficiency

- New journal entries since last update: **5** (Apr 5, 6, 7, 8, 10)
- Last mental model update: 2026-04-08
- Proceeding: Yes — rich signal week

---

## Summary

Strong signal week. Multiple corrections, explicit approvals, and architectural clarifications. Key themes: LinkedIn voice solidifying (em-dashes, attribution, framing), Sky vs. Claude Code workflow clarification, and several hypotheses ready to graduate. 14 proposed changes across promotions, boosts, retirements, and additions.

---

## Proposed Changes

### 1. PROMOTE: H10 → Stated Belief (Opportunity Framing)

**Current state**: H10 at 90% in Active Hypotheses. Flagged as "strong candidate for promotion — 1 more signal needed."

**Evidence this week**: April 6 — Will explicitly rejected "opportunistic" angle and requested "opportunity of getting AI right, especially by changing workflows and processes." This is the **4th independent confirming signal**.

**Proposed action**:
- Retire H10 from Active Hypotheses
- Merge into Communication Preferences (LinkedIn Voice) — upgrade existing "Framing: Opportunity/adaptation default" entry to 95% and add this as the clinching evidence

---

### 2. RETIRE: H16 (No Hashtags) — Already a Stated Belief

**Current state**: H16 at 70%, listed in Active Hypotheses. But it's already in Communication Preferences as "No hashtags (Confidence: 90%)".

**This week**: 515 startups post published April 6 — no hashtags confirmed.

**Proposed action**: Remove H16 from Active Hypotheses. Boost Communication Preferences entry to 95% (2+ posts confirmed).

---

### 3. RETIRE: H23 (No Em-Dashes) — Already a Stated Belief

**Current state**: H23 at 75% in Active Hypotheses. Already stated in Communication Preferences as "No em-dashes (Confidence: 85%)."

**Proposed action**: Remove H23 from Active Hypotheses. No confidence change needed — 85% appropriate for 1 explicit data point.

---

### 4. RETIRE: H8 — Stale; Absorbed into Existing Pattern

**Current state**: H8 at 70%, flagged as stale since early March. No new evidence this week.

**Status**: >4 weeks since last signal. Substance already captured in "Exploration → Summary/Confirmation → Implementation" Mode Pattern.

**Proposed action**: Retire H8. Add a single line to the existing mode pattern:
> Note: architectural/systemic topics tend to require more exploration rounds before Will signals implementation readiness.

---

### 5. BOOST: H20 (Proactive System Hygiene) → 80%

**Current state**: H20 at 75%, 2 signals from same day (Apr 5). Flagged "need cross-session confirmation."

**This week**: April 6 — Will independently identified that the LinkedIn agent needs its own domain knowledge wiki before it was flagged as a gap ("LinkedIn agent should have its own knowledge wiki and skills, similar to the other project agents"). This is a **3rd signal across 2 different days**.

**Proposed action**: Boost H20 confidence to 80%. Update evidence note.

---

### 6. BOOST: H24 (Claude Code as Implementation Layer) → 70%

**Current state**: H24 at 60%, 1 data point (Apr 8).

**This week (retroactive)**: April 6 session also confirmed: "I'll pass it to claude code who has access to host" — Will used Sky for architecture/instructions and Claude Code for execution on the host machine. This is a **2nd signal across 2 days**.

**Proposed action**: Boost H24 to 70%. Add new behavioral pattern:

> **Sky as Orchestrator, Claude Code as Implementor** (NEW — 2 sessions confirmed):
> Will uses Sky for planning, architecture, orchestration, and cross-agent coordination. System-level / host-level implementation gets routed to Claude Code.
> Implication: Don't assume Sky has host access. When designing system changes, deliver clear instructions Will can hand to Claude Code. Don't volunteer to "just do it" on host-side tasks.

---

### 7. ADD: LinkedIn Schedule Timezone Fix

**Issue**: Mental model still references "7am AEDT" for LinkedIn schedule. DST ended April 5 — Sydney is now AEST (UTC+10) until October.

**Proposed action**: Update LinkedIn goal to:
> 5x/week (Mon–Fri, 7am AEST / UTC+10). Note: review cron timezone offset each April and October when Sydney DST transitions.

---

### 8. ADD: Melbourne Trip (Short-term Goal)

**Evidence**: April 10 brain dump — "Book flights to Melbourne." No dates or context yet.

**Proposed action**: Add minor note to Short-term Goals:
> **Melbourne trip** (Confidence: 60% — single brain dump, no dates yet): Flights not yet booked as of 2026-04-10.

---

### 9. ROTATE: Recent Learning Events

**Add (in chronological order)**:

1. **2026-04-06: Em-dash and Attribution Corrections** — Will manually changed em-dashes to hyphens in final post ("makes it less like it'd AI written"); also explicitly corrected attributed framing ("researchers call this X") to assertive articulation ("own the argument"). Two linguistic signals in one session.

2. **2026-04-06: Sky's Role Explicitly Defined** — Will stated: "Sky is the general purpose agent and orchestrator. Sky is the main agent that has elevated access and can orchestrate between all agents." Also: global wiki scope is cross-cutting for ALL agents, not consulting-only.

**Rotate out** (currently 12 events — at limit; archive oldest to keep top 8–10):
- Archive candidate: "2026-03-07: Premature Implementation Correction" — fully absorbed into Mode Patterns
- Archive candidate: "2026-03-07: Response Length Correction" — fully absorbed into Communication Preferences

---

### 10. HOUSEKEEPING: Active Hypotheses Duplicates

**Issue**: H10, H16, H23 are all already stated as beliefs in the mental model but still appear in Active Hypotheses. This creates redundancy and cognitive load.

**Action**: After promotions above, Active Hypotheses should have: H7, H11, H13, H14, H15, H17, H18, H19, H20, H21, H22, H24.

---

## Hypotheses Status Table (Post-Review)

| ID  | Current | Proposed | Reason |
|-----|---------|----------|--------|
| H7  | 80% Testing | No change | Insufficient new data |
| H8  | 70% Stale | ❌ Retire | >4 weeks stale; absorbed into Mode Patterns |
| H10 | 90% Testing | ✅ Promote → 95% belief | 4th confirming signal |
| H11 | 85% Testing | No change | — |
| H13 | 80% Testing | No change | — |
| H14 | 65% Testing | No change | — |
| H15 | 70% Testing | No change | — |
| H16 | 70% Testing | ❌ Retire | Already stated belief; 2nd confirmation |
| H17 | 70% Testing | No change | — |
| H18 | 85% Testing | No change | 3 signals but only 2 contexts — keep testing |
| H19 | 70% Testing | No change | — |
| H20 | 75% Testing | 🔼 80% | 3rd signal, cross-session confirmed |
| H21 | 70% Testing | No change | — |
| H22 | 70% Testing | No change | — |
| H23 | 75% Testing | ❌ Retire | Already stated belief |
| H24 | 60% Testing | 🔼 70% | 2nd signal, add behavioral pattern |

---

## Gaps Still to Explore

- **Granola pipeline**: Still blocked since March. No new signal this week. May be deprioritised — worth asking Will at next opportunity.
- **Mission Control chat bidirectionality**: Will requested chat-style todo feedback (April 6) — no follow-up signal yet.
- **H7 (data-backed posts)**: Only 2 signals. Needs more post comparisons to validate properly.
- **H22 (security consciousness)**: Only 1 data point. Watch next credential discussion.
- **Gim Defense Health**: New name from April 10 brain dump. Unknown entity — may be a client or prospect. Route to aid-coo if Will mentions it again.

---

## Next Review

Scheduled: 2026-04-17
Watch for: H10 in use as promoted belief, H24 (more Claude Code routing evidence), Melbourne trip logistics, any Mission Control chat feature emerging.

---

*Draft only — no changes applied to mental-model.md. Awaiting Will's review.*
