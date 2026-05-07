# 反模式 Checklist

14 个常见反模式 + 5 个中文项目特有反模式。每个附修法。生成 README 前 / 生成后必须对照自检。

---

## 反模式 1：项目名 + logo，没人话解释做什么

**症状**：
```markdown
# CoolProject
![logo](logo.png)

## Installation
npm install coolproject
```

**问题**：访客看到名字猜不出做什么。YC 原则："Don't use company name as headline."

**修法**：项目名下面**必须**有一行 ≤120 字符 tagline。

---

## 反模式 2："Obvious to me" 安装

**症状**：
```markdown
## Installation
make install
```

不说前置条件、不说平台、不说依赖。

**修法**：
- 至少给一行可粘贴跑的命令（`npm install foo` 等）
- 列出最低环境要求（"需要 Node 20+"）
- 多平台时给出推荐路径，其他折叠

---

## 反模式 3：跳过 Why 直接进 Install

**症状**：项目名 + logo + 紧跟 Installation。

**问题**：读者还没决定要装就被甩命令。

**修法**：Hero 后必须有"What is X"或"Why X"一段，让读者先 buy in。

---

## 反模式 4：形容词堆砌

**症状**：
> A fast, modern, scalable, beautiful, lightweight, extensible framework for building...

**问题**：每个词都是无锚点空话，读者扫一眼就会忽略。

**修法**：每个 claim 配证据：
- "fast" → "0.3s 启动（cold start，benchmark 在 docs/bench.md）"
- "modern" → "ES2023 + TypeScript 5"
- "scalable" → "已在 Stripe 跑 500M req/day"
- "beautiful" → 配截图

---

## 反模式 5：巨型一段式无 heading

**症状**：长达 500 字的一整段，没 heading 没 bullet 没代码块。

**问题**：违反 F-pattern 和扫读习惯。

**修法**：
- 每 80-150 字一个 heading
- 关键信息用 bullet
- 代码用 ```fence

---

## 反模式 6：滥用 emoji 和 HTML

**症状**：
```markdown
# 🚀✨🔥 CoolProject 🎉🌟💫

<div align="center"><h2>🌈🎨 The 🚀 best 🔥 framework 💎 for 🦄 modern 🌟 web 🎯</h2></div>
```

**问题**：
- raw markdown 不可读
- 屏幕阅读器友好度差
- 看起来不专业（HN 高频抱怨）

**修法**：
- emoji 用在 feature bullet 前缀（统一风格），不要洒在标题
- HTML 仅用于必需的居中 / 图片包裹
- 测试：把 README 在终端 `cat` 一遍，看是否还能读懂

---

## 反模式 7：Demo 缺失

**症状**：500 行文字，0 张图。

**问题**：开发者工具/消费产品没视觉等于自杀。

**修法**：
- 至少一张 hero 截图 / GIF
- Skill 生成时**必须**留 hero 占位符 + 在图片任务清单中标注

---

## 反模式 8：Stale README

**症状**：
- 命令复制粘贴跑不起来
- 版本号是 1 年前的
- 链接 404
- 截图是初版 UI

**问题**：最强的"项目已死"信号。

**修法**：
- Skill 生成的命令基于实际项目 manifest
- Last release 日期自动从 GitHub API 拉
- 用户每次 release 后跑 `--rewrite` 模式

---

## 反模式 9：Marketing 喧宾夺主

**症状**：3 屏品牌故事 + 创始人愿景 + 路演视频，才到 install。

**问题**：开发者没耐心。营销内容应在中后段。

**修法**：
- Hero 区只放 tagline + 1 张图 + 1 行命令
- "我们的故事 / 愿景"放 README 末尾或独立页面

---

## 反模式 10：TOC 在 30 行短 README 里

**症状**：50 行的 README 配了 15 行 TOC。

**问题**：TOC 反让人滚动疲劳。

**修法**：Standard README spec 规则：**只有 README > 100 行才加 TOC**。GitHub 自带 TOC 入口（侧栏目录），多数情况下也不需要。

---

## 反模式 11：Contributing / Acknowledgements 占据黄金位

**症状**：Hero 之后第二节就是 "How to Contribute"。

**问题**：贡献指南是给贡献者看的，不是给评估者看的。占了黄金位 = 浪费首屏注意力。

**修法**：Contributing 和 Acknowledgements 永远放底部。

---

## 反模式 12：License 缺失

**症状**：根本没说 license。

**问题**：法律上不可商用。企业用户立刻 pass。

**修法**：必须有 License section + LICENSE 文件 + SPDX identifier。

---

## 中文项目特有反模式（额外 5 条）

### CN-1：直接搬英文表达

**症状**："{{project}} 是一个 modular extensible 的 framework"，中英混杂、机翻味重。

**修法**：中文版重写文案，用地道中文。

### CN-2：群二维码失效

**症状**：贴了 QQ 群图，群早满，没人维护。

**修法**：QR 旁配文字（群号 / 加好友拉群的微信号），并设定半年 review 期。

### CN-3：shields.io badge 加载慢

**症状**：国内访问 shields.io 间歇慢，badge 加载半天。

**修法**：
- 减少 badge 数量（≤4 枚）能显著缓解
- 自建 OSS 缓存（把 shields.io 拉的 SVG 镜像到自家 CDN）
- 关键 badge（version / license）可改为静态写入文字（如"License: MIT"）
- ⚠️ 不要使用未经验证的"镜像域名"——很多看起来像镜像的域名实际不存在或不稳定，反而让 badge 全部失效

### CN-4：`utm_source` 跟踪参数泛滥

**症状**：每个 link 后面 `?utm_source=github&utm_medium=readme...`

**问题**：开源项目带营销 utm 显得功利。

**修法**：开源 README 不带 utm；商业版页面可以。

### CN-5：截图全英文 UI

**症状**：中文 README 配的全是英文 UI 截图。

**修法**：中英两版各自配对应语言截图。

---

## 反模式 13：Hero 后塞装饰性 ASCII（细化反模式 9）

**症状**：
```text
$ /myproject

⛔ STAGE 1 ──────────────────────
  ...
⛔ STAGE 2 ──────────────────────
  ...
⛔ STAGE 3 ──────────────────────
  ...
```

紧跟 hero 区，用 emoji + 框线画一段"工作流流程图"或"伪交互对话"，假装是 CLI 输出。

**问题**：
- **真实性陷阱**：这个 ASCII 块**不是真实可跑的命令输出**，而是用 emoji 和框线手画的演示物，会误导读者以为产品长这样
- **首屏被装饰物占据**：违反"Hero 区只放 tagline + 1 张图 + 1 行命令"
- **emoji 滥用**：⛔ ✅ 🔥 等 emoji 被用作"步骤标记"，但与语义不匹配（⛔ 是禁止符号，不是步骤）
- **没有 hero 截图占位符也凑数**：用装饰物占住了本该给 hero 截图/GIF 的位置

**修法**：
- 严格执行 SKILL.md §4.6 的 ASCII 块约束：必须是真实命令 + 真实输出，≤ 6 行
- 没有真实简短可演示的命令 → 直接空着或放 hero 截图占位符 + 在 image-plan 标 must
- 不要"为了好看"画流程图——用户判断"项目活着、能跑"靠的是真实证据，不是装饰物

**反例与修例对照**：

❌ 反例（13 行装饰对话）：
```
> 帮我重写 README
  扫描项目：foo（CLI · Node.js）
  推荐 archetype：A
  三个问题：
    1. ...
> [回答 3 个问题]
  反模式自检：通过 15、升级 2
  已生成：README.md ...
```

✅ 修例（直接省略，hero 紧跟 what-is 一句话）：
```markdown
# project-name

**Tagline 一句话。**

[badges] [nav]

---

一段 what-is（≤ 30 汉字）+ 紧跟 install 命令一行。
```

---

## 反模式 14：双语切换条与 nav 语言链接重复

**症状**：
```html
<p align="center">
  <img alt="中文（当前）" src=".../lang-中文-red...">
  <a href="README_en.md"><img alt="English" src=".../lang-English-blue..."></a>
</p>

# project-name
**tagline**

[安装] · [使用] · [English](README_en.md)
```

最顶部一个 lang badge 切换条，下面 nav 行又有 `[English]` 链接——同一个功能放两次。

**问题**：
- 重复信息浪费首屏纵向空间（badge 切换条占 ~80px 高度）
- 视觉噪声，让 hero 区变拥挤
- 用户已经能从 nav 切换语言，顶部那条是冗余

**修法**：
- 二选一硬规则（详见 `bilingual-patterns.md`）：
  - **方案 A（推荐）**：nav 行内嵌 `[English]` / `[中文]` 链接，**省略**顶部 lang badge 切换条
  - **方案 B**：项目无 nav 行时，才用顶部 lang badge 切换条
- **禁止两种同时存在**

---

## 自检 Checklist

> **唯一来源**：完整 checklist 见 `principles.md` 末尾（避免维护两份）。本文件只列反模式本身的修法。

生成 README 后，参考 `principles.md` 末尾的 17 项 checklist 跑一遍。其中与本文件直接对应的反模式覆盖了：首屏三问、形容词审查、Demo 缺失、Quick start 位置、emoji/HTML 节制、链接活性、命令可跑、License、双语本地化、截图本地化、群二维码补救等。
