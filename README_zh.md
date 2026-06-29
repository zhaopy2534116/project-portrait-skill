# Project Portrait · 项目画像

[English](./README.md)

对任意项目代码库进行系统化梳理，产出 7 份层次递进的文档，用于面试准备与新人上手。

## 做了什么

Project Portrait 引导 Claude Code 通过结构化的 11 阶段流程，产出：

| # | 文档 | 核心问题 |
|---|------|----------|
| 00 | 项目面试总结 | 怎么用一段话讲清楚这个项目？ |
| 01 | 项目背景与需求 | 为什么做？解决什么问题？ |
| 02 | 核心流程梳理 | 系统怎么运转的？ |
| 03 | 架构设计文档 | 系统怎么设计的？ |
| 04 | 主要模块梳理 | 每个模块干什么？ |
| 05 | 技术亮点与难点 | 有什么值得说的？ |
| 06 | 项目优化方向 | 下一步怎么做得更好？ |

每份文档互相链接，形成可导航的项目知识图谱。

## 安装

```bash
git clone https://github.com/<user>/project-portrait-skill.git ~/.claude/skills/project-portrait-skill
```

或安装到指定项目：将目录复制到 `<project>/.claude/skills/` 下。

## 如何使用

1. 对 Claude Code 说：`/project-portrait` 或"帮我梳理项目"
2. Claude Code 会探索代码库，必要时向你提问，最终在 `docs_project_portrait/` 下产出 7 份文档

输出目录可自定义——在对话中说"输出到 docs/ 下"即可。

## 你需要

- Claude Code
- 至少有一些代码文件的项目（5K-50K 行效果最佳）
- 最好有 README 或 CLAUDE.md 提供业务背景

## 目录结构

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
