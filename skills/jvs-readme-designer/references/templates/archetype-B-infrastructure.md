# Archetype B：基础设施 / 平台型 骨架

适用：DB / BaaS / 云服务 / API gateway / 监控。

强调：大客户 logo 墙、硬核数字、架构图、Self-host vs Cloud 决策。

---

## 中文版骨架（README.md）

```markdown
<p align="center">[lang switcher]</p>

<div align="center">
[logo]

# {{project}}

**{{tagline_zh — 推荐"结果承诺型"或"硬核数字型"}}**

[License | Docker pulls | Stars | Discord — ≤6 枚 badges]

[文档] · [Cloud]({{cloud_url}}) · [GitHub] · [Discord]
</div>

<p align="center">
<img src="assets/hero.png" alt="{{project}}" width="900">
<!-- IMG: hero — 推荐放架构图或主控台截图 -->
</p>

> {{one_sentence_definition_zh}}

## 谁在用

<p align="center">
<a href="..."><img src="assets/adopters/customer1.svg" height="40"></a>
<a href="..."><img src="assets/adopters/customer2.svg" height="40"></a>
...
</p>

## 数字说话

| 指标 | 数据 |
|---|---|
| 处理请求量 | {{requests_per_day}} |
| Uptime | {{uptime}} |
| 部署节点 | {{nodes}} |
| 平均响应延迟 | {{latency}} |

数据来自 [status.{{domain}}]({{status_url}})。

## 核心能力

- [x] **{{capability_1}}** — {{evidence_1}} [→ 文档]({{doc_1}})
- [x] **{{capability_2}}** — {{evidence_2}} [→ 文档]({{doc_2}})
- [x] **{{capability_3}}** — {{evidence_3}} [→ 文档]({{doc_3}})
- [x] **{{capability_4}}** — {{evidence_4}} [→ 文档]({{doc_4}})
- [x] **{{capability_5}}** — {{evidence_5}} [→ 文档]({{doc_5}})
- [ ] **{{roadmap_item}}** —（roadmap，预计 {{eta}}）

## 架构

```mermaid
{{mermaid_arch_diagram}}
```

或见 [完整架构图](assets/architecture.svg)。

## 快速开始

### Self-host

```bash
{{self_host_command}}
```

### Cloud

5 分钟跑起来：[{{cloud_signup_url}}]({{cloud_signup_url}})

| | Self-host | Cloud |
|---|---|---|
| 维护 | 你来 | 我们 |
| 起步成本 | 服务器费用 | 免费额度 |
| 扩展性 | 自行处理 | 自动 |
| 数据控制 | 完全 | 由我们托管 |

## 行业用例

{{use_case_paragraphs}}

## 文档

[{{docs_url}}]({{docs_url}})

## 参与贡献

{{community_section}}

## License

[{{license}}](LICENSE)
```

---

## English version skeleton (README_en.md)

```markdown
<p align="center">
  <a href="README.md"><img alt="中文" src="https://img.shields.io/badge/lang-中文-blue?style=flat-square"></a>
  &nbsp;
  <img alt="English (current)" src="https://img.shields.io/badge/lang-English-red?style=flat-square">
</p>

<div align="center">
[logo with picture/srcset]

# {{project}}

**{{tagline_en — outcome-promise or hard-numbers formula recommended}}**

[badges — License | Docker pulls | Stars | Discord — ≤6]

[Docs] · [Cloud]({{cloud_url}}) · [GitHub] · [Discord]
</div>

<p align="center">
<img src="assets/hero.png" alt="{{project}}" width="900">
</p>

> {{one_sentence_definition_en}}

## Trusted by

<p align="center">
<a href="..."><img src="assets/adopters/{{adopter_1_slug}}.svg" height="40"></a>
<a href="..."><img src="assets/adopters/{{adopter_2_slug}}.svg" height="40"></a>
...
</p>

## By the numbers

| Metric | Value |
|---|---|
| Requests / day | {{requests_per_day}} |
| Uptime | {{uptime}} |
| Deployment nodes | {{nodes}} |
| Avg latency | {{latency}} |

Live data: [status.{{domain}}]({{status_url}}).

## Capabilities

- [x] **{{capability_1}}** — {{evidence_1_en}} [→ Docs]({{doc_1}})
- [x] **{{capability_2}}** — {{evidence_2_en}} [→ Docs]({{doc_2}})
- [x] **{{capability_3}}** — {{evidence_3_en}} [→ Docs]({{doc_3}})
- [x] **{{capability_4}}** — {{evidence_4_en}} [→ Docs]({{doc_4}})
- [x] **{{capability_5}}** — {{evidence_5_en}} [→ Docs]({{doc_5}})
- [ ] **{{roadmap_item}}** — (roadmap, ETA {{eta}})

## Architecture

```mermaid
{{mermaid_arch_diagram}}
```

Or see [full architecture](assets/architecture.svg).

## Quick Start

### Self-host

```bash
{{self_host_command}}
```

### Cloud

5-minute setup: [{{cloud_signup_url}}]({{cloud_signup_url}})

| | Self-host | Cloud |
|---|---|---|
| Maintenance | You | Us |
| Cost | Server fees | Free tier |
| Scaling | Manual | Auto |
| Data control | Full | Hosted |

## Industry use cases

{{use_case_paragraphs_en}}

## Documentation

[{{docs_url}}]({{docs_url}})

## Community

{{community_section}}

## License

[{{license}}](LICENSE)
```

