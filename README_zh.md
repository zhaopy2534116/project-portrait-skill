# Project Portrait · 项目画像

[English](./README.md)

对前端、后端、测试、算法、SDK、CLI、数据管道、基础设施或混合型项目进行系统化梳理，产出有证据支撑的项目画像文档，用于面试准备、新人上手、架构评审和知识交接。

## 做了什么

Project Portrait 引导 Claude Code 通过会适配项目类型的结构化流程，产出：

| # | 文档 | 核心问题 |
|---|------|----------|
| 00 | 项目总览 | 怎么快速、准确地讲清楚这个项目？ |
| 01 | 项目背景与需求 | 为什么做？解决什么问题？ |
| 02 | 核心流程梳理 | 系统怎么运转的？ |
| 03 | 架构与设计文档 | 已确认的事实基准是什么？ |
| 04 | 主要模块梳理 | 每个模块干什么？ |
| 05 | 技术亮点与难点 | 哪些设计有价值、困难或风险？ |
| 06 | 项目改进方向 | 下一步可以怎样务实改进？ |

每份文档互相链接，并把关键结论追溯到源码、仓库文档或明确标注的推断。

## 安装

```bash
npx skills add <user>/project-portrait-skill -g -y
```

`-g` 安装到用户全局（`~/.claude/skills/`），`-y` 跳过确认。安装到指定项目用 `npx skills add <user>/project-portrait-skill -y`。

## 如何使用

1. 对 Claude Code 说：`/project-portrait` 或"帮我梳理项目"
2. Claude Code 会判断项目类型、探索代码库，在证据不足时向你提问，最终在 `docs_project_portrait/` 下产出文档

输出目录可自定义——在对话中说"输出到 docs/ 下"即可。

## 你需要

- Claude Code
- 至少有一些代码文件的项目
- 最好有 README、CLAUDE.md、设计文档、测试、示例或其他上下文证据

## 目录结构

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
