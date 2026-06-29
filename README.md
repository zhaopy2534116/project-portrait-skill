# Project Portrait

[中文文档](./README_zh.md)

Project Portrait is a skill for systematically analyzing frontend, backend, testing, algorithm, SDK, CLI, data, infrastructure, or mixed codebases. It helps produce evidence-grounded project portrait documents for interview preparation, onboarding, architecture review, and knowledge transfer.

## What It Does

Given a project codebase, Project Portrait guides Claude Code through a structured, project-type-aware process to produce:

| # | Document | Core Question |
|---|----------|---------------|
| 00 | Executive Summary | How can this project be explained quickly and accurately? |
| 01 | Background & Requirements | Why does this project exist? |
| 02 | Core Flow Walkthrough | How does the system actually work? |
| 03 | Architecture and Design | What is the confirmed fact baseline? |
| 04 | Module Breakdown | What does each module do? |
| 05 | Technical Highlights & Challenges | What is meaningful, difficult, or risky? |
| 06 | Improvement Directions | Where can the system realistically improve? |

Each document links to the others and traces important claims back to source code, repository docs, or explicitly marked assumptions.

## Install

```bash
npx skills add <user>/project-portrait-skill -g -y
```

`-g` installs globally, and `-y` skips confirmation. To install into a specific project, run:

```bash
npx skills add <user>/project-portrait-skill -y
```

The installable skill lives in `project-portrait/`, not at the repository root. Keep this layout: when `SKILL.md` is at the repository root, `npx skills add` may install only `SKILL.md` and omit bundled files such as `_facts-template.md` and `references/project-types.md`.

## How To Use

1. Tell Claude Code: `/project-portrait` or "help me analyze this project".
2. Claude Code will classify the project type, explore the codebase, ask questions when evidence is insufficient, and produce documents in `docs_project_portrait/`.

The output directory is configurable. For example, say "output to docs/" in your prompt.

## Requirements

- Claude Code
- A project with at least some code files
- Ideally a README, CLAUDE.md, design docs, tests, examples, or other evidence for context

## Structure

```text
project-portrait-skill/
|-- README.md
|-- README_zh.md
|-- LICENSE
`-- project-portrait/
    |-- SKILL.md
    |-- _facts-template.md
    `-- references/
        `-- project-types.md
```

## License

Apache-2.0
