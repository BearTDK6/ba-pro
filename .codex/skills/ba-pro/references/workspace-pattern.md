# Workspace Pattern

Use a feature-centric workspace unless the repository already has a stronger established convention.

## Default Layout

```text
features/
  <domain>/
    <feature>/
      01_discovery/
      02_requirements/
      03_analysis/
      04_solution/
      05_uat/
      06_delivery/
      07_decisions/
      assets/

shared/
  glossary/
  stakeholders/
  business-rules/
  decisions/
  raid/
  references/
```

## Placement Rules

- Put request-specific documents inside the feature folder.
- Put documents with value across multiple features inside `shared/`.
- Put screenshots, exports, and diagrams inside the feature's `assets/` folder.
- Keep templates outside live feature folders unless the repository explicitly treats them as working files.

## Naming Rules

- Use lowercase kebab-case for folders and files.
- Prefix dated working files when helpful, for example `2026-04-20-project-brief.md`.
- Keep domain and feature names stable over time.

## Refactor Rules

- Do not move cross-feature documents into a feature folder.
- Do not duplicate shared business rules into multiple feature folders unless the user explicitly wants local copies.
- Preserve existing user-authored content during refactors.
