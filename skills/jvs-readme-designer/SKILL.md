---
name: jvs-readme-designer
description: Interview-driven, marketing-grade README designer for code projects (open-source or internal). Treats README as a landing page with hero, archetype-aware sections, trust signals, bilingual output, and an image task plan — not a doc dump. 中文触发：写/重写/重做/重做一遍/美化/设计/双语/中英 README、GitHub 门面、GitHub 项目首页、项目 landing page、开源发布前/项目宣传/项目门面、README 太烂/太朴素/太简陋/没人看/像广告。English triggers：write/rewrite/redesign/polish/beautify/improve/craft README, bilingual or zh+en README, GitHub front page, open-source launch README, project landing page on GitHub, README too plain/no one reads my README. Supports `--quick`（按需 1-5 问，可选直接跳过用默认）和 `--full`（深度访谈最多 7 问），`--rewrite`（保留金句改弱段）和 `--patch`（只补窟窿）。
---

<!--
@input:    用户的项目目录（代码、manifest 文件、现有 README、assets/ 等）+ 用户在访谈阶段的回答
@output:   README.md（中文）+ README_en.md（英文，可选）+ docs/readme-image-plan.md（图片任务清单）+ assets/.gitkeep（占位）
@rule:     如本文件 @input 或 @output 发生变化，必须更新本注释并检查 _INDEX.md
-->

# /jvs-readme-designer — 像产品官网那样设计 README

把开源项目的 README 当作 **landing page** 而非文档来设计。它的 KPI 是 **conversion**（star、install、第一个 PR），不是 completeness。

> `jvs` 是作者前缀（namespace），用户**不需要输入 jvs 来触发**——通过描述意图即可命中。

## 核心信念

1. **首屏定生死** — 5 秒内必须答清"做什么 / 给谁 / 怎么开始"
2. **Show, don't tell** — 每一个 claim 必须有证据（demo / GIF / benchmark / 代码 / 真实用例）
3. **Archetype 驱动** — 不同产品类型有不同 README 结构，不一刀切
4. **信任信号系统化** — badges + adopters + 最近 release + 真实截图共同证明"项目活着、社区健康"
5. **克制比繁复更显高级** — 反对滥用 emoji / 居中 HTML / 动态 SVG / TOC 在短 README 里

---

## 调用方式与模式（三维正交）

参数分三个独立维度，可任意组合：

| 维度 | 选项 | 默认 |
|---|---|---|
| **流程** | `--quick`（按项目情况问 1-5 个，可一键跳过用默认） / `--full`（深度访谈最多 7 问） / `--rewrite`（重写已有 README） / `--patch`（只补缺失） | `--quick` |
| **输出语言** | `--bilingual`（中英双版） / `--en-only` / `--zh-only` | `--bilingual` |
| **图片任务清单** | `--with-images` / `--no-images` | `--with-images` |

示例：
```
/jvs-readme-designer                          # quick + bilingual + with-images
/jvs-readme-designer --full                   # full + bilingual + with-images
/jvs-readme-designer --rewrite --en-only      # 重写已有，输出仅英文
/jvs-readme-designer --patch --zh-only        # 仅补丁中文 README
```

> **流程维度互斥**（quick / full / rewrite / patch 四选一），其他两维度可与任一流程组合。

**默认输出**：`README.md`（中文）+ `README_en.md`（英文）+ `docs/readme-image-plan.md`。

> **持久化偏好**：用户可通过 `EXTEND.md` 设置默认值（如永远默认 `--full` 模式，或永远 `--zh-only`），见仓库根的 `EXTEND.md` 模板。

---

## 什么时候 *不* 用本 Skill

避免误触发的边界声明：

| 场景 | 推荐做法 |
|---|---|
| 改一行错字 / 修一个链接 | 直接 Edit，不用 Skill |
| 项目没有任何代码（纯 dotfiles / awesome-list） | 用普通 markdown 编辑，本 Skill 假设有 software 可介绍 |
| README 是别人的项目（你不维护） | 不要跑——你不该重写别人的门面 |
| 想生成 CHANGELOG / API docs / wiki | 这些不是 README 范畴；用对应工具 |
| 项目只供个人 reference（不公开） | 个人 README 不需要营销，用最简结构即可 |

---

## 工作流程（5 阶段，含 ⛔ BLOCKING 门控）

```
SCAN → ⛔ INTERVIEW → ⛔ ARCHETYPE → DRAFT → ⛔ REVIEW
```

⛔ 标记的环节是 BLOCKING——**必须等用户确认**才能进入下一阶段，避免 5 步流程黑箱跑完后才发现走错方向。

### 阶段 1：SCAN（本地扫描，不联网）

**硬约束**：
- **只读本地文件**，不调用 GitHub API、不假设有网络
- **禁止臆造数字**（stars / downloads / last release date 等用 shields.io 自动 URL 在渲染时拉取，Skill 不写入字面值）
- **禁止假冒 social proof**（adopters 客户名、testimonials 引言必须由用户提供）

**扫描清单**：

1. **manifest 文件**（按存在的取）：
   `package.json` / `Cargo.toml` / `pyproject.toml` / `setup.py` / `go.mod` / `pom.xml` / `build.gradle` / `Gemfile` / `composer.json` / `CMakeLists.txt` / `mix.exs` / `pubspec.yaml`

2. **入口形态**（用 manifest + 文件结构推断）：
   - **CLI**：`bin` 字段 / `src/main.rs` 含 `clap` / `entry_points` console_scripts / 项目根有 `Makefile` 入口
   - **Library**：`main`/`exports`/`lib` 字段，无 `bin`
   - **Web app**：依赖含 `next`/`vite`/`gatsby`/`remix`/`nuxt`/`astro`/`sveltekit`
   - **Mobile**：`Podfile` / Android `build.gradle` / Flutter `pubspec.yaml`
   - **Desktop**：`tauri.conf.json` / `electron-builder.json` / `package.json` 含 `electron`
   - **AI/Model**：`requirements.txt` 含 `torch`/`transformers`/`vllm`/`langchain` 等
   - **Docs / Skill / Config 仓库**（无可执行入口）：触发"零代码 fallback"提示，建议用户改用普通 markdown
   - **Monorepo**：根 `package.json` 含 `workspaces` / `pnpm-workspace.yaml` / `turbo.json` / `lerna.json` / `nx.json` → 询问用户"为根 README 还是子包 README 设计"

3. **现有视觉资产清单**：
   `assets/` / `docs/img/` / `docs/images/` / `.github/assets/` / `media/` / `images/` 下的图片文件

4. **现有 README**（如有）：
   读取后提取：标题、长度（行数）、是否双语、最后修改时间、明显金句（含数字 / testimonial / benchmark / use case）

5. **trust signals 现状**（存在性扫描）：
   `.github/workflows/` / `LICENSE` / `LICENSE.md` / `CHANGELOG.md` / `SECURITY.md` / `CONTRIBUTING.md` / `CODE_OF_CONDUCT.md`

6. **i18n 信号**：
   是否已有 `README_en.md` / `README.zh-CN.md` / `i18n/` / `docs/zh/`

7. **语种信号**（推断默认双语策略）：
   - 现有 README 主体语言（看前 100 字符 cjk 比例）
   - manifest description 字段语种
   - 主要 commit message 语种（采样 10 条）

8. **生态位粗略信号**（无网络，仅本地推断）：
   - 现有 README 是否提到大客户 / 名人引言 / benchmark 数字（→ 暗示有 social proof 可复用）
   - 是否提到强对手 / "alternative to X" / "replacement for X"（→ 触发 archetype E 候选）
   - .git 目录的 commit 数（粗略活跃度，>500 commit 视为成熟项目）

**⛔ BLOCKING — 输出"项目自动画像"+ 推荐配置，等用户确认或修正后才能进入 INTERVIEW**：

```
项目画像（本地扫描，未联网）：
- 名称：foo
- 类型：CLI 工具（Node.js · TypeScript）
- 现有 README：缺失 / 70 行 / 单语英文 / 无截图 / 无 badges
- 视觉资产：assets/logo.svg ✅, 截图 ❌
- Trust signals：✅ LICENSE  ✅ CI  ❌ CHANGELOG  ❌ CONTRIBUTING
- 主语种：英文（commits）/ 中文（README description）
- 监测到的 social proof：—（建议用 --quick 模式）

建议配置：
- 模式：--quick（项目尚无 social proof，深度访谈意义有限）
- 双语：M1（中文优先 + 英文版）
- Archetype：A（开发者工具型 / CLI）

确认 / 调整？
```

**SCAN 失败的 fallback**：
- **无 manifest**：询问用户"项目类型是？"（CLI / library / web app / docs / 其他），并提示"我会用最小信息生成，建议你之后用 `--patch` 补充"
- **mirror 仓库**（GitHub 是镜像）：询问主仓库 owner/repo，不要默认填 GitHub 路径
- **私有仓库**：跳过 shields.io / contrib.rocks / star-history（这些只对公开仓库工作），改用纯文字状态

### 阶段 2：INTERVIEW（按需问、动态裁剪、可整段跳过）

读 `references/interview-questions.md`。

**核心原则——访谈不是固定脚本**：
- 提问数量根据 SCAN 结果**动态决定**（项目越完整、信号越多 → 问得越少）
- **硬上限**：`--quick` 模式最多 5 个，`--full` 模式最多 7 个。任何场景下都不能超过 `--full` 上限
- **硬下限**：0 个——SCAN 已经能完整推断的项目可以直接进入下一阶段
- 用户随时可以选 "全用默认/跳过"——这是显式提供的选项，不是隐含

#### 2.1 进入 INTERVIEW 时的开场分流（**必须**）

每次进入 INTERVIEW 阶段，第一步**必须**先用 AskUserQuestion 让用户从 3 个选项里选一个：

| 选项 | 行为 |
|---|---|
| **答几个关键问题**（默认推荐） | Skill 按 SCAN 决策树选 1-5 个最关键的问题（quick）或 1-7 个（full） |
| **只答最最关键的 1-2 个** | Skill 只问"一句话定位"+ 必要时"目标用户"，其他全用默认/SCAN 推断 |
| **全用默认值，直接跳过访谈** | 0 个问题。Skill 用 SCAN 信号 + 项目类型默认值直接生成草稿，所有不确定项标 ⚠️ 让用户在 REVIEW 阶段决定 |

不要给用户固定列出 3 / 5 / 7 个问题——这违反"按需问"原则。

#### 2.2 问题池（按优先级，命中即问，未命中即跳过）

按以下优先级取问题，最多取够 quick 模式 5 个 / full 模式 7 个：

**P0（核心，几乎所有项目都会问）**：
1. **一句话定位**：你的项目用一句话告诉别人是干什么的？
2. **目标用户 + 核心目的**：谁会装它？他们用了能做什么？避免什么痛？

**P1（条件触发，命中才问）**：
3. **主路径行动**：你最希望访客读完后做什么？（仅当 SCAN 无法从项目类型推断默认行动时）
4. **差异化**：vs 1-2 个竞品（仅当用户在前面提到"类似 X"或现有 README 含"alternative to X"）
5. **典型使用场景** 2-3 个（仅当 P0 答案抽象，无具体场景）

**P2（补强，仅 `--full` 模式启用）**：
6. **信任锚**：大客户 / 真实推荐 / 性能数据 / 用户量
7. **双语策略 + 国内特有元素**（按 SCAN 检测中文优先时）

**条件附加问（与上面池子合并计数，不另算）**：
- 检测到中文项目 → 国内元素问题归为 7
- 检测到 Cloud/Enterprise 文件夹 → 询问商业版描述（替换 P1 中的某一题）
- 检测到现有 README > 200 行 → 询问是 `--rewrite` 还是 `--patch`（这是流程问题，**应在阶段 1 SCAN 末尾就问**，不占 INTERVIEW 配额）

#### 2.3 提问规范

- **批量提问**：用 AskUserQuestion 一次性问完所有命中的问题，不要逐个对话式来回
- AskUserQuestion 不可用时，在 chat 中按编号列出，让用户一条回复回答多个
- 每问标 type：`single-select` / `multi-select` / `free-text` / `inspiration`
- 每个 single/multi-select 问题**必须提供"全用默认"选项**——用户随时可以中途让 Skill 跳过剩余
- 用户答案 → 模板变量映射见 `references/answer-to-template-map.md`

#### 2.4 默认值后备（用户跳过访谈或某题时如何兜底）

当用户选"全用默认"或具体某题没答：
- 一句话定位 → 用项目目录名 + 自动从 manifest description 抽取
- 目标用户 → 按项目类型默认（CLI 工具 → "需要 X 的开发者"；SaaS → "需要 X 的团队"）
- 主路径行动 → 按项目类型默认（CLI → install；SaaS → try demo / sign up；library → npm install + 第一个 example）
- 差异化 → 留空，章节不渲染
- 信任锚 → 留空，章节不渲染（条件渲染规则会自动跳过）

**所有走默认值的字段在 REVIEW 阶段必须高亮**（用 ⚠️ 标），让用户决定是否定稿。

### 阶段 3：ARCHETYPE（自动决策 + 用户确认）

读 `references/archetypes.md`。**Skill 主动给出推荐**，不让用户从 5 个里盲选。

**自动决策器**（基于 SCAN + INTERVIEW）：

```
信号优先级（从高到低，命中即定）：

1. 用户答案含强对手名（Chrome / VSCode / Notion / Slack 等）+ 提供了真实 testimonial
   → 强烈建议 E（第三方背书优先型）

2. 入口形态 = AI/Model OR 用户答案含"agent / LLM / 全新概念"
   → D（新品类教育型），可选借 B 的架构图

3. 入口形态 = 基础设施类（DB / BaaS / 部署 / 监控 / API gateway / 自托管平台）
   → B（基础设施/平台型）

4. 入口形态 = Desktop / Mobile / 创作者工具（视频/音频/写作/白板）
   → C（消费/创作者工具型）

5. 入口形态 = Web app / SaaS：
   - 强调 self-host → B
   - 强调即开即用 + 终端用户 → C
   - 默认 → C（用户后续可改）

6. 入口形态 = CLI / SDK / Library / IDE 插件 / DevTool
   → A（开发者工具型）— 默认兜底

7. 项目仅有几十 stars + 单人维护 → 自动加上 "minimal-asset 模式"（见阶段 4.6）
```

**⛔ BLOCKING — 用户确认环节**：
- 给推荐 archetype 一句话理由
- 列出"section 顺序方案"（具体到当前项目，不是模板抽象）
- 让用户确认 / 改 archetype / 调整 section 顺序

不通过 = 不进入 DRAFT。避免错落 archetype 后整份 README 失败。

**Section 拼装契约**：
- archetype 决定**主框架**（hero 套路 + 必出 section + 排序）
- 用户可在 review 时插入其他 archetype 的 section（如 A 型加 D 的 architecture mermaid）
- 拼装规则：所有 section 模板从 `references/section-library.md` 拉，archetype 只是"建议组合"

### 阶段 4：DRAFT（生成 README）

#### 4.1 Hero 区（黄金 5 秒，硬约束）

- 居中 logo（占位 `assets/logo.svg`，明暗双版本用 `<picture>`）
- H1 = 项目名（与仓库名一致）
- Tagline 紧跟 H1（**约束**：中文 ≤30 汉字 / 英文 ≤120 字符；按 `references/tagline-formulas.md` 6 套路之一）
- Badge 行（≤6 枚：version / license / build / downloads / discord / 1 个 archetype 特定）
- 顶部一行 nav（Docs · Demo · Discord · 语言切换）
- 紧跟 1 张 hero 视觉（screenshot / GIF / video thumbnail，**留占位符 + 在图片任务清单标注**）
- 1 段 ≤30 汉字的"What is X" 定义
- 1 行 install/quickstart 命令

#### 4.2 中段（Why / Features / How）

- 每个 feature 必须配**证据载体**（按优先级）：可交互 demo > GIF > 截图占位 > 代码片段 > benchmark 数字 > before/after
- emoji bullet 或 ✅ checkbox 任选其一，**统一全篇**（不可混用）
- 每段第一句即结论
- 一种主推安装方式 + 其他方式折叠（`<details>`）
- archetype 决定本段呈现形式（A/D 用 emoji bullet，B 用 checkbox，C 用网格图，E 用引言墙）

#### 4.3 信任 + 社区段（条件渲染）

| Section | 渲染条件 |
|---|---|
| Adopters logo 墙 | 用户提供了 ≥3 个真实 adopters |
| Testimonials | 用户提供了 ≥2 条真实引言（含人名 + title） |
| Star History | 项目 ≥1k stars（用户答 Q6 信号 / 现有 README 透露） |
| Contributors 头像墙 | 项目 ≥10 contributors（粗略：commit author 数采样） |
| Sponsors | 用户明确说有 OpenCollective / GitHub Sponsors |
| 国内社群（微信/飞书 QR） | SCAN 检测中文优先 + 用户在 INTERVIEW 确认 |

**不满足条件的 section 不渲染**——避免"50 stars 项目放 Star History 反成显穷"。

#### 4.4 收尾段

- Contributing 一段话 + 链 `CONTRIBUTING.md`（如不存在则提示用户创建）
- Security policy 链（如有）
- License 一行（**SCAN 已检测**：LICENSE 不存在 → 不写 broken link，改写"License: TBD（建议补 LICENSE 文件）"提示用户）

#### 4.5 双语处理

默认 **M1：中文优先双文件**（详见 `references/bilingual-patterns.md`）：
- `README.md` = 中文版
- `README_en.md` = 英文版
- 语言切换**只放一处**（**反冗余硬规则**）：
  - 优先方案：在 hero nav 行内嵌 `[English](README_en.md)` / `[中文](README.md)`——最克制，不占首屏纵向空间
  - 仅当项目无 nav 行时，才在文件最顶部加 lang badge 切换条
  - **禁止同时存在**顶部 lang badge + nav 行语言链接（这是占首屏空间的冗余信息）
- silent fail 修复：当前语言的链接/badge **不是链接**（避免点了刷新本页的死循环）
- 单语模式（`--zh-only` / `--en-only`）**不放切换条**

详细决策表与模板见 `references/bilingual-patterns.md`。

**双语生成对称约束**：
- 中英版 sections 1:1 对应（不能英文版多 3 节、中文版只有 5 节）
- 中文版不是机翻——按中文表达习惯重写文案
- 中英版各自配本地化截图（如 UI 有双语）

#### 4.6 最小素材模式（minimal-asset）

**触发条件**：项目 stars < 100 / 无 logo / 无截图 / 单人维护 / 第一次写 README

**降级策略**：
- Hero 视觉用**代码块 input/output 对照**代替 GIF——**严格约束**：
  - **真实性硬规则**：必须是项目真实可跑的命令 + 真实输出。不准虚构、不准伪装"假装是 CLI 输出"
  - **行数硬上限**：≤ 6 行（含命令行）。超过 6 行 = 不再是"hero 视觉"，是另一节
  - **禁止形态**：emoji + 框线流程图、伪装成多阶段 pipeline 的装饰块、"用户回答 / 系统回应"对话模拟、所有非真实交互的"演示"
  - 标准例子：
    ```
    $ foo run example.txt
    ✓ Processed 1.2k tokens
    ✓ Output saved to result.json
    ```
  - **如果项目根本没有真实简短可演示的命令** → 直接省略 hero 视觉块，不要硬凑。空着也比塞装饰物好
- Logo 不强求，可省略（保留 H1 即可）
- Badges 减到 3 枚（license + version + ci）
- 不渲染 Adopters / Testimonials / Star History / Contributors（条件不满足）
- `image-plan.md` 全部标 `priority: nice-to-have`，不让用户被 TODO 吓跑

#### 4.7 图片任务清单

生成 `docs/readme-image-plan.md`（见 `references/image-plan.md`）：
- 每张图占位符对应一条任务（路径 + 用途 + 建议尺寸 + 制作方式）
- 标 `priority: must / should / nice-to-have`
- 占位符在 README 中用 placeholder 服务：**统一用 `https://placehold.co/`**（via.placeholder.com 已停服，禁用）
- 自动生成的（mermaid / star-history / contrib.rocks）直接给方案，不让用户做

#### 4.8 输出卫生（生成阶段强制检查，**不可跳过**）

生成的 README 是给**所有读者**看的，不是给当前用户看的。任何**与当前 user 个人相关**的本地信息都禁止出现在生成内容中。

**强制黑名单——绝对禁止出现在生成的 README / 模板 / 示例中**：

| 禁止内容 | 例子 | 替换为 |
|---|---|---|
| 真实 home 目录名 | `/Users/jvever/...`、`/home/alice/...`、`C:\Users\bob\...` | `~/...` 或更通用的占位 |
| 当前用户的个人代码目录名 | `~/Code/18-My_Skills/`、`~/work/`、`~/Projects/MyStuff/` | `<your-code-dir>/`、`~/projects/` 这类**通用、读者也能识别**的路径 |
| 当前 git 用户名 / email | `git config user.name`、`user.email` | 不出现，或用 `<your-name>` |
| 当前机器/SSH 配置细节 | hostname、私有 SSH host alias | 不出现 |
| 当前用户的 GitHub owner（除非项目本身的 owner） | 用户的私人 fork URL | 用 `<owner>/<repo>` 或项目实际 owner |

**生成阶段的强制检查**：
- DRAFT 完成后、进入反模式自检前，先用正则扫描所有生成文件：
  - `/Users/[^/]+/`、`/home/[^/]+/`、`C:\\Users\\[^\\]+\\`
  - `~/[A-Z][a-zA-Z]*/[0-9]+-` 这类带数字前缀目录的形态（典型个人代码目录组织）
- 命中任一项 → **不进入 REVIEW，自动回到 DRAFT 修复**
- 修复策略：
  - 安装/克隆命令：`~/.claude/skills/<name>` 或 `~/projects/<name>` 或 `<your-code-dir>/<name>`
  - 任何路径里出现"看起来像个人组织习惯"的目录名（如 `18-xxx`、`my_*`、`work/`）→ 删除该层，给最简通用路径

**问"用户想把项目放哪"是反模式**——不要在 INTERVIEW 阶段问安装路径。安装路径只能用通用占位符（`~/.claude/skills/...` 或 `<your-code-dir>/...`），不要"为了准确"去问用户。

**例外**：项目自身的目录结构展示（如"项目结构"那段）只能用项目仓库相对名（`jvs-readme-designer/`），**禁止**用用户本地的绝对/家目录路径。

#### 4.9 反模式自检（自动循环 ≤2 轮）

生成草稿后，对照 `references/anti-patterns.md` 跑 checklist。

**自动可修类**（直接修，不打扰用户）：
- emoji 滥用（标题里的 emoji 删掉，feature bullet 前缀保留）
- HTML 滥用（删多余的 `<div>` 包裹）
- 占位符语法错（统一 `{{var}}`）
- 链接格式错
- License broken link（改成 "License: TBD"）

**必须升级到 REVIEW 类**（在自检报告里列出，让用户决定）：
- 形容词堆砌但 INTERVIEW 没拿到证据 → 标 ⚠️ "缺证据"
- Stale 命令（无法判断）→ 标 ⚠️ "请人工确认"
- Tagline 不够吸引人（主观）→ 列 2 个 alternative 让用户选

**循环上限**：自动循环 ≤ 2 轮；2 轮后剩余问题强制升级到 REVIEW。

### 阶段 5：⛔ REVIEW（人工 review + 迭代）

把 README 草稿展示给用户，列出：
- ✅ 已自动修复的问题（一行一项）
- ⚠️ 升级 review 的问题（带建议选项）
- ❓ 主观决策点（tagline 终选 / 排序调整）

让用户回答：
- 哪一段最打动你？哪一段你想删？
- 哪个 claim 你觉得没有足够证据？
- 哪个 section 顺序你想调？
- 图片任务清单里有哪些做不到的？是否换方案？

**迭代 1-2 轮**。**不要用户没说就主动改**（避免 over-engineering）。

最后输出 reminder：

> 已生成 README 与图片任务清单。建议下次 release 跑 `/jvs-readme-designer --rewrite` 保持鲜活——README 是活的产品页，半年不更新会显死。

---

## --rewrite 模式专用流程

`--rewrite` 不是从头重写，而是 **三段处理**：

1. **保留区**（不动）：用户的原创金句（含数字 / testimonial 原文 / 真实场景描述 / 已得到反馈良好的段落）
2. **重写区**（改）：形容词堆砌段、stale 段（命令 / 链接 / 版本号）、不符合当前 archetype 的段
3. **补漏区**（加）：当前缺失的必要 section（hero 不全 / 没有 quickstart / 缺 license 等）

**输出方式**：先给"diff 报告"（保留 X 段、重写 Y 段、补 Z 段），用户批准后再生成新 README。**不黑箱重写**。

---

## --patch 模式专用流程

`--patch` 是最轻量的差量改动：
- 只接受用户指定的具体诉求（"加 hero / 改 tagline / 补 trust signals"）
- 不动其他 section
- 不启动 INTERVIEW（除非缺关键信息）
- 适合用户对现有 README 已基本满意，只想补窟窿

---

## 输出文件清单

| 文件 | 内容 | 必出 |
|---|---|---|
| `README.md` | 中文版 README | ✅（除非 `--en-only`） |
| `README_en.md` | 英文版 README | ✅（除非 `--zh-only`） |
| `docs/readme-image-plan.md` | 图片/视觉资产任务清单 | ✅（除非 `--no-images`） |
| `assets/.gitkeep` | 占位目录（如不存在） | 按需 |

---

## 引用资源

`references/` 目录：
- `principles.md` — 7 条核心设计原则（自检 checklist 的 single source of truth）
- `interview-questions.md` — 访谈问题（quick / full / 附加）
- `answer-to-template-map.md` — INTERVIEW 答案 → 模板变量映射表
- `archetypes.md` — 5 种 archetype 详解 + 决策树
- `tagline-formulas.md` — 6 种 tagline 套路
- `section-library.md` — section 模板库（**唯一真理源**）
- `trust-signals.md` — 14 种信任信号 + 模板
- `bilingual-patterns.md` — 4 种双语模式
- `image-plan.md` — 图片任务清单生成规则
- `anti-patterns.md` — 反模式 checklist
- `domestic-elements.md` — 中文社区特有元素
- `scope-out.md` — 不该用本 Skill 的场景
- `templates/` — 5 种 archetype 骨架（中英双版）

---

## 与其他 Skill 的协作

- **不替代** `/builder` `/pm` `/cto` `/designer`：本 Skill 只管 README，不动代码或 spec
- **可被 /builder 调用**：feature 接近 release 时，Builder 可建议跑本 Skill 更新门面
- **可被 /designer 调用**：Designer 处理 "外部表面"（gui/cli/api/lib）时，README 这一表面路由到本 Skill

---

## 维护提醒

每次 release / 每 3 个月 / star 数翻倍 时，跑一遍 `--rewrite` 或 `--patch`。README 不维护就会死——这是最强的"项目还活着"信号。
