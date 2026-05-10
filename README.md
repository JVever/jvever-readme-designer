<div align="center">

# jvever-readme-designer

**把 README 当 landing page 来设计，不是文档堆砌。**

[![License: CC BY-SA 4.0](https://img.shields.io/badge/license-CC%20BY--SA%204.0-lightgrey)](LICENSE) ![Bilingual](https://img.shields.io/badge/lang-zh%20%2B%20en-blue)

[SKILL](skills/jvever-readme-designer/SKILL.md) · [CHANGELOG](CHANGELOG.md) · [English](README_en.md)

</div>

---

一个 Skill：你说一句「帮我写 README」，它读你的项目代码、自己做完所有设计决策，输出中英双语营销级 README。**你只需要审稿。**

> Skill 是 Claude Code、Cursor、Codex 等 AI 编辑器通用的便携格式——下面以 Claude Code 为例。

---

## 它能帮你做到

- 🔍 **0 追问起步** — 读你的 manifest、commit、入口形态，能推断的事不问；多数项目跑完真的 0 个问题
- 🎯 **5 种骨架自动选** — CLI / 基础设施 / 消费工具 / 新品类 / 第三方背书，每种 hero 套路都不同，不一刀切
- 🛡 **错了自己修，可疑的让你定** — 路径泄露 / broken link / 装饰 ASCII / 标题 emoji 等机械错自动修；主观判断标 ⚠️ 让你审
- 🌏 **中英双语 + 国内生态自动启用** — 飞书 / ModelScope / 一键部署等，中文项目就出，英文项目就静默

---

## 快速开始

```bash
git clone https://github.com/JVever/jvever-readme-designer.git
cp -r jvever-readme-designer/skills/jvever-readme-designer ~/.claude/skills/
```

在你的项目里启动 Claude Code，对它说：

```
> /jvever-readme-designer
```

它会扫项目、自动决策、生成 `README.md` + `README_en.md` + `docs/readme-image-plan.md`，**只在审稿环节叫你**。

<details>
<summary>其他模式 / 持久化偏好</summary>

```bash
/jvever-readme-designer --full               # 追问宽容度更高
/jvever-readme-designer --rewrite --en-only  # 重写已有，只输出英文
/jvever-readme-designer --patch --zh-only    # 只补已有中文 README 的窟窿
```

复制 `skills/jvever-readme-designer/EXTEND.md` 到项目根可永久覆盖默认值。

Cursor / Codex 等其他 AI 编辑器的 Skill 路径请参考各自文档，原理一致。

</details>

---

## License

[CC BY-SA 4.0](LICENSE) — 自由复用、修改、商用，**衍生作品需署名 + 同协议开源**。
