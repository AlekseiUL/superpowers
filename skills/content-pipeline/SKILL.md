---
name: content-pipeline
description: This skill orchestrates the handoff between marketing strategy and copywriting execution. It serves as the manager that coordinates the `marketing` and `copywriting` subagents to produce high-quality, strategically aligned content.
version: 1.0.0
---

This skill orchestrates the handoff between marketing strategy and copywriting execution. It serves as the manager that coordinates the `marketing` and `copywriting` subagents to produce high-quality, strategically aligned content.

## 1. Workflow Diagram

The pipeline follows a strict linear flow from business definition to strategy to execution.

```mermaid
graph TD
    A[User Request] --> B[Business Analyst (Definition)]
    B -->|Project Definition| C[Marketing Agent (Strategy)]
    C -->|Strategy Brief| D[Copywriting Agent (Execution)]
    D -->|Final Text| E[Review & Output]
```

**Steps:**
1.  **Input Analysis**: Receive the user's topic or goal.
2.  **Definition Phase**: Dispatch the `business-analyst` subagent to define the product features, scope, and business goals. Output: **Project Definition**.
3.  **Strategy Phase**: Dispatch the `marketing` subagent, providing the **Project Definition** as context, to analyze the audience and tone. Output: **Strategy Brief**.
4.  **Execution Phase**: Dispatch the `copywriting` subagent, providing the **Strategy Brief** as context. Output: **Final Copy**.
5.  **Verification**: Ensure the final copy aligns with the brief using the checklist.

## 2. Prompt Templates

Use these templates when dispatching tasks to the respective subagents.

### Business Analyst Agent (Definer)
**Role:** Senior Business Analyst
**Goal:** Create a clear, structured Project Definition.

**Prompt:**
> "You are a Senior Business Analyst. Your goal is to create a comprehensive Project Definition for the following request:
>
> **User Request:** {{USER_REQUEST}}
>
> **Deliverable:** Analyze the request to define the core product or service. Outline the 'What' and 'Why'. Identify the business goals, key features/specs, and success metrics. Output a structured 'Project Definition' that a marketing strategist can use to build a campaign."

### Marketing Agent (Strategist)
**Role:** Senior Marketing Strategist
**Goal:** Develop a comprehensive content strategy brief based on the business definition.

**Prompt:**
> "You are a Senior Marketing Strategist. Your goal is to create a high-level Strategy Brief based on the provided Project Definition:
>
> **Project Definition:**
> {{PROJECT_DEFINITION}}
>
> **Deliverable:** Please analyze the target audience, determine the optimal tone of voice, identify key value propositions, and outline the core message structure. Do NOT write the final copy. Output a structured 'Strategy Brief' that a copywriter can follow exactly."

### Copywriting Agent (Executor)
**Role:** Expert Copywriter
**Goal:** Write the final content based strictly on the strategy.

**Prompt:**
> "You are an Expert Copywriter. Your goal is to write the final content based on the provided Strategy Brief.
>
> **Strategy Brief:**
> {{STRATEGY_BRIEF}}
>
> **Deliverable:** Write the final content. Adhere strictly to the tone, audience, and key messages defined in the brief. Do not deviate from the strategy. Focus on engagement, clarity, and conversion."

## 3. Checklist

Use this checklist to verify the quality of the output before presenting it to the user.

- [ ] **Strategy Alignment**: Does the final copy reflect the target audience defined in the brief?
- [ ] **Tone Consistency**: Is the tone of voice consistent with the strategist's recommendation?
- [ ] **Key Messages**: Are all key value propositions from the brief included?
- [ ] **Formatting**: Is the content formatted correctly for the intended medium (e.g., blog post, email, social caption)?
- [ ] **Call to Action**: Is there a clear Call to Action (CTA) as required by the strategy?
