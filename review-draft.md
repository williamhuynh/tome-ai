# ToME Review Draft — 2026-04-17 (Weekly)

*Coverage: 2026-04-10 → 2026-04-17 (8 days)*
*Triggered by: scheduled weekly review*
*Status: DRAFT — pending Will's approval before applying to mental-model.md*

---

## Data Sufficiency

- 8 journal entries in the past week (daily coverage)
- Mental model last updated today (2026-04-17 nightly observe) — H18/H25/H20 promotion, H28/H29 added
- Proceeding because weekly cadence + user-scheduled task

Most Tier 1 signals from this week have already been applied by nightly observe runs. This review focuses on **what's still pending**, **stale hypotheses**, **goal evolution**, and **calibration**.

---

## 1. Hypothesis Housekeeping

### Candidates for Promotion

**H27 — Thinking-partner mode signalled with explicit phrases**
- Current confidence: 75% | Tracked since 2026-04-16
- Evidence now: 4+ instances across 2 sessions (AiD rate positioning 2026-04-16, entire SkyMeet arc 2026-04-17)
- **Proposal**: Promote to Behavioral Patterns at 80% confidence. Belief wording:
  > *Will signals thinking-partner mode with phrases like "Help me think through it", "I wonder…", "I'm not sure whether…", "What's the difference?". When triggered, present options with tradeoffs and honest recommendation — don't execute the first reasonable interpretation. Mode applies to strategic positioning AND architecture tasks; executable tasks (send this draft, book this meeting) still bypass this mode.*
- One concern: all confirming signals are within-session architectural/positioning work. Could hold one more cycle if we want cross-domain evidence (e.g., client/email drafting triggering it without architecture).

### Candidates for Retirement / Staleness Review

**H7 — LinkedIn data/evidence posts outperform**
- Last evidence: 2026-04-06 (Gen Z labor post). No LinkedIn post observed this week.
- **Proposal**: Mark as stale-but-valid. Keep, but flag "awaiting next LinkedIn post cycle for revalidation."

**H13, H14, H15, H16 — LinkedIn voice micropatterns**
- No published posts this week → no new data on any of them.
- **Proposal**: Cluster-flag as "dormant — revalidate when LinkedIn cadence resumes." Confidence levels unchanged.

**H17 — Upstream alignment over custom fork**
- Last evidence: 2026-04-04 (OneCLI decision). 13 days without data.
- **Proposal**: Keep at 70%. Add explicit "next validation: SkyMeet dependency choices."

**H19 — Notifications through existing channels**
- Last evidence: 2026-04-05 (worker containers). 12 days without data.
- **Proposal**: Keep at 70%. Flag for SkyMeet observation — meeting notifications are an obvious future test case.

**H24 — Routes implementation to Claude Code, not Sky**
- Last evidence: 2026-04-08. Since then, Will has engaged Sky directly for all architecture (SkyMeet 2026-04-17 was entirely with Sky).
- **Proposal**: Weaken to 40% or split. The pattern may be narrower than originally framed: Will routes to Claude Code only for existing-codebase refactors, not for new-system architecture. Consider rephrasing:
  > *H24 (revised): Will routes localised code changes within existing systems (container, nanoclaw infra) to Claude Code; he keeps new system design / greenfield architecture with Sky.*
- My recommendation: rephrase rather than retire — one more test cycle.

### Hypotheses Carrying Forward

- **H8** (exploration-before-implementation) — reconfirmed this week (SkyMeet 7-round arc, Westpac). Consider nudging 75% → 80%.
- **H10** (opportunity framing) — no new posts; keep at 90%.
- **H11** (recursive polish preferred) — Dave/Nine email iteration 2026-04-13 reconfirms. Nudge 85% → 88%.
- **H21** (adaptive schemas over rigid templates) — no new data, keep 70%.
- **H22** (security-conscious) — SharePoint question 2026-04-15 (2nd signal) + SkyMeet "nanoclaw vs app layer" question 2026-04-17 (3rd signal). **Proposal**: Nudge 75% → 80%.
- **H26** (AiD data routing to aid-coo) — mixed signal 2026-04-16 (client emails yes, in-flight internal task no). Keep at 65%. Scope is "new AiD tasks," not "migrate in-flight."
- **H28** (reference tool as UX benchmark) — 1 strong signal; wait for 2nd. Keep 65%.
- **H29** (no speculative abstraction layers) — 1 explicit cut, pairs with Scope Exploration Pattern. Keep 70%.

---

## 2. New Patterns to Capture (Not Yet in Mental Model)

### 2a. Rapid-Fire Iterative Refinement on Concrete Tasks
- **Evidence**: 5-6 cost rate adjustments in ~10 min (2026-04-14); ~12 rounds on rate positioning email (2026-04-16)
- **Distinction**: When tasks are concrete/numerical, Will does NOT enter exploration mode — he iterates fast and expects Sky to keep state between corrections without re-explanation.
- **Proposal**: Add as sub-pattern under Mode Patterns:
  > *When task is concrete/numerical (not exploratory), Will iterates rapidly with terse corrections and expects Sky to maintain full state. Do not re-explain the task between iterations; acknowledge the change and produce the updated output.*

### 2b. Positioning as Deliberate Signal (Financial/Naming)
- **Evidence**: 2026-04-16 rate emails — "I want to position us to be much more deep in expertise… injecting positioning in the rates" + "we are the AI team" (rejecting ML Engineer substitution)
- **Proposal**: Add to Values or Behavioral Patterns at 75%:
  > *Will treats pricing, titles, and framing as deliberate positioning artefacts — not neutral labels. When a choice could signal capability tier, identity, or differentiation, treat it as strategic not administrative.*

### 2c. Meta-Awareness of Agent Learning Compliance (H30 — new)
- **Evidence**: 2026-04-15 — Will asked aid-coo explicitly if it had updated its understanding re: em-dash feedback.
- **Proposal**: Add H30 at 55% confidence:
  > *H30: Will periodically checks whether agents have internalised his corrections, not just whether the output reflects them. Implication: ToME/wiki updates should surface visibly when asked, and rules should be explicit in agent CLAUDE.md/wiki rather than implicit.*

### 2d. Cost/Precedent Rationalisation (H31 — new)
- **Evidence**: 2026-04-17 — Will accepted Deepgram cloud after being reminded Granola already uses AssemblyAI cloud. Precedent-based rather than principle-based reasoning.
- **Proposal**: Add H31 at 55% confidence:
  > *H31: When evaluating privacy/sovereignty tradeoffs, Will weighs consistency with existing tool exposure over abstract principle. Implication: when proposing cloud dependencies, name the analogous existing dependency to anchor the decision.*

---

## 3. Goal Evolution

### New Short-Term Goal — SkyMeet (Windows Electron meeting co-pilot)
- Confidence: 85%
- Sidecar pattern, Deepgram Nova-3 streaming, MC Meetings module + naa-project specialist integration
- Explicit Granola replacement intent: "I will replace granola if this works well."
- Three build todos captured (MC Meetings module, naa-project in-meeting mode, Windows Electron app)
- **Proposal**: Add to Short-term goals. Retire "Granola → OneDrive → Sky pipeline" goal — SkyMeet supersedes it.

### Evolved / Superseded
- **Granola → agent workflow** (currently 85%) → **SUPERSEDED by SkyMeet**. Keep a note of the evolution in journal; remove from current goals.

### Goal Status Check Needed
- **Consistent LinkedIn presence (5x/week)** — No observed posts this week across journal entries. Unclear whether cadence is paused, automated-silent, or just not surfacing in Sky's observation channel. **Flag for Will**: is LinkedIn schedule still active?

### Goal Reconfirmed
- Daily AI news digest — running.
- AI-native todo system — running; 8 consecutive days heavy usage; PWA launched 2026-04-16.
- Personal KM → client deliverable — Westpac connection active 2026-04-13.

---

## 4. Calibration Check

- P1 (MC dog-fooding continues) — **Confirmed**. 7 consecutive days.
- P2 (todo-system delegation over ad-hoc) — **Confirmed**. Multiple instances.
- H25/H18/H20 promotion predictions — all validated.
- P3 (thinking-partner signal phrases) — **Confirmed** 2026-04-16 + 2026-04-17.

**Observation**: Promotions this week held to the "3+ signals across 2+ sessions" bar. Calibration looks right. Continue the discipline.

**Under-represented domain**: LinkedIn voice work. Most LinkedIn-voice beliefs and hypotheses have no fresh validation this month. If LinkedIn cadence has paused, flag these as dormant rather than ageing passively.

---

## 5. Proposed Mental Model Edits Summary

| # | Change | Section | Action |
|---|--------|---------|--------|
| 1 | Promote H27 → belief at 80% | Behavioral Patterns | Add "Thinking-Partner Mode Invocation" |
| 2 | Retire H27 from Active Hypotheses | Active Hypotheses | Mark promoted |
| 3 | Add "Rapid-Fire Iterative Refinement" | Mode Patterns | New sub-pattern |
| 4 | Add "Positioning as Deliberate Signal" | Values or Behavioral | New pattern at 75% |
| 5 | Add H30 (agent learning compliance check) | Active Hypotheses | 55% |
| 6 | Add H31 (cost/precedent rationalisation) | Active Hypotheses | 55% |
| 7 | Nudge H8 75% → 80% | Active Hypotheses | Confidence update |
| 8 | Nudge H11 85% → 88% | Active Hypotheses | Confidence update |
| 9 | Nudge H22 75% → 80% | Active Hypotheses | Confidence update (3rd signal) |
| 10 | Revise H24 wording (refactors vs greenfield) | Active Hypotheses | Rephrase, 40% |
| 11 | Flag H7/H13/H14/H15/H16 as dormant | Active Hypotheses | Status annotation |
| 12 | Add SkyMeet as short-term goal (85%) | Current Goals | New entry |
| 13 | Retire Granola → OneDrive goal (superseded) | Current Goals | Remove |
| 14 | Rotate out oldest learning event if >10 | Recent Learning Events | Trim if needed |

---

## 6. Questions for Will Before Applying

1. **LinkedIn cadence**: Is the 5x/week Mon–Fri schedule still active? No posts observed in journal coverage for 2 weeks. Should the goal stay, pause, or evolve?
2. **H27 promotion timing**: Promote thinking-partner mode now (80%), or hold one more cycle for cross-domain signal (e.g., email drafting triggering it)?
3. **H24 retention**: Retire or rephrase "Will routes implementation to Claude Code"? My recommendation: rephrase.
4. **Positioning as Deliberate Signal**: Add as Value or Behavioral Pattern? (Leans value — it's about *what matters*, not just *what he does*.)

---

## Next Review
Scheduled: 2026-04-24 (weekly cadence) unless user-triggered earlier.
