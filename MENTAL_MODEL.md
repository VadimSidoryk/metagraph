# How to work with metagraph — a human guide

> This is not rules for agents. This is an explanation for you — how to think about the system and when to use it.

---

## What the system does for you

Every day, automatically:
- **18:00** — an agent reads your email and Slack, extracts only what matters, writes to `scratch.md` (1 line per item)
- **08:00** — an agent reads `scratch.md` and suggests creating tasks or notes. You say yes/no — takes 3–5 minutes

Every week (Monday):
- The agent checks progress toward your goals and flags anything falling behind

You do manually:
- Add quick notes to `scratch.md` at any time (on the go, by voice, by text)
- Confirm or edit the agent's suggestions during morning triage
- Create goals (once per quarter)

---

## When to create what

Simple rule: **when in doubt — write to scratch. The agent will sort it out.**

If you want to create something explicitly:

| What's happening | What to create |
|---|---|
| Something concrete needs to be done | **Task (T-series)** → tell the agent "create task: ..." |
| Learned an important fact, need reference info | **Knowledge node (C-series)** → "add knowledge: ..." |
| Made a decision and want to log it | **Decision node (C-series)** → "log decision: ..." |
| Have a quarterly / half-year goal | **Goal node (C-series)** → "create goal: ..." |
| Note about a person (how to work with them) | **Personal node (C-series)** → "add profile: ..." |

---

## What a good week looks like

**Morning, 3–5 minutes** (daily):
> The agent shows 3–7 entries from scratch. You respond: "yes, yes, no, task but deadline Friday, no". The agent creates nodes and clears the processed items.

**On the go** (any time):
> A thought on the way to work → open scratch.md, write one line: `[meeting Anton] make offer by end of week`. Nothing else to think about.

**Monday morning, 5 minutes** (automatic):
> The agent sends a goal signal: "Q2 goal 1 — ✅ on track, Q2 goal 2 — ⚠️ falling behind, here's why". You decide what to do.

**Once a quarter, 30 minutes**:
> You and the agent write the quarter's summary, create goals for the next one. The graph saves everything.

---

## What you do NOT need to remember

- No need to know IDs (C1001, T1003) — the agent assigns them
- No need to know frontmatter — the agent fills it in
- No need to write wikilinks — the agent connects them
- No need to think about git — the agent commits every change

---

## First steps (get started in 10 minutes)

1. **Tell the agent:** *"Create my first goal for Q2 2026"* — the agent will ask 2–3 questions and create a goal node
2. **Write in scratch.md** any one task or thought that's in your head right now
3. **Tell the agent:** *"Run P1004"* — it will process scratch and suggest creating the first task

That's it. The system works.

---

## When something feels unclear

Just tell the agent something like:
- *"I have a meeting with Anton today and I need to do something about the budget"* → the agent will create a task
- *"I've decided not to take investment this year"* → the agent will log the decision
- *"I want to see what's in my graph right now"* → the agent will show active goals and tasks

**No need to think about structure. Just say what's happening.**
