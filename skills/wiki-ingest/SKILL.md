---
name: wiki-ingest
description: Ingest new content (meeting notes, emails, docs, any text) into a project wiki. Extracts entities, decisions, findings, and actions. Updates up to 10 pages per run.
---

# Wiki Ingest

Process source content and update the project wiki. Follows the schema rules defined in `wiki/SCHEMA.md`.

## When to Use

- User pastes meeting notes, client documents, emails, or any content to be captured
- Trigger phrases: "ingest this", "add this to the wiki", "capture these notes", "update the wiki with this"
- Also at project session start: "sync the wiki with what happened"

## Prerequisites

The project wiki must exist at `wiki/` in the current group folder with:
- `wiki/SCHEMA.md` — defines page types and rules
- `wiki/index.md` — catalog of all pages (may be empty initially)
- `wiki/log.md` — operation log (may be empty initially)

If the wiki doesn't exist yet, create it first by running the initialization steps at the bottom of this skill.

## Ingest Workflow

### Step 1: Load context
Read `wiki/SCHEMA.md` and `wiki/index.md` to understand:
- What page types exist for this project
- What pages already exist (to decide update vs. create)

### Step 2: Parse the source content
Extract the following from the input:
- **Entities**: People, organisations, systems mentioned (create/update entity pages)
- **Decisions**: Any decisions made — what was decided, by whom, rationale (append to `decisions.md`)
- **Findings**: Observations, analysis, insights (create/update finding pages)
- **Actions**: Action items (note the owner and due date; these go in the relevant meeting or finding page, not a separate actions page)
- **Meeting details**: Date, attendees, agenda topics, key discussion points (if the source is meeting notes)

### Step 3: Determine page operations (max 10 total)
For each extracted item, decide:
- **Update existing page**: if a matching page is listed in `index.md`
- **Create new page**: if no matching page exists

Prioritise:
1. Meeting page (if source is meeting notes — always create one)
2. New entities (if not yet captured)
3. Updated entities (new information about known entities)
4. Decisions (always append, never overwrite)
5. Findings (if significant insight worth preserving)

If more than 10 page operations are needed, prioritise by importance and note the overflow in `log.md` for follow-up.

### Step 4: Write pages
Apply the page rules from SCHEMA.md:
- **meeting pages**: immutable once written, named `meetings/YYYY-MM-DD-{topic}.md`
- **entity pages**: evolving, update in place
- **finding pages**: evolving, update in place; mark `#promote` in log if reusable beyond this engagement
- **decisions.md**: append-only, never edit previous entries

Page header format (include at top of every page):
```
---
type: {meeting|entity|finding|decision-log}
last-updated: YYYY-MM-DD
source: {brief description of source, e.g. "kickoff call notes", "client brief PDF"}
---
```

### Step 5: Update index.md
For each new page created, add a line:
```
- [Page Title](relative/path/to/page.md) — one-line summary — last updated YYYY-MM-DD
```

For updated pages, update the "last updated" date on the index line.

### Step 6: Append to log.md
Log every ingest operation:
```
[YYYY-MM-DD HH:MM] ingest: {source description} ({delivery method: paste|file|email}) → created {n} pages, updated {n} pages: {list of pages}
```

If any findings were tagged for promotion:
```
[YYYY-MM-DD HH:MM] #promote: {finding page path} — {one-line reason}
```

### Step 7: Confirm to user
Brief confirmation: what was ingested, which pages were created or updated.

---

## Initialising a New Wiki

If no wiki exists for this project yet:

```bash
mkdir -p wiki/meetings wiki/entities wiki/findings
```

Create `wiki/SCHEMA.md` using the standard template:

```markdown
# Wiki Schema — [Project Name]

## Page Types
- **meeting**: one page per meeting, named {YYYY-MM-DD}-{topic}.md, immutable after creation
- **entity**: one page per significant person/org/system, named by entity, evolving
- **finding**: observations and analysis, evolving; tag with #promote in log.md if reusable
- **decision**: append-only; all decisions for this engagement in decisions.md

## Ingest Rules
When content arrives (any format — notes, email, doc, file):
1. Read SCHEMA.md and index.md
2. Extract: entities mentioned, decisions made, findings, action items
3. Create or update relevant pages (max 10 per ingest)
4. Create a meeting page if source is meeting notes
5. Append to log.md: [YYYY-MM-DD HH:MM] ingest: {source} ({delivery}) → {pages changed}
6. Update index.md if new pages created
7. Tag #promote in log.md for any reusable insight

## index.md format
One line per page:
- [page title](path) — one-line summary — last updated YYYY-MM-DD

## Confidentiality
All content is client-confidential. Never write client-specific detail to global wiki without anonymization.
```

Create `wiki/index.md`:
```markdown
# Wiki Index — [Project Name]

*No pages yet.*
```

Create `wiki/log.md`:
```markdown
# Wiki Log — [Project Name]
```

---

## Edge Cases

**Source is just a few bullet points (not formal notes):**
Still ingest — create a brief meeting page or append to an existing finding. Less content just means fewer pages updated.

**Same entity appears across many meetings:**
Update the existing entity page each time. Don't create duplicates.

**Decision conflicts with earlier decision:**
Append the new decision with a note: "Supersedes decision from YYYY-MM-DD." Never edit the earlier entry.

**Source is an email thread:**
Extract the key decisions and any new context. Create a finding page if there's substantive insight. No need to create a "meeting" page for email threads — only for synchronous meetings.

**Unclear whether something is a finding or a decision:**
Decision = something was agreed/committed to. Finding = observation or analysis. When in doubt, use finding.
