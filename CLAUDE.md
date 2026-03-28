# ToME — Theory of Mind Expanded for AI

Portable mental model system. Tracks user preferences, communication style, behavioral patterns, and goals across AI environments.

## Data

- Mental model: `mental-model.md`
- Journal: `journal/` (daily observation entries)

## Skills

Four skills in `skills/` implement the ToME protocol:

| Skill | When |
|-------|------|
| `/init-tome` | Start of every session — loads mental model, activates ToME behavior |
| `/tome-observe` | After significant exchanges — captures learning signals to journal |
| `/tome-adapt` | Before complex responses — consults mental model to adapt style |
| `/tome-review` | Weekly/monthly — extracts patterns, validates predictions, prunes stale beliefs |

## Environment Setup

Each environment needs two things:

1. **Skills installed** — Copy or symlink `skills/*` into the environment's skill directory
2. **CLAUDE.md reference** — Tell the agent where ToME data lives

### Claude Code / Cowork

Add to your project's `CLAUDE.md` or `~/.claude/CLAUDE.md`:

```markdown
## ToME

ToME data is at ~/tome/.
Always run `/init-tome` at the start of every session.
```

Install skills:

```bash
cp -r ~/tome/skills/* ~/.claude/skills/
# Or for a specific project:
cp -r ~/tome/skills/* .claude/skills/
```

### NanoClaw

Set `TOME_DIR` in `.env` (defaults to `~/tome`). The container runner mounts it and syncs skills automatically.
