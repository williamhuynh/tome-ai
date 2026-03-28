# ToME-AI

**Theory of Mind Expanded for AI** — a structured mental model system that helps AI assistants understand and predict a specific user's preferences, communication style, decision patterns, and values.

## Philosophy

Understanding a user isn't about guessing. ToME treats it as a falsifiable, testable body of knowledge:

- **Captures learning events systematically** from real interactions
- **Tracks confidence levels** on every belief, distinguishing conviction from speculation
- **Tests predictions methodically** via explicit hypotheses with validation criteria
- **Evolves through evidence** — beliefs are promoted when confirmed, retired when stale

## Structure

```
tome/
├── mental-model.md    # The living mental model
├── journal/           # Session observation logs
│   ├── 2026-03-09.md
│   ├── 2026-03-13.md
│   └── ...
└── review-draft.md    # Weekly automated review
```

### Mental Model

The core file, organized into:

| Section | Purpose |
|---------|---------|
| **Current Goals** | Immediate, short-term, and long-term goals with confidence ratings |
| **Professional Context** | Role, company, audience, communication addresses |
| **Values & Priorities** | Ranked beliefs with supporting evidence and implications |
| **Communication Preferences** | Style rules, voice guidelines, correction history |
| **Knowledge State** | Three-tier assessment: expert, proficient, learning |
| **Behavioral Patterns** | Observable decision-making and interaction patterns |
| **Recent Learning Events** | Top observations with dates and confidence levels |
| **Active Hypotheses** | Testable predictions with validation strategies |

### Journal

Date-stamped session logs that capture:

- **Corrections** — what went wrong, what the user said, what was learned
- **Approvals** — what worked, with strength of approval language noted
- **Mode Transitions** — when the user shifts between exploration, summary, and implementation
- **Patterns** — meta-level observations about how the user works
- **Predictions** — new hypotheses or confidence updates on existing ones

### Weekly Review

Automated review that surfaces:

- Unapplied recommendations from previous reviews
- Stale hypotheses (no new signals in 2+ weeks)
- Prediction windows nearing expiry
- Confidence calibration checks
- Journal gaps

## How Agents Use ToME

1. **Pre-interaction calibration** — check the model before proposing ideas or approaches
2. **Communication adaptation** — shape outputs to match values and style preferences
3. **Timing decisions** — know when the user is exploring vs. ready to implement
4. **Fact-checking discipline** — soften unverified claims when the user is known to verify
5. **Approval disambiguation** — check session context rather than assuming recency

## Integration

ToME is designed to be mounted into AI agent containers as a read-write volume. Agents observe interactions and update the model through structured skills (observe, adapt, review).

## License

Private repository. All contents are personal mental model data.
