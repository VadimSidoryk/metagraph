# Metagraph Index

## ID Counters

| Series  | Prefix | Last assigned | Next to use |
|---------|--------|---------------|-------------|
| Context | C      | 1000          | C1001       |
| Task    | T      | 1000          | T1001       |
| Process | P      | 1007          | P1008       |

_Update this table immediately when assigning a new ID — before creating the file._

---

## Context Node Registry

| ID    | Title | Subtype  | Status  | File path                          |
|-------|-------|----------|---------|------------------------------------|
| —     | —     | —        | —       | —                                  |

---

## Task Registry

| ID    | Title | Status      | Priority | Assignee | Creator | File path                     |
|-------|-------|-------------|----------|----------|---------|-------------------------------|
| —     | —     | —           | —        | —        | —       | —                             |

---

## Process Registry

| ID    | Title | Status  | Schedule | File path                          |
|-------|-------|---------|----------|------------------------------------|
| P1001 | Sync Remote Knowledge Nodes         | active | daily at 09:00        | processes/P1001.md |
| P1002 | Goal Progress Review                | active | weekly on Monday      | processes/P1002.md |
| P1003 | Email & Slack Filter — Scratch      | active | daily at 18:00        | processes/P1003.md |
| P1004 | Scratch Triage — Daily Graph Writer | active | daily at 08:00        | processes/P1004.md |
| P1005 | Graph Integrity Check               | active | weekly on Sunday      | processes/P1005.md |
| P1007 | OKR Lifecycle — Horizon Graduation  | active | last week of quarter  | processes/P1007.md |

---

## Archived

| ID    | Original type | Archived date | Reason summary                     |
|-------|---------------|---------------|------------------------------------|
| —     | —             | —             | —                                  |

---

## Context Subtypes

| Subtype   | Folder path            | Description                                              |
|-----------|------------------------|----------------------------------------------------------|
| goal      | context/goal/          | OKR goals with horizon (quarter/half-year/year)          |
| personal    | context/personal/        | People (`about`) or personalal reflections (`reflection`) — entirely PRIVATE |
| decision  | context/decision/      | Decision log tables per domain                           |
| knowledge | context/knowledge/     | Reference knowledge with external source link            |
