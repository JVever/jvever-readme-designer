# Archetype D：新品类教育型 骨架

适用：LLM agent 框架 / 全新概念 / 没有同类参照物的项目。

强调：拟人化定位、视频 demo、详细解释"我是什么"、架构图、"why not X" 段。

---

## 中文版骨架（README.md）

```markdown
<p align="center">[lang switcher]</p>

<div align="center">
[logo]

# {{project}}

**{{tagline_zh — 推荐"拟人/隐喻型"}}**

[badges]

[文档]({{docs}}) · [视频 Demo]({{video}}) · [Discord]({{discord}})
</div>

<p align="center">
<img src="assets/hero-thumbnail.png" alt="{{project}} 演示视频" width="800">
<!-- IMG: hero — 推荐放可点击的视频缩略图，链接到 YouTube/Bilibili -->
</p>

> {{one_sentence_definition_zh — 用熟悉事物作类比}}

## {{project}} 是什么

{{paragraph_1_zh — 用 1 段话给出品类锚点}}

{{paragraph_2_zh — 用 1 个具体场景说明能做什么}}

{{paragraph_3_zh — 给出"为什么需要这个新概念"}}

## 核心能力

### {{capability_1}}

![]({{cap1_img}})

{{cap1_paragraph_zh}}

### {{capability_2}}

![]({{cap2_img}})

{{cap2_paragraph_zh}}

### {{capability_3}}

![]({{cap3_img}})

{{cap3_paragraph_zh}}

### {{capability_4}}

![]({{cap4_img}})

{{cap4_paragraph_zh}}

## 架构与原理

```mermaid
{{mermaid_diagram}}
```

详细原理见 [How {{project}} works]({{how_it_works_doc}})。

## 试着这样用

```bash
{{example_1_command}}
```

```bash
{{example_2_command}}
```

更多示例：[examples/]({{examples_path}})。

## 为什么不是 {{existing_solution}}？

{{comparison_paragraph_zh — 直面对比，给出何时该用哪个}}

| 场景 | {{project}} | {{existing_solution}} |
|---|---|---|
| {{scenario_1}} | ✅ | ❌ |
| {{scenario_2}} | ✅ | ⚠️ 部分 |
| {{scenario_3}} | ⚠️ | ✅ |

## 快速开始

```bash
{{quickstart_command}}
```

详见 [快速上手]({{quickstart_doc}})。

## 社区

{{community_section}}

## License

[{{license}}](LICENSE)
```

---

## English version skeleton (README_en.md)

```markdown
<p align="center">[lang switcher with English current]</p>

<div align="center">
[logo]

# {{project}}

**{{tagline_en — anthropomorphic / metaphor formula recommended}}**

[badges]

[Docs]({{docs}}) · [Video Demo]({{video}}) · [Discord]({{discord}})
</div>

<p align="center">
<img src="assets/hero-thumbnail.png" alt="{{project}} demo" width="800">
</p>

> {{one_sentence_definition_en — use familiar metaphor}}

## What is {{project}}

{{paragraph_1_en — provide category anchor}}

{{paragraph_2_en — concrete scenario showing what it can do}}

{{paragraph_3_en — why this new concept is needed}}

## Capabilities

### {{capability_1}}

![]({{cap1_img}})

{{cap1_paragraph_en}}

### {{capability_2}}

![]({{cap2_img}})

{{cap2_paragraph_en}}

### {{capability_3}}

![]({{cap3_img}})

{{cap3_paragraph_en}}

### {{capability_4}}

![]({{cap4_img}})

{{cap4_paragraph_en}}

## Architecture & how it works

```mermaid
{{mermaid_diagram}}
```

Deep dive: [How {{project}} works]({{how_it_works_doc}}).

## Try it

```bash
{{example_1_command}}
```

```bash
{{example_2_command}}
```

More: [examples/]({{examples_path}}).

## Why not {{existing_solution}}?

{{comparison_paragraph_en — direct comparison}}

| Scenario | {{project}} | {{existing_solution}} |
|---|---|---|
| {{scenario_1}} | ✅ | ❌ |
| {{scenario_2}} | ✅ | ⚠️ partial |
| {{scenario_3}} | ⚠️ | ✅ |

## Quick Start

```bash
{{quickstart_command}}
```

See [Getting started]({{quickstart_doc}}).

## Community

{{community_section}}

## License

[{{license}}](LICENSE)
```

