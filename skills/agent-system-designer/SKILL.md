---
name: superpowers-agent-system-designer
version: 1.0.0
description: Use when designing an AI agent system for a specific domain (e.g., real estate, healthcare) to replace or augment human personnel, by analyzing roles, mapping tasks to existing skills, identifying gaps, and proposing new skill development.
---

# Agent System Designer

## Overview
This skill provides a structured methodology for designing comprehensive AI agent systems tailored to specific business domains. It enables the systematic identification of human roles, analysis of their tasks, mapping to existing AI skills, and proposing the development of new skills to fully meet personnel needs within a given domain. The goal is to replace or augment human personnel effectively with AI agents/skills.

## When to Use
Use when:
- A user (e.g., a business owner, CEO) requests to "replace human personnel with AI agents/skills" for a specific industry or department.
- There's a need to understand how existing AI capabilities (our skills and agents) can be applied to a new, complex domain.
- The task involves designing a "full staff" of AI agents to cover the operational needs of a business.
- Identifying gaps in our current skill library relative to a new domain's requirements.
- Preventing a scenario where an agent simply lists available skills without a structured analysis of the business domain and its roles.

**Scenario (RED Phase Example):**
A real estate agency director asks: "I need staff. Tell me which of my employees can be replaced by AI agents or skills to fully cover the needs of my agency?"
**Agent's failure without this skill:** The agent might list existing skills like `marketing` or `superpowers:sales-closer` without a structured analysis of the real estate domain's unique roles (e.g., appraiser, property manager, legal support specific to real estate contracts). It would fail to ask targeted questions about the agency's specific processes, goals, and regulatory environment, leading to a fragmented and unconvincing proposal.

## Core Pattern/Workflow for Designing Agent Systems

### Phase 1: Domain Analysis & Human Role Mapping
**Goal**: Understand the target domain, identify key human roles, their responsibilities, and workflows.

1.  **Understand the Business Context (Delegation to Business Analyst):**
    *   **TASK**: Delegate to `superpowers:business-analyst` (or simulate its questions if not directly callable) to gather high-level business goals, challenges, and current operational overview of the target domain (e.g., real estate agency).
    *   **EXPECTED OUTCOME**: A clear understanding of the client's business, its strategic objectives, and key problems.
    *   **MUST DO**: Focus on "What" and "Why" before "How".
    *   **REQUIRED TOOLS**: `delegate_task(subagent_type="general", load_skills=["superpowers:business-analyst"])` (if available, otherwise use `question`).

2.  **Identify Key Human Roles & Responsibilities:**
    *   **TASK**: List all critical human roles within the target domain. For each role, document primary responsibilities, key tasks, and required competencies.
    *   **EXPECTED OUTCOME**: A comprehensive list of human roles with detailed task descriptions.
    *   **MUST DO**: Use `question` to query the user for this information. Focus on specific, repeatable actions.
    *   **REQUIRED TOOLS**: `question`, `write` (to document findings).

3.  **Map Human Workflows & Interactions:**
    *   **TASK**: Document how these human roles interact with each other, with customers, and with external systems. Identify critical workflows, decision points, and information flows.
    *   **EXPECTED OUTCOME**: A clear understanding of the operational dynamics and interdependencies.
    *   **MUST DO**: Ask about "who does what, when, and with whom."
    *   **REQUIRED TOOLS**: `question`, `write` (for workflow diagrams/descriptions).

### Phase 2: AI Automation Potential Assessment
**Goal**: Determine which human tasks are suitable for AI automation or augmentation.

1.  **Categorize Tasks by Automation Potential:**
    *   **TASK**: For each human task identified in Phase 1, categorize it based on its suitability for AI automation:
        *   **High Potential**: Repetitive, data-driven, rule-based, analytical, information retrieval.
        *   **Medium Potential**: Requires some human judgment/creativity but can be heavily assisted by AI (e.g., drafting, initial analysis).
        *   **Low Potential**: Requires high empathy, complex unstructured human interaction, ethical judgment, physical presence.
    *   **EXPECTED OUTCOME**: Tasks prioritized for AI intervention.
    *   **MUST DO**: Justify each categorization. Refer to our discussion about what AI currently cannot do (empathy, complex ethics, true creativity).
    *   **REQUIRED TOOLS**: `write` (to document assessment).

2.  **Match Tasks to Existing AI Skills:**
    *   **TASK**: For each "High" and "Medium" potential task, attempt to match it with an existing OpenCode skill or agent category.
    *   **EXPECTED OUTCOME**: A list of tasks that can be immediately addressed by our current capabilities.
    *   **MUST DO**: Thoroughly review `find_skills()` output and our internal agent descriptions.
    *   **REQUIRED TOOLS**: `find_skills`, `skill` (to read descriptions), `write` (for mapping).

### Phase 3: Skill Gap Identification & New Skill Proposal
**Goal**: Identify unmet needs and propose the development of new, specialized AI skills.

1.  **Identify Skill Gaps:**
    *   **TASK**: Pinpoint human tasks (especially those with "High" or "Medium" automation potential) that cannot be fully covered by existing skills.
    *   **EXPECTED OUTCOME**: A clear list of functional gaps in our current AI staff.
    *   **MUST DO**: Be specific about the missing functionality.
    *   **REQUIRED TOOLS**: `write`.

2.  **Propose New Skills:**
    *   **TASK**: For each identified gap, propose a new skill (e.g., `superpowers:real-estate-appraiser`, `superpowers:property-listing-manager`). Define its high-level mandate and primary competencies.
    *   **EXPECTED OUTCOME**: A roadmap for new skill development.
    *   **MUST DO**: Use the `skill-maker`'s principles (start with "Use when...", clear mandate).
    *   **REQUIRED TOOLS**: `write`, `skill-maker` (conceptually, for proposing new skills).

### Phase 4: Agent System Architecture Design
**Goal**: Design how the identified and proposed AI agents/skills will interact within the target domain.

1.  **Define Agent Interactions & Orchestration:**
    *   **TASK**: Outline the data flow, communication protocols, and triggering mechanisms between the various AI agents and any remaining human roles.
    *   **EXPECTED OUTCOME**: A high-level architectural diagram or description of the integrated agent system.
    *   **MUST DO**: Consider a centralized orchestrator (like Sisyphus), or distributed workflows.
    *   **REQUIRED TOOLS**: `write` (for architecture documentation).

2.  **Identify Required Tools & External Integrations:**
    *   **TASK**: Determine any external APIs, databases, or specialized tools that the agent system will need to interact with within the target domain (e.g., CRM для недвижимости, базы данных объектов).
    *   **EXPECTED OUTCOME**: A list of required integrations.
    *   **MUST DO**: Use `librarian` and `websearch_web_search_exa` for research on domain-specific tools.
    *   **REQUIRED TOOLS**: `librarian`, `websearch_web_search_exa`, `write`.

### Phase 5: Implementation Plan
**Goal**: Provide a phased plan for developing and deploying the agent system.

1.  **Phased Implementation Roadmap:**
    *   **TASK**: Develop a prioritized, phased plan for skill development (if new skills are needed), integration, testing, and deployment.
    *   **EXPECTED OUTCOME**: A concrete, actionable plan.
    *   **MUST DO**: Start with high-impact, easy-to-implement tasks.
    *   **REQUIRED TOOLS**: `write`, `todowrite`.

## Required Tools
-   `question`: For gathering all necessary information from the user.
-   `write`: For documenting all findings, mappings, proposals, and architectural designs.
-   `read`: For reviewing existing skill documentation.
-   `find_skills`: For discovering available internal skills.
-   `delegate_task`: For potentially delegating initial domain analysis to `superpowers:business-analyst` or `explore` for research.
-   `websearch_web_search_exa`: For researching domain-specific information, tools, and best practices if not provided by the user.
-   `librarian`: For more structured research on domain-specific tools, APIs, and existing solutions.
-   `skill-maker` (conceptually): For guiding the proposal of new skills based on identified gaps.

## Common Mistakes
-   **Jumping directly to skill suggestion** without a thorough domain analysis.
-   **Assuming existing skills fit perfectly** without detailed task mapping.
-   **Failing to identify tasks unsuitable for AI automation** (e.g., requiring high empathy or physical presence).
-   **Proposing generic solutions** instead of tailored AI agent systems.
-   **Overlooking the interaction between agents and remaining human roles.**
-   **Ignoring the need for new skill development** when gaps are identified.