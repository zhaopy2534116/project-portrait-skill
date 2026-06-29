---
name: project-portrait
description: Systematically analyze a software project and produce evidence-grounded project portrait documents for interview preparation, onboarding, architecture review, or knowledge transfer. Use for frontend apps, backend services, test frameworks, algorithms, SDKs/libraries, CLI tools, data pipelines, infrastructure projects, or mixed repositories when the user asks to understand, document, review, explain, or summarize a codebase.
---

# Project Portrait

Analyze a codebase and produce a readable, evidence-grounded project portrait. The goal is not to fill a fixed template; the goal is to help a real reader understand what the project does, how it works, what matters, and where the risks or improvement opportunities are.

Default output directory: `docs_project_portrait/`, unless the user specifies another path.

## Core Principles

- Treat source code as the primary evidence. README, design docs, issues, and commit messages are supporting evidence.
- Do not invent business context, architecture, performance claims, usage scale, or design motivation. Mark uncertain points as `待确认` / `To confirm`.
- Adapt every document to the project type. Do not write API, database, deployment, async task, UI, algorithm, or testing sections when the project does not have that concern.
- Prefer fewer high-quality sections over many shallow sections. If only three strong highlights exist, write three.
- Keep reader value explicit: every section should answer "what is this, where is it, why does it matter, and what evidence supports it?"
- Write in the user's conversation language. Translate headings and placeholders semantically when the user is using English.

## Companion Files

| File | When to use |
|------|-------------|
| `_facts-template.md` | Copy to the output directory as `_facts.md` before exploration, then fill it while reading the codebase. |
| `references/project-types.md` | Read after Phase 0 to adapt exploration, facts, and document structure to the detected project type. |

## Phase 0: Clarify Scope

Before writing documents, state assumptions and choose an execution mode.

1. Identify the reader goal:
   - `interview`: concise story, tradeoffs, highlights, likely follow-up questions.
   - `onboarding`: architecture map, development entry points, module responsibilities, common workflows.
   - `architecture-review`: design decisions, risks, boundaries, scalability, maintainability.
   - `knowledge-transfer`: balanced project handbook with links, glossary, and operational context.
2. Detect the project type:
   - frontend app, backend service, full-stack app, test project, algorithm/ML project, SDK/library, CLI/tooling, data pipeline, infrastructure, monorepo, or mixed.
3. Estimate scale using repository file inventory and source line counts:
   - small: under 5K source lines
   - medium: 5K-30K source lines
   - large: over 30K source lines
4. Read `references/project-types.md` and select only the relevant type guidance.
5. If the project type or reader goal is genuinely unclear, ask the user. Otherwise proceed with the most likely interpretation and record it in `_facts.md`.

## Phase 1: Create the Fact Ledger

Create the output directory and copy `_facts-template.md` to `<output>/_facts.md`.

Fill `_facts.md` continuously while exploring. Every important claim in the final documents should trace back to one of:

- `源码确认`: exact file, symbol, config, test, route, component, function, or script.
- `文档确认`: README, docs, comments, issue text, or commit message.
- `推断`: inferred from code structure or naming; explain the inference basis.
- `待确认`: cannot be confirmed from available artifacts.

Use `待确认` instead of guessing. A readable document with a few explicit unknowns is better than a polished but unreliable document.

## Phase 2: Explore the Codebase

Explore in this order, adapting details by project type:

1. Repository map: top-level folders, package/workspace layout, generated/build/vendor folders to ignore.
2. Entry points: app bootstraps, exported APIs, CLI commands, tests, training scripts, notebooks, pipelines, infrastructure roots.
3. Configuration: environment variables, config files, feature flags, build settings, runtime parameters.
4. Dependency surface: frameworks, major libraries, external systems, runtime platforms, toolchain.
5. Core flows: user flows, request flows, command flows, test flows, algorithm/data flows, or package API flows.
6. Domain model: business entities, UI state, data schemas, test fixtures, algorithm inputs/outputs, infrastructure resources.
7. Cross-cutting behavior: error handling, logging, security, validation, caching, concurrency, accessibility, observability, reproducibility.
8. Quality signals: tests, type checks, linting, CI, benchmarks, examples, docs, release/versioning.

For each layer, record evidence in `_facts.md`. Include file paths and symbol names, not vague statements like "the service layer handles business logic."

## Phase 3: Lock the Baseline Document First

Write `03-architecture-and-design.md` first. It is the single fact baseline for the other documents.

Required sections:

```markdown
# 03 - Architecture and Design

> **Reader Guide**
> This document explains the confirmed structure, boundaries, and design decisions of the project.

## 1. Project Snapshot
| Dimension | Confirmed Finding | Evidence |
|-----------|-------------------|----------|

## 2. Repository Map
Describe the folder/module layout and what each important area owns.

## 3. Runtime or Usage Model
Adapt this section:
- frontend: browser/app runtime, routing, rendering, state update path
- backend: request lifecycle, workers, storage, external integrations
- test project: test execution model, fixtures, mocking, reporting
- algorithm: input data, preprocessing, algorithm stages, output/evaluation
- SDK/library: public API surface, package boundaries, extension points
- CLI/tooling: commands, arguments, config precedence, exit behavior
- data/infrastructure: pipeline/resource topology, deployment/apply flow

## 4. Core Flows
Document the main flows with source-linked steps and diagrams where useful.

## 5. Key Modules
Summarize responsibilities, important files, public interfaces, and dependencies.

## 6. Data and State
Adapt to the project: database tables, UI state, fixtures, schemas, artifacts, model weights, cache, files, queues, or infrastructure state.

## 7. External Boundaries
Document external APIs, services, browser/device APIs, package consumers, CI systems, datasets, cloud resources, or none.

## 8. Design Decisions and Tradeoffs
Only include decisions supported by code/docs. Mark inferred motivations clearly.

## 9. Risks and Unknowns
List confirmed risks, weak evidence, missing docs, and questions for maintainers.
```

Rules:

- Remove or rename sections that do not apply.
- Every table row that contains a count, name, path, config default, or dependency must have evidence.
- If a section would be empty, replace it with a short "Not applicable" note and explain why, or remove it if the removal improves readability.

## Phase 4: Produce the Document Set

After `03` is stable, produce the remaining documents. Keep the `00-06` numbering by default, but adapt titles and internal sections to the reader goal and project type.

### `01-background-and-requirements.md`

Purpose: explain why the project exists and what problem it solves.

Include:

- project positioning in one paragraph
- target users or consumers
- main use cases or workflows
- requirements mapped to implemented capabilities
- non-goals or boundaries when visible from code/docs
- unknown business context if the repository does not provide it

Avoid technical jargon unless the project itself is technical infrastructure and the target reader expects it.

### `02-core-flows.md`

Purpose: explain how the project actually runs.

Include 1-4 core flows depending on project scale. Each flow should include:

- trigger/input
- major steps with file or symbol evidence
- state/data changes
- branches, failure paths, or edge cases when important
- final output/result

Use ASCII or Mermaid diagrams only when they clarify the flow. Do not add diagrams for decoration.

### `04-module-breakdown.md`

Purpose: help a developer locate responsibilities quickly.

Include:

- module index
- key files or packages
- responsibilities
- important classes/functions/components/tests/commands/resources
- dependencies between modules
- "read this first" guidance for maintainers

For large repositories, summarize secondary modules instead of exhaustively documenting every file.

### `05-highlights-and-challenges.md`

Purpose: identify what is technically meaningful.

Select only evidence-backed items. For each highlight:

- title
- what the design does
- why it matters
- what would be worse without it
- evidence links

For each challenge:

- problem
- why it is hard in this project
- current handling
- remaining risk or tradeoff

Do not force a fixed count. Small projects may have 2-3 strong items; larger systems may have more.

### `00-executive-summary.md`

Purpose: give the fastest coherent overview. Write this after all detailed documents.

Include:

- one-paragraph summary
- project type and audience
- the most important flows
- the most important architecture facts
- strongest highlights and risks
- links to detailed documents

For interview mode, make it sound like a spoken explanation. For onboarding or review mode, make it more direct and navigable.

### `06-improvement-directions.md`

Purpose: propose realistic next steps grounded in the current system.

Include:

- current state
- limitation or risk
- proposed improvement
- expected value
- cost/complexity
- evidence from the codebase

Allow project-specific improvements:

- frontend: UX consistency, accessibility, render performance, state complexity, testability
- backend: API boundaries, data consistency, resilience, observability, scalability
- tests: coverage gaps, flakiness, fixture design, CI feedback time
- algorithms: evaluation, reproducibility, complexity, data quality, benchmarking
- SDK/library: API stability, examples, compatibility, release process
- CLI/tooling: error messages, config model, composability, platform support
- infrastructure/data: drift, rollback, monitoring, data quality, lineage

Avoid generic advice like "add cache", "add tests", or "improve performance" unless tied to concrete evidence.

## Phase 5: Quality Bar

Apply these rules to every delivered document:

- Start with a short reader guide: what this document answers and who should read it.
- Prefer "conclusion -> evidence -> implication" paragraphs.
- Use tables for comparison and inventories; use prose for explanation and tradeoffs.
- Keep headings specific. Replace "Module 1" with the actual module name.
- Link related documents and local source files where useful.
- Maintain one vocabulary for the same concept across all documents.
- Do not include empty placeholder headings.
- Do not bury uncertainty. Put unknowns in a visible "Risks and Unknowns" or "To Confirm" section.

## Phase 6: Cross-Review

Before finishing, perform a cross-review using `<output>/_facts.md`.

Required checks:

1. Claim audit: extract all numeric claims, named entities, config defaults, API names, component names, command names, algorithm names, and external dependencies from the documents.
2. Evidence audit: verify every audited item against source code or documentation.
3. Consistency audit: ensure the same concept has the same name and count across all documents.
4. Link audit: verify all cross-document links and source file references.
5. Applicability audit: remove or rename sections that were inherited from a mismatched project type.
6. Readability audit: remove filler, repeated explanations, and unsupported praise.

If a claim cannot be verified, either remove it, weaken it, or mark it as `待确认`.

## Phase 7: Finalize

Deliver:

- the generated document paths
- a short summary of what was covered
- any important unknowns or limitations
- the verification performed

Do not modify the source project except for the requested documentation output. If the user explicitly asks to store project-specific pitfalls in a repo guide, update the appropriate project guidance file separately.
