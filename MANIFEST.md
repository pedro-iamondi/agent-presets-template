# Agent Presets Template manifest

## Identity

- Name: Agent Presets Template
- Version: 0.1.0
- Reference date: April 28, 2026
- Goal: Standardize how AI agents work in company projects using presets,
  local skills, and progressive context loading.
- Author: Pedro H. Iamondi
- LinkedIn: [Pedro H. Iamondi on LinkedIn](https://www.linkedin.com/in/pedro-henrique-iamondi)
- Instagram: [Pedro H. Iamondi on Instagram](https://www.instagram.com/peh.iamondi/)

## Path convention

All paths mentioned in this template are relative to the root of the project
where the template was installed.

Examples:

- `AGENTS.md`
- `.agent-presets/base.md`
- `.agent-skills/seo/SKILL.md`
- `scratch/`

## Installed presets

- Common base: `.agent-presets/base.md`
- Next.js landing page: `.agent-presets/landing-page.md`
- Next.js blog: `.agent-presets/blog.md`
- React SaaS system: `.agent-presets/saas-react.md`
- General maintenance: `.agent-presets/maintenance.md`
- Release audit: `.agent-presets/audit-release.md`

## Installed skills

Local skills live in `.agent-skills/` and were selected from the Tech Leads
Club Agent Skills catalog. When an upstream skill includes supporting files
such as `references/`, `scripts/`, `rules/`, or `assets/`, keep those files
with the local copy so the skill can run as intended.

- accessibility
- best-practices
- codenavi
- coding-guidelines
- core-web-vitals
- docs-writer
- frontend-design
- mermaid-studio
- perf-lighthouse
- playwright-skill
- react-best-practices
- security-best-practices
- seo
- technical-design-doc-creator
- tlc-spec-driven
- web-quality-audit

## Skill sources

- [Tech Leads Club Agent Skills repository](https://github.com/tech-leads-club/agent-skills)
- [Tech Leads Club Agent Skills site](https://tech-leads-club.github.io/agent-skills/)
- [Skills registry consulted](https://github.com/tech-leads-club/agent-skills/blob/main/packages/skills-catalog/skills-registry.json)

## Update rule

1. Update skills intentionally, preferably in a dedicated branch.
2. Compare relevant changes with the upstream registry before replacing local
   content.
3. Do not edit copied skills without recording the decision in the project
   history.
4. Update this manifest whenever presets, skills, or usage rules change.
5. Validate links and paths after any update.

## Future suggestions

No new skills were added beyond the ones already installed. For future
iterations, evaluate architecture and tooling skills from the original registry
only when there is real demand, for example:

- coupling-analysis
- modular-decomposition
- component-common-domain-detection
- chrome-devtools
- gh-fix-ci
