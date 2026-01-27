---
name: superpowers-robust-skill-invocation
version: 1.0.0
description: Use when attempting to access a skill that was previously reported as "not found" or when direct invocation of a skill fails, to ensure reliable discovery and access to skill documentation.
---

# Robust Skill Invocation

## Overview
This skill provides a robust, multi-step workflow for reliably discovering and accessing other skills, especially when initial direct invocation attempts fail. It minimizes user frustration and ensures that even if a skill cannot be directly executed, its documentation can still be retrieved.

## When to Use
Use when:
- An initial attempt to call a skill (e.g., via `skill()` or `slashcommand()`) results in a "Command/skill not found" error, despite a belief that the skill exists.
- There's ambiguity about the exact name or path of a skill.
- The goal is to provide the user with information about a skill, even if its executable command cannot be triggered.
- Preventing a scenario like the "Sales Closer" incident, where multiple attempts to access a known skill failed.

## Core Pattern/Workflow for Robust Skill Discovery and Invocation

1.  **Initial Attempt (Direct Invocation):**
    *   **TASK**: Attempt to invoke the skill directly using `slashcommand(command='/skill-name')` or `skill(name='skill-name')` if the skill is known to be directly executable.
    *   **Goal**: Achieve the most direct and efficient access to the skill.
    *   **MUST DO**: Note the exact command used and any error messages received.

2.  **Verification via `find_skills()`:**
    *   **TASK**: If the initial attempt fails with a "not found" error, use `find_skills()` to get a comprehensive list of all available skills and their respective directories.
    *   **Goal**: Confirm the existence of the skill and retrieve its exact registered name and file path.
    *   **MUST DO**: Parse the output of `find_skills()` to locate the target skill. Note the `Directory` field.

3.  **Path Refinement and `SKILL.md` Identification:**
    *   **TASK**: From the `Directory` field obtained in Step 2, construct the full path to the `SKILL.md` file (e.g., `/Users/aleksejulanov/.config/opencode/superpowers/skills/skill-name/SKILL.md`).
    *   **Goal**: Identify the precise location of the skill's documentation file.
    *   **MUST DO**: Account for potential discrepancies between `skill-name` (as listed by `find_skills()`) and the actual directory name (e.g., `superpowers:sales-closer` might be in a `sales-closer` directory). The `find_skills()` output directly provides the `Directory`.

4.  **Documentation Retrieval (`read`):**
    *   **TASK**: Use the `read` tool with the constructed `SKILL.md` path to retrieve the skill's documentation content.
    *   **Goal**: Obtain the full description and workflow of the skill, even if it cannot be directly invoked.
    *   **MUST DO**: Handle potential `read` errors (e.g., file not found, permission denied).

5.  **Information Presentation & Problem Reporting:**
    *   **TASK**: Present the retrieved skill documentation to the user. If the skill could not be directly invoked but its documentation was found, inform the user about the discrepancy and suggest that the `skill-maker` agent investigate the registration issue.
    *   **Goal**: Fully answer the user's request for skill information and provide actionable feedback for system improvement.
    *   **MUST DO**: Clearly state if the skill is executable or if only its documentation is available.

## Required Tools
-   `slashcommand`: For attempting direct skill invocation.
-   `skill`: For attempting direct skill invocation (alternative to `slashcommand`).
-   `find_skills`: Essential for robust discovery of available skills and their paths.
-   `read`: For retrieving the `SKILL.md` documentation.
-   `bash` (mkdir): For initial setup if creating a new skill.
-   `write`: For creating new `SKILL.md` files or updating existing ones.
-   `todowrite`: For managing the skill creation/update process.

## Common Mistakes
-   **Assuming a skill's directory name perfectly matches its registered name** (e.g., `superpowers:sales-closer` might be in a `sales-closer` folder). `find_skills()` provides the exact directory.
-   **Giving up after a single "not found" error** from `slashcommand` or `skill`.
-   **Failing to use `find_skills()`** as the authoritative source for skill existence and location.
-   **Not reporting discrepancies** between skill existence (via `find_skills()`) and invokability (via `slashcommand`/`skill`). This hinders system improvement.