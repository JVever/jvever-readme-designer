<p align="center">
  <img alt="中文（当前）" src="https://img.shields.io/badge/lang-中文-red?style=flat-square">
  &nbsp;
  <a href="README.md"><img alt="English" src="https://img.shields.io/badge/lang-English-blue?style=flat-square"></a>
</p>

<div align="center">

# jvs-readme-designer

**像设计产品官网一样为开源项目设计 README。**

把 README 当 landing page，而不是文档堆。

![类型](https://img.shields.io/badge/类型-Claude_Code_Skill-7C3AED?style=flat-square)
![状态](https://img.shields.io/badge/状态-v2.1_生产可用-green?style=flat-square)
![双语](https://img.shields.io/badge/输出-中文+English-orange?style=flat-square)
![许可](https://img.shields.io/badge/license-MIT-blue?style=flat-square)

[安装](#安装) · [使用](#使用) · [模式](#工作模式三维正交) · [为什么](#为什么需要它) · [English](README.md)

</div>

---

```text
> 帮我重写这个项目的 README

  扫描项目：foo（CLI · Node.js · TypeScript）
  推荐 archetype：A（开发者工具型）
  三个问题：
    1. 用一句话说你的项目做什么？
    2. 谁会装它？他们用了能完成什么？
    3. 读完，你最希望访客做什么？

> [回答 3 个问题]

  反模式自检（17 项）：通过 15、升级 2 项请你判断
  已生成：README.md · README_en.md · docs/readme-image-plan.md
```

一个 Claude Code Skill：先访谈你，再为你的项目挑选合适的 archetype，最后生成产品级 README——中英双版 + 配套图片任务清单。

---

## 为什么需要它

大多数开源 README 都是文档堆——装命令 + 功能列表 + License，访客 5 秒后离开。

写得好的那些（Linear / Cursor / Vercel / Supabase / FastGPT / Lobe Chat）把 README 当成了产品 landing page：

- Hero 区 5 秒答清"做什么 / 给谁 / 怎么开始"
- 每个 claim 都配证据（GIF / benchmark / 代码 / before-after）
- 信任信号系统化（adopters / testimonials / 真实数字 / 最近 release）
- 结构因产品类型而异，不一刀切

这个 Skill 把这套"设计产品页"的手艺固化下来。你回答 3 个问题，它选对 archetype，跑反模式自检，输出中英双版。

---

## 主要特性

- **5 种 archetype** —— A 开发者工具 / B 基础设施 / C 消费工具 / D 新品类教育 / E 第三方背书优先。基于 SCAN + 访谈信号自动决策。
- **6 种 tagline 套路** —— 品类定义型 / 结果承诺型 / 身份共鸣型 / 第三方背书型 / 拟人隐喻型 / 硬核数字型。
- **17 项反模式自检** —— 唯一真理源在 `references/principles.md`，DRAFT 生成前自动跑。能自动改的直接修，主观判断的升级到人工 review。
- **默认中英双语** —— 中文优先（M1：`README.md` + `README_en.md`），切换条遵循"当前语言 badge 不带链接"规则，避免 silent fail。
- **图片任务清单** —— 单独输出 `docs/readme-image-plan.md`，每张图标优先级 + 尺寸 + 制作建议。可自动生成的（Star History / contributors / mermaid 架构图）跳过。
- **信任信号条件渲染** —— Star History 仅 ≥1k stars 才放、contributors 头像墙仅 ≥10 人才放、adopters 仅在用户提供真实名单时才放——避免 50 stars 项目放 Star History 反成"显穷"。
- **国内特有元素** —— 微信/飞书/QQ 群、ModelScope/HF 双链接、Bilibili 视频、阿里云/Sealos/Zeabur 一键部署、整合包下载。
- **`EXTEND.md` 持久化偏好** —— 自定义默认 archetype、双语策略、emoji 风格、信任信号阈值。
- **scope-out 边界声明** —— 明确"什么时候不该用本 Skill"，避免在 dotfiles / 单点改动 / 私人项目上误触发。

---

## 工作模式（三维正交）

三个独立维度，可任意组合：

| 维度 | 选项 | 默认 |
|---|---|---|
| **流程** | `--quick`（3 问） / `--full`（7 问） / `--rewrite`（保留金句、改弱段、补缺漏） / `--patch`（只补缺失，不访谈） | `--quick` |
| **输出语言** | `--bilingual` / `--en-only` / `--zh-only` | `--bilingual` |
| **图片任务** | `--with-images` / `--no-images` | `--with-images` |

```bash
/jvs-readme-designer                       # quick + bilingual + with-images
/jvs-readme-designer --full                # 深度访谈，7 问
/jvs-readme-designer --rewrite --en-only   # 重写已有，只输出英文
/jvs-readme-designer --patch               # 只补窟窿，不动其他
```

持久化默认值 → 在项目根放一份 `EXTEND.md`。

---

## 安装

```bash
# 克隆仓库
git clone <仓库地址> ~/Code/18-My_Skills/12-jvs-readme-designer

# 符号链接到 Claude Code 的 skills 目录
ln -s ~/Code/18-My_Skills/12-jvs-readme-designer/skills/jvs-readme-designer \
      ~/.claude/skills/jvs-readme-designer

# 验证
ls ~/.claude/skills/jvs-readme-designer
# → SKILL.md  EXTEND.md  _INDEX.md  references/
```

重启 Claude Code，下次会话自动加载。

---

## 使用

在 Claude Code 里说下面任一话即可触发（中英都可）：

- "帮我重做这个项目的 README"
- "我的 README 太朴素了"
- "GitHub 项目首页要发布了，做一下门面"
- "Polish my README"
- "Write a marketing-grade README for this project"

Skill 自动启动后会带你走 5 阶段，每个 ⛔ 等你确认。

显式调用：`/jvs-readme-designer`（可加 flag）。

---

## 工作流程

```
SCAN → ⛔ INTERVIEW → ⛔ ARCHETYPE → DRAFT → ⛔ REVIEW
```

| 阶段 | 内容 |
|---|---|
| **SCAN** | 本地扫项目（manifest / 资产 / 现有 README / LICENSE / CI）。**不联网、不臆造数据**。输出"项目自动画像"等你确认。 |
| **⛔ INTERVIEW** | 3 问（quick）或 7 问（full），用 `AskUserQuestion` 批量提问。SCAN 已知的问题不再问。 |
| **⛔ ARCHETYPE** | 决策树推荐 1 种 archetype，给出当前项目的具体 section 排序（不是抽象模板）。允许改。 |
| **DRAFT** | 生成 `README.md` + `README_en.md` + `docs/readme-image-plan.md`。自检循环 ≤2 轮，自动修安全问题。 |
| **⛔ REVIEW** | 列出已自动修复的项、升级到人工的项、主观决策点（如 tagline 备选）。1-2 轮迭代后定稿。 |

---

## 项目结构

```
12-jvs-readme-designer/
├── README.md                          # 英文（主）
├── README_CN.md                       # 中文（当前）
├── CHANGELOG.md
├── research/
│   └── synthesis.md                   # 60+ 项目/官网调研汇总，17 条洞察
└── skills/
    └── jvs-readme-designer/           # 实际 Claude Code skill
        ├── SKILL.md                   # 主入口，5 阶段流程（404 行）
        ├── EXTEND.md                  # 用户偏好持久化模板
        ├── _INDEX.md
        └── references/
            ├── principles.md          # 7 条核心原则 + 唯一真理源 checklist
            ├── interview-questions.md
            ├── answer-to-template-map.md
            ├── archetypes.md          # 5 种 archetype + 决策树
            ├── tagline-formulas.md
            ├── section-library.md     # section 模板库（唯一真理源）
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

完整清单见 [scope-out.md](skills/jvs-readme-designer/references/scope-out.md)。简短版：

- 改一行错字 / 修一个链接 → 直接 Edit，不要跑 5 阶段流程
- 纯 dotfiles / awesome-list / 非软件仓库 → 用普通 markdown
- 内部工具不需要做营销 → 最简结构即可
- 别人的项目 → 不要重写别人的门面

---

## 状态与路线图

- **v2.1**（当前）—— 生产可用。通过了 4-reviewer 评审 + 验证轮。
- **v3**（计划中）—— 量化评估：在真实开源项目 fixture 集上跑 Skill，按 17 项 checklist 自动评分。

已知限制：
- E 型 archetype（第三方背书优先）需要真实可验证的引言，**Skill 不会伪造**——这是设计原则。
- SCAN **不调用 GitHub API**（避免 hallucinate stars / version 数字）；需要实时数据的 badge 用 shields.io URL，渲染时拉取。

---

## License

[MIT](LICENSE) © 2026 jvs
