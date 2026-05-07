<div align="center">

# jvever-readme-designer

**像设计产品官网一样为开源项目设计 README。**

把 README 当 landing page，而不是文档堆。

![类型](https://img.shields.io/badge/类型-Claude_Code_Skill-7C3AED?style=flat-square)
![状态](https://img.shields.io/badge/状态-v2.1_生产可用-green?style=flat-square)
![双语](https://img.shields.io/badge/输出-中文+English-orange?style=flat-square)
![许可](https://img.shields.io/badge/license-MIT-blue?style=flat-square)

[安装](#安装) · [使用](#使用) · [模式](#工作模式三维正交) · [为什么](#为什么需要它) · [English](README.md)

</div>

---

一个 Skill：先扫描你的项目，再让你选择愿意花多少时间答题（多答 / 只答最关键的 / 全用默认跳过）。问几个由模型基于"还缺什么关键信息"自主决定，不固定数量。最后输出产品级双语 README + 配套图片任务清单。

> Skill 是 Claude Code、Cursor、Codex 等 AI 编辑器都支持的通用扩展格式——本项目装到任意一种里都能用。

---

## 为什么需要它

大多数开源 README 都是文档堆——装命令 + 功能列表 + License，访客 5 秒后离开。

写得好的那些（Linear / Cursor / Vercel / Supabase / FastGPT / Lobe Chat）把 README 当成了产品 landing page：

- 首屏 5 秒就能答清楚"做什么 / 给谁 / 怎么开始"
- 每个卖点都配证据（动图 / 性能数据 / 代码 / 前后对比）
- 信任信号系统化（真实用户、用户评价、可验证数字、最近一次发布）
- 结构因产品类型而异，不一刀切

这个 Skill 把这套"设计产品页"的手艺固化下来。它先扫描项目，让你选择愿意花多少时间答题，模型基于信息缺口决定问什么、问几个（不固定），自动挑选项目类型，跑机械检测 + 主观原则双层自检，输出中英双版。

---

## 主要特性

- **5 种项目类型自动匹配** —— 开发者工具 / 基础设施 / 消费工具 / 新品类教育 / 第三方背书优先。基于扫描结果 + 访谈信号自动决策。
- **6 种标语套路** —— 品类定义型 / 结果承诺型 / 身份共鸣型 / 第三方背书型 / 拟人隐喻型 / 硬核数字型。
- **5 条正向原则 + 机械检测分离** —— 主观判断走 [`principles.md`](skills/jvever-readme-designer/references/principles.md) 5 条原则；明确对错的检测（路径泄露 / broken link / 占位符 / 中英混杂黑名单等）走 [`auto-checks.md`](skills/jvever-readme-designer/references/auto-checks.md) 强制 lint。
- **访谈信息驱动，不按数字配额** —— 用户决定愿意花多少时间答题，模型基于"还缺什么关键信息"决定问什么、问几个，不固定上限。
- **默认中英双语** —— 中文优先（`README.md` + `README_en.md`），切换条遵循"当前语言不点击自身"规则，避免点了刷新本页的死循环。
- **图片任务清单** —— 单独输出 `docs/readme-image-plan.md`，每张图标优先级 + 尺寸 + 制作建议。可自动生成的（Star History / 贡献者头像墙 / mermaid 架构图）跳过。
- **信任信号条件渲染** —— Star History 仅 ≥1k stars 才放、贡献者头像墙仅 ≥10 人才放、用户名单仅在用户提供真实信息时才放——避免 50 stars 项目放 Star History 反成"显穷"。
- **国内特有元素** —— 微信/飞书/QQ 群、ModelScope/HF 双链接、Bilibili 视频、阿里云/Sealos/Zeabur 一键部署、整合包下载。
- **`EXTEND.md` 持久化偏好** —— 自定义默认类型、双语策略、emoji 风格、信任信号阈值。
- **边界声明** —— 明确"什么时候不该用本 Skill"，避免在 dotfiles / 单点改动 / 私人项目上误触发。

---

## 工作模式（三维正交）

三个独立维度，可任意组合：

| 维度 | 选项 | 默认 |
|---|---|---|
| **流程** | `--quick`（默认；模型按缺口和你的意愿动态问） / `--full`（候选池更广，偏向多问） / `--rewrite`（保留金句、改弱段、补缺漏） / `--patch`（只补缺失，不访谈） | `--quick` |
| **输出语言** | `--bilingual` / `--en-only` / `--zh-only` | `--bilingual` |
| **图片任务** | `--with-images` / `--no-images` | `--with-images` |

提问数量不固定。每次访谈开头 Skill 让你选意愿强度——多答 / 只答最关键的 / 全用默认跳过。在你给的边界内，模型基于"还有哪些信息缺失会让结果明显打折"自主决定问什么、问几个。

```bash
/jvever-readme-designer                       # 默认：双语 + 图片清单 + 按需访谈
/jvever-readme-designer --full                # 深度访谈
/jvever-readme-designer --rewrite --en-only   # 重写已有，只输出英文
/jvever-readme-designer --patch               # 只补窟窿，不动其他
```

持久化默认值 → 在项目根放一份 `EXTEND.md`。

---

## 安装

最简单的方式（推荐）——直接克隆到 Claude Code 的 skills 目录：

```bash
git clone https://github.com/<owner>/jvever-readme-designer.git \
  ~/.claude/skills/jvever-readme-designer

# 验证
ls ~/.claude/skills/jvever-readme-designer/skills/jvever-readme-designer
# → SKILL.md  EXTEND.md  _INDEX.md  references/
```

> 把 `<owner>` 替换成实际的 GitHub 仓库 owner。

如果你想把仓库放在自己的代码目录、再用符号链接到 skills 目录：

```bash
# 克隆到你自己习惯的代码目录
git clone https://github.com/<owner>/jvever-readme-designer.git <你的代码目录>/jvever-readme-designer

# 符号链接
ln -s <你的代码目录>/jvever-readme-designer/skills/jvever-readme-designer \
      ~/.claude/skills/jvever-readme-designer
```

Cursor / Codex 等其他 AI 编辑器：参考各自文档把 `skills/jvever-readme-designer` 注册为 skill 即可。

重启编辑器后下次会话自动加载。

---

## 使用

在你的 AI 编辑器里说下面任一话即可触发（中英都可）：

- "帮我重做这个项目的 README"
- "我的 README 太朴素了"
- "GitHub 项目首页要发布了，做一下门面"
- "Polish my README"
- "Write a marketing-grade README for this project"

Skill 自动启动后会带你走 5 阶段，每个 ⛔ 等你确认。

显式调用：`/jvever-readme-designer`（可加参数）。

---

## 工作流程

```
SCAN → ⛔ INTERVIEW → ⛔ 选类型 → DRAFT → ⛔ REVIEW
```

| 阶段 | 内容 |
|---|---|
| **SCAN** | 本地扫项目（项目清单 / 资产 / 现有 README / 许可证 / 持续集成配置）。**不联网、不臆造数据**。输出"项目自动画像"等你确认。 |
| **⛔ INTERVIEW** | 开头让你选意愿强度（多答 / 只答关键 / 全用默认）；模型基于信息缺口决定问什么、问几个，**不固定数量**。已知答案不再问。 |
| **⛔ 选类型** | 决策树推荐 1 种类型，给出当前项目的具体章节排序（不是抽象模板）。允许改。 |
| **DRAFT** | 生成 `README.md` + `README_en.md` + `docs/readme-image-plan.md`。自检循环 ≤2 轮，自动修安全问题。 |
| **⛔ REVIEW** | 列出已自动修复的项、升级到人工的项、主观决策点（如标语备选）。1-2 轮迭代后定稿。 |

---

## 项目结构

```
jvever-readme-designer/
├── README.md                          # 英文（主）
├── README_CN.md                       # 中文（当前）
├── CHANGELOG.md
├── research/
│   └── synthesis.md                   # 60+ 项目/官网调研汇总，17 条洞察
└── skills/
    └── jvever-readme-designer/           # 实际 skill 内容
        ├── SKILL.md                   # 主入口，5 阶段流程
        ├── EXTEND.md                  # 用户偏好持久化模板
        ├── _INDEX.md
        └── references/
            ├── principles.md          # 5 条核心原则（主观判断唯一来源）
            ├── auto-checks.md         # 机械检测清单（DRAFT 强制 lint）
            ├── interview-questions.md
            ├── answer-to-template-map.md
            ├── archetypes.md          # 5 种类型 + 决策树
            ├── tagline-formulas.md
            ├── section-library.md     # 章节模板库（唯一真理源）
            ├── trust-signals.md
            ├── bilingual-patterns.md
            ├── image-plan.md
            ├── anti-patterns.md
            ├── domestic-elements.md
            ├── scope-out.md           # 不该用本 Skill 的场景
            └── templates/
                ├── archetype-A-dev-tool.md
                ├── archetype-B-infrastructure.md
                ├── archetype-C-consumer-tool.md
                ├── archetype-D-new-category.md
                ├── archetype-E-endorsement-first.md
                └── _universal-blocks.md
```

---

## 怎么做出来的

5 路并行调研 Agent 调研了 **60+ 开源项目 README**（Cursor / Aider / OpenHands / LangChain / Vercel / Supabase / PostHog / ChatTTS / FastGPT / Dify / Lobe Chat / MaxKB ……）+ 软件产品官网（Linear / Stripe / Raycast / Notion / Arc / Warp ……）+ 7 个设计方法论来源（Standard README spec / Tom Preston-Werner 的 RDD / StoryBrand SB7 / JTBD / NN/G F-pattern 研究 ……）。

然后跑了 **4 个独立 Reviewer Agent**（设计理性 / 实战可用性模拟 / 反模式扫描 / 触发与命名）+ 一轮验证。最终评分：**8.5 / 10**，30 个问题中 27 个完整修复。

完整过程见 [research/synthesis.md](research/synthesis.md)。

主要设计影响：
- **Standard README spec** —— Richard Litt
- **README Driven Development** —— Tom Preston-Werner（2010）
- **StoryBrand SB7** —— Donald Miller
- **Jobs-to-be-Done** —— Tony Ulwick / Christensen
- **认知科学** —— F-pattern 阅读（NN/G）/ 选择悖论（Iyengar 果酱实验）/ Peak-end rule（Kahneman）

---

## 什么时候不该用它

完整清单见 [scope-out.md](skills/jvever-readme-designer/references/scope-out.md)。简短版：

- 改一行错字 / 修一个链接 → 直接 Edit，不要跑 5 阶段流程
- 纯 dotfiles / awesome-list / 非软件仓库 → 用普通 markdown
- 内部工具不需要做营销 → 最简结构即可
- 别人的项目 → 不要重写别人的门面

---

## 状态与路线图

- **v3.0**（当前，2026-05-07）—— 架构重构：命名统一为 `jvever`；设计哲学从反模式驱动转向正向原则驱动（5 原则 + 机械检测分离）；访谈从配额驱动转向信息驱动（不固定数量、无硬上限）。
- **v4**（计划中）—— 量化评估：在真实开源项目样本集上跑 Skill，按 5 原则 + 机械检测自动评分。

已知限制：
- 第三方背书型项目需要真实可验证的引言，**Skill 不会伪造**——这是设计原则。
- 扫描阶段**不调用 GitHub API**（避免凭空捏造 stars 数 / 版本号）；需要实时数据的 badge 用 shields.io URL，渲染时拉取。

---

## License

[MIT](LICENSE) © 2026 jvever
