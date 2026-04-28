# Agent Presets Template

This repository provides a standardized structure to guide AI agents such as Cursor, Claude, Cline, and others during the company's software development cycle.

The main goal is to reduce hallucinations, save tokens, and keep architecture, security, and code quality consistent through progressive context disclosure.

## Author

Created by Pedro H. Iamondi.

*   LinkedIn: https://www.linkedin.com/in/pedro-henrique-iamondi
*   Instagram: https://www.instagram.com/peh.iamondi/

## Project Structure

The structure is modular by design, so agents do not need to read unnecessary instructions for simple tasks.

*   `AGENTS.md`: The entry point. Contains global rules, usage policies, and guidance for when to use each preset.
*   `AGENTS.pt-BR.md`: Portuguese copy of the agent instructions.
*   `MANIFEST.md`: Template catalog. Lists version, presets, installed skills, skill sources, and the update rule.
*   `MANIFEST.pt-BR.md`: Portuguese copy of the manifest.
*   `.agent-presets/`: Context files focused on specific scenarios, such as landing pages, blogs, and SaaS. They instruct the agent on how to approach each project type and which skills to consult.
*   `.agent-skills/`: Local copies of the official [Tech Leads Club](https://github.com/tech-leads-club/agent-skills) skills. They are detailed manuals for engineering domains such as SEO, accessibility, security, React, architecture, and more.
*   `scratch/`: Folder for disposable drafts, intermediate reports, and temporary agent outputs.
*   `README.pt-BR.md`: Portuguese copy of this README.

## Path Convention

All paths mentioned in this template are relative to the **project root** where the template was installed.

Examples:

*   `.agent-presets/base.md`
*   `.agent-presets/saas-react.md`
*   `.agent-skills/seo/SKILL.md`
*   `scratch/`

## Installation

This structure is portable. You can clone it to start a new project or integrate it into an existing repository.

### Existing Project

1. Download or clone this repository.
2. Copy `AGENTS.md` to the **root** of your current project.
3. Copy `MANIFEST.md` plus the `.agent-presets/`, `.agent-skills/`, and `scratch/` folders to the **root** of your project.
4. Optionally copy the `*.pt-BR.md` files if your team wants Portuguese documentation available in the project.

### New Project

1. Clone this repository.
2. Initialize your framework, such as Next.js or Vite, inside this same folder.
3. Start coding with agent support.

## Usage

The golden rule is **do not load everything at once**. That wastes tokens and confuses the agent.

The ideal workflow is:

1.  **Base context:** Whenever starting a new conversation or project, make sure the agent reads `AGENTS.md`. In tools such as Cursor, you can reference `@AGENTS.md` or add it to workspace rules.
2.  **Common base:** The agent should always load `.agent-presets/base.md`.
3.  **Direction:** Tell the agent your goal and ask it to load at most one specific preset from `.agent-presets/`, except for final audits.
    *   *Prompt example:* "I need you to create the pricing page. Read `AGENTS.md` first and decide which preset in `.agent-presets/` best applies."
    *   *Direct example:* "@.agent-presets/saas-react.md Create a login form following these guidelines."

Use `MANIFEST.md` as the template catalog whenever you need to review which presets and skills are available.

## Presets vs Skills

Understanding the difference helps guide the AI more effectively:

*   **Presets (`.agent-presets/`)**: Your **starting point**. Invoke them when starting a task, such as creating a landing page or running a release audit. The preset defines the task context and orchestrates the work.
*   **Skills (`.agent-skills/`)**: The **specialized tools**. Most of the time, **you do not need to invoke skills manually**. Presets already link to them. When an agent guided by a preset needs to apply an SEO rule, it should consult `.agent-skills/seo/SKILL.md`.

## Task Sizing

To avoid wasting time and tokens analyzing the whole architecture for a simple change, always direct the task scope. The structure instructs agents to work in three main modes:

### 1. Small Tasks (`quick` mode)

*   **What it is:** Color changes, position adjustments, isolated local refactors, typo fixes, or changes in up to 3 files, such as adjusting a button.
*   **How to request it:** Be direct, mention the file, and classify the task to avoid unnecessary reading.
    *   *Example:* "Adjust the primary button margin in `Header.tsx` to `mt-4`. Treat this as a `quick` task."

### 2. Medium Tasks (`standard` mode)

*   **What it is:** Changing or implementing a small feature that is already expected by the current scope and architecture, such as adding a new field to an existing form or creating a visual component based on an existing one.
*   **How to request it:** Ask the agent to read the specific area preset and inspect the code before implementing, without creating excessive documentation.
    *   *Example:* "@.agent-presets/saas-react.md Add the 'Phone' field to the user profile. Inspect the relevant components and implement it as a `standard` task."

### 3. Large Tasks (`full-sdd` mode)

*   **What it is:** Creating an unplanned feature, starting a new project from scratch, building complex integrations such as a new payment gateway, or changing the main architecture.
*   **How to request it:** Require the agent to create a technical planning document, SDD - Software Design Document, before coding. The agent will load heavier architecture skills for this.
    *   *Example:* "We need to create a new reports dashboard from scratch. Read `@AGENTS.md`, load `@.agent-presets/saas-react.md`, and start a `full-sdd` task. Create the technical design document for review before implementation."

## Prompt Examples by Scenario

### Quick Task

> Read `AGENTS.md` and treat this as a `quick` task. Adjust the primary button margin in `Header.tsx`, inspect only relevant files, and validate with the smallest applicable check.

### Landing Page

> Read `AGENTS.md`, load `.agent-presets/base.md` and `.agent-presets/landing-page.md`. Create the landing page pricing section while preserving SEO, accessibility, and performance. Inspect existing components before changing files.

### Blog or Post

> Read `AGENTS.md`, load `.agent-presets/base.md` and `.agent-presets/blog.md`. Add a new post following the current content structure, validating slug, metadata, and internal links.

### React SaaS

> Read `AGENTS.md`, load `.agent-presets/base.md` and `.agent-presets/saas-react.md`. Add the "Phone" field to the user profile, reusing existing patterns and handling loading, error, and success states.

### General Maintenance

> Read `AGENTS.md`, load `.agent-presets/base.md` and `.agent-presets/maintenance.md`. Investigate why the table filter is not updating correctly, find the root cause, apply the smallest safe fix, and validate the flow.

### Release Audit

> Read `AGENTS.md`, load `.agent-presets/base.md` and `.agent-presets/audit-release.md`. Run a pre-deploy audit and report blockers, recommendations, and executed validations. Do not fix automatically without authorization.

### Full-SDD Feature

> Read `AGENTS.md`, load `.agent-presets/base.md` and the most appropriate specific preset. This is a `full-sdd` task: create the technical design document first for review before implementing.
