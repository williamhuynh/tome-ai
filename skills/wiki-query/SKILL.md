---
name: wiki-query
description: Query the project wiki or global wiki to answer a question. Reads the index, loads relevant pages, and synthesizes an answer. Use when asked about clients, past decisions, findings, or any knowledge captured in the wiki.
---

# Wiki Query

Answer questions using knowledge captured in the wiki. More reliable than memory — always check the wiki for project-specific facts.

## When to Use

- Questions about a client, stakeholder, or project context
- Questions about past decisions made during an engagement
- Questions about findings or recommendations from prior work
- "What do we know about X?", "What was decided on Y?", "Has this come up before?"
- Preparing for a meeting: "What's the context on this client?"

## Which Wiki to Query

**Project wiki** (`wiki/` in the current group folder):
- Client-specific information, meeting notes, decisions, findings for this engagement

**Global wiki** (Sky's folder at `groups/main/wiki/`, accessible to Sky only):
- Reusable frameworks, patterns, domain knowledge
- Cross-project insights (anonymized)

Query the project wiki first. If the question is about methodology or general domain knowledge, also check the global wiki.

## Query Workflow

### Step 1: Read the index
Read `wiki/index.md` (and `groups/main/wiki/index.md` for global queries).

Scan the index to identify which pages are likely relevant to the question.

### Step 2: Load relevant pages
Load only the pages that seem relevant — typically 1–5 pages. Avoid loading the entire wiki unless necessary.

Prioritise:
- Direct matches (e.g., question about "Acme Corp" → load `entities/acme-corp.md`)
- Temporal relevance (e.g., "latest decision on X" → load `decisions.md`)
- Cross-reference (e.g., question references a meeting → load that meeting page)

### Step 3: Synthesize
Compose an answer from the loaded pages. Be specific — cite the source page and date where possible.

Example:
> "According to the kickoff meeting notes (2026-04-05), the client's main concern is regulatory compliance under the EU AI Act. The CTO (see `entities/jane-smith-cto.md`) has final sign-off authority on the engagement scope."

### Step 4: Flag gaps
If the wiki doesn't contain enough information to answer the question:
- Say so clearly
- Suggest running `/wiki-ingest` if there's relevant content that hasn't been captured yet

### Step 5: Optional synthesis save
If the answer synthesizes across multiple pages and will likely be needed again, offer to save it:
> "Want me to save this synthesis as a finding page for future reference?"

If yes, create `findings/synthesis-{topic}.md` with the synthesized content.

---

## Cross-Wiki Query (Sky only)

When Sky queries across projects (e.g., "have we seen this client type before?"):

1. Read the global wiki index: `groups/main/wiki/index.md`
2. Scan project wikis: `groups/*/wiki/index.md` (Sky has read access to all project folders)
3. Load relevant pages from whichever wikis contain relevant content
4. Synthesize across sources — but note: project wiki content is client-confidential. When synthesizing for the user, only surface patterns, not client-identifying details unless in the specific project context.

---

## Edge Cases

**No wiki exists yet:**
Inform the user the wiki hasn't been set up for this project yet, and offer to run `/wiki-ingest` on some initial content to create it.

**Question is about something recent that hasn't been ingested:**
Check conversation history if the answer is available there. Suggest running `/wiki-ingest` to capture it for next time.

**Contradictory information across pages:**
Surface both versions with dates. The more recent entry in `decisions.md` supersedes earlier ones. For entity/finding pages, the page content itself should be the current state.
