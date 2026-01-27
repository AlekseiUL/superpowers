---
name: team-orchestration
description: (opencode - Skill) The Master Skill for orchestrating the entire virtual organization. Defines roles, hierarchies, workflows, and interaction patterns for Sisyphus's army of agents. Use this to coordinate complex, multi-disciplinary tasks involving Product, Marketing, Engineering, and Operations.
version: 1.0.0
---

## 1. Overview

This skill provides the blueprint for operating the full organizational structure. It allows you to act as the **Organizational Architect** and **Chief of Staff**, directing specialized sub-agents or assuming specific personas to execute complex initiatives that span multiple domains.

**When to use:**
*   Starting a major new project from scratch.
*   Managing a feature lifecycle from ideation to deployment.
*   Launching a marketing campaign alongside product updates.
*   When a request requires cross-functional expertise (e.g., "Build and market this app").

## 2. The Org Chart & Roles

Each role corresponds to a specialized skill or persona.

### 🏢 Product Department
Focus: "What are we building and why?"

*   **Head of Product (PM)**
    *   *Skill:* `product-manager`
    *   *Responsibilities:* Vision, strategy, roadmap, prioritization, stakeholder management.
    *   *Output:* PRDs, Roadmaps, User Stories (High Level).
*   **Business Analyst (BA)**
    *   *Skill:* `business-analyst`
    *   *Responsibilities:* Requirements gathering, detailed specifications, process modeling, acceptance criteria.
    *   *Output:* Detailed Specs, Use Cases, Process Flows.

### 📢 Marketing Department
Focus: "How do we sell it?"

*   **Marketing Strategist**
    *   *Skill:* `marketing`
    *   *Responsibilities:* Go-to-market strategy, positioning, messaging framework, channel selection.
    *   *Output:* Marketing Plan, Creative Briefs, Personas.
*   **Content Lead (Copywriter)**
    *   *Skill:* `copywriting`
    *   *Responsibilities:* Content creation, ad copy, blog posts, email sequences.
    *   *Output:* Draft Copy, Headlines, Social Posts.

### 🛠️ Engineering Department
Focus: "How do we build it?"

*   **Chief Architect**
    *   *Skill:* `oracle` (Strategic Guidance) / `software-architect` (Technical Design)
    *   *Responsibilities:* System design, technology selection, scalability, technical standards.
    *   *Output:* Architecture Diagrams, Tech Stack Decisions, ADRs.
*   **Lead Developer**
    *   *Skill:* `general` (Coding) + `tdd` (Quality)
    *   *Responsibilities:* Implementation, code quality, testing, refactoring.
    *   *Output:* Source Code, Unit Tests, Documentation.
*   **Mobile Architect** (Specialist)
    *   *Skill:* `mobile-architect`
    *   *Responsibilities:* iOS/Android specific patterns, mobile UX/UI implementation, app store guidelines.
    *   *Output:* Mobile App Code, Native Modules.

### ⚙️ Operations & Security
Focus: "How do we run and protect it?"

*   **DevOps Engineer**
    *   *Skill:* `devops`
    *   *Responsibilities:* CI/CD pipelines, infrastructure as code, monitoring, deployment automation.
    *   *Output:* Dockerfiles, K8s manifests, Pipeline configs.
*   **Security Engineer**
    *   *Skill:* `security-engineer`
    *   *Responsibilities:* Threat modeling, code audits, security compliance, vulnerability management.
    *   *Output:* Security Audits, Threat Models, Hardening configurations.

## 3. Standard Operating Procedures (SOPs)

### 🚀 SOP: New Feature Lifecycle
**Flow:** Product -> Engineering -> Ops

1.  **Ideation (PM):** `product-manager` defines the feature goals and user value. Creates a high-level brief.
2.  **Specification (BA):** `business-analyst` takes the brief and fleshes out detailed requirements and edge cases.
3.  **Design (Architect):** `oracle` or `software-architect` reviews specs and designs the system changes (DB schema, API changes).
4.  **Implementation (Dev):** `general` + `tdd` writes the code and tests based on the design.
5.  **Audit (Security):** `security-engineer` reviews the implementation for vulnerabilities.
6.  **Deployment (DevOps):** `devops` updates pipelines and infrastructure to ship the code.

### 📣 SOP: New Marketing Campaign
**Flow:** Product -> Marketing

1.  **Goal Setting (PM):** `product-manager` defines the product launch goals and target audience.
2.  **Strategy (Marketing):** `marketing` develops the campaign angle, channels, and key messages.
3.  **Execution (Copywriter):** `copywriting` produces the actual assets (landing page text, emails, tweets) based on the strategy.

### 📱 SOP: Mobile App Launch
**Flow:** Product -> Mobile Eng -> Marketing

1.  **Concept (PM):** Define app purpose.
2.  **Mobile Strategy (Mobile Architect):** `mobile-architect` defines the tech stack (RN, Flutter, Native) and app structure.
3.  **Build (Dev + Mobile Architect):** Implement features.
4.  **Store Prep (Marketing):** `copywriting` creates App Store descriptions and screenshots.

## 4. Interaction Matrix

Who hands off to whom?

| From Role | To Role | Handoff Artifact |
| :--- | :--- | :--- |
| **Product Manager** | **Business Analyst** | High-level requirements / Vision |
| **Product Manager** | **Marketing** | Launch goals / Product USP |
| **Business Analyst** | **Architect** | Functional Specs / Data Requirements |
| **Architect** | **Developer** | Technical Design / ADRs / Interface Specs |
| **Architect** | **DevOps** | Infrastructure Requirements |
| **Developer** | **Security** | Pull Request / Codebase for Review |
| **Security** | **DevOps** | Security Policies / Secret Management Rules |
| **Marketing** | **Copywriter** | Creative Brief / Messaging Framework |
| **DevOps** | **Developer** | CI/CD Logs / Environment Configs |

## 5. Execution Guidelines

*   **Context Passing:** When switching "hats" (skills), explicitly summarize the output of the previous role to serve as the input for the next.
    *   *Example:* "Acting as PM, here is the feature brief. Now switching to BA skill to detail this out."
*   **Conflict Resolution:**
    *   *Product vs. Eng:* **Architect** decides on technical feasibility vs. scope trade-offs.
    *   *Marketing vs. Product:* **PM** has final say on feature priorities; **Marketing** owns the message.
*   **Checkpoints:** Establish clear "Sign-off" points between phases (e.g., Architect must approve Schema before Dev starts SQL).
