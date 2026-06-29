# _facts - Exploration Ledger and Review Checklist

> Internal working file. Copy this to the output directory as `_facts.md` before exploration. Fill it while reading the repository, then use it during cross-review. It is not a polished deliverable.

## Scope

- **Project name**:
- **Repository path**:
- **Output directory**:
- **Reader goal**: interview / onboarding / architecture-review / knowledge-transfer / other
- **Detected project type**: frontend / backend / full-stack / test / algorithm-ML / SDK-library / CLI-tooling / data-pipeline / infrastructure / monorepo / mixed / other
- **Scale estimate**:
- **Out of scope**:

## Evidence Legend

Use one of these labels for every important claim:

- `源码确认`: confirmed by source code
- `文档确认`: confirmed by README, docs, comments, issues, or commit messages
- `推断`: inferred from code structure, naming, or dependency usage
- `待确认`: cannot be verified from available artifacts

## Project Snapshot

| Claim | Evidence level | Source |
|-------|----------------|--------|
| One-sentence summary | | |
| Primary users/consumers | | |
| Main capabilities | | |
| Runtime or usage model | | |
| Key constraints | | |

## Repository Map

| Path | Role | Evidence level | Notes |
|------|------|----------------|-------|
| | | | |

## Technology Stack

| Dimension | Choice | Evidence source | Notes |
|-----------|--------|-----------------|-------|
| Language/runtime | | | |
| Frameworks | | | |
| Build/test tools | | | |
| Storage/state | | | |
| External systems | | | |
| Deployment/runtime platform | | | |
| Other important dependencies | | | |

## Type-Specific Inventory

Fill only the rows that apply. Add project-specific rows when needed.

| Item | Count/value | Evidence source | Counting rule |
|------|-------------|-----------------|---------------|
| Source files | | | exclude generated/vendor/build files |
| Public APIs or exports | | | |
| Routes/pages/screens | | | frontend/full-stack |
| UI components/hooks/stores | | | frontend |
| API endpoints | | | backend/full-stack |
| Database tables/collections/schemas | | | backend/data |
| Jobs/workers/pipeline tasks | | | backend/data |
| CLI commands/subcommands | | | CLI/tooling |
| Test suites/cases/fixtures | | | test projects or any repo with tests |
| Algorithm stages/models/metrics | | | algorithm/ML |
| SDK packages/modules | | | library/SDK |
| Infrastructure resources/modules | | | infrastructure |
| CI workflows/jobs | | | |

## Core Flows

| Flow | Trigger/input | Major steps | Output/result | Evidence |
|------|---------------|-------------|---------------|----------|
| | | | | |

## Data, State, and Artifacts

| Name | Type | Producer | Consumers | Evidence |
|------|------|----------|-----------|----------|
| | | | | |

## External Boundaries

| Boundary | Direction | Purpose | Evidence | Risk/unknown |
|----------|-----------|---------|----------|--------------|
| | inbound/outbound | | | |

## Design Decisions and Tradeoffs

| Decision | Current choice | Evidence level | Why it matters | Tradeoff/risk |
|----------|----------------|----------------|----------------|---------------|
| | | | | |

## Highlights Candidates

Only promote a candidate to `05` if you can explain what would be worse without it.

| Candidate | Evidence | Why it matters | What would be worse without it |
|-----------|----------|----------------|--------------------------------|
| | | | |

## Challenges and Risks

| Issue | Evidence | Current handling | Remaining risk |
|-------|----------|------------------|----------------|
| | | | |

## Unknowns to Confirm

| Question | Why it matters | Best person/source to confirm |
|----------|----------------|-------------------------------|
| | | |

---

## Cross-Review Checklist

### Claim Audit

- [ ] Extracted all numeric claims from generated documents.
- [ ] Extracted all named entities: modules, classes, functions, components, commands, APIs, tables, schemas, datasets, models, resources, external systems.
- [ ] Extracted all config defaults, limits, assumptions, and runtime requirements.
- [ ] Verified each extracted item against source code or repository docs.
- [ ] Marked unverifiable items as `待确认` or removed them.

### Applicability Audit

- [ ] Removed or renamed sections inherited from a mismatched project type.
- [ ] No API/database/deployment/UI/algorithm/testing section is present unless the project actually has that concern.
- [ ] Document depth matches project size and reader goal.

### Consistency Audit

- [ ] Counts match across `00-06`.
- [ ] The same concept uses the same name across all documents.
- [ ] `03` remains the source of truth for architecture facts.
- [ ] Updates to `03` were propagated to other documents.

### Link and Navigation Audit

- [ ] Cross-document links resolve.
- [ ] Source file links point to real files.
- [ ] Headings are specific and useful.
- [ ] Each document starts with a short reader guide.

### Quality Audit

- [ ] No empty placeholder sections remain.
- [ ] No unsupported praise or generic improvement advice remains.
- [ ] Highlights explain "what would be worse without this design."
- [ ] Risks and unknowns are visible instead of hidden in prose.
- [ ] Final documents are readable without opening `_facts.md`.
