# Triage Rules — P1004 Auto-Classification

This file defines the rules for automatic classification of entries from `scratch.md`.
Used by process [[P1004]] to split into: auto-create, propose, ask, discard.

Edit this file manually as experience accumulates. Review and refine after each month of use.

---

## Confidence Levels

### 🟢 HIGH — create automatically (no confirmation)

Create node without confirmation if **all** conditions are met:
- Sender is in `context/personal/` (known person)
- Explicit deadline present (`by [date]`, `until Friday`, `asap`)
- Single clear action (one verb: confirm, send, reply, call)
- Entry does not appear to duplicate an existing task in `tasks/todo/`

**What is created:** T-series task, `priority: high`, deadline from text, `creator: process:P1004`

**Examples:**
```
Anton → confirm marketing budget, by Fri              → ✅ auto T-series
CEO → review contract draft, send by EOD              → ✅ auto T-series
```

---

### 🟡 MEDIUM — propose to user (one confirmation)

Propose if:
- Action exists but no deadline — or deadline is vague (`soon`, `sometime`)
- Or sender is unknown (not in personal nodes)
- Or entry could be either a task or knowledge

**What to show:**
```
[entry]
→ Task: "[title]" | priority: medium | deadline: null
   Confirm? (yes / no / edit)
```

**Examples:**
```
Marina → reply re onboarding in #product              → 🟡 propose (no deadline)
Investor X → sent term sheet, needs response          → 🟡 propose (unknown sender)
read article about OKR systems                        → 🟡 propose (task or knowledge?)
```

---

### 🔵 KNOWLEDGE — propose as knowledge node

Propose C-series (knowledge) if:
- No specific action required from you
- Contains a fact, link, insight, or conclusion
- Keywords: `learned`, `article`, `research`, `fact`, `important to know`, `found`

**Examples:**
```
read — competitors launched feature X                 → 🔵 propose C knowledge
new personal data law starting July                   → 🔵 propose C knowledge
```

---

### ⚫ DISCARD — delete without creating a node

Delete automatically (no confirmation) if:
- No verb and no fact — pure noise
- Duplicates an entry from the last 48 hours
- Automated notification (CI/CD, monitoring system, newsletter)
- Entry is older than 14 days and was not processed

**Examples:**
```
ok                                                    → ⚫ discard
remind me later                                       → ⚫ discard (no details)
[newsletter] Weekly digest from ProductHunt           → ⚫ discard
```

---

## Rules for Specific People

Add to this section as personal nodes are created. Example:

```
# Anton (C1002):
# - His requests are always HIGH priority
# - "soon" from him = 2 business days
```

---

## Rules for Channels/Sources

```
# Slack #general → MEDIUM by default (lots of noise)
# Slack #decisions → HIGH by default (everything matters)
# email starred → HIGH by default
# email CC → DISCARD by default unless @mention
```

---

## Changelog

| Date       | What changed   | Why                                         |
|------------|----------------|---------------------------------------------|
| 2026-04-03 | Created v1.0   | Initial rules before first use              |
