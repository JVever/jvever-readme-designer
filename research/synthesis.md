# jvever-readme-designer 调研汇总

> 5 路并行 Agent 调研结果的综合提炼，作为 Skill 设计的依据。

## 调研覆盖

| 路 | 范围 | 样本数 |
|---|---|---|
| 1 | GitHub AI / 开发者工具类 README | 12 |
| 2 | GitHub 框架 / 库 / 应用类 README | 18 |
| 3 | 中文社区高热度开源项目 README | 15 |
| 4 | 软件产品官网 / landing page | 13 |
| 5 | README 设计方法论与认知科学 | 综合多源 |
| **合计** | | **58 个项目/官网/方法论** |

---

## 一、核心洞察（17 条，按 Skill 设计相关度排序）

### A. 关于 Hero 区（黄金 5 秒）

1. **首屏必须答三问**：做什么 / 给谁 / 怎么开始。Title + tagline + 1 张视觉 + 1 行 install 命令必须在不滚动可见区。
2. **Tagline 公式有 6 种套路**：品类定义型、结果承诺型、身份共鸣型、第三方背书型、拟人/隐喻型、硬核数字型——选择取决于产品阶段和目标受众。
3. **Logo + 居中布局**几乎是行业默认（成熟项目 95% 用 `<p align="center">`）。
4. **明暗双 logo（picture/srcset）** 是"我们关心细节"的隐形信号。

### B. 关于卖点呈现（Show, Don't Tell）

5. **每个 claim 必须配 1 个证据**：截图、GIF、代码、benchmark、before/after 之一。形容词堆砌（fast/modern/scalable）= 0 信息量。
6. **Feature 区有 12 种武器**：代码片段、性能数字、客户成果、logo 墙、testimonials、用户量、奖项、动态演示、诚实区、对标竞品、live demo、吉祥物。
7. **Quick start 越短越自信**：1 行命令 > 多行步骤。多种安装方式应折叠次要选项，主路径只露一条。

### C. 关于信任建立

8. **14 种信任信号**：CI 通过、版本号、release 频率、stars、license、coverage、真实截图、Used by、贡献者头像墙、Sponsors、Security policy、Changelog、Code of Conduct、Discord——构成"项目还活着、社区健康"的证据链。
9. **Adopters logo 墙是最强 social proof**——OpenHands "Trusted by TikTok/VMware/Apple" 直接搬企业网站做法。
10. **Star History 折线图**已成成熟项目标配。

### D. 关于结构与节奏

11. **倒金字塔 + 受众分层**：tagline → demo → quickstart → features → docs → architecture → contributing → license。每个 section 第一句即结论。
12. **Section 排序有 5 种 pattern**：开发者工具型、基础设施型、消费者/创作者工具型、新品类教育型、第三方背书优先型。不同产品类型对应不同顺序。
13. **README 长度悖论**：Tailwind / shadcn / Astro 用 < 50 行赢得敬意，LobeHub 用 968 行被诟病。**README 不是文档，是门面**——超过的部分外链出去。

### E. 关于双语（中文社区特殊议题）

14. **中文优先项目（FastGPT/MaxKB/Bisheng）默认结构**：`README.md`（中文）+ `README_en.md`（英文）+ 顶部一行语言切换 badge。
15. **国内特有元素**：飞书/微信/QQ 群二维码、ModelScope/HF 双链接、Bilibili 演示、Yuque 文档、阿里云一键部署、整合包下载——是国内项目的差异化武器。

### F. 关于反模式（避雷清单）

16. **十大常见反模式**：① 项目名 + logo 没解释；② obvious-to-me 安装；③ 跳过 Why 直接 Install；④ 形容词堆砌；⑤ 巨型一段式无 heading；⑥ 滥用 emoji/HTML；⑦ Demo 缺失；⑧ Stale README（命令跑不起来）；⑨ Marketing 喧宾夺主；⑩ License 缺失。
17. **过度装饰是高频抱怨**：满屏 emoji + 居中 HTML + 动态 SVG 让 raw 文件不可读、屏幕阅读器友好度差。**克制比繁复更显高级**（参考 Tailwind/shadcn）。

---

## 二、5 种 README 原型（Archetype）

每种原型对应不同产品类型，决定了 section 顺序和卖点呈现策略。

| 原型 | 适用项目类型 | Hero 套路 | Section 顺序 | 代表 |
|---|---|---|---|---|
| **A. 开发者工具型** | CLI/SDK/编辑器插件 | 品类定义 + 多状态 UI | Hero → 数字/logo 墙 → 功能模块×N（每模块带截图/代码）→ 名人 testimonial → 文档/CTA | Cursor, Vercel, Warp, Linear, Bun |
| **B. 基础设施/平台型** | DB/BaaS/云服务 | 结果承诺 + 硬核数字 | Hero → 大客户 logo → 性能数字带 → 产品矩阵 → 行业案例 → 文档入口 | Supabase, Stripe, PostHog |
| **C. 消费/创作者工具型** | 桌面 app/视频/写作工具 | 身份共鸣 + 强视觉 | Hero（视频/截图）→ Logo 墙 → 功能卡片网格（10+）→ 用例分人群 → 价格/下载 | Raycast, Notion, Descript, Excalidraw |
| **D. 新品类教育型** | LLM agent/全新概念 | 拟人/隐喻 + 教育性定义 | Hero → "我是什么" → 4-5 个 capability → 视频演示 → 工具替代计算器 → CTA | Claude, OpenHands, AutoGen |
| **E. 第三方背书优先型** | 已有强势对手的赛道 | 用户引言当 H1 | Hero（引言）→ 截图 → 更多引言 → 下载 | Arc（"Chrome replacement I've been waiting for"）|

---

## 三、必备 / 推荐 / 可选 sections 清单

**必备（任何 README 都要有）**
1. Title（与仓库名一致）
2. Tagline（≤120 字符的一句话定位）
3. Hero visual（screenshot / GIF / asciinema / banner，至少占位）
4. Install / Quick start（一行命令优先）
5. License（SPDX）

**强烈推荐**
6. Badges（version/build/license/downloads，≤6 枚）
7. Features（emoji bullet 或 ✅ checkbox，每条配证据）
8. Documentation 外链
9. Contributing 外链
10. 多语言切换（中英双语项目必备）

**按场景可选**
- TOC（仅当 README > 100 行才加）
- Architecture diagram（基础设施/复杂系统）
- Adopters / Used by（有真实大客户时）
- Testimonials（有名人或真实用户引言时）
- Star History（≥1k stars 时）
- Sponsors / Sponsorship（OpenCollective/GitHub Sponsors）
- Roadmap（活跃迭代项目）
- Security policy
- Changelog 链接
- 国内特有：微信/飞书群、ModelScope 链接、Bilibili 演示、国内一键部署

---

## 四、双语处理的 4 种模式

| 模式 | 主文件 | 副文件 | 切换方式 | 适用 |
|---|---|---|---|---|
| **M1 中文优先双文件**（推荐国内项目） | `README.md`（中文）| `README_en.md` / `README.en.md` | 顶部 badge 一行 | 主要面向国内用户，兼顾国际 |
| **M2 英文优先双文件** | `README.md`（英文）| `README.zh-CN.md` / `docs/zh/README.md` | 顶部 badge 一行 | 国际化为主，中文为辅 |
| **M3 多语言子目录** | `README.md`（英文）| `i18n/README.{lang}.md` | 顶部 badge 阵 | 5+ 语言的大型项目 |
| **M4 单文件中英对照** | `README.md`（中英叠加）| 无 | 段落内并列 | 极简项目，README < 60 行 |

**Skill 默认采用 M1**（中文优先 + `README_en.md`），符合用户"中文优先"偏好。

---

## 五、图片/视觉素材规划清单

按"必要性"分级，Skill 在 README 中留占位符 + 配套生成"图片任务清单"：

**强烈推荐（不放就缺一只眼）**
- `assets/banner.png` 或 `assets/hero.gif` — 首屏主视觉（screenshot 或 demo GIF）
- `assets/logo.svg` 或 `assets/logo.png` — Logo（建议明暗双版本）

**推荐（让 README 像产品页）**
- `assets/feature-{1,2,3}.png` — 重点功能截图（按 archetype 数量不同）
- `assets/architecture.svg` — 架构图（B/D 原型必备）
- `assets/screenshot-dark.png` / `assets/screenshot-light.png` — 配合主题切换

**国内项目特有**
- `assets/wechat-group-qr.png` — 微信群二维码
- `assets/lark-group-qr.png` — 飞书群二维码
- `assets/bilibili-thumbnail.png` — B 站演示视频缩略图

**自动生成可行的**
- Mermaid 架构图（`mermaid` code block，无需图片）
- Star History（star-history.com 自动生成 URL）
- Contributors 头像墙（contrib.rocks 自动生成 URL）
- shields.io badges（运行时拼 URL）

---

## 六、设计 Skill 的 7 条核心原则（按重要度）

1. **首屏定生死** —— 5-second test 是硬约束。Hero 必答三问。
2. **倒金字塔 + 受众分层** —— 最广受众的信息最上面，越往下越细节。每段第一句即结论。
3. **Show, don't tell** —— 每个抽象 claim 必须有证据（demo/GIF/benchmark/代码/真实用例）。
4. **基于 JTBD 而非 feature list 写定位** —— 描述用户想完成的真实 job 和当前的痛，再给方案。
5. **信任信号系统化布置** —— badges + adopters + last release + 真实截图 + changelog，构成完整证据链。
6. **降低认知负荷** —— 一节一要点；推荐唯一安装路径；CTA 只一个主操作；F-pattern 友好（heading 关键词前置）。
7. **README 是活的产品页** —— 不是写完就结束，每次 release 必须 review。这是最强的"项目还活着"信号。

---

## 七、Skill 的关键决策点

基于以上洞察，Skill 设计需要回答：

1. **如何识别项目类型**？通过文件签名（package.json / Cargo.toml / pyproject.toml / 是否有 web UI / 是否是 CLI / 是否是 SDK）+ 用户访谈。
2. **如何选 archetype**？项目类型 → archetype 推荐 → 用户确认。
3. **如何写 tagline**？引导用户用 6 种 tagline 套路之一，提供示例。
4. **如何写 features**？强制每条 ≤ 1 行 + 1 个证据（图/代码/数字）。
5. **如何处理双语**？默认 M1，但允许用户切换。
6. **如何处理图片**？规划清单 + 占位符路径 + 给用户的"图片任务清单"。
7. **如何避免反模式**？内置反模式 checklist，生成前自检。
