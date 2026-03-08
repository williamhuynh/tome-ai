# ToME — Theory of Mind Expanded for AI

Portable mental model system. Tracks user preferences, communication style, behavioral patterns, and goals across AI environments.

## Data

- Mental model: `mental-model.md`
- Journal: `journal/` (daily observation entries)

## Skills

Five skills implement the ToME protocol:

| Skill | When |
|-------|------|
| `/init-tome` | Start of every session — loads mental model, activates ToME behavior |
| `/tome-observe` | After significant exchanges — captures learning signals to journal |
| `/tome-adapt` | Before complex responses — consults mental model to adapt style |
| `/tome-review` | Weekly/monthly — extracts patterns, validates predictions, prunes stale beliefs |
| `/tome-sync` | Pull from GitHub at session start; push after observations or at session end |

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

### Cowork (Mounted Folder Setup)

ToME data is mounted at: `/sessions/trusting-wonderful-darwin/mnt/tome`  
Git PAT stored at: `/sessions/trusting-wonderful-darwin/mnt/tome/.git-pat`  
Git working dir (ephemeral): `/tmp/tome-ai`

**Start of every Cowork session:**
1. Run `/tome-sync` (pull mode) — clones repo to /tmp, merges remote changes, syncs to mounted folder
2. Run `/init-tome` — loads mental model and today's journal, activates ToME behavior

**During session:**
- `/tome-adapt` before complex responses
- `/tome-observe` after significant exchanges (also syncs changes to mounted folder)

**End of session / periodically:**
- Run `/tome-sync` (push mode) — commits and pushes changes to GitHub

### NanoClaw

Set `TOME_DIR` in `.env` (defaults to `~/tome`). The container runner mounts it and syncs skills automatically.
