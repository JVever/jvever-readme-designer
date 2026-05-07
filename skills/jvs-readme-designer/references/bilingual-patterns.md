# 双语 README 处理的 4 种模式

中英双语项目的 README 怎么组织。Skill 默认采用 M1（中文优先双文件），其他模式按用户需求切换。

---

## M1 中文优先双文件（默认 / 推荐国内项目）

### 文件结构

```
README.md          # 中文版（默认显示在 GitHub 仓库首页）
README_en.md       # 英文版
```

### 语言切换：二选一硬规则

**只放一处，不重复。** Hero 区已经有 nav 行（如 `[安装] · [使用] · [English]`），就**不要**再在最顶部加一个 lang badge 切换条——那是冗余信息，浪费首屏纵向空间。

决策表：

| 场景 | 切换条放在 |
|---|---|
| Hero nav 行有语言切换链接（M1 默认） | **只放 nav 行**，省略顶部 lang badge |
| Hero nav 行没有语言切换 / 项目无 nav 行 | 顶部加 lang badge 切换条 |
| 单语模式（`--zh-only` / `--en-only`） | 都不放，避免链向不存在的文件 |

**关键规则（避免 silent fail）**：
- 当前语言 badge / 链接**不是链接**（点了刷新本页/形成死循环就是 silent fail）
- 仅切换目标语言用 `<a>` 包裹

#### 方案 A：nav 行内嵌（推荐，最克制）

中文版：
```markdown
[安装](#安装) · [使用](#使用) · [模式](#模式) · [English](README_en.md)
```
英文版：
```markdown
[Install](#installation) · [Usage](#usage) · [Modes](#modes) · [中文](README.md)
```

#### 方案 B：顶部 badge 切换条（仅当 nav 不含语言切换时使用）

中文版顶部：
```markdown
<p align="center">
  <img alt="中文（当前）" src="https://img.shields.io/badge/lang-中文-red?style=flat-square">
  &nbsp;
  <a href="README_en.md"><img alt="English" src="https://img.shields.io/badge/lang-English-blue?style=flat-square"></a>
</p>
```

英文版顶部：
```markdown
<p align="center">
  <a href="README.md"><img alt="中文" src="https://img.shields.io/badge/lang-中文-blue?style=flat-square"></a>
  &nbsp;
  <img alt="English (current)" src="https://img.shields.io/badge/lang-English-red?style=flat-square">
</p>
```

（红色 badge = 当前语言，蓝色 = 切换目标）

**单语模式不要放切换条**（`--zh-only` / `--en-only` → 删除整段切换条，否则链向不存在的文件导致 404）。

### 适用
- 主要面向国内开发者，兼顾国际
- 中文社区驱动的项目（FastGPT / MaxKB / Bisheng / DeepSeek）

---

## M2 英文优先双文件

### 文件结构

```
README.md          # 英文版
README.zh-CN.md    # 中文版（也可叫 README_zh.md）
```

### 切换条同 M1，但红蓝相反

### 适用
- 国际化为主，中文为辅
- 全球开源项目，但希望对中国社区友好（lobe-chat / Qwen / Dify）

---

## M3 多语言子目录

### 文件结构

```
README.md          # 英文版
i18n/
  README.zh-CN.md
  README.ja.md
  README.fr.md
  README.de.md
  README.es.md
  README.ru.md
  ...
```

或：

```
README.md
docs/
  zh/
    README.md
  ja/
    README.md
  ...
```

### 顶部切换条

```markdown
<p align="center">
  English
  | <a href="i18n/README.zh-CN.md">简体中文</a>
  | <a href="i18n/README.ja.md">日本語</a>
  | <a href="i18n/README.fr.md">Français</a>
  | <a href="i18n/README.de.md">Deutsch</a>
  | <a href="i18n/README.es.md">Español</a>
  | ...
</p>
```

或 badge 阵：

```markdown
<p align="center">
  <a href="README.md"><img src="https://img.shields.io/badge/-English-blue"></a>
  <a href="i18n/README.zh-CN.md"><img src="https://img.shields.io/badge/-简体中文-red"></a>
  <a href="i18n/README.ja.md"><img src="https://img.shields.io/badge/-日本語-green"></a>
  ...
</p>
```

### 适用
- 5+ 种语言的大型国际化项目
- 有翻译社区 / volunteers 的项目（Supabase / Dify）

---

## M4 单文件中英对照

### 文件结构

```
README.md  # 同时含中英
```

### 组织方式 1：段落内并列

```markdown
# {{project}}

**让 PDF 转 Markdown 像呼吸一样简单。**

**Convert PDF to Markdown as easy as breathing.**

## 快速开始 / Quick Start

```bash
npm install ...
```

中文：装上后跑 `pdf2md input.pdf`，30 秒后你拿到一个 markdown。

English: After install, run `pdf2md input.pdf` and get a markdown in 30 seconds.
```

### 组织方式 2：上下分两半

```markdown
# {{project}}

## 中文

[完整中文 README]

---

## English

[Full English README]
```

### 适用
- 极简项目，README < 100 行
- 不想维护两份文件
- 中英用户都需要看到

### 缺点
- 阅读体验差（要跳过另一半）
- 不利于 GitHub README 渲染（首屏被一半占用）

---

## Skill 决策逻辑

```
默认 → M1（中文优先双文件）

用户在访谈中说：
- "国际化为主" / "主要给海外用户" → M2
- "5+ 种语言" / "已有 i18n 社区" → M3
- "极简，不想两份" / "项目 < 50 行 README" → M4
- 单语命令行参数：
  - --en-only → 只生成 README.md（英文）
  - --zh-only → 只生成 README.md（中文）
```

---

## 双语处理的 6 个最佳实践

### 1. 不是字面翻译，而是文化适配

中文 README 不应该是英文的硬翻译：
- ❌ "The fast, all-in-one X" → "快速、一体化的 X"（机翻）
- ✅ "X 是个又快又全能的 X"（口语化中文）

中英文文案可以**有不同的卖点排序**：
- 英文版强调 "fast / scalable / open source"
- 中文版强调 "国内可用 / 中文友好 / 与国内生态打通"

### 2. 截图本地化

如果 UI 有中英两版，README 截图也应配套：
- 中文 README → 中文 UI 截图
- 英文 README → 英文 UI 截图

不能两个 README 都用同一张英文截图。

### 3. 链接本地化

中文 README 优先链接到中文资源：
- 文档 → docs.fastgpt.cn 优于 github.com/x/x/wiki
- 视频 → Bilibili 优于 YouTube
- 仓库镜像 → ModelScope / Gitee 优于 HuggingFace（如果都有）

### 4. 切换条放在最顶部，不在 hero 之后

切换条 = README 第一行（badge 形式）或紧跟 logo 之前。**不要放到中间**。

### 5. 双语保持结构对称

中英版的 sections 应该 1:1 对应（避免英文版有 8 节、中文版有 5 节）。

### 6. 维护成本警告

双语 README 维护成本翻倍。Skill 在生成后明确告知用户：
> "已生成中英双版。每次更新 README 时，记得同步两份，否则会出现内容漂移。"

---

## 国内项目特有：超出双语的多渠道入口

中文项目除了 README，还会用：
- **微信公众号**（链接 + 二维码）
- **飞书 wiki**（深度文档放飞书）
- **Bilibili 演示视频**（替代 YouTube）
- **知乎专栏**（行业分析 / 技术博客）
- **掘金**（技术分享）
- **Gitee / GitCode**（国内镜像仓库）
- **国内云一键部署按钮**（阿里云 / Sealos / Zeabur / 火山引擎）

详见 `domestic-elements.md`。
