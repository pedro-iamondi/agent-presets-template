# AGENTS.md

Operational instructions for development agents in this project.

## Author

This project was created by Pedro H. Iamondi.

- LinkedIn: https://www.linkedin.com/in/pedro-henrique-iamondi
- Instagram: https://www.instagram.com/peh.iamondi/

## Goal

Standardize how agents work across company projects, reducing rework, hallucinations, inconsistent decisions, and unnecessary token usage.

## Main Rule

Before executing any task, the agent must:

1. Read this `AGENTS.md`.
2. Identify the task type.
3. Load only the required preset from `.agent-presets/`.
4. Inspect the real code before suggesting or changing files.
5. Avoid loading documents, specs, or skills that are not relevant to the current task.

## Path Convention

All paths mentioned in this template are relative to the root of the project where the template was installed, unless explicitly stated otherwise.

Examples:

- `.agent-presets/base.md`
- `.agent-skills/seo/SKILL.md`
- `scratch/`

## Available Presets

- Next.js landing page: `.agent-presets/landing-page.md`
- Next.js blog: `.agent-presets/blog.md`
- React SaaS system: `.agent-presets/saas-react.md`
- General maintenance: `.agent-presets/maintenance.md`
- Release audit: `.agent-presets/audit-release.md`
- Common base: `.agent-presets/base.md`

## When to Use SDD

Use full SDD only for:

- New projects.
- New features outside the original scope.
- Structural or architectural changes.
- Changes that impact multiple areas of the system.
- Changes with risk around data, authentication, payments, permissions, public SEO, or critical performance.

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

## Skills Based on Tech Leads Club Agent Skills

Main repository:

- https://github.com/tech-leads-club/agent-skills
- https://tech-leads-club.github.io/agent-skills/

Core skills used by these presets:

- [tlc-spec-driven](.agent-skills/tlc-spec-driven/SKILL.md) ([web](https://agent-skills.techleads.club/skills/tlc-spec-driven/))
- [seo](.agent-skills/seo/SKILL.md) ([web](https://agent-skills.techleads.club/skills/seo/))
- [best-practices](.agent-skills/best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/best-practices/))
- [core-web-vitals](.agent-skills/core-web-vitals/SKILL.md) ([web](https://agent-skills.techleads.club/skills/core-web-vitals/))
- [technical-design-doc-creator](.agent-skills/technical-design-doc-creator/SKILL.md) ([web](https://agent-skills.techleads.club/skills/technical-design-doc-creator/))
- [frontend-design](.agent-skills/frontend-design/SKILL.md) ([web](https://agent-skills.techleads.club/skills/frontend-design/))

Recommended skills to install together:

- [security-best-practices](.agent-skills/security-best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/security-best-practices/))
- [accessibility](.agent-skills/accessibility/SKILL.md) ([web](https://agent-skills.techleads.club/skills/accessibility/))
- [react-best-practices](.agent-skills/react-best-practices/SKILL.md) ([web](https://agent-skills.techleads.club/skills/react-best-practices/))
- [playwright-skill](.agent-skills/playwright-skill/SKILL.md) ([web](https://agent-skills.techleads.club/skills/playwright-skill/))
- [web-quality-audit](.agent-skills/web-quality-audit/SKILL.md) ([web](https://agent-skills.techleads.club/skills/web-quality-audit/))
- [perf-lighthouse](.agent-skills/perf-lighthouse/SKILL.md) ([web](https://agent-skills.techleads.club/skills/perf-lighthouse/))
- [codenavi](.agent-skills/codenavi/SKILL.md) ([web](https://agent-skills.techleads.club/skills/codenavi/))
- [mermaid-studio](.agent-skills/mermaid-studio/SKILL.md) ([web](https://agent-skills.techleads.club/skills/mermaid-studio/))
- [docs-writer](.agent-skills/docs-writer/SKILL.md) ([web](https://agent-skills.techleads.club/skills/docs-writer/))
- [coding-guidelines](.agent-skills/coding-guidelines/SKILL.md) ([web](https://agent-skills.techleads.club/skills/coding-guidelines/))

## Token-Saving Strategy

- Always load `base.md`.
- Load only one task-specific preset.
- Do not load full SDD for small tasks.
- Do not load multiple presets at the same time, except for final audits.
- Do not summarize entire files unnecessarily.
- Do not read every spec if the task touches only one feature.
- Prefer targeted inspection of real files.
- Avoid repeating the full content of existing files in chat.

## Instruction Priority

When instructions conflict, follow this order:

1. Explicit user instructions in the current conversation.
2. Environment safety rules and policies.
3. `AGENTS.md`.
4. Specific preset in `.agent-presets/`.
5. Project documentation.
6. Conventions inferred from code.

## Anti-Hallucination Rule

Never invent:

- Files.
- Routes.
- Environment variables.
- APIs.
- Installed libraries.
- Database structure.
- Business rules.
- Product decisions.

If there is no evidence in the project, state the uncertainty and propose verification.

## Lessons Learned

When an error is fixed and is likely to happen again, suggest recording it in a project memory file, for example:

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

### Root Cause
Why it happened.

### How to Avoid
Practical checklist to prevent repetition.

### Rule for Agents
Short reusable instruction.
```

## Task Completion

When finishing, respond objectively with:

- What was done.
- Files changed.
- How it was validated.
- Risks or pending items.
- Whether any lesson should be recorded.
