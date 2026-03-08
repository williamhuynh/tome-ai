---
name: tome-sync
description: Sync ToME data with GitHub. Use at session start to pull latest, and at session end (or periodically) to push changes. Handles the git operations needed to keep ToME up to date across sessions.
---

# ToME Sync — Cowork Git Bridge

Handles pulling from and pushing to the GitHub `tome-ai` repo. Because the mounted Windows folder doesn't support git file locking, git operations run from `/tmp` and files are synced to/from the mounted folder.

## Paths

- **Mounted folder** (persistent, survives sessions): `/sessions/trusting-wonderful-darwin/mnt/tome`
- **Git working dir** (ephemeral, VM-local): `/tmp/tome-ai`
- **PAT file**: `/sessions/trusting-wonderful-darwin/mnt/tome/.git-pat`
- **Repo**: `https://github.com/williamhuynh/tome-ai.git`

## When to Invoke

- **Pull** (`mode: pull`) — at the start of a session, before loading the mental model
- **Push** (`mode: push`) — after significant ToME observations, at end of session, or when asked to sync

## Process

### Pull Mode (session start)

Run these bash steps:

```bash
# 1. Read PAT
PAT=$(cat /sessions/trusting-wonderful-darwin/mnt/tome/.git-pat)
REMOTE="https://williamhuynh:${PAT}@github.com/williamhuynh/tome-ai.git"

# 2. Clone if not already present this session
if [ ! -d /tmp/tome-ai/.git ]; then
  git clone "$REMOTE" /tmp/tome-ai
else
  echo "Repo already cloned this session"
fi

# 3. Copy any locally modified data files from mounted folder into git working dir
# (local changes take priority over remote for data files)
rsync -av --exclude='.git-pat' --exclude='.git-credentials' --exclude='*.skill' \
  /sessions/trusting-wonderful-darwin/mnt/tome/ /tmp/tome-ai/

# 4. Pull latest from GitHub (merges remote changes)
cd /tmp/tome-ai && git config user.email "will@theoc.ai" && git config user.name "Will Huynh"
cd /tmp/tome-ai && git pull origin main 2>&1

# 5. Sync back to mounted folder so it has latest
rsync -av --exclude='.git' /tmp/tome-ai/ /sessions/trusting-wonderful-darwin/mnt/tome/
```

If there are merge conflicts, the local (mounted folder) version wins for data files (journal, mental-model.md).

### Push Mode (after observations / end of session)

```bash
# 1. Read PAT
PAT=$(cat /sessions/trusting-wonderful-darwin/mnt/tome/.git-pat)
REMOTE="https://williamhuynh:${PAT}@github.com/williamhuynh/tome-ai.git"

# 2. Sync latest from mounted folder to git working dir
rsync -av --exclude='.git-pat' --exclude='.git-credentials' --exclude='*.skill' \
  /sessions/trusting-wonderful-darwin/mnt/tome/ /tmp/tome-ai/

# 3. Stage, commit, push
cd /tmp/tome-ai
git config user.email "will@theoc.ai"
git config user.name "Will Huynh"
git remote set-url origin "$REMOTE"
git add journal/ mental-model.md
git status
git diff --cached --stat

# Only commit if there are changes
if git diff --cached --quiet; then
  echo "No changes to push"
else
  DATE=$(date +%Y-%m-%d)
  git commit -m "ToME update: ${DATE} [Cowork]"
  git push origin main
  echo "Pushed to GitHub"
fi

# 4. Sync back to mounted folder
rsync -av --exclude='.git' /tmp/tome-ai/ /sessions/trusting-wonderful-darwin/mnt/tome/
```

## Output

After pull: confirm "ToME synced from GitHub — ready."
After push: confirm "ToME pushed to GitHub — [N] changes committed." or "Nothing to push."
