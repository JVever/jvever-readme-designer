# Tagline 6 种套路

Tagline 是 README 第二行的灵魂。**字数约束**：中文 ≤30 汉字 / 英文 ≤120 字符。紧跟项目名 H1。

---

## 套路 1：品类定义型

**公式**：
> [产品] is the [新品类 / 老品类升级] for [人群], built for [核心价值]

**何时用**：
- 你想抢占一个新品类
- 或重定义老品类（"不是 X，是 X 的下一代"）

**示例**：
- 中：「Linear——为团队和 agent 设计的产品开发系统」
- 英："Linear is the product development system for teams and agents"
- 中："Warp 是一个 agentic 开发环境（终端的下一代）"
- 英："Warp is the agentic development environment"

**反模式**：
- 不要用模糊词："a modular extensible framework"——0 信息量
- 不要用排比："fast, modern, beautiful, scalable"——同样 0 信息量

---

## 套路 2：结果承诺型

**公式**：
> [做某事] in [时间] / 达成 [结果]
> Scale to [量级]

**何时用**：
- 基础设施 / 工具类
- 价值在"省时间 / 能扩展"
- 用户决策成本主要在"是否能跑得起"

**示例**：
- 中："Supabase——周末上线，规模千万"
- 英："Build in a weekend. Scale to millions."
- 中："Vite——下一代前端构建工具，快得让你怀疑人生"
- 英："Next Generation Frontend Tooling"

**反模式**：
- 不要承诺无法量化的结果："变得更好"
- 数字要可验证，不要夸大

---

## 套路 3：身份共鸣型

**公式**：
> For [某种自我认同 / 人群]

**何时用**：
- 买家选择标准是情感 / 身份，而非具体功能
- 消费类、创作者工具、生活方式类
- 已有竞品但你的人群更窄/更深

**示例**：
- 中："Claude——为解题人设计的 AI"
- 英："The AI for Problem Solvers"
- 中："Raycast——你通往一切的快捷方式"
- 英："Your shortcut to everything"

**反模式**：
- 人群太宽（"for everyone"）= 等于没有
- 身份要可识别（"AI-fluent teams" 比 "modern teams" 更具体）

---

## 套路 4：第三方背书型

**公式**：
> "[用户原话评价]" — [可识别的人]

**何时用**：
- 项目还小，自夸信服力低
- 已有早期用户 / 知名媒体的好评
- 已有强势对手，借第三方的嘴比自己说更安全

**示例**：
- "Arc is the Chrome replacement I've been waiting for." — David Pierce, The Verge
- "I've replaced 80% of my IDE usage with Aider." — @ESR
- "终于不用再写 Webpack 配置了。" — 知乎用户 @某某

**反模式**：
- 引言来源不可验证 / 假托
- 引言来自项目作者自己 / 团队成员
- 引言太长（> 1 句话失去冲击力）

---

## 套路 5：拟人 / 隐喻型

**公式**：
> Meet [拟人化角色]. [它做什么]
> Like [熟悉事物] for [新场景]

**何时用**：
- 抽象功能（agent / AI 协作 / 全新概念）需要降维
- 用户需要"30 秒理解你是什么"
- 新品类教育型项目

**示例**：
- 中："Notion——见见你的'夜班'。它 24/7 帮你工作"
- 英："Meet the night shift."
- 中："Descript——像打字一样剪视频"
- 英："Video editing is as easy as typing"

**反模式**：
- 隐喻太牵强（"像火箭那样的数据库"）
- 隐喻不为目标人群所熟悉

---

## 套路 6：硬核数字型

**公式**：
> [巨型数字] / [行业级承诺]

**何时用**：
- B2B / 企业级
- 信任成本极高的领域（金融、安全、医疗）
- 已有规模，可以用数字压住

**示例**：
- "Stripe—Financial infrastructure to grow your revenue." 副线 "$1.9T processed, 99.999% uptime"
- "Cloudflare—Connect, protect, and build everywhere. 20% of the web's traffic."

**反模式**：
- 数字虚假（"100% reliable"——没有任何系统是 100%）
- 数字无意义（"我们有 1000 个 commit"）
- 数字与卖点无关（"项目存在 5 年了"——年龄不是卖点）

---

## 选择套路的决策

```
项目阶段：
├─ 早期 / 小项目：
│   ├─ 有真实用户引言 → 套路 4（第三方背书）
│   ├─ 没有 → 套路 1（品类定义）或 套路 3（身份共鸣）
└─ 成熟 / 已有规模：
    ├─ 基础设施 / 量化价值 → 套路 2（结果承诺）或 套路 6（硬核数字）
    ├─ 全新概念 → 套路 5（拟人隐喻）
    └─ 开发者工具 → 套路 1（品类定义）
```

---

## 中文 tagline 的额外注意

- **不要硬翻译英文**："The fast, all-in-one X" → "快速、一体化的 X"——读起来不像中文
- **善用中文短句**：4-8 字一段，节奏感强
- **保留品牌情绪**：DeepSeek "源自中国，献给世界"；Bisheng "匠心，对标活字印刷"
- **避免直白吆喝**："最好的 X" / "唯一的 X"——立刻失分
- **必要时双语并列**：中英文 tagline 各一行，互补不重复
