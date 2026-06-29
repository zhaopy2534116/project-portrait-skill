# Project Portrait

[中文文档](./README_zh.md)

Systematically analyze frontend, backend, testing, algorithm, SDK, CLI, data, infrastructure, or mixed codebases and produce evidence-grounded project portrait documents for interview prep, onboarding, architecture review, and knowledge transfer.

## What it does

Given a project codebase, Project Portrait guides Claude Code through a structured, project-type-aware process to produce:

| # | Document | Core Question |
|---|----------|---------------|
| 00 | Executive Summary | How to explain this project quickly and accurately? |
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

`-g` installs globally to `~/.claude/skills/`, `-y` skips confirmation. Or install to a specific project with `npx skills add <user>/project-portrait-skill -y`.

## How to use

1. Tell Claude Code: `/project-portrait` or "帮我梳理项目"
2. Claude Code will classify the project type, explore your codebase, ask questions when evidence is insufficient, and produce documents in `docs_project_portrait/`.

The output directory is configurable — just say "output to docs/" in your prompt.

## What you need

- Claude Code
- A project with at least some code files
- Ideally a README, CLAUDE.md, design docs, tests, examples, or other evidence for context

## Structure

```
project-portrait-skill/
├── README.md
├── README_zh.md
├── LICENSE
├── SKILL.md
├── _facts-template.md
└── references/
    └── project-types.md
```

## License

Apache-2.0
