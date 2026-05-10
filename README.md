<div align="center">

# jvever-readme-designer

**把 README 当 landing page 来设计，不是文档堆砌。**

[![License: CC BY-SA 4.0](https://img.shields.io/badge/license-CC%20BY--SA%204.0-lightgrey)](LICENSE) [![Claude Code Skill](https://img.shields.io/badge/Claude_Code-Skill-orange)](https://docs.claude.com/en/docs/claude-code/skills) ![Bilingual](https://img.shields.io/badge/lang-zh%20%2B%20en-blue)

[SKILL](skills/jvever-readme-designer/SKILL.md) · [CHANGELOG](CHANGELOG.md) · [English](README_en.md)

</div>

---

## 这是什么

一个 Claude Code Skill：你说一句「帮我写 README」，它先**读你的项目代码**，自己做完所有设计决策（archetype 选型、tagline 套路、section 顺序、卖点排序、双语策略），过两层自检，最后输出**中英双语营销级 README** + 图片任务清单。

它不替你做的事只有一件：**审稿**。

> Skill 是 Claude Code、Cursor、Codex 等 AI 编辑器通用的便携格式——装一次，到处可用。

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

或者用自然语言触发：

```
> 帮我把这个项目的 README 重写成 landing page
> 我的 README 太朴素了，做一下门面
```

Skill 会扫项目、做决策、生成草稿，**只在审稿环节叫你**。

---

## 为什么用它

### 1. 默认读代码，不问能推断的事

大多数 README 工具上来就是「请回答这 7 个问题」。本 Skill 第一步是**扫描**——manifest（package.json / Cargo.toml / pyproject.toml / go.mod / pubspec.yaml ……）、入口形态（CLI / 库 / Web app / Mobile / Desktop / AI 模型 / Skill）、主语种、视觉资产、trust signals 现状。

**能从代码推断的，不问你**。模型只在「这个信息缺了会让 README 明显打折」时才追问，**绝不**把"tagline 套路"、"section 顺序"这种设计题抛给用户。

多数项目跑完是 **0 个追问**。

### 2. 5 种 archetype 自动决策，不一刀切

不同产品有不同的 README 骨架。Skill 自己选：

| Archetype | 适用 | Hero 套路 |
|---|---|---|
| **A** 开发者工具型 | CLI / SDK / 库 / IDE 插件 / Skill | 品类定义 + 真实命令演示 |
| **B** 基础设施型 | DB / BaaS / 云 / API gateway | 结果承诺 + 大客户墙 |
| **C** 消费工具型 | 桌面 app / 视频音频 / 写作 | 身份共鸣 + 强视觉 |
| **D** 新品类教育型 | LLM agent / 全新概念 | 拟人 / 隐喻 + 视频 demo |
| **E** 第三方背书型 | 已有强对手的赛道 | 用户原话当 H1 |

决策器按 manifest + 入口形态自动选；不达标的 archetype（如 E 需要真实 testimonial）自动回落 A。所有 section 模板从 [section-library.md](skills/jvever-readme-designer/references/section-library.md) 取——**唯一真理源**，没有副本。

### 3. 主观判断 + 机械检测两层自检

DRAFT 完成后两层把关：

- **5 条核心原则**（[principles.md](skills/jvever-readme-designer/references/principles.md)）解决主观判断——首屏定生死 / 基于 Job 而非 feature / Show, don't tell / 克制即专业 / 信任信号 + 鲜活维护。每条挂反例锚作记忆点。
- **机械检测**（[auto-checks.md](skills/jvever-readme-designer/references/auto-checks.md)）解决客观对错——本地路径泄露（`/Users/<x>/`）、license broken link、`via.placeholder.com` 已停服、双语切换 silent fail、占位符未替换、装饰 ASCII 超长、标题 emoji……每项 regex 或字符串黑名单，命中即修或阻断。

**判断题归判断题，查表题归查表题**——v3 重构的核心。

### 4. 中英双语 + 国内生态接口

国内开源项目双语需求天然高。默认走 **M1 中文优先双文件**（`README.md` 中 + `README_en.md` 英），**不机翻**——按各自语言习惯重写。

中文项目自动启用一组**条件渲染**的国内 section（不打扰国际化项目）：飞书 / 微信 / QQ 群、ModelScope / WiseModel 镜像（AI 项目）、阿里云 / Sealos / Zeabur 一键部署、Bilibili 演示、Gitee / GitCode 镜像、Trendshift / HelloGitHub 排行 badge。

### 5. 信任信号阈值化，避免显穷

50 stars 项目放 Star History 反而暴露弱势。Skill 按阈值条件渲染：

| Section | 渲染条件 |
|---|---|
| Star History | ≥1k stars |
| Contributors 头像墙 | ≥10 contributors |
| Adopters 墙 | 用户提供 ≥3 个真实采用方 |
| Testimonials | 用户提供 ≥2 条真实引言 |
| Contributing 段 | 有邀请信号（CoC / template / 多人维护 / 现 README 含「欢迎贡献」）|

不达标就不渲染，让 README **该亮的亮，该藏的藏**。

---

## 工作流程

```
READ+DECIDE  →  DRAFT  →  ⛔ REVIEW
```

| 阶段 | 做什么 |
|---|---|
| **READ+DECIDE** | 本地扫项目（manifest / 资产 / 现有 README / LICENSE / CI），**不联网、不臆造**。自己决策 archetype、双语策略、tagline 套路、section 顺序。0-3 个真正缺的关键未知一次性问完。 |
| **DRAFT** | 生成 `README.md` + `README_en.md` + `docs/readme-image-plan.md`。两层自检循环 ≤2 轮，可自动修的直接修。 |
| **⛔ REVIEW** | 唯一阻塞点。展示「已自动修复」+「⚠️ 走默认值的字段」，等你审稿。1-2 轮迭代结束。 |

---

## 触发参数（三维正交）

```bash
/jvever-readme-designer                          # quick + bilingual + with-images（默认）
/jvever-readme-designer --full                   # 追问宽容度更高
/jvever-readme-designer --rewrite --en-only      # 重写已有，只输出英文
/jvever-readme-designer --patch --zh-only        # 只补已有中文 README 的窟窿
```

| 维度 | 选项 | 默认 |
|---|---|---|
| 流程 | `--quick` / `--full` / `--rewrite` / `--patch` | `--quick` |
| 输出语言 | `--bilingual` / `--en-only` / `--zh-only` | `--bilingual` |
| 图片任务清单 | `--with-images` / `--no-images` | `--with-images` |

持久化偏好：复制 `skills/jvever-readme-designer/EXTEND.md` 到项目根，永久覆盖默认值。

---

## 什么时候 *不* 用

| 场景 | 推荐做法 |
|---|---|
| 改一行错字 / 修链接 | 直接 Edit |
| 纯 dotfiles / awesome-list（没代码） | 用普通 markdown |
| README 是别人项目（你不维护） | 不要跑——你不该重写别人门面 |
| 想生成 CHANGELOG / API docs / wiki | 用对应工具 |
| 个人 reference（不公开） | 用最简结构即可 |

---

## 项目结构

```
jvever-readme-designer/
├── README.md                                # 中文（本文件）
├── README_en.md                             # English
├── CHANGELOG.md
├── LICENSE                                  # CC BY-SA 4.0
├── docs/
│   └── readme-image-plan.md                 # 图片任务清单
├── research/
│   └── synthesis.md                         # 60+ 项目调研
├── assets/                                  # 视觉资产占位
└── skills/
    └── jvever-readme-designer/
        ├── SKILL.md                         # 主入口，3 阶段流程
        ├── EXTEND.md                        # 用户偏好模板
        └── references/
            ├── principles.md                # 5 条核心原则
            ├── auto-checks.md               # 机械 lint
            ├── archetypes.md                # 5 archetype + 决策器
            ├── tagline-formulas.md          # 6 种 tagline 套路
            ├── section-library.md           # section 模板（唯一真理源）
            ├── trust-signals.md             # 信任信号清单
            ├── bilingual-patterns.md        # 双语模式
            └── image-plan.md                # 图片任务清单生成规则
```

---

## 怎么做出来的

5 路并行 sub-agent 调研了 **60+ 开源 README**（Cursor、Aider、OpenHands、LangChain、Vercel、Supabase、PostHog、ChatTTS、FastGPT、Dify、Lobe Chat、MaxKB ……）和产品 landing page（Linear、Stripe、Raycast、Notion、Arc、Warp ……），加上 7 份设计方法论原典。

之后过 4 路独立 reviewer agent（设计合理性 / 真实使用模拟 / 反模式审查 / 触发命名审查）+ 一轮校验。完整过程见 [research/synthesis.md](research/synthesis.md)。

主要设计影响：
- **Standard README spec** — Richard Litt
- **README Driven Development** — Tom Preston-Werner（2010）
- **StoryBrand SB7** — Donald Miller
- **Jobs-to-be-Done** — Tony Ulwick / Christensen
- **认知科学** — F-pattern 阅读模式（NN/G）、选择过载（Iyengar/Lepper）、峰终定律（Kahneman）

---

## 维护

每次 release / 每 3 个月 / star 数翻倍时，跑一遍：

```
> /jvever-readme-designer --rewrite
```

让 Skill 重新评估 archetype / hero 力度 / trust signals 状态。README 是活的产品页，半年不更新会显死。

---

## License

[CC BY-SA 4.0](LICENSE) — 自由复用、修改、商用，**衍生作品需署名 + 同协议开源**。
