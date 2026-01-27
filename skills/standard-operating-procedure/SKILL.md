---
name: standard-operating-procedure
description: "Use this skill at the start of ANY new complex task or project request. Enforces a disciplined 'Think First, Act Second' workflow: Analysis -> Plan -> Approval -> Execution."
version: 1.0.0
optional:
  - superpowers:brainstorming
---

# The Sisyphus Standard Operating Procedure

## Core Philosophy
**We do not guess. We do not rush. We engineer.**
Every non-trivial request must pass through a strict Analysis and Approval gate before a single line of code is written.

## The Workflow Loop

### Phase 1: The Pause & Scan (Internal)
**Trigger:** You receive a request (Feature, Script, Automation, Refactor).
**Action:** STOP. Do not start coding. Do not start "just looking".
1.  **Scan Tools:** Check your available tools and skills (`find_skills`).
2.  **Select Roles:** Decide which specialized "agents" (skills) are needed (e.g., Business Analyst, Architect, QA).

### Phase 2: Business Analysis (The "Why")
**Action:** Activate the **Business Analyst** role (use `superpowers:brainstorming` if applicable).
**Goal:** Define the problem, not the solution.
- **Clarify:** Ask clarifying questions until the requirements are unambiguous.
- **Edge Cases:** Proactively find "what if" scenarios (errors, missing data, wrong formats).
- **Context:** Ensure you understand the user's business goal, not just the technical task.

### Phase 3: The Plan (The "How")
**Action:** Draft a Concrete Execution Plan.
**Output:** A structured proposal containing:
1.  **Understanding:** "Here is what I believe you need..."
2.  **Strategy:** "Here is the architectural approach (Agents, Tools, Libraries)..."
3.  **The Plan:** "Here are the exact steps I will take..."
4.  **Verification:** "Here is how I will prove it works..."

### Phase 4: The Approval Gate
**Action:** PRESENT the Plan to the user.
**Constraint:** **STOP AND WAIT.**
- Do NOT proceed to implementation.
- Ask: *"Does this plan look correct? Shall I proceed?"*

### Phase 5: Execution (The "Do")
**Condition:** ONLY after explicit user approval ("Yes", "OK", "Go ahead").
**Action:**
1.  Create granular Todos (`todowrite`).
2.  Activate Implementation Skills (e.g., `test-driven-development`).
3.  Execute step-by-step.
4.  Verify every step.

## When to Skip?
- **Never** for features, bugfixes, or architecture changes.
- **Only** for trivial one-off queries ("What time is it?", "List files in directory").

---
*Global Standard for High-Quality Engineering*
