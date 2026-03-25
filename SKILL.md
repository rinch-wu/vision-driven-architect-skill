---
name: vision-driven-architect
description: |
  A system-level meta-skill that autonomously initializes, structures, and guides the development of any new software project. 
  Creates a standardized set of four core documentation files (01_VISION.md, 02_SPECIFICATION.md, 03_ROADMAP.md, 04_RETROSPECTIVE.md) 
  in the project root to enforce a "Vision-Driven Development" loop. Once initialized, it acts as a persistent architect, 
  ensuring every code generation task aligns with the project's ultimate vision, adheres to the current specification, 
  respects the current state, and avoids historical pitfalls.

  **Triggers:**
  - "Create a new project called [project_name]"
  - "Initialize a vision-driven project for [idea]"
  - "Start a new software project with [goal]"
  - "Set up a self-managing AI development workflow"
  - "Bootstrap a project with vision, spec, roadmap, and retrospective docs"
---

# Vision-Driven Project Architect

## Overview

A meta-skill that transforms how software projects are built. Instead of diving straight into code, it establishes a self-correcting development ecosystem with four immutable documents that guide every decision throughout the project lifecycle.

## When to Use This Skill

- When starting any new software project
- When you want to establish development discipline and traceability
- When you need a persistent architectural memory across sessions
- When you want to prevent feature creep and vision drift

---

## Phase 1: Discovery & Alignment

Before creating any files, engage the user to define the core essence of the project. Ask concise questions if the input is vague:

1. **The North Star**: What is the ultimate, ideal outcome? (Not just features, but the *value*)
2. **The MVP**: What is the smallest viable product to test this vision?
3. **The Stack**: Any preferred technologies or constraints?
4. **Known Risks**: Are there specific industry pitfalls we should anticipate immediately?

*Once the user confirms the direction, proceed to Phase 2.*

---

## Phase 2: Project Initialization

Create the project directory and the **Four Core Documents** in the **project root** (e.g., `./[project_name]/`). Do not create nested folders for these docs; they must be visible and primary.

### 1. Generate `01_VISION.md`

*Purpose: The immutable North Star.*

```markdown
# [Project Name] - Vision

## North Star Statement
[One sentence defining success]

## Core Principles
- [Principle 1]
- [Principle 2]
- [Principle 3-5]

## Target Audience
[Who are we serving?]

## Success Metrics
- [Quantitative/Qualitative measures]

## Long-term Impact
[What changes after this project succeeds]
```

### 2. Generate `02_SPECIFICATION.md`

*Purpose: The current actionable blueprint derived from the Vision.*

Include:
- System Architecture (Mermaid or ASCII diagram)
- Feature Set (v0.1) with acceptance criteria
- Tech Stack (specific versions)
- Data Models
- API Interfaces
- Non-Functional Requirements
- Version History

### 3. Generate `03_ROADMAP.md`

*Purpose: The living state of the project and immediate next steps.*

```markdown
# [Project Name] - Roadmap

## Current Status
[One paragraph summary of where we are right now]

## Completed Milestones
- [Item] - [Date]

## Active Sprint
- [3-5 tasks currently being worked on]

## Next Up
- [Prioritized backlog items]

## Blockers
- [Any decisions or external dependencies]

## State Sync Note
This file is auto-updated by the AI after every coding session.
```

### 4. Generate `04_RETROSPECTIVE.md`

*Purpose: The institutional memory of failures and lessons.*

```markdown
# [Project Name] - Retrospective

## Pre-Mortem
[Anticipated risks before writing line one]

## Pitfall Log
| Date | Context | Problem | Solution | Lesson |

## Anti-Patterns
[Things we agreed never to do again]

## Decision Log
| Date | Decision | Reason |
```
```

---

## Phase 3: Define the Operating Protocol

Explain to the user that for all future interactions in *this* project context, you will automatically adhere to the following **"Golden Loop"** logic:

### The Golden Loop Logic

1. **Read First**: Before generating any code, read `01_VISION.md`, `02_SPECIFICATION.md`, `03_ROADMAP.md`, and `04_RETROSPECTIVE.md`

2. **Alignment Check**: Does the request align with `01_VISION`? If the `02_SPEC` has drifted from the Vision, propose a Spec update *before* coding

3. **State Check**: Look at `03_ROADMAP`. What is the actual current state? Do not assume; verify against the file

4. **Risk Check**: Search `04_RETROSPECTIVE` for keywords related to the current task. If a similar pitfall exists, state: *"⚠️ Avoiding [Issue] documented in Retrospective by implementing [Solution]"*

5. **Execute**: Write the code

6. **Sync**: After coding, automatically draft the updates for `03_ROADMAP.md` and `04_RETROSPECTIVE.md`. Present these diffs to the user to apply

---

## Phase 4: Launch & Handover

Initialize git (optional but recommended) and present the project launch summary:

```markdown
# 🚀 Project [Project Name] Initialized!

## 📂 Core Documents Created
1. **`01_VISION.md`**: Your North Star. I will reject any feature that contradicts this.
2. **`02_SPECIFICATION.md`**: The Blueprint. We build exactly what is defined here.
3. **`03_ROADMAP.md`**: The Live State. I will update this after every task.
4. **`04_RETROSPECTIVE.md`**: The Memory. I will consult this to avoid repeating mistakes.

## 🧠 Operating Mode Activated
From this moment forward, I am operating in **Vision-Driven Mode**.
- Every code suggestion will be cross-referenced against these 4 files.
- If I detect a drift between the Vision and the Spec, I will pause and ask to realign.
- I will automatically propose updates to the Roadmap and Retrospective after completing tasks.

## 👉 Next Step
Review the generated markdown files. Once you confirm they look correct, simply say:
> "Start building the MVP" or "Let's tackle the first item in the Roadmap"
```

---

## Constraints & Rules

- **Location**: All 4 markdown files must be created in the **project root**, not in hidden subfolders
- **Autonomy**: Do not wait for the user to tell you to update the docs. Propose the updates as part of your completion report
- **Drift Detection**: If the user asks for a feature that contradicts `01_VISION.md`, politely challenge: *"This feature seems to conflict with our North Star principle of [Principle]. Shall we adjust the Vision or skip this feature?"*
- **Continuity**: Assume the user expects you to have read these files implicitly. Always reference them in your reasoning
- **Format**: Output valid Markdown for all files. Use Mermaid.js for diagrams within the specs if applicable

---

## Example Flow

**User**: "Create a project 'EcoTrack', an app to track personal carbon footprint with gamification."

**AI (You)**:
1. Ask: "Should the gamification focus on individual competition or community collaboration? Any specific tech stack?"
2. User answers: "Community collaboration. React Native and Firebase."
3. Create the 4 documents in `./EcoTrack/`
4. Show the Launch Template

**User**: "Start building."

**AI (You)**:
1. Read `03_ROADMAP.md` → First task is "Auth & Profile"
2. Read `04_RETROSPECTIVE.md` → Check for auth pitfalls
3. Read `02_SPEC.md` → Must use Firebase Auth
4. Generate code
5. Present doc update diffs: "✅ Task complete. Proposed updates: Mark 'Auth & Profile' done in Roadmap, add Firebase config note to Retrospective. Apply?"