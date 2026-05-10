<div align="center">

# jvever-readme-designer

**读你的代码、最多问 3 个问题、生成营销级双语 README**

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](LICENSE) [![Type: Skill](https://img.shields.io/badge/type-Skill-blue.svg)](skills/jvever-readme-designer/SKILL.md)

[SKILL.md](skills/jvever-readme-designer/SKILL.md) · [CHANGELOG](CHANGELOG.md) · [English](README_en.md)

</div>

> 把 README 当 **landing page** 来设计，不是文档目录。KPI 是 5 秒留住访客、让他想 `git clone`——不是把所有功能写全。

> Skill 在 Claude Code / Cursor / Codex 等 AI 编辑器通用——下面以 Claude Code 为例。

## 它能帮你做到

- 🧭 **5 种骨架自动选** — CLI / 基础设施 / 创作者工具 / 新品类 / 第三方背书各有套路，决策器读 manifest 自动定，不一刀切
- ✍️ **0-3 个问题就动手** — 能从代码推断的事不问；只在 license / 大客户名单 / 主观调性这类客观未知时一次性追问
- 🌏 **中英双版同时出** — 不是机翻，按各自语言习惯重写文案、卖点排序也可以不同
- 🛡 **错了自己修，可疑的让你定** — 路径泄露、broken link、占位符没替换这类"对错明确"的自动修；tagline 力度、章节取舍这类主观判断升级到你审稿
- 📋 **图片任务清单顺手生成** — `docs/readme-image-plan.md` 列出 hero / logo / 截图清单，告诉你优先级和制作工具

## 快速开始

把 Skill 文件夹放到 Claude Code 的 skills 目录（系统级 `~/.claude/skills/` 或项目级 `.claude/skills/`），然后在任意项目里说：

```
/jvever-readme-designer
```

不到 30 秒就能拿到中英双版 README + 图片任务清单。

<details>
<summary>其他模式 / 流程参数</summary>

```
/jvever-readme-designer --rewrite       # 保留金句、改弱段、补缺漏
/jvever-readme-designer --patch         # 只补窟窿，不重写
/jvever-readme-designer --en-only       # 仅英文
/jvever-readme-designer --full          # 追问宽容度更高（默认 quick 多数 0 追问）
```

完整参数与设计原则见 [`SKILL.md`](skills/jvever-readme-designer/SKILL.md)。

</details>

## License

[CC BY-SA 4.0](LICENSE) © 2026 JVever
