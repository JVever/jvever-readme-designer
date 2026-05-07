<div align="center">

# jvever-readme-designer

**把 README 当 landing page 而非文档来设计**

[![License](https://img.shields.io/badge/license-TBD-lightgrey)](#license) [![Claude Code Skill](https://img.shields.io/badge/Claude_Code-Skill-orange)](https://docs.claude.com/en/docs/claude-code/skills) [![Bilingual](https://img.shields.io/badge/lang-zh%20%2B%20en-blue)](README_en.md)

[SKILL.md](skills/jvever-readme-designer/SKILL.md) · [CHANGELOG](CHANGELOG.md) · [English](README_en.md)

</div>

> 一个 Claude Code Skill：当你说"帮我写 README"时，它先扫你的项目代码，做**缺口驱动的访谈**（不问能推断的事），按 **archetype 自动决策**拼装骨架，过 **5 条原则 + 机械检测两层自检**，最后生成中英双语营销级门面。

```bash
git clone https://github.com/JVever/jvever-readme-designer.git
cp -r jvever-readme-designer/skills/jvever-readme-designer ~/.claude/skills/
# 然后在项目里启动 Claude Code，对它说 /jvever-readme-designer
```

---

## 这个 Skill 是什么？

**简短版**：一个让 Claude Code 在你项目里**像产品经理 + 设计师 + 文案那样设计 README** 的方法论包。

**详细版**：

它不是模板生成器（不是 readme.so 那种填空），也不是单条 prompt。它是 Claude Code Skill 形态的**结构化方法论**：

- 默认**先读你的代码**——manifest、commit history、现有 README、入口形态、视觉资产、trust signals 状态——能推断的不问你
- 只在**真正缺信息时才追问**（缺口驱动，不是固定问卷；用户决定意愿强度，模型决定问什么）
- 按你的项目类型**自动决策 archetype**（5 种：开发者工具型 / 基础设施型 / 消费工具型 / 新品类教育型 / 第三方背书型）
- 用 **5 条核心原则**做主观判断（首屏定生死 / 基于 Job 而非 feature / Show don't tell / 克制即专业 / 信任信号 + 鲜活维护）
- 用**机械检测清单**做客观 lint（路径泄露 / broken link / 占位图服务停服 / 双语 silent fail 等，对错明确）
- 默认生成 **中英双语**（README.md + README_en.md）+ 一份 `docs/readme-image-plan.md` 图片任务清单

**结果**：你的 README 从"不到 100 行的文档堆砌"变成"5 秒能看清产品 → 30 秒愿意试用 → 1 分钟有信任建立"的 landing page。

---

## 快速开始

```bash
# 1. 把 Skill 装进 Claude Code
git clone https://github.com/JVever/jvever-readme-designer.git
cp -r jvever-readme-designer/skills/jvever-readme-designer ~/.claude/skills/

# 2. 在你的项目里启动 Claude Code，说：
> /jvever-readme-designer

# 或用自然语言触发：
> 帮我把这个项目的 README 重写成 landing page 风格
```

<details>
<summary>触发参数与模式（三维正交）</summary>

```
/jvever-readme-designer                          # quick + bilingual + with-images（默认）
/jvever-readme-designer --full                   # 多答几个问题，质量优先
/jvever-readme-designer --rewrite --en-only      # 重写已有 README，只输出英文
/jvever-readme-designer --patch --zh-only        # 只补已有中文 README 的窟窿
```

完整参数说明见 [SKILL.md](skills/jvever-readme-designer/SKILL.md)。

</details>

<details>
<summary>持久化偏好（EXTEND.md）</summary>

复制 `skills/jvever-readme-designer/EXTEND.md` 到你的项目根，按需调整默认值（永远默认 `--full`、永远 `--zh-only`、强制某种 emoji 风格等）。

</details>

---

## 为什么用这个 Skill

### 1. 默认读你的代码，不问不必问的问题

大部分 README 生成器一上来就是"请回答这 7 个问题"。本 Skill 的第一步是**扫描**：

- manifest（package.json / Cargo.toml / pyproject.toml / go.mod / Gemfile / pubspec.yaml ……）
- 入口形态（CLI / Library / Web app / Mobile / Desktop / AI Model 等 11 种特征推断）
- commit message 主语种、现有 README 的金句、trust signals 现状（LICENSE / CI / CHANGELOG / SECURITY）

**能从代码推断的，不问你**。只问"读完代码仍真正不知道、且不问会让 README 质量打折"的事。在"动态缺口评估 + 意愿强度三档"双层决策下，访谈通常 0-5 个问题——而不是固定 7 题。

### 2. 5 种 archetype 自动决策，不一刀切

不同产品类型有不同的 README 骨架：

| Archetype | 适用 | Hero 套路 |
|---|---|---|
| **A 开发者工具型** | CLI / SDK / 库 / IDE 插件 | 品类定义 + asciinema |
| **B 基础设施 / 平台型** | DB / BaaS / 云服务 / API gateway | 结果承诺 + 大客户墙 |
| **C 消费 / 创作者工具型** | 桌面 app / 视频音频 / 写作 | 身份共鸣 + 强视觉 |
| **D 新品类教育型** | LLM agent / 全新概念 | 拟人 / 隐喻 + 视频 demo |
| **E 第三方背书优先型** | 已有强势对手的赛道 | 用户原话当 H1 |

决策器按"manifest 信号 + 入口形态 + 用户答案"自动选，并允许混搭（如 A 型 CLI 借 D 的 architecture mermaid）。所有 section 模板从 [`section-library.md`](skills/jvever-readme-designer/references/section-library.md) 取——**唯一真理源**，没有副本。

### 3. 信仰原则 + 机械检测两层自检

**主观判断** 走 [5 条核心原则](skills/jvever-readme-designer/references/principles.md)：首屏定生死 / 基于 Job 而非 feature / Show, don't tell / 克制即专业 / 信任信号 + 鲜活维护。每条挂"反例锚"作记忆点。

**客观检测** 走 [机械 lint](skills/jvever-readme-designer/references/auto-checks.md)：本地路径泄露（`/Users/<x>/`）、broken license link、`via.placeholder.com` 已停服、双语切换 silent fail、占位符未替换、hero 后装饰 ASCII 超长、标题 emoji……每项对错明确，自动修或阻断进入 REVIEW。

> 主观判断与机械规则**不混在一起**——v3 重构的核心是把"判断题"与"查表题"分开，让模型在判断题上发挥判断力，在查表题上严格守规。

### 4. 默认中英双语 + 国内生态接口

国内开源项目双语需求天然高，但大多数 README 生成器只懂英文。本 Skill 默认走 **M1 中文优先双文件**（`README.md` 中 + `README_en.md` 英），并内置一组国内特有 section（**条件渲染**，不打扰国际化项目）：

- 飞书 / 微信 / QQ 社群入口
- ModelScope / WiseModel / OpenXLab 模型镜像（AI 项目）
- 阿里云计算巢 / Sealos / Zeabur / 1Panel 一键部署
- Bilibili 演示视频
- Gitee / GitCode / Atomgit 国内镜像仓库
- Trendshift / HelloGitHub / OSCHINA 排行 badge

---

## 核心特性

- 🔍 **代码先读，缺口才问** — manifest / commit / 入口形态先扫一遍，问的问题是项目特定函数，不是固定模板
- 🎯 **5 种 archetype 自动决策** — 决策器按入口形态 + 用户答案选骨架，允许跨型混搭
- 📐 **section-library 唯一真理源** — 16 个 section 模板都在一份文档里，无副本无漂移
- 🛡 **主观原则 + 机械检测两层自检** — 5 条原则做判断题，lint 清单做查表题，互不污染
- 🌏 **中英双语默认 + 国内生态内置** — M1 中文优先，飞书 / ModelScope / 一键部署等条件渲染
- 📦 **图片任务清单同步生成** — `docs/readme-image-plan.md` 列出每张图的位置 / 用途 / 尺寸 / 优先级 / 制作工具
- ⚡ **`--rewrite` / `--patch` 增量模式** — 不黑箱重写。先给 diff 报告（保留 X 段、重写 Y 段、补 Z 段），用户批准后再生成

---

## 参与贡献

这是早期项目，欢迎反馈：

- 🐛 **报告 Issue** — archetype 决策错误 / 检测漏报 / 模板缺陷
- 💡 **Feature Request** — 新 archetype / 新 section 模板 / 新 lint 规则
- 📖 **改进 references 文档** — `references/` 下任一文件
- 💻 **PR 欢迎**

变更历史见 [CHANGELOG.md](CHANGELOG.md)。

---

## License

License: TBD（建议补 LICENSE 文件，推荐 MIT）。
