# 5 种 README Archetype

每种原型对应不同产品类型，决定 section 顺序和卖点呈现策略。SCAN + INTERVIEW 后，Skill 推荐 1 种，用户可改。

---

## A. 开发者工具型（Developer Tool）

### 适用
- CLI 工具
- SDK / 库
- IDE / 编辑器插件
- DevTools / 终端
- 开发者本地用的 GUI 工具

### Hero 套路
**品类定义型** + 多状态 UI 截图 / asciinema / 代码 diff

文案模板：
> X is the [新品类 or 老品类升级] for [开发者细分人群], built for [核心价值]

示例：
- "Linear is the product development system for teams and agents"
- "Bun is a fast all-in-one JavaScript runtime"

### Section 顺序（克制优先，钩子前置）

**默认骨架（5-7 段，不要更多）**：

1. **Hero**（logo + H1 + tagline + ≤3 枚 badge + nav）
2. **一句话定义** — 1 段，紧接 Hero 之后说"这是什么 / 你说一句它做什么 / 你只做什么"
3. **它能帮你做到 / Why X**（**4-6 emoji bullet × 每条 1-2 行**——这是钩子，必须在 Quickstart 之前）
4. **Quickstart**（1-3 行命令；其他模式折叠）
5. **License**

**条件渲染（仅满足条件才出）**：
- Adopters / Testimonials / Star History / Numbers / Contributors（按 trust-signals 阈值）
- Contributing 段（按 §14 邀请信号）
- 国内特有元素（按主语种为中文 + 用户确认）

**默认不生成的段（除非用户明确要求或有强信号）**：
- ❌ 项目结构 / 文件树 — GitHub 自带，重复
- ❌ "怎么做出来的" / 研究过程 / 设计理念 — 作者自嗨，不是 landing page 内容
- ❌ 维护提醒 / "每次 release 跑一遍 X" — 这是给已用户的 FAQ，应放在 SKILL.md 内部
- ❌ "什么时候不用本工具" — 防御性写作；用户决定要用时不会反问"我是不是用错场景"
- ❌ "How it works" 详细流程图 — 除非 archetype 是 D 新品类需要教育，A 型不需要
- ❌ 详细 architecture 图 — 除非 archetype 是 B 基础设施

**判定方法**：每个 ## 段过一道"删了这段，目标读者会损失什么具体能帮他做决策的信息？"——答不出 → 删整段。原则 4 克制即专业的硬应用。

### 关键武器
- 代码片段（show, don't tell）
- before/after diff
- 名人 testimonial
- benchmark 数字

### 代表项目
Cursor / Vercel / Warp / Linear / Bun / Aider / Continue

### 反例
AutoGPT（首屏先放 System Requirements，焦虑前置）

---

## B. 基础设施 / 平台型（Infrastructure / Platform）

### 适用
- 数据库 / DBaaS
- BaaS（Firebase 替代品）
- 云服务 / 部署平台
- API gateway / 中间件
- 监控 / 日志 / Observability

### Hero 套路
**结果承诺型** + 抽象/动态视觉 + 硬核数字

文案模板：
> Build [结果] in [时间]. Scale to [量级].

示例：
- "Supabase: Build in a weekend. Scale to millions."
- "Vercel: Build and deploy on the AI Cloud."

### Section 顺序
1. Hero（logo + tagline + 巨型 logo 墙）
2. **大客户 logo 墙**（紧跟 hero）
3. **硬核数字带**（uptime / QPS / 处理规模）
4. **Architecture 图**（嵌入 SVG）
5. **核心能力 ✅ checkbox 列表**
6. **Quick start**
7. **Self-host vs Cloud 决策表**
8. **Industry use cases**
9. **Documentation** 外链
10. **Contributing / License**

### 关键武器
- 大客户 logo 墙
- uptime / QPS 数字
- 架构图
- ✅ checkbox 能力清单
- Self-host vs Cloud 对比表

### 代表项目
Supabase / Stripe / PostHog / Appwrite

### 反例
README 全是营销话术、没有任何技术细节——基础设施型买家不吃这套。

---

## C. 消费 / 创作者工具型（Consumer / Creator Tool）

### 适用
- 桌面 app（Tauri / Electron）
- 视频 / 音频 / 图像 编辑工具
- 写作 / 笔记 / 白板工具
- 终端用户（含半技术）使用的应用

### Hero 套路
**身份共鸣型** + 强视觉（视频 / 大截图）

文案模板：
> For [某种自我认同 / 人群]
> Your shortcut to [核心价值]

示例：
- "Raycast: Your shortcut to everything"
- "Excalidraw: Virtual whiteboard for sketching hand-drawn like diagrams"

### Section 顺序
1. Hero（视觉占满首屏）
2. **Logo 墙**（如有，紧跟 hero）
3. **功能卡片网格**（10+ 张截图，每个 ≤2 句话）
4. **用例分人群**（"For Designers / For Teams / For Solo Devs"）
5. **Download / Install**（多平台并列）
6. **Pricing / 商业版**（如有）
7. **Community / Discord / Forum**
8. **License**

### 关键武器
- 高密度功能截图（10+ 张）
- 用例分人群
- 多平台下载矩阵
- 用户社区入口

### 代表项目
Raycast / Notion / Descript / Excalidraw / Folo

### 反例
只有文字没有截图——消费产品死刑。

---

## D. 新品类教育型（New Category Education）

### 适用
- LLM agent 框架
- 全新概念的开源项目
- 没有同类参照物的"我是什么"型项目

### Hero 套路
**拟人/隐喻型** + 教育性定义 + 视频 demo

文案模板：
> Meet [拟人化角色]. [它做什么]
> Like [熟悉事物] for [新场景].

示例：
- "Notion: Meet the night shift."
- "OpenHands: AI agents that work with you, not for you"

### Section 顺序
1. Hero（拟人定位 + 视频 demo）
2. **What is X**（详细定义，至少 1 段 + 1 个示意图）
3. **How it works**（架构图 + 数据流图）
4. **4-5 个 capability 模块**（每个 1 张图 + 1 段说明）
5. **Use cases / 试着这样用**
6. **Quick start**
7. **Comparison: Why not [现有方案]**
8. **Community**
9. **License**

### 关键武器
- 视频 demo（YouTube / Bilibili 嵌入缩略图）
- 拟人化叙事
- 架构图 / 数据流图
- "Why not X" 段直面对比

### 代表项目
Claude / OpenHands / AutoGen / LangChain

### 反例
LobeHub（968 行，TOC 反复折叠，信息密度低）——新品类不是"什么都说"，是"把核心概念说透"。

---

## E. 第三方背书优先型（Endorsement-First）

### 适用
- 已有强势对手的赛道（如新浏览器 vs Chrome、新 IDE vs VSCode）
- 项目还小，自夸信服力低，但有早期用户的好评
- 品牌型 / 社区驱动型项目

### Hero 套路
**第三方背书型**：用真实用户引言当 H1

文案模板：
> "[用户原话评价]" — [用户身份]

示例（Arc）：
> "Arc is the Chrome replacement I've been waiting for."
> — David Pierce, The Verge

### Section 顺序
1. Hero（用户原话当 H1 + 产品截图 + Twitter/X 出处）
2. **More testimonials**（第二屏放更多用户引言）
3. **Features 截图墙**
4. **Download**
5. **Community**
6. **License**

### 关键武器
- 用户引言当 H1
- Testimonials 高密度（10+ 条）
- 第三方媒体引用

### 代表项目
Arc / Aider（次代表，用 30+ testimonial 压底）

### 反例
没有真实用户的项目硬选 E 型 → 假大空，立刻劝退。**E 型有门槛**。

### 对比锚硬规则（避免稻草人）

E 型 / Why 段做对比时：
- **找真正的同类对手**——"比 Spark 更专注于时区"是稻草人（Spark 是邮件 app，本来不是同类）
- **只在功能确实不同时才提**——同质化对比反而暴露弱势
- **不确定有哪些同类 → 宁可不比较**——伪对比比无对比更伤信任
- **绝不"对手定义型 tagline + 编造对手缺点"**——读者去查 30 秒就识破，杀伤力极强

判定方法：把要对比的对手单独列出，问"目标读者会同时考虑这两个产品吗？"——不会就是稻草人。

---

## Archetype 决策器（信号优先级）

按优先级从高到低判定，**第一个命中即定**。E 型与其他平级——只要信号强就先选。

```
┌─ 信号 1：用户 INTERVIEW Q4/Q6 答案中
│        含强对手名（Chrome / VSCode / Notion / Slack / Webpack 等）
│        + 提供了真实可验证的 testimonial
│   → E（第三方背书优先型）
│   理由：已有强对手时正面叫板风险高，借第三方的嘴更安全
│
├─ 信号 2：入口形态 = AI/Model（requirements.txt 含 torch/transformers/langchain/vllm）
│        OR 用户答案含 "agent / LLM / 全新概念 / 没有同类参照物"
│   → D（新品类教育型）
│   可选：借 B 的架构图增强工程性
│
├─ 信号 3：入口形态 = 基础设施类
│        DB / BaaS / 部署平台 / API gateway / 监控 / 自托管平台
│        OR 用户描述强调"高并发 / 多租户 / 集群 / SLA"
│   → B（基础设施/平台型）
│
├─ 信号 4：入口形态 = Desktop（Tauri/Electron）/ Mobile / 创作者工具
│        视频/音频/图像/写作/白板/笔记
│   → C（消费/创作者工具型）
│
├─ 信号 5：入口形态 = Web app / SaaS（next/vite/gatsby/nuxt/sveltekit）
│   ├─ 用户强调 self-host → B
│   ├─ 用户强调即开即用 + 终端用户 → C
│   └─ 默认 → C（用户后续可改）
│
├─ 信号 6：入口形态 = CLI / SDK / Library / IDE 插件 / DevTool
│   → A（开发者工具型，默认兜底）
│
└─ 信号 7（无 manifest 或全部不命中）：
   → 询问用户项目类型；如项目不属于 software（dotfiles / awesome-list / 个人 reference / 内部专用），建议改用普通 markdown 编辑而非本 Skill
```

## E 型的特殊触发规则（自动化）

E 型门槛高（必须有真实可验证的 testimonial）。Skill 应在以下时机主动建议升级到 E：

1. **SCAN 阶段**：现有 README 文本提到 "alternative to X" / "X replacement" / "the next X" 等对标语句
2. **INTERVIEW Q4**：用户差异化答案出现 Chrome/VSCode/Notion/Slack 等已知大对手名
3. **INTERVIEW Q6**：用户提供了 ≥2 条带人名+title 的真实 testimonial

满足 1+3 或 2+3 → 自动建议从默认 archetype 切换到 E，让用户决定。

**未达门槛但选 E**：Skill 应警告"E 型需要真实可验证的引言，建议改回 A/C/D"。

## Section 拼装契约（DRAFT 阶段使用）

DRAFT 阶段不再加载预存的"完整 archetype 骨架"——直接按下面的契约从 [`section-library.md`](section-library.md) 拼装：

1. **主 archetype 由决策器选定** → 取本文件中该 archetype 的 "Section 顺序" 列表
2. **Hero 风格** → 用该 archetype 的 "Hero 套路"（套路名对应 [`tagline-formulas.md`](tagline-formulas.md) 中的具体公式）
3. **Feature 段呈现形式** → 按 "关键武器"决定用哪种变体（A/D 用 emoji bullet，B 用 checkbox，C 用卡片网格，E 用引言墙）
4. **每个 section 的具体模板** → 全部从 `section-library.md` 取（**唯一真理源**）；不允许在本文件或其他地方维护 section 模板的副本
5. **条件渲染** → 信任段（adopters / testimonials / star history / contributors / sponsors）按 [`trust-signals.md`](trust-signals.md) 的渲染条件判定，不满足条件的整段不出现

### Archetype 混搭

archetype 不是死的。允许"以 A 为主，借 B 的架构图，借 D 的拟人化定位"。

- 主 archetype 决定 hero 套路 + section 排序
- 模型在 DRAFT 时可基于实际项目特征插入其他 archetype 的 section（如 A 型 CLI 项目借 D 的 architecture mermaid 段）
- 用户也可在 REVIEW 时要求插入

**示例**：A 型项目（CLI）+ 借 D 的 architecture：
```
hero（A）→ what is X（A）→ quick start（A）→ features（A）→
architecture（D, mermaid）→ why X（A）→ adopters（A，条件渲染）→ contributing → license
```
