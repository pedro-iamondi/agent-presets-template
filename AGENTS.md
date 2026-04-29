# AGENTS.md

Operational instructions for development agents in this project.

## Author

This project was created by Pedro H. Iamondi.

- [Pedro H. Iamondi on LinkedIn](https://www.linkedin.com/in/pedro-henrique-iamondi)
- [Pedro H. Iamondi on Instagram](https://www.instagram.com/peh.iamondi/)

## Goal

Standardize how agents work across company projects. Use this template to
reduce rework, hallucinations, inconsistent decisions, and unnecessary token
usage.

## Main rule

Before executing any task, the agent must:

1. Read this `AGENTS.md`.
2. Identify the task type.
3. Load only the required preset from `.agent-presets/`.
4. Inspect the real code before suggesting or changing files.
5. Avoid loading documents, specs, or skills that are not relevant to the task.

## Path convention

All paths mentioned in this template are relative to the root of the project
where the template was installed, unless explicitly stated otherwise.

Examples:

- `.agent-presets/base.md`
- `.agent-skills/seo/SKILL.md`
- `scratch/`

## Available presets

- Next.js landing page: `.agent-presets/landing-page.md`
- Next.js blog: `.agent-presets/blog.md`
- React SaaS system: `.agent-presets/saas-react.md`
- General maintenance: `.agent-presets/maintenance.md`
- Release audit: `.agent-presets/audit-release.md`
- Common base: `.agent-presets/base.md`

## SDD usage

Use full SDD only for:

- New projects.
- New features outside the original scope.
- Structural or architectural changes.
- Changes that impact multiple areas of the system.
- Changes with risk around data, authentication, payments, permissions,
  public SEO, or critical performance.

Do not use full SDD for:

- Small fixes.
- Simple visual adjustments.
- Local refactors.
- Copy changes.
- Lint, type, or test fixes.
- Changes in up to 3 files without architectural impact.

For small tasks, use quick mode:

1. Understand the problem.
2. Inspect relevant files.
3. Apply the smallest safe change.
4. Validate.
5. Record a lesson only if the issue is recurring or relevant.

## Tech Leads Club skills

These presets use skills based on Tech Leads Club Agent Skills:

- [Tech Leads Club Agent Skills repository](https://github.com/tech-leads-club/agent-skills)
- [Tech Leads Club Agent Skills site](https://tech-leads-club.github.io/agent-skills/)

Core skills used by these presets:

- [tlc-spec-driven local skill](.agent-skills/tlc-spec-driven/SKILL.md)
  ([tlc-spec-driven web reference](https://agent-skills.techleads.club/skills/tlc-spec-driven/))
- [seo local skill](.agent-skills/seo/SKILL.md)
  ([seo web reference](https://agent-skills.techleads.club/skills/seo/))
- [best-practices local skill](.agent-skills/best-practices/SKILL.md)
  ([best-practices web reference](https://agent-skills.techleads.club/skills/best-practices/))
- [core-web-vitals local skill](.agent-skills/core-web-vitals/SKILL.md)
  ([core-web-vitals web reference](https://agent-skills.techleads.club/skills/core-web-vitals/))
- [technical-design-doc-creator local skill](.agent-skills/technical-design-doc-creator/SKILL.md)
  ([technical-design-doc-creator web reference](https://agent-skills.techleads.club/skills/technical-design-doc-creator/))
- [frontend-design local skill](.agent-skills/frontend-design/SKILL.md)
  ([frontend-design web reference](https://agent-skills.techleads.club/skills/frontend-design/))

Recommended skills to install together:

- [security-best-practices local skill](.agent-skills/security-best-practices/SKILL.md)
  ([security-best-practices web reference](https://agent-skills.techleads.club/skills/security-best-practices/))
- [accessibility local skill](.agent-skills/accessibility/SKILL.md)
  ([accessibility web reference](https://agent-skills.techleads.club/skills/accessibility/))
- [react-best-practices local skill](.agent-skills/react-best-practices/SKILL.md)
  ([react-best-practices web reference](https://agent-skills.techleads.club/skills/react-best-practices/))
- [playwright-skill local skill](.agent-skills/playwright-skill/SKILL.md)
  ([playwright-skill web reference](https://agent-skills.techleads.club/skills/playwright-skill/))
- [web-quality-audit local skill](.agent-skills/web-quality-audit/SKILL.md)
  ([web-quality-audit web reference](https://agent-skills.techleads.club/skills/web-quality-audit/))
- [perf-lighthouse local skill](.agent-skills/perf-lighthouse/SKILL.md)
  ([perf-lighthouse web reference](https://agent-skills.techleads.club/skills/perf-lighthouse/))
- [codenavi local skill](.agent-skills/codenavi/SKILL.md)
  ([codenavi web reference](https://agent-skills.techleads.club/skills/codenavi/))
- [mermaid-studio local skill](.agent-skills/mermaid-studio/SKILL.md)
  ([mermaid-studio web reference](https://agent-skills.techleads.club/skills/mermaid-studio/))
- [docs-writer local skill](.agent-skills/docs-writer/SKILL.md)
  ([docs-writer web reference](https://agent-skills.techleads.club/skills/docs-writer/))
- [coding-guidelines local skill](.agent-skills/coding-guidelines/SKILL.md)
  ([coding-guidelines web reference](https://agent-skills.techleads.club/skills/coding-guidelines/))

## Convex skills

Use Convex skills when a project uses Convex as the backend, database, or
real-time data layer. Load only the Convex skill that matches the task.

Source:

- [Convex Agent Skills repository](https://github.com/get-convex/agent-skills)

Installed Convex skills:

- [convex local skill](.agent-skills/convex/SKILL.md): Route general Convex
  work to the most specific Convex skill.
- [convex-quickstart local skill](.agent-skills/convex-quickstart/SKILL.md):
  Start a new Convex project or add Convex to an existing app.
- [convex-setup-auth local skill](.agent-skills/convex-setup-auth/SKILL.md):
  Set up authentication for a Convex app.
- [convex-create-component local skill](.agent-skills/convex-create-component/SKILL.md):
  Build a reusable Convex component with clear boundaries.
- [convex-migration-helper local skill](.agent-skills/convex-migration-helper/SKILL.md):
  Plan and run Convex migrations safely.
- [convex-performance-audit local skill](.agent-skills/convex-performance-audit/SKILL.md):
  Investigate Convex performance problems and bottlenecks.

When a task touches Convex data, auth, migrations, production performance, or
schema changes, treat it as at least `standard`. Use `full-sdd` when the change
affects data modeling, permissions, production migrations, or multiple app
areas.

## Token-saving strategy

- Always load `base.md`.
- Load only one task-specific preset.
- Do not load full SDD for small tasks.
- Do not load multiple presets at the same time, except for final audits.
- Do not summarize entire files unnecessarily.
- Do not read every spec if the task touches only one feature.
- Prefer targeted inspection of real files.
- Avoid repeating the full content of existing files in chat.

## Instruction priority

When instructions conflict, follow this order:

1. Explicit user instructions in the current conversation.
2. Environment safety rules and policies.
3. `AGENTS.md`.
4. Specific preset in `.agent-presets/`.
5. Project documentation.
6. Conventions inferred from code.

## Anti-hallucination rule

Never invent:

- Files.
- Routes.
- Environment variables.
- APIs.
- Installed libraries.
- Database structure.
- Business rules.
- Product decisions.

If there is no evidence in the project, state the uncertainty and propose
verification.

## Lessons learned

When an error is fixed and is likely to happen again, suggest recording it in a
project memory file, for example:

- `.agent-memory/known-errors.md`
- `.agent-memory/lessons-learned.md`
- `.agent-memory/project-decisions.md`

Do not record every small error. Record only reusable patterns.

Recommended template:

```md
## YYYY-MM-DD - short title

### Context
What was being done.

### Error
What happened.

### Root cause
Why it happened.

### How to avoid
Practical checklist to prevent repetition.

### Rule for agents
Short reusable instruction.
```

## Task completion

When finishing, respond objectively with:

- What was done.
- Files changed.
- How it was validated.
- Risks or pending items.
- Whether any lesson should be recorded.
