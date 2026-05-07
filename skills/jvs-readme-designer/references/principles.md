# 7 条核心设计原则

按重要度排序。生成 README 时每条都会作为自检 checkbox。

## 1. 首屏定生死

**原则**：访客 5 秒内必须能答清"做什么 / 给谁 / 怎么开始"，否则关闭。

**硬约束**：以下元素必须出现在不滚动可见区：
- 项目名（H1）
- Tagline（中文 ≤30 汉字 / 英文 ≤120 字符；中英版分别约束）
- 核心 badge 行（≤6 枚）
- 1 张 hero 视觉（screenshot / GIF / banner，至少占位）
- 1 行 install 命令（或 try online 按钮）

**反例**：Cursor README（13 行打发，没有视觉）；AutoGPT（首屏先放 System Requirements 长表，焦虑前置）。

## 2. 倒金字塔 + 受众分层

**原则**：最广受众的信息在最上面，越往下越细节。

**Section 顺序的默认骨架**：
```
tagline → demo → quickstart → features →
docs link → architecture → adopters/testimonials →
contributing → license
```

**每段第一句即结论**（front-load 关键词）。"Install via npm" 优于 "You can install this by using npm"。

## 3. Show, don't tell

**原则**：每个抽象 claim 必须配一个具体证据。

**证据载体（优先级从高到低）**：
1. 可交互 live demo / playground 链接
2. Animated GIF / video 截图
3. Static screenshot
4. 代码片段（"输入 → 输出"对照）
5. Benchmark 数字（"处理 10MB 文件 0.3s vs alternative 4.2s"）
6. Before / After 对比
7. 客户使用结果（"X 公司用了之后构建从 7m 降到 40s"）

**反例**：feature 行写 "fast, modern, scalable, beautiful"——0 信息量。
**正例**：feature 行 "**0.3s 启动**（cold start，benchmark 在 [docs/bench.md](docs/bench.md)）"。

## 4. 基于 JTBD 而非 feature list 写定位

**原则**：先描述用户想完成的真实 job 和当前的痛，再给方案。

**JTBD 结构**：
> When I'm [情境] / I want to [job] / so I can [更高目标]
>
> Currently [现状的痛点]
>
> [项目名] [给的解法]

**对 README 的影响**：Hero 区第一段不是"我们有 A/B/C 功能"，而是"在 X 场景下，你想做 Y，但 Z 让你头疼——我们让 Y 变得简单"。

**也明确"不为谁服务"**：在 Why 段或 Features 之后加一段 "When NOT to use [项目]"，反而吸引到对的人。

## 5. 信任信号系统化布置

**原则**：用证据链证明"项目能用、还活着、社区健康"。

**14 种信任信号**（详见 `trust-signals.md`）：CI badge / version / release 频率 / stars / license / coverage / 真实截图 / Used by / contributors / sponsors / security / changelog / CoC / docs site。

**最强 3 个**：
- **Used by / Adopters logo 墙**（OpenHands "Trusted by TikTok/VMware/Apple"）
- **真实大佬 testimonial**（Cursor 黄仁勋/Karpathy/Collison）
- **客户成果数字**（Vercel "build 7m → 40s, 24x faster"）

**反信号要避免**：last commit 1 年前、issue 堆积无人回、CI 红、README 全是 TODO、license 缺失。

## 6. 降低认知负荷

**原则**：每节一个要点；推荐唯一安装路径；CTA 只一个主操作；F-pattern 友好。

**应用**：
- **一节一要点**（认知负荷理论：工作记忆 ~4 chunk）
- **推荐唯一安装路径**（Hick's Law / 选择悖论：6 种 vs 24 种 jam 实验）；其他方式折叠到 `<details>` 里
- **CTA 重复 3 次但只一种文案**（hero / features 段中 / 页脚）
- **Heading 和 bullet 用关键词开头**（F-pattern eyetracking）
- **Raw markdown 必须可读**——克制 HTML 包裹和 emoji 滥用，避免屏幕阅读器不友好
- **TOC 仅当 README > 100 行**（Standard README spec）

## 7. README 是活的产品页

**原则**：不是写完就结束，每次 release 必须 review。

**Tom Preston-Werner 的 README Driven Development**：写 README 是在设计软件本身。

**对 Skill 的影响**：
- 生成的 README 自带 "last updated" 注释
- 命令 / 版本号 / 链接全部基于实际项目状态生成，不臆造
- 输出后提醒用户："每次 release 跑一遍 /jvs-readme-designer --rewrite，保持鲜活"

---

## 自检 Checklist（**唯一真理源** — single source of truth）

> 这是 Skill 在 DRAFT 阶段 4.8 自检循环对照的清单。`anti-patterns.md` 不重复，只描述每条反模式的"修法"。

### 原则层（来自 7 条核心原则）
- [ ] **#1 首屏三问**：Hero 区能 5 秒内答清做什么/给谁/怎么开始？
- [ ] **#1 Tagline 字数**：中文 ≤30 汉字 / 英文 ≤120 字符？
- [ ] **#1 Hero 视觉**：是否至少有 1 张 hero 视觉（或明确占位符 + image-plan 任务）？
- [ ] **#1 Quick start 位置**：是否在 README 前 1/3？
- [ ] **#2 倒金字塔**：每段第一句是否即结论（front-load 关键词）？
- [ ] **#3 Show don't tell**：每个 claim 是否配证据载体（demo / GIF / benchmark / 代码 / 数字）？
- [ ] **#3 形容词审查**：fast/modern/scalable/beautiful 是否都配了证据？
- [ ] **#4 JTBD**：是否描述了用户的真实 job 和痛点，而非 feature dump？
- [ ] **#5 信任信号**：是否布置了 ≥3 个信任信号（badges + adopters + 真实截图等）？
- [ ] **#6 唯一安装路径**：主路径只有一条，其他用 `<details>` 折叠？
- [ ] **#6 emoji 节制**：是否仅用于 feature bullet 前缀，未洒在标题？
- [ ] **#6 HTML 节制**：是否只用于必要的居中和图片，raw markdown 仍可读？
- [ ] **#6 TOC 必要性**：README < 100 行是否避免了 TOC？
- [ ] **#7 鲜活**：命令/版本号是否基于实际项目状态而非臆造？

### 工程层（避免 silent fail）
- [ ] **链接活性**：所有外链实际可达（不假托不存在的镜像域名）？
- [ ] **License 处理**：LICENSE 文件存在 → 链接；不存在 → 写"License: TBD"而非 broken link？
- [ ] **双语切换条**：当前语言 badge 不是链接？单语模式下整段切换条已删除？
- [ ] **占位图服务**：使用 `placehold.co`（via.placeholder.com 已停服）？
- [ ] **adopters 占位符**：未硬编码 stripe/vercel/shopify 等真实公司名？
- [ ] **占位符语法**：模板内 `{{var}}` 全部已替换，URL 中的占位符已 URL-encode？

### 双语层（仅 bilingual 模式）
- [ ] **本地化**：中文版不是机翻？文案按中文表达习惯重写？
- [ ] **截图本地化**：中英版是否各自配对应语言的 UI 截图？
- [ ] **结构对称**：中英版 sections 1:1 对应？

### 国内层（仅启用国内元素时）
- [ ] **群二维码补救**：是否同时给文字补救（微信号/QQ群号）？
- [ ] **utm 参数**：开源 README 是否避免了 utm_source 跟踪参数？
