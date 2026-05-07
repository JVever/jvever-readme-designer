# Archetype A：开发者工具型 骨架

适用：CLI / SDK / IDE 插件 / 库 / DevTools。

`{{var}}` 是 Skill 在生成时用 INTERVIEW + SCAN 的回答替换的占位符。

---

## 中文版骨架（README.md）

```markdown
<!-- 当前语言（中文）badge 不带 <a>，避免 silent fail；仅切换目标语言才用链接 -->
<p align="center">
  <img alt="中文（当前）" src="https://img.shields.io/badge/lang-中文-red?style=flat-square">
  &nbsp;
  <a href="README_en.md"><img alt="English" src="https://img.shields.io/badge/lang-English-blue?style=flat-square"></a>
</p>

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/logo-light.svg">
  <img alt="{{project}} logo" src="assets/logo.svg" width="180">
</picture>

# {{project}}

**{{tagline_zh}}**

[![License](https://img.shields.io/github/license/{{owner}}/{{repo}})](LICENSE) [![Version]({{version_badge}})]({{registry_url}}) [![CI](https://github.com/{{owner}}/{{repo}}/actions/workflows/ci.yml/badge.svg)](.github/workflows) [![Downloads]({{downloads_badge}})]({{registry_url}}) [![Discord]({{discord_badge}})]({{discord_url}})

[文档]({{docs_url}}) · [Demo]({{demo_url}}) · [Changelog](CHANGELOG.md) · [Discord]({{discord_url}})

</div>

<p align="center">
  <img src="assets/hero.gif" alt="{{project}} demo" width="800">
  <!-- IMG: hero — 见 docs/readme-image-plan.md -->
</p>

> {{one_sentence_definition_zh}}

```bash
{{quickstart_command}}
```

---

## 为什么需要 {{project}}

{{pas_paragraph_zh — 用 PAS 框架：当前的痛 → 现有方案的局限 → 我们的解法}}

## ✨ 主要特性

- **{{feature_1_emoji}} {{feature_1_name}}** — {{feature_1_evidence}}
- **{{feature_2_emoji}} {{feature_2_name}}** — {{feature_2_evidence}}
- **{{feature_3_emoji}} {{feature_3_name}}** — {{feature_3_evidence}}
- **{{feature_4_emoji}} {{feature_4_name}}** — {{feature_4_evidence}}
- **{{feature_5_emoji}} {{feature_5_name}}** — {{feature_5_evidence}}

## 快速开始

最简单的方式：

```bash
{{primary_install_command}}
```

<details>
<summary>其他安装方式</summary>

{{alternative_install_methods}}

</details>

跑起来：

```bash
{{first_run_command}}
```

详见 [快速上手指南]({{quickstart_doc_url}})。

## 与同类工具对比

{{comparison_table_or_paragraph}}

## 谁在用

{{adopters_section_or_omit}}

## 用户怎么说

{{testimonials_section_or_omit}}

## 文档

完整文档见 [{{docs_url}}]({{docs_url}})。

## 参与贡献

我们欢迎任何形式的贡献。请先阅读 [CONTRIBUTING.md](CONTRIBUTING.md)。

{{community_section}}

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos={{owner}}/{{repo}}&type=Date)](https://star-history.com/#{{owner}}/{{repo}}&Date)

## License

[{{license}}](LICENSE) © {{year}} {{author}}
```

---

## English version skeleton (README_en.md)

```markdown
<!-- 当前语言（English）badge 不带 <a>；仅切换到中文才用链接 -->
<p align="center">
  <a href="README.md"><img alt="中文" src="https://img.shields.io/badge/lang-中文-blue?style=flat-square"></a>
  &nbsp;
  <img alt="English (current)" src="https://img.shields.io/badge/lang-English-red?style=flat-square">
</p>

<div align="center">

[logo with picture/srcset]

# {{project}}

**{{tagline_en}}**

[badges]

[Docs]({{docs_url}}) · [Demo]({{demo_url}}) · [Changelog](CHANGELOG.md) · [Discord]({{discord_url}})

</div>

[hero gif]

> {{one_sentence_definition_en}}

```bash
{{quickstart_command}}
```

---

## Why {{project}}

{{pas_paragraph_en}}

## ✨ Features

- **{{feature_1_emoji}} {{feature_1_name}}** — {{feature_1_evidence_en}}
- ...

## Quick Start

```bash
{{primary_install_command}}
```

<details>
<summary>Other install methods</summary>
{{alternative_install_methods}}
</details>

```bash
{{first_run_command}}
```

See [Quickstart guide]({{quickstart_doc_url}}).

## Compared to alternatives

{{comparison_table_or_paragraph_en}}

## Who's using {{project}}

{{adopters_section_or_omit}}

## What users say

{{testimonials_section_or_omit}}

## Documentation

Full docs at [{{docs_url}}]({{docs_url}}).

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Star History

[chart]

## License

[{{license}}](LICENSE) © {{year}} {{author}}
```
