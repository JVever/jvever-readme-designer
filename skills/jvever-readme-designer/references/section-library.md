# Section 模板库

**唯一真理源**——所有 archetype 拼装时都从这里取 section 模板。

每个 section 给中英双版骨架。生成时按 archetype 选用，按条件渲染规则决定是否出现。

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

## §8 Adopters / Used by（条件渲染：用户提供 ≥3 个真实 adopters 才出）

> **真实性硬规则**：占位符必须用 `{{adopter_n_*}}` 变量；**不要写 stripe / vercel / shopify 这类真实公司名**——一旦不替换会变成"我们的客户是 Stripe"的伪信号。如果用户没有真实 adopters，**整段不渲染**。

```markdown
## 谁在用

<p align="center">
  <a href="{{adopter_1_url}}" target="_blank"><img src="assets/adopters/{{adopter_1_slug}}.svg" height="40" alt="{{adopter_1_name}}"></a>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <a href="{{adopter_2_url}}" target="_blank"><img src="assets/adopters/{{adopter_2_slug}}.svg" height="40" alt="{{adopter_2_name}}"></a>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <a href="{{adopter_3_url}}" target="_blank"><img src="assets/adopters/{{adopter_3_slug}}.svg" height="40" alt="{{adopter_3_name}}"></a>
</p>

> 完整名单见 [ADOPTERS.md](ADOPTERS.md)。在用 {{project}}？欢迎 [PR 添加你的 logo]({{adopters_pr_url}})。
```

**约束**：
- 真实存在 + 已获用户授权
- SVG 优先（缩放清晰）
- 高度统一（40-50px）
- 排序：按知名度，从最响的开始
- 至少 5 个，少了显寒酸；多于 12 个建议挪到 ADOPTERS.md

---

## §9 Testimonials（条件渲染：用户提供 ≥2 条真实引言才出）

### 纯 markdown 版（兼容性最好，推荐）

```markdown
## 用户怎么说

> "{{quote_1}}"
> — **{{name_1}}**, {{title_1}} @ {{company_1}}

> "{{quote_2}}"
> — **{{name_2}}**, {{title_2}}

> "{{quote_3}}"
> — **{{name_3}}**
```

### Table 版（含头像）

```markdown
## 用户怎么说

<table>
<tr>
<td width="33%" align="left">
  <img src="assets/avatar/{{slug_1}}.jpg" width="60" align="left">
  <b>{{name_1}}</b><br>
  <sub>{{title_1}}, {{company_1}}</sub>
  <p>"{{quote_1}}"</p>
</td>
<td width="33%" align="left">...</td>
<td width="33%" align="left">...</td>
</tr>
</table>
```

⚠️ GitHub markdown sanitizer 会剥掉 `<img style="...">` 中的 `style` 属性，圆形头像（`border-radius: 50%`）在 GitHub 不生效。如需圆形头像，预处理为圆形 PNG。

**约束**：
- 至少 3 条；超过 5 条折叠或外链
- 每条含人名 + title + 公司（至少 2 项）
- 引言 ≤ 2 句
- **绝不伪造**——被发现是社区死刑

---

## §10 Numbers / 客户成果数字（条件渲染：用户提供可验证 benchmark 才出）

```markdown
## 实际效果

<div align="center">

| 项目 | 改进前 | 改进后 | 提升 |
|---|---|---|---|
| {{metric_1}} | {{before_1}} | {{after_1}} | **{{improvement_1}}** |
| {{metric_2}} | {{before_2}} | {{after_2}} | **{{improvement_2}}** |
| {{metric_3}} | {{before_3}} | {{after_3}} | **{{improvement_3}}** |

数据来自 [docs/benchmarks.md](docs/benchmarks.md)。

</div>
```

**约束**：
- 数字必须可验证（链接到 benchmark 文档）
- 至少 3 个数字（少了单薄）
- 用百分比 + 绝对值组合（"-91% (从 7m 12s 到 40s)"）
- 拒绝"行业领先"这类无锚点表述

---

## §11 Star History（条件渲染：≥1k stars 才出）

```markdown
## Star History

[![Star History Chart](https://api.star-history.com/svg?repos={{owner}}/{{repo}}&type=Date)](https://star-history.com/#{{owner}}/{{repo}}&Date)
```

少于 1k stars 不要放——反成"显穷"信号。

---

## §12 Contributors（条件渲染：≥10 contributor 才出）

```markdown
## 贡献者

<a href="https://github.com/{{owner}}/{{repo}}/graphs/contributors">
  <img src="https://contrib.rocks/image?repo={{owner}}/{{repo}}" alt="contributors" />
</a>

Made with [contrib.rocks](https://contrib.rocks).
```

自动更新，零维护。少于 10 个贡献者头像墙不饱满，不要放。

---

## §13 Sponsors（条件渲染：用户明确说有 sponsorship 才出）

```markdown
## 赞助 & 支持

{{project}} 由 [GitHub Sponsors](https://github.com/sponsors/{{owner}}) 与 [OpenCollective](https://opencollective.com/{{project}}) 支持。

<p align="center">
  <a href="https://github.com/sponsors/{{owner}}">
    <img src="https://opencollective.com/{{project}}/backers.svg?width=890" />
  </a>
</p>

特别鸣谢以下赞助商：

<p align="center">
  <a href="{{sponsor_1_url}}"><img src="assets/sponsor-1.svg" height="50"></a>
</p>
```

---

## §14 Contributing（开源项目必需）

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

## §15 国内特有元素（条件渲染：项目主语种为中文 + 用户确认时按需组合）

国内项目相比国际项目，README 通常多出"本地化生态对接"元素。下列各小节按需启用，不必全用。

### 15.1 社群入口

```markdown
## 加入社区

<table>
<tr>
<td align="center" width="33%">
<b>微信群</b><br>
<img src="assets/wechat-group-qr.png" width="180"><br>
<sub>群满请加 <code>{{wx_id}}</code> 备注 GitHub 拉你进群</sub>
</td>
<td align="center" width="33%">
<b>飞书群</b><br>
<img src="assets/lark-group-qr.png" width="180">
</td>
<td align="center" width="33%">
<b>QQ 群</b><br>
<code>{{qq_group_id}}</code><br>
<sub><a href="{{qq_join_link}}">点击加入</a></sub>
</td>
</tr>
</table>
```

**关键约束**：群二维码会过期 / 群会满，**必须同时给文字补救**（微信号 / QQ 群号），不能只放二维码。

### 15.2 微信公众号

```markdown
关注公众号「{{name}}」获取更新：

<img src="assets/wechat-official-qr.png" width="180">
```

### 15.3 国内云一键部署

```markdown
## 一键部署

<a href="{{aliyun_url}}"><img src="https://img.shields.io/badge/阿里云-计算巢一键部署-FF6A00"></a>
<a href="{{sealos_url}}"><img src="https://cdn.jsdelivr.net/gh/labring-actions/templates@main/Deploy-on-Sealos.svg"></a>
<a href="{{zeabur_url}}"><img src="https://zeabur.com/button.svg"></a>
```

主要平台：阿里云计算巢 / Sealos / Zeabur / 腾讯云 / 火山引擎 / 华为云 / 1Panel。

### 15.4 模型镜像（AI 项目特有）

国内 AI 项目几乎必给多个模型仓库，因为 HuggingFace 国内访问慢：

```markdown
## 模型下载

| 平台 | 链接 | 适用 |
|---|---|---|
| 🤗 Hugging Face | [{{hf_link}}]({{hf_link}}) | 海外用户 |
| 🌐 ModelScope（魔搭） | [{{ms_link}}]({{ms_link}}) | 国内首选 |
| 📦 WiseModel | [{{wm_link}}]({{wm_link}}) | 国内备用 |
| 🔬 OpenXLab | [{{xlab_link}}]({{xlab_link}}) | 学术友好 |
```

### 15.5 国内镜像仓库

```markdown
## 国内镜像

代码镜像（同步 GitHub）：
- [Gitee](https://gitee.com/{{owner}}/{{repo}})
- [GitCode](https://gitcode.com/{{owner}}/{{repo}})
- [Atomgit](https://atomgit.com/{{owner}}/{{repo}})

文档镜像：
- [Yuque（语雀）](https://www.yuque.com/{{owner}}/{{book}})
- [中文文档（自建域名）]({{docs_zh_cn}})
```

### 15.6 演示视频（Bilibili 优于 YouTube）

```markdown
## 演示视频

[![Bilibili 演示](assets/bilibili-thumbnail.png)](https://www.bilibili.com/video/{{bv}})

或观看 [YouTube 版](https://www.youtube.com/watch?v={{yt_id}})。
```

### 15.7 Windows 整合包（一键启动，常见于 AI 项目）

```markdown
## Windows 整合包（一键启动）

无需配 Python 环境，下载即可双击运行：

| 版本 | 下载 | 大小 |
|---|---|---|
| v{{version}} (CUDA 12) | [百度网盘]({{bdy_url}}) / [HuggingFace]({{hf_url}}) / [ModelScope]({{ms_url}}) | 4.2 GB |
| v{{version}} (CPU only) | 同上 | 3.8 GB |

下载后解压，双击 `start.bat` 启动。
```

### 15.8 商业版 / 商业咨询入口

```markdown
## 商业版

{{project}} 提供企业版（私有化部署 + 技术支持 + SLA），请联系：

- 商业邮箱：[business@{{domain}}](mailto:business@{{domain}})
- 商业咨询表单：[飞书表单]({{lark_form}})
- 微信：{{biz_wx}}
```

### 15.9 国内排行榜 badge

```markdown
[![Trendshift](https://trendshift.io/api/badge/repositories/{{repo_id}})](https://trendshift.io/repositories/{{repo_id}})
```

类似的：HelloGitHub 月榜 / 开源中国（OSCHINA）热门 / 知乎技术榜。

### 15.10 知乎 / 掘金 / Bilibili 链接

```markdown
## 阅读更多

- [项目设计哲学（知乎专栏）](https://zhuanlan.zhihu.com/p/{{id}})
- [技术细节（掘金）](https://juejin.cn/post/{{id}})
- [Bilibili 教学频道](https://space.bilibili.com/{{uid}})
```

### 15.11 情怀型开场（少用）

部分国内项目用文化锚点开场（如毕昇活字、敦煌、二十四节气）。**注意**：必须有真实文化共鸣，强行套用反成减分项。

---

## §16 License（必需）

```markdown
## License

[{{license_name}}](LICENSE) © {{year}} {{author}}
```

---

## Section 排序原则

- 必需 sections（Hero / Quick Start / License）位置不变
- 推荐 sections 按 archetype 决定的顺序（见 [`archetypes.md`](archetypes.md)）
- "信任锚"类（adopters / testimonials / numbers）尽量插在 hero 与 features 之间
- "社区/参与"类放接近底部
- 国内特有 section 通常放在 contributing 之前 或 license 之前
- License 永远最后
