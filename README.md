# BA Workspace for VSCode

This repository is scaffolded as a practical Business Analyst workspace with `domain/feature` as the main organizing model. Each feature acts like a mini BA pack, while `shared/` holds reusable artifacts that should not be duplicated.

## Workspace Goals

- Keep feature-level BA artifacts together and easy to review.
- Reduce context switching when working on one request or release item.
- Separate feature-specific work from cross-feature shared knowledge.
- Standardize prompt-driven analysis and documentation.
- Keep Markdown and CSV as default formats so files stay diff-friendly.

## Structure

```text
.
├── .vscode/
├── features/
│   └── hotel/
│       └── allotment/
│           ├── 01_discovery/
│           ├── 02_requirements/
│           ├── 03_analysis/
│           ├── 04_solution/
│           ├── 05_uat/
│           ├── 06_delivery/
│           ├── 07_decisions/
│           └── assets/
├── shared/
│   ├── glossary/
│   ├── stakeholders/
│   ├── business-rules/
│   ├── decisions/
│   ├── raid/
│   └── references/
├── prompts/
└── templates/
```

## How The Model Works

- `features/<domain>/<feature>/` contains all artifacts specific to one feature or request.
- Subfolders inside each feature still follow the BA lifecycle so the document flow remains predictable.
- `shared/` stores documents that apply across multiple features, such as a domain glossary, common stakeholders, shared business rules, and master governance logs.
- `templates/` stays reusable and should not hold live project content.
- `prompts/` stays global because the same AI prompts can be reused across many features.

## Suggested Workflow

1. Create or open a feature folder such as `features/hotel/allotment/`.
2. Start in `01_discovery/` with the project brief, stakeholder context, and current-state findings.
3. Capture requirements in `02_requirements/` and track analysis outputs in `03_analysis/`.
4. Prepare target-state artifacts in `04_solution/`.
5. Build UAT and validation assets in `05_uat/`.
6. Track readiness and rollout notes in `06_delivery/`.
7. Record feature decisions, actions, and risks in `07_decisions/`.
8. Put common information that should be reused by more than one feature in `shared/`.

## How To Use

- Open `ba-workspace.code-workspace` in VSCode.
- Install the recommended extensions from `.vscode/extensions.json`.
- Create a new feature folder under `features/<domain>/<feature>/` by copying the shape used in `features/hotel/allotment/`.
- Copy the needed template from `templates/` into the correct subfolder of the feature and rename it.
- Use a prompt from `prompts/` when working with ChatGPT, Codex, Copilot Chat, or another AI assistant.
- Store screenshots, exports, and diagrams in the feature's `assets/` folder.

## Naming Convention

- Prefix live artifacts with a date where useful: `2026-04-20-project-brief.md`
- Use lowercase kebab-case for filenames.
- Keep one major artifact per file.
- Keep domain and feature names stable over time so links do not drift.

## Minimal Operating Rules

- Record assumptions explicitly.
- Separate confirmed facts from proposed solutions.
- Link decisions back to requirements or risks.
- Put shared knowledge in `shared/` instead of copying it into multiple features.
- Keep acceptance criteria testable.
- Update traceability whenever scope changes.
