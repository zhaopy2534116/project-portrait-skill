# Project Portrait 项目画像

[English](./README.md)

Project Portrait 是一个用于系统分析代码项目的 skill，适用于前端、后端、测试、算法、SDK、CLI、数据管道、基础设施或混合型代码库。它会产出有证据支撑的项目画像文档，可用于面试准备、新人上手、架构评审和知识交接。

## 它做什么

给定一个项目代码库后，Project Portrait 会引导 Claude Code 按项目类型进行结构化分析，并产出：

| # | 文档 | 核心问题 |
|---|------|----------|
| 00 | 项目总览 | 怎样快速、准确地讲清楚这个项目？ |
| 01 | 项目背景与需求 | 为什么做这个项目？它解决什么问题？ |
| 02 | 核心流程梳理 | 系统实际如何运转？ |
| 03 | 架构与设计 | 已确认的事实基线是什么？ |
| 04 | 模块拆解 | 每个模块负责什么？ |
| 05 | 技术亮点与挑战 | 哪些设计有价值、困难或存在风险？ |
| 06 | 改进方向 | 下一步可以怎样务实改进？ |

每份文档会互相链接，并将关键结论追溯到源码、仓库文档或明确标注的推断。

## 安装

```bash
npx skills add <user>/project-portrait-skill -g -y
```

`-g` 表示全局安装，`-y` 表示跳过确认。安装到当前项目时使用：

```bash
npx skills add <user>/project-portrait-skill -y
```

可安装的 skill 位于 `project-portrait/` 子目录，不在仓库根目录。请保持这个布局：如果 `SKILL.md` 放在仓库根目录，`npx skills add` 可能只安装 `SKILL.md`，漏掉 `_facts-template.md` 和 `references/project-types.md` 等辅助文件。

## 如何使用

1. 对 Claude Code 说：`/project-portrait` 或“帮我梳理项目”。
2. Claude Code 会判断项目类型、探索代码库，在证据不足时向你提问，并在 `docs_project_portrait/` 下产出文档。

输出目录可以自定义。例如，在对话中说“输出到 docs/”。

## 你需要什么

- Claude Code
- 至少包含一些代码文件的项目
- 最好有 README、CLAUDE.md、设计文档、测试、示例或其他上下文证据

## 目录结构

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
