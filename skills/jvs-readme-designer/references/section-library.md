# Section 模板库

每个 section 给中英双版骨架。生成时按 archetype 选用。

---

## §1 Hero（必需）

### 中文版

```markdown
<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/logo-light.svg">
  <img alt="{{project}} logo" src="assets/logo.svg" width="180">
</picture>

# {{project}}

**{{tagline_zh}}**

[![License](https://img.shields.io/github/license/{{owner}}/{{repo}})](LICENSE) [![Version](https://img.shields.io/{{registry}}/v/{{package}})](https://...)  [![CI](https://github.com/{{owner}}/{{repo}}/actions/workflows/ci.yml/badge.svg)](.github/workflows) [![Discord](https://img.shields.io/discord/...?label=Discord)](https://discord.gg/...)

[文档]({{docs_url}}) · [Demo]({{demo_url}}) · [Discord]({{discord_url}}) · [English](README_en.md)

</div>

<p align="center">
  <img src="assets/hero.gif" alt="{{project}} demo" width="800">
  <!-- 占位：参考 docs/readme-image-plan.md 中 hero.gif 任务 -->
</p>

> **{{one_sentence_definition_zh}}**

```bash
{{quickstart_command}}
```
```

### English

```markdown
<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/logo-light.svg">
  <img alt="{{project}} logo" src="assets/logo.svg" width="180">
</picture>

# {{project}}

**{{tagline_en}}**

[badges...]

[Docs]({{docs_url}}) · [Demo]({{demo_url}}) · [Discord]({{discord_url}}) · [中文](README.md)

</div>

[hero visual...]

> **{{one_sentence_definition_en}}**

```bash
{{quickstart_command}}
```
```

---

## §2 What is {{project}}（推荐）

```markdown
## {{project}} 是什么？

{{2-3 句段落：先给品类锚点（"是 X 的开源替代"或"全新的 X 类工具"），再说 JTBD。}}

**它能做什么：**
- {{capability 1}}
- {{capability 2}}
- {{capability 3}}

**它不为谁服务：**
- {{anti-user 1}}：建议用 {{alternative}}
```

英文版：
```markdown
## What is {{project}}?

{{paragraph}}

**What it does:**
- ...

**When NOT to use {{project}}:**
- ...
```

---

## §3 Quick Start（必需）

### 简洁式（推荐）

```markdown
## 快速开始

```bash
{{single_command}}
```

不到 30 秒就能跑起来。如需其他平台/包管理器，见 [安装方式](#installation)。
```

### 折叠式（多平台时）

```markdown
## 快速开始

```bash
npm install {{package}}
```

<details>
<summary>其他安装方式</summary>

**pnpm**
```bash
pnpm add {{package}}
```

**yarn**
```bash
yarn add {{package}}
```

**Docker**
```bash
docker run {{image}}
```

**从源码**
```bash
git clone ... && cd ... && make
```

</details>
```

---

## §4 Features（推荐）

### Emoji bullet 风（适合 A 开发者工具型 / D 新品类教育型）

```markdown
## ✨ 主要特性

- ⚡ **{{feature_1_name}}** — {{1 句证据，含数字/截图链/代码}}
- 🔒 **{{feature_2_name}}** — {{...}}
- 🌍 **{{feature_3_name}}** — {{...}}
- 🛠 **{{feature_4_name}}** — {{...}}
- 📦 **{{feature_5_name}}** — {{...}}
- 🎯 **{{feature_6_name}}** — {{...}}
```

### Checkbox 风（适合 B 基础设施型）

```markdown
## 核心能力

- [x] **托管 Postgres 数据库** — [文档](docs/database)
- [x] **认证与授权** — Email / OAuth / Magic link [文档](docs/auth)
- [x] **实时订阅** — 数据库变更秒级推送 [文档](docs/realtime)
- [x] **存储** — 大文件上传、CDN 加速 [文档](docs/storage)
- [x] **Edge Functions** — 全球节点跑 TypeScript [文档](docs/functions)
- [ ] **AI 向量** —（roadmap，预计 v2.0）
```

### 卡片网格风（适合 C 消费/创作者工具型）

```markdown
## 功能一览

| | | |
|---|---|---|
| ![](assets/feat-1.png)<br>**{{feat_1}}**<br>{{1 句}} | ![](assets/feat-2.png)<br>**{{feat_2}}**<br>{{1 句}} | ![](assets/feat-3.png)<br>**{{feat_3}}**<br>{{1 句}} |
| ![](assets/feat-4.png)<br>**{{feat_4}}**<br>{{1 句}} | ![](assets/feat-5.png)<br>**{{feat_5}}**<br>{{1 句}} | ![](assets/feat-6.png)<br>**{{feat_6}}**<br>{{1 句}} |
```

---

## §5 Why {{project}} / 为什么选我们（推荐）

### 对比表式（已有竞品时）

```markdown
## 为什么选 {{project}}

| 维度 | {{project}} | {{competitor_1}} | {{competitor_2}} |
|---|---|---|---|
| {{dim_1}} | ✅ | ❌ | ⚠️ 部分 |
| {{dim_2}} | ✅ | ✅ | ❌ |
| {{dim_3}} | ✅ | ⚠️ 收费 | ❌ |
```

### 痛点叙事式（新品类时）

```markdown
## 为什么需要 {{project}}

**当前的痛**：{{描述用户在场景 X 中的痛苦}}

**现有方案的局限**：
- 方案 A：{{为什么不够}}
- 方案 B：{{为什么不够}}

**{{project}} 的解法**：{{核心思路 1 句话 + 1 个示例}}
```

---

## §6 Use Cases（C / D archetype 推荐）

```markdown
## 使用场景

### 场景 1：{{scenario_name}}

{{描述一个具体的"我是 X 角色，我用 {{project}} 做 Y"}}

### 场景 2：{{scenario_name}}
...
```

---

## §7 Architecture（B / D archetype 推荐）

```markdown
## 架构

![架构图](assets/architecture.svg)

或用 mermaid 自动渲染：

```mermaid
flowchart LR
    User[用户] --> CLI[{{project}} CLI]
    CLI --> Engine[核心引擎]
    Engine --> Plugins[插件系统]
    Engine --> Output[输出]
```
```

---

## §8 Adopters / Used by（如有）

```markdown
## 谁在用

<p align="center">
  <a href="https://example.com"><img src="assets/adopter-1.svg" height="40"></a>
  &nbsp;&nbsp;&nbsp;
  <a href="https://example.com"><img src="assets/adopter-2.svg" height="40"></a>
  ...
</p>

更多见 [ADOPTERS.md](ADOPTERS.md)。

> 在用 {{project}}？欢迎 [PR 添加你的 logo](https://github.com/...)。
```

---

## §9 Testimonials（如有）

```markdown
## 用户怎么说

> "{{quote 1}}"
> — **{{name 1}}**, {{title 1}} @ {{company 1}}

> "{{quote 2}}"
> — **{{name 2}}**, {{title 2}}

> "{{quote 3}}"
> — **{{name 3}}**
```

---

## §10 Star History（≥ 1k stars 时推荐）

```markdown
## Star History

[![Star History Chart](https://api.star-history.com/svg?repos={{owner}}/{{repo}}&type=Date)](https://star-history.com/#{{owner}}/{{repo}}&Date)
```

---

## §11 Contributors（开源项目推荐）

```markdown
## 贡献者

感谢所有贡献者！

<a href="https://github.com/{{owner}}/{{repo}}/graphs/contributors">
  <img src="https://contrib.rocks/image?repo={{owner}}/{{repo}}" />
</a>
```

---

## §12 Contributing（开源项目必需）

```markdown
## 参与贡献

我们欢迎任何形式的贡献！请先阅读 [CONTRIBUTING.md](CONTRIBUTING.md) 和 [Code of Conduct](CODE_OF_CONDUCT.md)。

**快速参与方式：**
- 🐛 报告 [Issue](https://github.com/{{owner}}/{{repo}}/issues)
- 💡 提交 Feature Request
- 📖 改进文档
- 💻 提交 Pull Request

加入 [Discord]({{discord}}) 与维护者直接交流。
```

---

## §13 国内特有元素（按需）

```markdown
## 加入社区

<table>
<tr>
<td align="center">
<b>微信群</b><br>
<img src="assets/wechat-group-qr.png" width="180"><br>
<sub>群满请加 <code>{{wx_id}}</code> 拉你进群</sub>
</td>
<td align="center">
<b>飞书群</b><br>
<img src="assets/lark-group-qr.png" width="180">
</td>
<td align="center">
<b>Discord</b><br>
<a href="{{discord}}">{{discord_short_url}}</a>
</td>
</tr>
</table>
```

国内云一键部署：

```markdown
## 一键部署

[![阿里云](https://img.shields.io/badge/阿里云-计算巢一键部署-FF6A00)]({{aliyun_url}})
[![Sealos](https://img.shields.io/badge/Sealos-Click_to_Deploy-2A2A2A)]({{sealos_url}})
[![Zeabur](https://img.shields.io/badge/Zeabur-Deploy-7B40ED)]({{zeabur_url}})
```

模型镜像（AI 项目）：

```markdown
## 模型下载

| 平台 | 链接 |
|---|---|
| 🤗 Hugging Face | [{{hf_link}}]({{hf_link}}) |
| 🌐 ModelScope | [{{ms_link}}]({{ms_link}}) |
| 📦 WiseModel | [{{wm_link}}]({{wm_link}}) |
```

---

## §14 License（必需）

```markdown
## License

[{{license_name}}](LICENSE) © {{year}} {{author}}
```

---

## Section 排序原则

- 必需 sections（Hero / Quick Start / License）位置不变
- 推荐 sections 按 archetype 决定的顺序（见 `archetypes.md`）
- "信任锚"类（adopters / testimonials）尽量插在 hero 与 features 之间
- "社区/参与"类放接近底部
- License 永远最后
