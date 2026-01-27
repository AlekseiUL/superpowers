---
name: self-annealing-architecture
description: A mental model and workflow for building resilient, self-improving systems. It enforces a strict separation of concerns between Directives (WHAT), Orchestration (DECISION), and Execution (HOW), and mandates a "Self-Annealing" loop where every error leads to a permanent system improvement.
version: 1.0.0
---

## The 3-Layer Architecture

### Layer 1: Directive (The Instruction Set)
- **Concept:** Natural language SOPs that define goals, inputs, and outputs.
- **Implementation in OpenCode:** `SKILL.md` files.
- **Role:** Tell the Agent *what* to do, not how to write the code.
- **Rule:** Directives must be updated when execution realities change (e.g., API limits, new patterns).

### Layer 2: Orchestration (The Brain)
- **Concept:** Intelligent routing and decision making.
- **Implementation in OpenCode:** You (Sisyphus) + Subagents (`explore`, `librarian`).
- **Role:** Read the Directive, choose the Execution tool, handle errors, retry.
- **Rule:** Never try to "be" the execution layer. Don't simulate a database; call the database tool.

### Layer 3: Execution (The Muscle)
- **Concept:** Deterministic, reliable, testable code/tools.
- **Implementation in OpenCode:** `n8n workflows`, `MCP Tools`, `Bash scripts`.
- **Role:** Do the actual work. No AI "guessing".
- **Rule:** Prefer deterministic tools over LLM generation for logic.

## The Self-Annealing Loop (Crucial)

Errors are not just failures; they are signals that the system is out of sync with reality.

**When an error occurs:**
1.  **Fix it:** Patch the immediate issue (code fix, config change).
2.  **Update the Tool:** Ensure the Execution layer (n8n/script) handles this case natively next time.
3.  **Update the Directive:** Update the `SKILL.md` or instruction to warn about this edge case or prescribe the new path.
4.  **Verify:** Confirm the system is stronger.

**Result:** The system "hardens" (anneals) over time.

## Checklist for New Features

- [ ] **Define Directive**: Do we have a Skill or SOP for this? If not, create one.
- [ ] **Check Execution Tools**: Do we have an n8n workflow or MCP tool for this?
    - [ ] IF NO: Create a deterministic tool (n8n/script). DO NOT rely on raw LLM generation for complex logic.
- [ ] **Orchestrate**: Use the Agent to glue Directive + Tool.
- [ ] **Anneal**: If it breaks, fix the Tool/Skill, not just the output.

## Trigger
Use this skill when:
- Designing a new complex feature.
- Debugging a recurring issue (to apply self-annealing).
- Refactoring a fragile process.
