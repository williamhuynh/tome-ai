---
name: setup
description: Set up ToME data directory and configure the current project to use it. Run once per machine or project. Creates the mental model, journal directory, and adds a CLAUDE.md reference.
---

# ToME Setup

First-time setup for ToME on this machine or project. Creates the data directory and configures the agent to use it.

Safe to re-run — all steps are idempotent.

## Process

### 1. Determine ToME Data Location

Ask the user where they want ToME data stored. Common options:

- `~/tome/` — recommended for personal use (shared across all projects)
- `./.tome/` — project-local (one mental model per project)

If the user has an existing ToME git repo, ask for the clone URL instead.

### 2. Create or Clone Data Directory

**If cloning from a repo:**

```bash
git clone <repo-url> <tome-dir>
```

**If creating fresh**, create the directory structure:

```bash
mkdir -p <tome-dir>/journal
touch <tome-dir>/journal/.gitkeep
```

Then create `<tome-dir>/mental-model.md` from this template:

```markdown
# Mental Model

*Last Updated: YYYY-MM-DD*

---

## Current Goals

### Immediate (This Week)
*To be populated through observation*

### Short-term (This Month)
*To be populated through observation*

### Long-term (This Quarter)
*To be populated through observation*

---

## Values & Priorities

*To be populated through observation.*

---

## Communication Preferences

*To be populated through observation.*

---

## Knowledge State

### Expert
### Proficient
### Learning

---

## Behavioral Patterns

*To be populated through observation.*

---

## Recent Learning Events

*Top 5-10 events, rotated.*

---

## Active Hypotheses

*Testable predictions to validate across sessions.*
```

And `<tome-dir>/.gitignore`:

```gitignore
journal/*
!journal/.gitkeep
```

### 3. Initialize Git (if fresh)

If the data directory is not already a git repo:

```bash
cd <tome-dir>
git init
git add -A
git commit -m "tome: initial setup"
```

Optionally ask the user if they want to connect a remote:

```bash
git remote add origin <remote-url>
git push -u origin main
```

### 4. Configure This Project

Add a ToME section to the project's `CLAUDE.md` (or create one if it doesn't exist):

```markdown
## ToME

ToME data is at `<tome-dir>`.
Always run `/tome:init-tome` at the start of every session.
```

### 5. Verify

Confirm:
- `<tome-dir>/mental-model.md` exists
- `<tome-dir>/journal/` directory exists
- CLAUDE.md has ToME reference

Report the setup result to the user.
