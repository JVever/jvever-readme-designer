---
name: jvever-readme-designer
description: Interview-driven, marketing-grade README designer for code projects (open-source or internal). Treats README as a landing page with hero, archetype-aware sections, trust signals, bilingual output, and an image task plan — not a doc dump. 中文触发：写/重写/重做/重做一遍/美化/设计/双语/中英 README、GitHub 门面、GitHub 项目首页、项目 landing page、开源发布前/项目宣传/项目门面、README 太烂/太朴素/太简陋/没人看/像广告。English triggers：write/rewrite/redesign/polish/beautify/improve/craft README, bilingual or zh+en README, GitHub front page, open-source launch README, project landing page on GitHub, README too plain/no one reads my README. Skill 默认读项目代码自己做决策；只在真正不能从代码推断、且会显著影响生成质量时追问，且只问倾向/客观未知/风险确认 3 类——绝不把设计决策（tagline 套路 / section 顺序 / archetype 选型 / 卖点排序）抛给用户。Supports `--quick` / `--full`（控制追问宽容度），`--rewrite`（保留金句改弱段）和 `--patch`（只补窟窿）。
---

<!--
@input:    用户的项目目录（代码、manifest 文件、现有 README、assets/ 等）+ 用户在追问阶段的回答（可能为 0 个）
@output:   README.md（中文）+ README_en.md（英文，可选）+ docs/readme-image-plan.md（图片任务清单）+ assets/.gitkeep（占位）
@rule:     如本文件 @input 或 @output 发生变化，必须更新本注释并检查 _INDEX.md
-->

# /jvever-readme-designer — 像产品官网那样设计 README

把开源项目的 README 当作 **landing page** 而非文档来设计。它的 KPI 是 **conversion**（star、install、第一个 PR），不是 completeness。

> `jvever` 是作者前缀（namespace），用户**不需要输入 jvever 来触发**——通过描述意图即可命中。

## 核心信念

1. **首屏定生死** — 5 秒内必须答清"做什么 / 给谁 / 怎么开始"
2. **Show, don't tell** — 每一个 claim 必须有证据（demo / GIF / benchmark / 代码 / 真实用例）
3. **Archetype 驱动** — 不同产品类型有不同 README 结构，不一刀切
4. **信任信号系统化** — badges + adopters + 最近 release + 真实截图共同证明"项目活着、社区健康"
5. **克制比繁复更显高级** — 反对滥用 emoji / 居中 HTML / 动态 SVG / TOC 在短 README 里
6. **Skill 替用户做决策** — 设计决策（tagline 套路 / archetype / section 顺序 / 卖点 / 视觉形态）是 Skill 的活，不是用户的负担

---

## 调用方式与模式（三维正交）

参数分三个独立维度，可任意组合：

| 维度 | 选项 | 默认 |
|---|---|---|
| **流程** | `--quick`（默认；模型只在真有缺口时追问，多数情况 0 问题） / `--full`（追问宽容度更高，倾向类问题更全） / `--rewrite`（重写已有 README） / `--patch`（只补缺失） | `--quick` |
| **输出语言** | `--bilingual`（中英双版） / `--en-only` / `--zh-only` | `--bilingual` |
| **图片任务清单** | `--with-images` / `--no-images` | `--with-images` |

示例：
```
/jvever-readme-designer                          # quick + bilingual + with-images
/jvever-readme-designer --full                   # full + bilingual + with-images
/jvever-readme-designer --rewrite --en-only      # 重写已有，输出仅英文
/jvever-readme-designer --patch --zh-only        # 仅补丁中文 README
```

> **流程维度互斥**（quick / full / rewrite / patch 四选一），其他两维度可与任一流程组合。

**默认输出**：`README.md`（中文）+ `README_en.md`（英文）+ `docs/readme-image-plan.md`。

> **持久化偏好**：用户可通过 `EXTEND.md` 设置默认值（如永远默认 `--full`，或永远 `--zh-only`），见仓库根的 `EXTEND.md` 模板。

---

## 什么时候 *不* 用本 Skill

| 场景 | 推荐做法 |
|---|---|
| 改一行错字 / 修一个链接 | 直接 Edit，不用 Skill |
| 项目没有任何代码（纯 dotfiles / awesome-list） | 用普通 markdown 编辑，本 Skill 假设有 software 可介绍 |
| README 是别人的项目（你不维护） | 不要跑——你不该重写别人的门面 |
| 想生成 CHANGELOG / API docs / wiki | 这些不是 README 范畴；用对应工具 |
| 项目只供个人 reference（不公开） | 个人 README 不需要营销，用最简结构即可 |

---

## 工作流程（3 阶段，1 个 BLOCKING）

```
READ+DECIDE → DRAFT → ⛔ REVIEW
```

**核心哲学**：

- Skill 替用户**做决策**——不是把决策抛回给用户
- 用户的工作只有最后一步：**审稿**
- 中间过程可能 **0 个**、最多 **3 个**追问，且**只能问 3 类问题**（见 §1.3）
- 唯一 BLOCKING 是 REVIEW——前面的步骤静默自动完成
- **绝不**问"你愿意答几个问题"这种 meta 问题——模型自己按缺口决定问几个

### 阶段 1：READ+DECIDE（自动）

#### 1.1 扫描

**硬约束**：
- **只读本地文件**，不调用 GitHub API、不假设有网络
- **禁止臆造数字**（stars / downloads / last release date 等用 shields.io 自动 URL 在渲染时拉取）
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
   - **Claude Code Skill / Prompt 包**：根目录或 `skills/<name>/` 下有 `SKILL.md`（含 frontmatter `name:` `description:`）
   - **Docs / Awesome / Config 仓库**（无可执行入口）：触发"零代码 fallback"提示，建议用户改用普通 markdown
   - **Monorepo**：根 `package.json` 含 `workspaces` / `pnpm-workspace.yaml` / `turbo.json` / `lerna.json` / `nx.json` → 追问"为根 README 还是子包 README 设计"（属于 1.3 客观未知，可问）

3. **现有视觉资产**：`assets/` / `docs/img/` / `docs/images/` / `.github/assets/` / `media/` / `images/` 下的图片文件

4. **现有 README**（如有）：标题 / 长度 / 是否双语 / 最后修改时间 / 明显金句（含数字 / testimonial / benchmark / use case）

5. **trust signals 现状**：`.github/workflows/` / `LICENSE` / `LICENSE.md` / `CHANGELOG.md` / `SECURITY.md` / `CONTRIBUTING.md` / `CODE_OF_CONDUCT.md`

6. **i18n 信号**：是否已有 `README_en.md` / `README.zh-CN.md` / `i18n/` / `docs/zh/`

7. **语种信号**：现有 README 主体语言（看前 100 字符 cjk 比例） / manifest description 字段语种 / commit message 采样

8. **生态位粗略信号**：现有 README 是否提到大客户 / 名人引言 / benchmark 数字 / 强对手对标（"alternative to X"）/ commit 数（>500 commit 视为成熟）

9. **是否已是本 Skill 输出**（避免 dogfooding 重写）：检测 `docs/readme-image-plan.md` 是否存在 + `README.md` 末尾是否含本 Skill 的 maintenance reminder。若是 → **建议默认改用 `--patch`**，避免把已经合规的产物再走一遍 `--quick`/`--full` 重写。

#### 1.2 自动决策（**不问用户**）

基于 1.1 扫描结果，**直接决策**以下事项——这些是 Skill 的活，**绝不**抛回给用户：

| 事项 | 决策依据 |
|---|---|
| **Archetype（A/B/C/D/E）** | 决策器（详见 [`references/archetypes.md`](references/archetypes.md)）按入口形态 + 现有 README 信号选；E 型有门槛，不达标自动回落 A |
| **双语策略（M1/M2/M3/M4）** | 主语种推断；中文项目默认 M1，英文项目默认 M2，5+ 语言或已有 i18n 目录默认 M3 |
| **minimal-asset 模式触发** | 无 logo / 无截图 / 单人维护 / commit 数较少 → 触发 |
| **Tagline 套路** | 按 archetype 默认套路（见 [`tagline-formulas.md`](references/tagline-formulas.md)） + 现有 README 第一段调性 |
| **Section 顺序** | 按 archetype 决定的骨架（见 archetypes.md），section 模板从 [`section-library.md`](references/section-library.md) 拉 |
| **Hero 视觉形态** | minimal-asset → 真实命令演示 ≤6 行；否则按 archetype 默认（GIF / 大截图 / 视频缩略图） |
| **Feature 呈现形式** | A/D 用 emoji bullet，B 用 checkbox，C 用卡片网格，E 用引言墙 |
| **Trust signal 渲染** | 按 [`trust-signals.md`](references/trust-signals.md) 条件渲染表自动判定 |
| **Badge 组合** | 按 archetype 推荐组合 + 实际可用的 trust signal |
| **国内特有元素** | 主语种为中文 + 用户没显式说"国际化为主" → 启用相关 section（条件渲染） |

#### 1.3 缺口判定与可选追问

扫描完毕后，模型评估：**还有什么不能从代码推断、又会显著影响生成质量的"关键未知"？**

- **0 个未知** → 直接进入 DRAFT，**不问任何问题**（多数项目应当如此）
- **1-3 个未知** → 一次性追问（一轮发完，**绝不**分多轮）
- **≥4 个未知** → 取最关键 3 个问，其他走默认/推断

模型自己决定问几个——**绝不**问用户"你愿意答几个问题"这种 meta 问题。

##### 追问硬规则

**只能问 3 类问题**：

| 类别 | 例子 | 判断标准 |
|---|---|---|
| **客观未知** | License 选哪个？是否真有可贴的大客户名单 / testimonial？monorepo 为根还是子包写？ | 不能从代码推断的事实 |
| **主观倾向** | 项目调性偏严肃专业还是有人情味？聚焦中国市场还是国际？技术口径还是业务口径？ | 用户偏好 / 项目气质 |
| **风险确认** | "我推断你的目标用户是 X，对吗？" "我看到 manifest description 写的 Y，作为一句话定位 OK 吗？" | 模型不确定的关键推断 |

**绝不允许问的（这些是 Skill 的活）**：

- ❌ Tagline 套路（品类定义型 / 结果承诺型 / 拟人型 ……）
- ❌ Section 顺序怎么排 / "section 顺序方案 OK 吗？"
- ❌ Why X 段突出哪些卖点
- ❌ Hero 视觉用什么形态
- ❌ Feature 段用 emoji bullet 还是 checkbox
- ❌ Badge 选哪几枚
- ❌ Archetype 选哪个（应自动决策）
- ❌ 任何形如"你觉得 A 好还是 B 好"的设计选项题

**判断方法**：把问题在心里读一遍——
- 答案是 **"用户的事实/偏好"** → 可以问
- 答案是 **"设计或方法论的选择"** → 不能问，Skill 自己决定

##### 提问的形式

- 一次性发出（AskUserQuestion 一次，至多 3 个 question）
- 每个 single/multi-select **必须含"全用默认 / 不知道"选项**——用户随时可全跳过
- 用户跳过 → 走推断/默认值，REVIEW 阶段以 ⚠️ 标记让用户最终判断
- **不要追问"还有别的吗"**——一次问完就走

#### 1.4 兜底默认值

未问到的字段：
- **能从项目推断**的（一句话定位 / 目标用户 / 主 CTA / 双语策略 / archetype）→ 用推断值
- **属于条件渲染**的（信任锚 / 差异化 / 国内元素）→ 留空，对应 section 不渲染（详见 [`trust-signals.md`](references/trust-signals.md)）
- **EXTEND.md 已设默认**的 → 用 EXTEND 值

走默认值的字段在 REVIEW 阶段以 ⚠️ 标记。

#### 1.5 信息播报（**不阻塞**）

完成 1.1-1.4 后，向用户**播报**画像和决策——这是信息共享，**不等用户确认**：

```
项目画像（本地扫描，未联网）：
- 名称：foo
- 类型：CLI 工具（Node.js · TypeScript）
- 现有 README：缺失 / 70 行 / 单语英文
- 视觉资产：assets/logo.svg ✅, 截图 ❌
- Trust signals：✅ LICENSE  ✅ CI  ❌ CHANGELOG
- 主语种：英文（commits）/ 中文（README description）

自动决策：
- Archetype：A（开发者工具型 / CLI）
- 双语：M1（中文优先 + 英文版）
- 模式：minimal-asset

继续生成（如需调整请打断）。
```

如有追问，**信息播报和追问在同一轮发出**（不要先播报、再等用户确认、再问追问——只一次往返）。播报放在 AskUserQuestion 之前的文字消息里，追问通过 AskUserQuestion 紧接发出。

> 让用户**有打断的权利**，但不要让用户**承担确认的义务**。

#### SCAN 失败的 fallback

- **无 manifest**：追问"项目类型是？"（CLI / library / web app / docs / 其他）—— 客观未知，可问
- **mirror 仓库**：追问主仓库 owner/repo —— 客观未知，可问
- **私有仓库**：跳过 shields.io / contrib.rocks / star-history（这些只对公开仓库工作），改用纯文字状态——自动处理，**不问**

### 阶段 2：DRAFT（自动生成）

#### 2.1 Hero 区（黄金 5 秒，硬约束）

- 居中 logo（占位 `assets/logo.svg`，明暗双版本用 `<picture>`；minimal-asset 模式可省略）
- H1 = 项目名（与仓库名一致）
- Tagline 紧跟 H1（**约束**：中文 ≤30 汉字 / 英文 ≤120 字符；按 [`tagline-formulas.md`](references/tagline-formulas.md) 6 套路之一，由 1.2 自动选定）
- Badge 行（≤6 枚：version / license / build / downloads / discord / 1 个 archetype 特定）
- 顶部一行 nav（Docs · Demo · Discord · 语言切换）
- 紧跟 1 张 hero 视觉（screenshot / GIF / video thumbnail，**留占位符 + 在图片任务清单标注**）
- 1 段 ≤30 汉字的"What is X" 定义
- 1 行 install/quickstart 命令

#### 2.2 中段（Why / Features / How）

- 每个 feature 必须配**证据载体**（按优先级）：可交互 demo > GIF > 截图占位 > 代码片段 > benchmark 数字 > before/after
- emoji bullet 或 ✅ checkbox 任选其一，**统一全篇**（不可混用）
- 每段第一句即结论
- 一种主推安装方式 + 其他方式折叠（`<details>`）
- archetype 决定本段呈现形式（A/D 用 emoji bullet，B 用 checkbox，C 用网格图，E 用引言墙）

#### 2.3 信任 + 社区段（条件渲染）

| Section | 渲染条件 |
|---|---|
| Adopters logo 墙 | 用户提供了 ≥3 个真实 adopters |
| Testimonials | 用户提供了 ≥2 条真实引言（含人名 + title） |
| Star History | 项目 ≥1k stars |
| Contributors 头像墙 | 项目 ≥10 contributors |
| Sponsors | 用户明确说有 OpenCollective / GitHub Sponsors |
| 国内社群（微信/飞书 QR） | SCAN 检测中文优先 + 用户提供二维码 |

**不满足条件的 section 不渲染**——避免"50 stars 项目放 Star History 反成显穷"。

#### 2.4 收尾段

- Contributing 一段话 + 链 `CONTRIBUTING.md`（如不存在则在 image-plan 中提示用户创建）
- Security policy 链（如有）
- License 一行（**SCAN 已检测**：LICENSE 不存在 → 不写 broken link，改写"License: TBD（建议补 LICENSE 文件）"）

#### 2.5 双语处理

默认 **M1：中文优先双文件**（详见 [`bilingual-patterns.md`](references/bilingual-patterns.md)）：
- `README.md` = 中文版
- `README_en.md` = 英文版
- 语言切换**只放一处**（**反冗余硬规则**）：
  - 优先方案：在 hero nav 行内嵌 `[English](README_en.md)` / `[中文](README.md)`——最克制
  - 仅当项目无 nav 行时，才在文件最顶部加 lang badge 切换条
  - **禁止同时存在**顶部 lang badge + nav 行语言链接
- silent fail 修复：当前语言的链接/badge **不是链接**（避免点了刷新本页的死循环）
- 单语模式（`--zh-only` / `--en-only`）**不放切换条**

**双语生成对称约束**：
- 中英版 sections 1:1 对应
- 中文版不是机翻——按中文表达习惯重写文案
- 中英版各自配本地化截图（如 UI 有双语）

#### 2.6 最小素材模式（minimal-asset）

**触发条件**（在 1.2 自动决策）：项目极早期 / 无 logo / 无截图 / 单人维护 / 第一次写 README

**降级策略**：
- Hero 视觉用**代码块 input/output 对照**代替 GIF——**严格约束**：
  - **真实性硬规则**：必须是项目真实可跑的命令 + 真实输出。不准虚构、不准伪装"假装是 CLI 输出"
  - **行数硬上限**：≤ 6 行（含命令行）
  - **禁止形态**：emoji + 框线流程图、伪装成多阶段 pipeline 的装饰块、"用户回答 / 系统回应"对话模拟
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

#### 2.7 图片任务清单

生成 `docs/readme-image-plan.md`（见 [`image-plan.md`](references/image-plan.md)）：
- 每张图占位符对应一条任务（路径 + 用途 + 建议尺寸 + 制作方式）
- 标 `priority: must / should / nice-to-have`
- 占位符在 README 中用 placeholder 服务：**统一用 `https://placehold.co/`**（via.placeholder.com 已停服，禁用）
- 自动生成的（mermaid / star-history / contrib.rocks）直接给方案，不让用户做

#### 2.8 DRAFT 自检（两层：先机械、后主观）

DRAFT 完成后必须跑两层自检，**全部通过**才能进入 REVIEW。

**第一层：机械检测（强制，不可跳过）** — 见 [`auto-checks.md`](references/auto-checks.md)

涵盖：路径泄露 / License 链接 / 占位图服务 / 占位符未替换 / 装饰 ASCII 超长 / 标题 emoji / 双语切换条规则 / 模式一致性 等。每项有明确 regex 或字符串模式 → 命中 = 失败 → 自动修或阻断进入 REVIEW。

**第二层：主观原则自检** — 见 [`principles.md`](references/principles.md) 5 条原则

| 原则 | 自检问 |
|---|---|
| 1. 首屏定生死 | Hero 区 5 秒能答清三问吗？没有装饰物喧宾夺主吗？ |
| 2. 基于 Job 而非 feature 列表 | 写的是用户 job/痛点，还是 feature dump？倒金字塔顺序对吗？ |
| 3. Show, don't tell | 每个 claim 配证据了吗？形容词都兜底了吗？ |
| 4. 克制即专业 | 每个元素能回答"删了读者损失什么"吗？冗余/装饰/低频英文有吗？ |
| 5. 信任信号 + 鲜活 | 信号有 ≥3 个吗？没用条件渲染过滤吗？命令鲜活吗？ |

**分流**：
- 自动可修（emoji 满天飞、多余 div、装饰 ASCII、低频英文、broken link）→ **直接修**，记入"已自动修复"
- 主观判断需要用户拿主意（如"tagline 不够吸引"）→ **暂存到 REVIEW 阶段**作为 ⚠️ 提示，**不在 DRAFT 阶段问用户**

**循环上限**：自动修循环 ≤ 2 轮；2 轮后剩余强制升级 REVIEW。

### 阶段 3：⛔ REVIEW（用户审稿，唯一 BLOCKING）

直接展示 3 份草稿：`README.md` / `README_en.md` / `docs/readme-image-plan.md`。

**REVIEW 是用户审稿，不是问卷**：
- 列**已自动修复**的问题（一行一项，让用户知道做了什么）
- 标 ⚠️ **走默认值/推断值**的字段（让用户知道哪里需要他确认）
- **不再列"主观决策点让用户选"**——这些 Skill 已经做了决策；用户如有意见，自然会在审稿时指出

**用户的回应空间**（不强制）：
- 看到不对劲的，直接说"那个 X 改成 Y"
- 看到 ⚠️ 字段，决定接受还是改
- 全 OK → 一句"OK"或"发布"即可结束

**不要追问"你还有别的意见吗"**——用户没说就是没意见。

按用户的具体反馈迭代 1-2 轮。**不要用户没说就主动改**（避免 over-engineering）。

最后输出 reminder：

> 已生成 README 与图片任务清单。建议下次 release 跑 `/jvever-readme-designer --rewrite` 保持鲜活——README 是活的产品页，半年不更新会显死。

---

## --rewrite 模式专用流程

`--rewrite` 不是从头重写，而是 **三段处理**：

1. **保留区**（不动）：用户的原创金句（含数字 / testimonial 原文 / 真实场景描述 / 已得到反馈良好的段落）
2. **重写区**（改）：形容词堆砌段、stale 段（命令 / 链接 / 版本号）、不符合当前 archetype 的段
3. **补漏区**（加）：当前缺失的必要 section（hero 不全 / 没有 quickstart / 缺 license 等）

**输出方式**：先在 REVIEW 阶段给"diff 报告"（保留 X 段、重写 Y 段、补 Z 段），用户批准后再生成新 README。**不黑箱重写**。

---

## --patch 模式专用流程

`--patch` 是最轻量的差量改动：
- 只接受用户指定的具体诉求（"加 hero / 改 tagline / 补 trust signals"）
- 不动其他 section
- 跳过 §1.3 追问（除非用户的诉求本身就含未知）
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

**核心信仰层**：
- `principles.md` — **5 条核心原则**（所有主观设计判断的唯一来源）
- `auto-checks.md` — **机械检测清单**（DRAFT 阶段强制运行的 lint）

**执行层**：
- `archetypes.md` — 5 种 archetype 详解 + 决策器 + section 拼装契约
- `tagline-formulas.md` — 6 种 tagline 套路
- `section-library.md` — section 模板库（**唯一真理源**，所有 archetype 拼装时从这里取）
- `trust-signals.md` — 信任信号清单 + 条件渲染规则
- `bilingual-patterns.md` — 双语模式
- `image-plan.md` — 图片任务清单生成规则

---

## 与其他 Skill 的协作

- **不替代** `/builder` `/pm` `/cto` `/designer`：本 Skill 只管 README，不动代码或 spec
- **可被 /builder 调用**：feature 接近 release 时，Builder 可建议跑本 Skill 更新门面
- **可被 /designer 调用**：Designer 处理 "外部表面"（gui/cli/api/lib）时，README 这一表面路由到本 Skill

---

## 维护提醒

每次 release / 每 3 个月 / star 数翻倍 时，跑一遍 `--rewrite` 或 `--patch`。README 不维护就会死——这是最强的"项目还活着"信号。
