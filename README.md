<div align="center">

# jvever-readme-designer

**把 README 当门面写——读你的代码、自动决策、产出中英两份**

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC_BY--SA_4.0-lightgrey.svg)](LICENSE)

[English](README_en.md)

</div>

> 一个写 README 的通用 Skill。装进 Claude Code / Cursor / Codex / Trae 这类 AI 编辑器，用一句话描述意图即触发——不必记命令。

---

## 它能帮你做到

- 🎯 **首屏定生死** —— 项目名、一句话定位、第一行命令在折叠线以上，访客不滚动就能判断要不要继续看
- 🧠 **能猜到的不问你** —— 自己读 `package.json` / `Cargo.toml` / 代码结构去推断；只在确实推不出且会显著影响产出的客观未知（License 选哪个 / 真有客户名单吗 / 调性偏严肃还是带人情味）才开口
- 🧱 **不同项目用不同骨架** —— CLI / 库 / 基础设施 / 桌面创作工具 / 全新概念项目，套错骨架门面就崩；它按项目类型自动选
- 🛡 **机械错自己改、判断错让你定** —— 路径里漏出 `/Users/你/...`、占位图服务挂掉、双语切换条点了刷新本页——这类先自己修；拿不准的留 ⚠️ 标记在最后审稿时让你拍板
- 🌏 **中文不是翻译出来的** —— 中英两份对称生成，但中文按中文表达习惯重写不机翻；语言切换全篇只放一处，绝不重复

## 快速开始

把 `skills/jvever-readme-designer/` 整个文件夹拷到你的 AI 编辑器的 Skill 目录（Claude Code 是 `~/.claude/skills/`，其他编辑器看自己的文档），然后在你的项目根目录用一句话开口：

```
帮我写个 README
重做一遍 README
我要发开源了，给我做下 GitHub 门面
```

它会先扫项目、把所有设计选择都做完、给你一份草稿。你只在最后审稿时说"OK"或"那段改成 Y"。

跑完会得到 3 份产物：

- `README.md` —— 中文版，必出
- `README_en.md` —— 英文版，默认出，可关
- `docs/readme-image-plan.md` —— 图片任务清单（每张图给出路径、用途、推荐尺寸、做法建议）

**本仓库自己就是它的产物——你现在读的这份 README 是它写的。**

<details>
<summary>支持的调用方式</summary>

```
/jvever-readme-designer                       # 默认：自动判断要不要追问，中英双版都出
/jvever-readme-designer --full                # 想多答几个问题、希望产出更贴你想法时
/jvever-readme-designer --rewrite --en-only   # 重写已有 README、只要英文版
/jvever-readme-designer --patch --zh-only     # 只补现有中文 README 的窟窿
```

`--quick` / `--full` / `--rewrite` / `--patch` 四选一，可与 `--zh-only` / `--en-only` / `--bilingual` 自由组合。

</details>

## License

[CC BY-SA 4.0](LICENSE) © 2026 JVever
