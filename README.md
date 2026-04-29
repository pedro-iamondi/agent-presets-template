# Agent Presets Template

This repository provides a standardized structure to guide AI agents such as
Cursor, Claude, Cline, and others during the company's software development
cycle.

Use it to reduce hallucinations, save tokens, and keep architecture, security,
and code quality consistent through progressive context disclosure.

## Author

Created by Pedro H. Iamondi.

- [Pedro H. Iamondi on LinkedIn](https://www.linkedin.com/in/pedro-henrique-iamondi)
- [Pedro H. Iamondi on Instagram](https://www.instagram.com/peh.iamondi/)

## Project structure

The structure is modular by design, so agents do not need to read unnecessary
instructions for simple tasks.

- `AGENTS.md`: Entry point with global rules, usage policies, and guidance for
  when to use each preset.
- `AGENTS.pt-BR.md`: Portuguese copy of the agent instructions.
- `MANIFEST.md`: Template catalog with version, presets, installed skills,
  skill sources, and the update rule.
- `MANIFEST.pt-BR.md`: Portuguese copy of the manifest.
- `.agent-presets/`: Context files focused on specific scenarios, such as
  landing pages, blogs, and SaaS. They explain how the agent should approach
  each project type and which skills to consult.
- `.agent-skills/`: Local copies of the official
  [Tech Leads Club Agent Skills](https://github.com/tech-leads-club/agent-skills).
  They are detailed manuals for engineering domains such as SEO,
  accessibility, security, React, and architecture.
- `.agent-skills/convex*/`: Local copies of
  [Convex Agent Skills](https://github.com/get-convex/agent-skills) for
  projects that use Convex as the backend, database, or real-time data layer.
- `scratch/`: Folder for disposable drafts, intermediate reports, and
  temporary agent outputs.
- `README.pt-BR.md`: Portuguese copy of this README.

## Path convention

All paths mentioned in this template are relative to the **project root** where
the template was installed.

Examples:

- `.agent-presets/base.md`
- `.agent-presets/saas-react.md`
- `.agent-skills/seo/SKILL.md`
- `scratch/`

## Installation

This structure is portable. You can clone it to start a new project or
integrate it into an existing repository.

### Existing project

1. Download or clone this repository.
2. Copy `AGENTS.md` to the **root** of your current project.
3. Copy `MANIFEST.md` plus the `.agent-presets/`, `.agent-skills/`, and
   `scratch/` folders to the **root** of your project.
4. Optional: Copy the `*.pt-BR.md` files if your team wants Portuguese
   documentation available in the project.

### New project

1. Clone this repository.
2. Initialize your framework, such as Next.js or Vite, inside this same folder.
3. Start coding with agent support.

## Usage

The key rule is **do not load everything at once**. Loading too much context
wastes tokens and can confuse the agent.

Use this workflow:

1. Start with base context. When you start a new conversation or project, make
   sure the agent reads `AGENTS.md`. In tools such as Cursor, you can reference
   `@AGENTS.md` or add it to workspace rules.
2. Load the common base. The agent must always load `.agent-presets/base.md`.
3. Direct the task. Tell the agent your goal and ask it to load at most one
   specific preset from `.agent-presets/`, except for final audits.

Use `MANIFEST.md` as the template catalog when you need to review which presets
and skills are available.

## Presets vs. skills

Understanding the difference helps you guide the AI more effectively:

- **Presets (`.agent-presets/`)**: Use presets as the starting point when you
  begin a task, such as creating a landing page or running a release audit. The
  preset defines the task context and orchestrates the work.
- **Skills (`.agent-skills/`)**: Use skills as specialized references. Most of
  the time, you do not need to invoke skills manually. Presets already link to
  them. When an agent guided by a preset needs to apply an SEO rule, it should
  consult `.agent-skills/seo/SKILL.md`.

## Task sizing

To avoid wasting time and tokens analyzing the whole architecture for a simple
change, always direct the task scope. The structure instructs agents to work in
three main modes.

### 1. Small tasks (`quick` mode)

Use `quick` mode for color changes, position adjustments, isolated local
refactors, typo fixes, or changes in up to 3 files.

Example prompt:

> Adjust the primary button margin in `Header.tsx` to `mt-4`. Treat this as a
> `quick` task.

### 2. Medium tasks (`standard` mode)

Use `standard` mode for small features that fit the current scope and
architecture, such as adding a field to an existing form or creating a visual
component based on an existing one.

Example prompt:

> `@.agent-presets/saas-react.md` Add the "Phone" field to the user profile.
> Inspect the relevant components and implement it as a `standard` task.

### 3. Large tasks (`full-sdd` mode)

Use `full-sdd` mode for unplanned features, new projects, complex integrations,
or main architecture changes. Ask the agent to create a technical planning
document before coding.

Example prompt:

> We need to create a reports dashboard from scratch. Read `@AGENTS.md`, load
> `@.agent-presets/saas-react.md`, and start a `full-sdd` task. Create the
> technical design document for review before implementation.

## Prompt examples by scenario

### Quick task

> Read `AGENTS.md` and treat this as a `quick` task. Adjust the primary button
> margin in `Header.tsx`, inspect only relevant files, and validate with the
> smallest applicable check.

### Landing page

> Read `AGENTS.md`, load `.agent-presets/base.md` and
> `.agent-presets/landing-page.md`. Create the landing page pricing section
> while preserving SEO, accessibility, and performance. Inspect existing
> components before changing files.

### Blog or post

> Read `AGENTS.md`, load `.agent-presets/base.md` and
> `.agent-presets/blog.md`. Add a new post following the current content
> structure, validating slug, metadata, and internal links.

### React SaaS

> Read `AGENTS.md`, load `.agent-presets/base.md` and
> `.agent-presets/saas-react.md`. Add the "Phone" field to the user profile,
> reusing existing patterns and handling loading, error, and success states.

### Convex backend

> Read `AGENTS.md`, load `.agent-presets/base.md`,
> `.agent-presets/saas-react.md`, and the most specific Convex skill for the
> task. Add Convex auth, inspect the existing schema and functions first, and
> validate the generated Convex types before finishing.

### General maintenance

> Read `AGENTS.md`, load `.agent-presets/base.md` and
> `.agent-presets/maintenance.md`. Investigate why the table filter is not
> updating correctly, find the root cause, apply the smallest safe fix, and
> validate the flow.

### Release audit

> Read `AGENTS.md`, load `.agent-presets/base.md` and
> `.agent-presets/audit-release.md`. Run a pre-deploy audit and report
> blockers, recommendations, and executed validations. Do not fix automatically
> without authorization.

### Full-SDD feature

> Read `AGENTS.md`, load `.agent-presets/base.md` and the most appropriate
> specific preset. This is a `full-sdd` task: create the technical design
> document first for review before implementing.
