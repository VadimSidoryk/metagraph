# Metagraph Index

## ID Counters

| Series  | Prefix | Last assigned | Next to use |
|---------|--------|---------------|-------------|
| Context | C      | 1000          | C1001       |
| Task    | T      | 1000          | T1001       |
| Process | P      | 1002          | P1003       |

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
| P1001 | Sync Remote Knowledge Nodes   | active | daily at 09:00   | processes/P1001.md |
| P1002 | Goal Progress Review          | active | weekly on Monday | processes/P1002.md |

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
