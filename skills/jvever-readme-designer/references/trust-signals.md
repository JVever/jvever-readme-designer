# 14 种信任信号 + 模板

README 的核心 KPI 之一是建立信任。"项目能用、还活着、社区健康"是访客最关心的。

---

## 信任信号清单（按权重）

| # | 信号 | 强度 | 实现方式 |
|---|---|---|---|
| 1 | **大客户 / Adopters logo 墙** | ⭐⭐⭐⭐⭐ | 真实公司 logo（如 OpenHands "Trusted by TikTok/VMware/Apple"）|
| 2 | **可识别名人 testimonial** | ⭐⭐⭐⭐⭐ | Cursor: 黄仁勋/Karpathy/Collison |
| 3 | **客户成果数字** | ⭐⭐⭐⭐⭐ | Vercel "build 7m → 40s" |
| 4 | **CI 通过 badge** | ⭐⭐⭐⭐ | shields.io 自动反映状态 |
| 5 | **stars / downloads / DAU** | ⭐⭐⭐⭐ | npm/PyPI/Docker 自动 badge |
| 6 | **真实 logo + 真实截图** | ⭐⭐⭐⭐ | 反对纯文字 README |
| 7 | **License + SPDX 标识** | ⭐⭐⭐⭐ | 缺失即"企业 pass" |
| 8 | **Last release 日期** | ⭐⭐⭐⭐ | 半年内有 release 是基本线 |
| 9 | **Contributors 头像墙** | ⭐⭐⭐ | contrib.rocks 自动生成 |
| 10 | **Sponsors 区** | ⭐⭐⭐ | OpenCollective / GitHub Sponsors，证明商业模型 |
| 11 | **Code coverage** | ⭐⭐⭐ | 工程严肃度 |
| 12 | **Security policy** | ⭐⭐⭐ | SECURITY.md 链接 |
| 13 | **Changelog** | ⭐⭐⭐ | 透明的演进 |
| 14 | **Code of Conduct** | ⭐⭐ | 社区成熟度 |

---

## Badges 的最佳实践

### 数量：≤6 枚

成熟项目反而徽章少（Tailwind 4 枚、shadcn 0 枚）。**不是堆得多就专业**。

### 推荐组合

#### 组合 A：通用开源项目
```markdown
[![License](https://img.shields.io/github/license/owner/repo)](LICENSE)
[![Version](https://img.shields.io/npm/v/package)](https://www.npmjs.com/package/package)
[![CI](https://github.com/owner/repo/actions/workflows/ci.yml/badge.svg)](.github/workflows)
[![Downloads](https://img.shields.io/npm/dm/package)](https://www.npmjs.com/package/package)
[![Discord](https://img.shields.io/discord/...?label=Discord)](https://discord.gg/...)
```

#### 组合 B：AI / 模型项目
```markdown
[![License](https://img.shields.io/github/license/owner/repo)](LICENSE)
[![Hugging Face](https://img.shields.io/badge/🤗-Hugging_Face-FFD21E)](https://huggingface.co/...)
[![ModelScope](https://img.shields.io/badge/魔搭-ModelScope-blue)](https://modelscope.cn/...)
[![Trendshift](https://trendshift.io/api/badge/repositories/...)](https://trendshift.io/...)
```

#### 组合 C：基础设施型
```markdown
[![License](https://img.shields.io/github/license/owner/repo)](LICENSE)
[![Docker Pulls](https://img.shields.io/docker/pulls/owner/repo)](https://hub.docker.com/r/owner/repo)
[![Stars](https://img.shields.io/github/stars/owner/repo?style=social)](https://github.com/owner/repo)
[![Discord](...)](...)
[![Production Status](https://img.shields.io/uptimerobot/status/m...)](https://...)
```

### 反模式

- **超过 8 枚**：扫读时稀释重点
- **重复信息**：stars + watchers + forks + contributors 全堆，意义稀释
- **过期 badge**：CI 红 / version 落后 / coverage 0% 反成劝退
- **shields.io 在国内慢**：考虑用阿里 OSS / 七牛镜像（少数项目这样做）

---

## Adopters logo 墙模板

> ⚠️ **硬规则**：占位符必须用 `{{adopter_n_*}}` 变量，**不要写 stripe / vercel / shopify 这类真实公司名**——一旦不替换会变成"我们的客户是 Stripe"的伪信号。如果用户答 Q6 没有 Adopters，**整段不渲染**。

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

**注意事项**：
- 真实存在 + 已获用户授权
- SVG 优先（缩放清晰）
- 高度统一（40-50px）
- 排序：按知名度，从最响的开始
- 至少 5 个，少了显寒酸；多于 12 个建议挪到 ADOPTERS.md

---

## Testimonials 模板

```markdown
## 用户怎么说

<table>
<tr>
<td width="33%" align="left">
  <img src="assets/avatar/jensen.jpg" width="60" align="left" style="border-radius: 50%; margin-right: 12px;">
  <b>Jensen Huang</b><br>
  <sub>CEO, NVIDIA</sub>
  <p>"{{quote}}"</p>
</td>
<td width="33%" align="left">...</td>
<td width="33%" align="left">...</td>
</tr>
</table>
```

⚠️ 注意 GitHub markdown sanitizer 会剥掉 `<img style="...">` 中的 `style` 属性，所以模板里的 `border-radius: 50%`（圆形头像）在 GitHub 不生效。如果需要圆形头像，建议直接预处理为圆形 PNG（用 Figma / Photoshop）再放到 `assets/avatar/`。

**或纯 markdown 版（兼容性更好）**：

```markdown
## 用户怎么说

> "我把 80% 的 IDE 使用换成了 Aider。"
> — **Eric S. Raymond**, [@esr](https://twitter.com/esr)

> "Cursor 是我用过最有效的代码编辑器。"
> — **Andrej Karpathy**, ex-Tesla AI Director

> "Linear 把我们团队的 velocity 提升了 2 倍。"
> — **Patrick Collison**, CEO @ Stripe
```

**约束**：
- 至少 3 条，超过 5 条考虑外链 / 折叠
- 每条带：人名 + title + 公司（至少 2 项）
- 头像可选；有则增加可信度
- 引言 ≤ 2 句话
- **不要伪造**——被发现是社区死刑

---

## 客户成果数字模板

```markdown
## 实际效果

<div align="center">

| 项目 | 改进前 | 改进后 | 提升 |
|---|---|---|---|
| Vercel build | 7m 12s | 40s | **-91%** |
| Cold start | 850ms | 120ms | **-86%** |
| 内存占用 | 512MB | 64MB | **-87%** |

数据来自 [docs/benchmarks.md](docs/benchmarks.md)。

</div>
```

**约束**：
- 数字必须可验证（链接到 benchmark 文档）
- 至少 3 个数字（少了显单薄）
- 用百分比 + 绝对值组合（"-91% (从 7m 12s 到 40s)"）
- 不要"行业领先"这类无锚点表述

---

## Star History 模板

```markdown
## Star History

[![Star History Chart](https://api.star-history.com/svg?repos={{owner}}/{{repo}}&type=Date)](https://star-history.com/#{{owner}}/{{repo}}&Date)
```

**何时用**：
- ≥1k stars 才放（少于这个反成"显穷"）
- 多 repo 项目可以放对比图

---

## Contributors 头像墙模板

```markdown
## 贡献者

<a href="https://github.com/{{owner}}/{{repo}}/graphs/contributors">
  <img src="https://contrib.rocks/image?repo={{owner}}/{{repo}}" alt="contributors" />
</a>

Made with [contrib.rocks](https://contrib.rocks).
```

**注意**：
- 自动更新，零维护
- 最适合 ≥10 个贡献者的项目（少了头像墙不饱满）

---

## Sponsors 模板

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
  <a href="https://example.com"><img src="assets/sponsor-1.svg" height="50"></a>
  ...
</p>
```

---

## 反信号清单（避免出现）

- ❌ Last commit > 1 年前（GitHub 自动显示，README 无法掩盖）
- ❌ Issue 堆积 100+ 无人回应
- ❌ CI badge 是红的
- ❌ License 缺失或 "All rights reserved"
- ❌ README 充满 `<!-- TODO -->`
- ❌ 命令复制粘贴跑不起来（README 与代码不同步）
- ❌ 假/失效 badges（"Build failing" 一直挂着）
- ❌ Roadmap 里写了一堆"将来 / 计划"但没有日期 / issue 链接
