# ARCHITECTURE.md — Technical Architecture

> Notion reference: [Chapter 2 — The Product Brief](https://www.notion.so/31d26a420611813499bfe07c988c97ac)

This document defines the technical architecture of your product. It is the reference your AI builder uses when making structural decisions. Keep it current — when the architecture changes, update this first.

---

## Architecture overview

<!-- Describe the system at a high level.
What are the main components? How do they connect?
A diagram description or ASCII sketch is useful here. -->

```
(sketch your architecture here)

e.g.
User → Frontend → API layer → AI layer
                            → Database
                            → External services
```

---

## Components

### Frontend
**Framework:**
**Hosting:**
**Key responsibilities:**
**Notes:**

### Backend / API
**Framework:**
**Hosting:**
**Key responsibilities:**
**Notes:**

### Database
**Technology:**
**Hosting:**
**Schema location:**
**Notes:**

### AI layer
**Model(s) used:**
**Prompt management:**
**Context strategy:**
**Fallback behaviour:**

### Auth
**Provider:**
**Session management:**
**Notes:**

### External integrations
<!-- List any third-party services the product depends on -->

| Service | Purpose | Critical path? |
|---|---|---|
| | | |

---

## Data flow

<!-- Walk through how data moves through the system for the core use case.
Step by step. -->

1.
2.
3.
4.

---

## Infrastructure

**Environments:**
<!-- e.g. local, staging, production -->

**CI/CD:**


**Secrets management:**


**Monitoring:**


---

## Scalability considerations

<!-- What will break first when the product grows?
Note the bottlenecks and the plan to address them (when relevant). -->

-
-

---

## Security considerations

<!-- What are the key security risks?
How are they mitigated? -->

-
-

---

## Technical debt log

<!-- What shortcuts were taken in the prototype that need to be addressed?
Keep this honest and updated. -->

| Item | Impact | Priority | Owner |
|---|---|---|---|
| | | | |
