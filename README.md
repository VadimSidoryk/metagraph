# Metagraph

A personal knowledge and task graph for AI-assisted work. Stores context, tasks, processes, and decisions in structured markdown files that any AI agent (Claude, Cursor, Windsurf, etc.) can read, write, and navigate.

---

## What is this?

Metagraph is a file-based knowledge system where:

- **Context nodes** hold facts about goals, people, decisions, and domain knowledge.
- **Tasks** are work items that move through a lifecycle (`todo → in-progress → done`).
- **Processes** are repeatable protocols that can be scheduled and run autonomously by agents.
- **Templates** are reusable output blueprints for messages, tickets, and documents.
- **Everything is linked** via wikilinks (`[[ID]]`) so tools like Obsidian can visualize the graph.

Agents follow the rules in [`CLAUDE.md`](CLAUDE.md) (also mirrored as [`.cursorrules`](.cursorrules) and [`.windsurfrules`](.windsurfrules)) and commit every change to git.

---

## How it works day-to-day

The graph runs a **two-stage daily pipeline** that keeps your task list and knowledge base up to date with minimal manual effort:

1. **18:00 — Capture** ([P1003](processes/P1003.md)): an agent scans your email and Slack, extracts only actionable items or new knowledge, and appends them to [`scratch.md`](scratch.md) (one line per item, with Google Calendar context).
2. **08:00 — Triage** ([P1004](processes/P1004.md)): an agent reads `scratch.md`, classifies each entry using [`triage-rules.md`](triage-rules.md), and proposes graph nodes (tasks or knowledge). You confirm or edit — takes 3–5 minutes.

On top of that:
- **Weekly Monday** — [P1002](processes/P1002.md) reviews goal progress and flags anything at risk.
- **Weekly Sunday** — [P1005](processes/P1005.md) runs a graph integrity check (broken links, orphaned nodes, stale entries).
- **End of quarter** — [P1007](processes/P1007.md) handles OKR lifecycle: close expired goals, open next quarter's goals.

You can also **add quick notes to `scratch.md` at any time** (on the go, by voice, by text) — the triage process will pick them up next morning.

For a more detailed human-oriented guide, see [`MENTAL_MODEL.md`](MENTAL_MODEL.md).

---

## Folder Structure

```
metagraph/
├── CLAUDE.md               ← full rules for all AI agents
├── MENTAL_MODEL.md         ← human guide: how to think about the system
├── .cursorrules            ← same rules, Cursor format
├── .windsurfrules          ← same rules, Windsurf format
├── INDEX.md                ← ID registry and counters
├── scratch.md              ← capture buffer for quick notes & filtered messages
├── triage-rules.md         ← auto-classification rules for P1004 triage
│
├── context/                ← knowledge nodes (C-series IDs)
│   ├── goal/               ← OKR-style goals (quarterly / half-year / annual)
│   ├── personal/           ← people and personal reflections (PRIVATE)
│   ├── decision/           ← decision logs per domain
│   └── knowledge/          ← reference knowledge with external sources
│
├── tasks/                  ← task tickets (T-series IDs)
│   ├── todo/
│   ├── in-progress/
│   ├── done/
│   └── ongoing/
│
├── processes/              ← process protocols (P-series IDs)
│
├── templates/              ← reusable output blueprints (no IDs)
│   ├── message/
│   ├── jira/
│   ├── task/
│   └── process/
│
└── archived/               ← soft-deleted nodes (original IDs preserved)
    ├── context/
    ├── tasks/
    └── processes/
```

---

## Entity Types

### Context Nodes (`C`-series)

Stored in `context/`. Each node is an atomic unit of knowledge.

| Subtype | Purpose | Key fields |
|---|---|---|
| `goal` | OKR-style goal with planning horizon | `horizon`, `task_refs`, Key Results table |
| `personal` | Person description or personal reflection | `variant: about\|reflection`, Interaction Rules, Private Notes |
| `decision` | Decision log for a domain (health, career…) | `domain`, decision table |
| `knowledge` | Reference knowledge from an external source | `source_type`, `source_ref`, `updated_at` |

**Goal nodes** are the most connected — they link to tasks, processes, decisions, and knowledge. Process [[P1002]] periodically evaluates their progress.

**Personal nodes** are intentionally sparse (1–2 links). They define interaction rules for working with a person and are read by any task or process involving that person. Their entire content is **private** — never output outside the graph.

**Knowledge nodes** are actively enriched: agents ask clarifying questions and fetch additional context to maximize the richness of `## Content`.

### Tasks (`T`-series)

Stored in `tasks/<status>/`. The folder is the status — agents move the file to reflect state changes.

```
todo/ → in-progress/ → done/
                     → ongoing/   (recurring, never moves to done)
```

Key frontmatter fields: `priority`, `deadline`, `creator`, `assignee`, `context_refs`.

Tasks document every graph change in `## Graph Changes` and every external side effect in `## External Changes`.

### Processes (`P`-series)

Stored in `processes/`. A process is a protocol that can be run by any agent on a schedule.

Each process file contains: purpose, step-by-step protocol, scheduled triggers, execution history, and improvement recommendations accumulated over time.

**Active processes:**

| ID | Name | Schedule |
|---|---|---|
| [P1001](processes/P1001.md) | Sync Remote Knowledge Nodes | Daily at 09:00 |
| [P1002](processes/P1002.md) | Goal Progress Review | Weekly on Monday |
| [P1003](processes/P1003.md) | Email & Slack Filter — Daily Scratch Writer | Daily at 18:00 |
| [P1004](processes/P1004.md) | Scratch Triage — Daily Graph Writer | Daily at 08:00 |
| [P1005](processes/P1005.md) | Graph Integrity Check | Weekly on Sunday at 20:00 |
| [P1007](processes/P1007.md) | OKR Lifecycle — Horizon Graduation | Last week of each quarter |

### Templates

Stored in `templates/`. Reusable output blueprints with `{{variable}}` placeholders. Used by processes and tasks to produce messages, Jira tickets, documents, etc. Templates have no IDs and are never archived.

---

## ID System

Every entity gets a unique ID at creation that never changes.

| Type | Prefix | Example |
|---|---|---|
| Context node | `C` | `C1001` |
| Task | `T` | `T1001` |
| Process | `P` | `P1001` |

Current counters and all registered entities are tracked in [`INDEX.md`](INDEX.md). Agents must update `INDEX.md` before creating any new file.

---

## Links

All relationships use **wikilinks**: `[[C1001]]` or `[[C1001|label]]`.

This makes the graph navigable in Obsidian, Foam, and similar tools — open the folder as a vault and get a visual knowledge graph automatically.

Links appear in:
- `## Related` sections in every node
- Frontmatter lists: `context_refs: ["[[C1001]]"]`, `task_refs: ["[[T1002]]"]`
- Table cells: decision log `Linked IDs` column
- Inline prose: *"this task implements [[C1001|the Q2 growth goal]]"*

---

## Tag Taxonomy

All entities use tags from a controlled vocabulary defined in [`CLAUDE.md`](CLAUDE.md) (section 13). Tags are grouped into dimensions:

| Dimension | Examples | Purpose |
|---|---|---|
| **domain** | `work`, `health`, `finance`, `learning`, `personal` | Area of life/work |
| **horizon** | `this-week`, `this-quarter`, `this-year`, `someday`, `recurring` | Time scale |
| **type-hint** | `reference`, `insight`, `research`, `decision-context` | Kind of knowledge (knowledge nodes only) |
| **source** | `from-email`, `from-slack`, `from-scratch`, `from-meeting` | Origin (knowledge & triage-created items) |

Rules: max 3 tags per entity, one per dimension. No invented tags — update the taxonomy first.

---

## Archiving

Nothing is ever hard-deleted. To archive an entity:

1. Agent asks the user for reason (context node) or feedback (task / process).
2. File moves to `archived/<type>/` with original filename.
3. An `## Archive Record` section is appended to the file.
4. `INDEX.md` is updated.

---

## Git Conventions

Every agent action that modifies the graph is a separate commit.

**Commit format:**
```
<type>(<ID>): <short reason>
```

| Type | When |
|---|---|
| `create` | New node or process created |
| `update` | Existing node updated |
| `archive` | Node moved to archived/ |
| `sync` | Automated process sync run |
| `task` | Task status change |
| `process` | Process protocol updated |

**Examples:**
```
create(C1001): add Q2 2026 growth goal
update(T1003): mark in-progress, assigned to agent
sync(P1001): daily remote knowledge sync — 3 nodes updated
archive(C1002): user requested — outdated project
```

---

## Using with AI Agents

### Claude Code

[`CLAUDE.md`](CLAUDE.md) is loaded automatically. Claude Code will follow all rules when working in this directory.

### Cursor

[`.cursorrules`](.cursorrules) is loaded automatically by Cursor.

### Windsurf / Cascade

[`.windsurfrules`](.windsurfrules) is loaded automatically by Windsurf.

### Obsidian

Open this folder as an Obsidian vault. All `[[wikilinks]]` resolve automatically and the Graph View shows the full node structure.

### Scheduling processes

To schedule a process (e.g. P1003 daily email filter), use your agent's scheduling tool with this prompt:

> *"Run process P1003 from the metagraph at `<path to this folder>`"*

---

## Frontmatter Reference

**All entities:**
```yaml
id, type, title, summary, created, modified, status, assignee, tags
```

`summary` — 1–2 sentences auto-generated by the agent at creation; allows scanning many nodes without reading full bodies.

**Tasks additionally:**
```yaml
priority: low | medium | high | critical
deadline: YYYY-MM-DD | null
creator: human | process:<P-ID> | task:<T-ID>
context_refs: ["[[C1001]]"]
```

**Goal nodes additionally:**
```yaml
horizon: Q2-2026 | H1-2026 | 2026
task_refs: ["[[T1001]]"]
```

**Knowledge nodes additionally:**
```yaml
source_type: file | google_doc | jira | figma | notion | url | other
source_ref: <path or URL>
updated_at: YYYY-MM-DD
```

**Personal nodes additionally:**
```yaml
variant: about | reflection
```

**Decision nodes additionally:**
```yaml
domain: health | career | finance | product | technical | other
```
