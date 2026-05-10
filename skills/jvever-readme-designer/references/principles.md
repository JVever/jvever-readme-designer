<!--
@input:    Skill 各阶段（SCAN / INTERVIEW / DRAFT / REVIEW）的设计判断
@output:   5 条正向原则——所有主观设计决策的唯一信仰来源
@rule:     新增/修改原则时同步更新本文件 + auto-checks.md（机械检测）+ SKILL.md 中的引用
-->

# 5 条核心原则

**README 设计的唯一信仰来源。** 所有主观判断回到这 5 条原则，不再额外查"反模式表"。

每条原则：
- **正向描述**——应该往哪个方向走
- **应用要点**——具体落地动作
- **反例锚**——历史踩过的具体坑（用作记忆锚，不展开成单独章节）

> **机械可检测的规则**（路径泄露、broken link、占位符未替换、license 缺失等）见 [`auto-checks.md`](auto-checks.md)。本文件只讲**需要判断力**的事。

---

## 原则 1：首屏定生死

**正向描述**：访客 5 秒内必须能答清"做什么 / 给谁 / 怎么开始"，否则关闭。Hero 区是整个 README 的 KPI——不是文档目录的开头，是 landing page 的"销售页"。

**应用要点**：
- 不滚动可见区必须包含：H1（项目名）/ Tagline（中文 ≤30 汉字、英文 ≤120 字符）/ 1 张 hero 视觉或占位符 / 1 行核心命令或行动按钮 / 不超过 6 枚 badge
- Quick-start 位置在 README 前 1/3
- Hero 区不放营销长篇、品牌故事、贡献指南——这些挪到中后段
- 没有 hero 视觉就**留空**或放占位符 + image-plan 任务，**不要**用装饰物（ASCII 流程图、emoji + 框线）凑数

**反例锚**：
- AutoGPT：首屏先放 System Requirements 长表，焦虑前置
- 本 skill v2 自身：hero 后塞 13 行伪 CLI 对话块，违反"hero 只放 tagline + 1 图 + 1 命令"
- 顶部 lang badge 切换条 + nav 行 English 链接同时存在，浪费首屏空间

---

## 原则 2：基于 Job 而非 feature 列表

**正向描述**：先描述用户想完成的真实任务和当前的痛点，再给方案。倒金字塔——最广受众的信息在最上面，越往下越细节。

**应用要点**：
- Hero 后第一段不是"我们有 A/B/C 功能"，而是"在 X 场景下，你想做 Y，但 Z 让你头疼——这个项目让 Y 变得简单"
- Section 顺序默认骨架：tagline → demo → quickstart → features → docs → 架构 → adopters/testimonials → contributing → license
- 每段第一句即结论。"Install via npm" 优于 "You can install this by using npm"
- 也明确"不为谁服务"——在 Why 段或 Features 之后加一段"什么时候不该用"，反而吸引到对的人
- **避免基线特征当卖点**：features 段只放"目标读者可能不预期、能让他们说'哇还能这样'"的东西。**品类应有的基础功能塞进卖点反而显得没东西可说**——菜单栏 app 把"住菜单栏"列卖点 ≈ 外卖 app 把"可以下单"列卖点。判断方法：把每条 bullet 单独读出，问"如果这条不写，目标读者会不会反过来惊讶（'居然没有？'）"——会的话是基线特征，不会才是真卖点。

**反例锚**：
- Feature dump：罗列 30 个 feature，没说用户为啥要用
- 形容词堆砌但 0 证据："fast / modern / scalable / beautiful"——访客瞬间识别为营销噪声
- 基线特征当卖点：菜单栏时区工具列"🌐 中英双语 / 🏠 安静住在菜单栏"——读者反应"就这？这不是默认就该有的吗"

---

## 原则 3：Show, don't tell

**正向描述**：每个抽象 claim 必须配一个具体证据。形容词需要数字、动图、或对比来兜底。

**应用要点**：

证据载体优先级（高到低）：
1. 可交互 live demo / playground 链接
2. 动图（GIF / video）
3. 静态截图
4. 代码片段（输入 → 输出对照）
5. 性能数字（"处理 10MB 文件 0.3s vs alternative 4.2s"）
6. 前后对比
7. 客户使用结果（"X 公司用了之后构建从 7 分钟降到 40 秒"）

形容词审查（典型例，**不是穷举黑名单**——遇到新词按"是否带具体内容支撑"判断）：

- 英文典型："fast / modern / scalable / beautiful / blazingly / production-ready / seamlessly / powerful / intuitive"
- 中文典型："智能 / 精准 / 强大 / 极速 / 一秒 / 一键 / 完美 / 全面 / 颠覆"

这些词出现，必须配数字 / 链接 / 对比兜底，否则删掉或改为具体描述。**"算法"**也常被滥用——简单的几行 if-judgement 求交集别叫"算法"，是过度包装。

**事实校验纪律（强制）**：每条"X 可以 / 支持 / 自动 Y"声明，DRAFT 写完后**回代码 grep 一次确认行为属实**——不允许仅凭项目印象写产品声明。模型容易抄 sub-agent / SCAN 总结里的描述，把矛盾糅进一句话；READme 一旦印发，错误声明会建错读者心智模型，代价大。

**反例锚**：
- "0.3 秒启动"配 benchmark 链接 ✓ vs "极快启动" ✗
- "智能算法精准定位"——"智能"+"精准"+"算法"三连，零信息量
- "一秒搞定 / 一键开会"——没数据支撑就是夸大
- 第三方背书型项目伪造引言——**绝不**为了凑信任信号编造 testimonial
- 写"每位同事工作时段可独立调整"，但代码里 setWorkHours 接受**城市名**为参数（按城市设、不按人）——抄 sub-agent 总结没回代码 verify 的典型事故

---

## 原则 4：克制即专业

**正向描述**：README 的每个元素都必须为"读者获取信息"服务。任何装饰、营销、自嗨、冗余成分都要回答："删掉它，读者损失什么？"——回答不出来，就删。

**应用要点**：
- **emoji**：仅用作 feature bullet 前缀（统一风格、不混用），不要洒在标题里、不要作为步骤标记（⛔ ✅ 🔥 等用作"流程图节点"是反模式）
- **HTML**：仅用于必要的居中（hero）和图片包裹。删除多余的 `<div>`，确保 raw markdown 在终端 `cat` 也可读
- **TOC**：README < 100 行不放 TOC——对短文档是噪声
- **装饰性 ASCII**：替代 hero 视觉的代码块**必须是真实命令 + 真实输出，≤ 6 行**。禁止 emoji + 框线流程图、伪交互对话、虚构 pipeline 演示
- **冗余功能元素**：同一功能不重复放（语言切换：顶部 lang badge **或** nav 行 English 链接，**只放一处**）
- **唯一安装路径**：主路径只有一条，其他用 `<details>` 折叠
- **CTA**：重复 3 次但只一种文案（hero / features 段中 / 页脚）
- **中英混杂节制**：中文版避免**不必要的**中英混杂——不是完全拒绝。判断标准是"换成中文之后，目标读者是更容易看懂还是更困惑？"——命令名、文件名、代码标识符、领域内已成共识的英文（如开发者文档里的 API/CLI/SDK，AI 圈的 embedding/agent）保留；半专业的方法论切片词（如设计套路、营销漏斗、用户评价）翻译成中文；分不清的留给 REVIEW 阶段问用户。**不维护黑白名单**——这条是判断题不是查表题。

**反例锚**：
- emoji 满天飞：`# 🚀✨🔥 CoolProject 🎉🌟💫`
- 装饰流程图：`⛔ STAGE 1 ──────── ⛔ STAGE 2 ────────`（本 skill v2 自己犯过）
- 多余 div：`<div align="center"><h2>...</h2></div>` 包了一层啥也没加
- 双语切换重复：顶部 lang badge + nav 行 English 链接同时存在
- 中英混杂用冷词：把领域外读者不熟的方法论术语以原英文塞进中文段落（典型如设计/营销/产品方法论里的英文切片词）

---

## 原则 5：信任信号 + 鲜活维护

**正向描述**：用证据链证明"项目能用、还活着、社区健康"；写完不是结束，每次 release 都要回头维护。

**应用要点**：

最强 3 类信任信号：
- **Used by / Adopters logo 墙**——OpenHands "Trusted by TikTok / VMware / Apple"
- **真实大佬 testimonial**——Cursor 的黄仁勋、Karpathy、Collison 引言
- **客户成果数字**——Vercel "build 7m → 40s, 24x faster"

完整 14 种信号清单见 [`trust-signals.md`](trust-signals.md)。

条件渲染（详见 trust-signals.md）：
- Star History 仅 ≥1k stars 才放
- Contributors 头像墙仅 ≥10 人才放
- Adopters 仅在用户提供真实名单时才放
- 不满足条件的 section 不渲染——避免"50 stars 项目放 Star History 反成显穷"

**鲜活的硬规则**：
- 命令 / 版本号 / 链接基于项目实际状态生成，**不臆造**
- 第三方背书型项目要的真实 testimonial，**Skill 不会伪造**——这是设计原则
- 输出后提醒用户：每次 release 跑一遍 `--rewrite`，保持鲜活

**反例锚**：
- last commit 1 年前 + issue 堆积无人回 + CI 红——最强"项目已死"信号
- 命令复制粘贴跑不起来 / 版本号是 1 年前的 / 链接 404 / 截图是初版 UI
- 50 stars 项目放 Star History——反成显穷
- 凭空捏造 stars / 用户量 / 客户名

---

## 这 5 条原则如何使用

**生成阶段**：DRAFT 完成后，对照 5 条原则做主观判断（每条问自己"这个 README 通过了吗？"）。

**自检循环**：自动可改的（emoji 满天飞、多余 div、装饰 ASCII 等）直接修；主观判断（tagline 够不够吸引、章节顺序合不合理）升级到 REVIEW 让用户决定。

**机械检测**：见 [`auto-checks.md`](auto-checks.md)——和这 5 条原则**不重复**，专门管"对错明确的检测"。

**用户表达偏好**：可以在 `EXTEND.md` 里覆盖默认决策（如统一 emoji 风格、永远不放 emoji、强制 TOC 等），但**不能修改这 5 条原则本身**——原则是 skill 的信仰底线。
