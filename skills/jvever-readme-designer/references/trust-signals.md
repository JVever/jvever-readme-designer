# 信任信号清单 + 条件渲染规则

README 的核心 KPI 之一是建立信任："项目能用、还活着、社区健康"是访客最关心的。

> **职责说明**：本文件管"哪些是信任信号、什么时候才该渲染、如何避免伪信任"。具体模板（adopters logo 墙、testimonials、numbers、star history、contributors、sponsors）全部在 [`section-library.md`](section-library.md) §8-§13。

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

## 条件渲染规则（决定哪些信号 section 真的出现）

| Section | 渲染条件 | 模板位置 |
|---|---|---|
| Adopters logo 墙 | 用户提供 ≥3 个真实 adopters（含名称 + URL + 授权确认） | `section-library.md` §8 |
| Testimonials | 用户提供 ≥2 条真实引言（含人名 + title，至少 2 项可识别身份信息） | `section-library.md` §9 |
| Numbers / 客户成果 | 用户提供可验证 benchmark 数字（链接到 benchmark 文档或第三方报告） | `section-library.md` §10 |
| Star History | 项目 ≥1k stars | `section-library.md` §11 |
| Contributors 头像墙 | 项目 ≥10 contributors | `section-library.md` §12 |
| Sponsors | 用户明确说有 OpenCollective / GitHub Sponsors / 私募赞助商 | `section-library.md` §13 |
| 国内社群（微信/飞书 QR） | SCAN 检测中文为主语种 + 用户在 INTERVIEW 确认愿意放群 | `section-library.md` §15.1 |

**不满足条件的 section 不渲染**——避免"50 stars 项目放 Star History 反成显穷"，"3 个贡献者放 contributors 头像墙不饱满"。

---

## 真实性硬规则（绝不允许 Skill 伪造）

- **Adopters**：真实存在 + 已获用户授权。占位符必须用 `{{adopter_n_*}}` 变量；**不允许写 stripe / vercel / shopify 等真实公司名**作为示例占位（一旦不替换会变成"我们的客户是 Stripe"的伪信号）
- **Testimonials**：**绝不伪造**——被发现是社区死刑。引言必须由用户提供 + 含可识别人名 + title；不允许"占位引言 + 伪人名"
- **Numbers**：数字必须可验证（链接到 benchmark 文档或第三方报告）；不允许"待补充" / "N/A" / "行业领先"等无锚点表述
- **Stars / downloads / DAU**：通过 shields.io 自动 URL 拉取，Skill **不写入字面数字**

如果用户在 INTERVIEW 阶段未提供任何信任锚，**Adopters / Testimonials / Numbers 整段不渲染**（不做"占位假冒"兜底）。

---

## Badges 最佳实践

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

### Badge 反模式

- **超过 8 枚**：扫读时稀释重点
- **重复信息**：stars + watchers + forks + contributors 全堆，意义稀释
- **过期 badge**：CI 红 / version 落后 / coverage 0% 反成劝退
- **shields.io 在国内慢**：考虑用阿里 OSS / 七牛镜像（少数项目这样做）

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
