# Project Portrait

[中文文档](./README_zh.md)

Systematically analyze any codebase and produce 7 layered documents for interview prep and developer onboarding.

## What it does

Given a project codebase, Project Portrait guides Claude Code through a structured 11-phase process to produce:

| # | Document | Core Question |
|---|----------|---------------|
| 00 | Interview Summary | How to explain this project in one breath? |
| 01 | Background & Requirements | Why does this project exist? |
| 02 | Core Flow Walkthrough | How does the system actually work? |
| 03 | Architecture Design | How is the system designed? |
| 04 | Module Breakdown | What does each module do? |
| 05 | Technical Highlights & Challenges | What's worth talking about in an interview? |
| 06 | Optimization Directions | Where can the system go next? |

Each document links to the others, forming a navigable knowledge graph of your project.

## Install

```bash
git clone https://github.com/<user>/project-portrait-skill.git ~/.claude/skills/project-portrait-skill
```

Or install to a specific project: copy the directory into `<project>/.claude/skills/`.

## How to use

1. Tell Claude Code: `/project-portrait` or "帮我梳理项目"
2. Claude Code will explore your codebase, ask you questions when needed, and produce 7 documents in `docs_project_portrait/`.

The output directory is configurable — just say "output to docs/" in your prompt.

## What you need

- Claude Code
- A project with at least some code files (best results with 5K-50K lines)
- Ideally a README or CLAUDE.md for business context

## Structure

```
project-portrait-skill/
├── README.md
├── README_zh.md
├── LICENSE
├── SKILL.md
└── _facts-template.md
```

## License

Apache-2.0
