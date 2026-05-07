# INTERVIEW 答案 → 模板变量映射表

让 Skill 在 DRAFT 阶段把用户的访谈回答精确填入模板，避免黑箱推测。

---

## 映射表

| INTERVIEW 问题 | 模板变量 | 出现位置 |
|---|---|---|
| Q1 一句话定位 | `{{tagline_zh}}` / `{{tagline_en}}` | Hero 区 H1 之下 |
| Q2 目标用户 | `{{target_audience_zh}}` / `{{target_audience_en}}` | Hero 区第二段 + Why 段 |
| Q3 核心 job + 痛 | `{{pas_paragraph_zh}}` / `{{pas_paragraph_en}}`、`{{one_sentence_definition_zh}}` | Hero 之后 / Why 段 |
| Q4 差异化 | `{{comparison_table_or_paragraph}}` | Why 段 / "Compared to alternatives" 段 |
| Q5 使用场景 | `{{use_case_paragraphs}}`（数组）| Use cases 段 |
| Q6 信任锚 | 多变量（见下表） | Adopters / Testimonials / Numbers 段 |
| Q7 主 CTA | `{{primary_cta_text}}` + Hero 区 nav 顺序 | Hero 区 + 页脚 |
| 双语策略 | 决定使用 M1/M2/M3/M4 + 切换条 | 全文 |
| 国内元素 | 决定是否渲染 domestic-community / mirror / one-click-deploy | 收尾段 |

---

## Q6 信任锚 → 多变量分发

| 信任锚类型（多选） | 模板变量 |
|---|---|
| A. 大客户 / Adopters | `{{adopter_1_name}}`, `{{adopter_1_url}}`, `{{adopter_1_logo_path}}`（用户自己提供 SVG）... |
| B. 名人 testimonial | `{{testimonial_n_quote}}`, `{{testimonial_n_name}}`, `{{testimonial_n_title}}` |
| C. Benchmark 数字 | `{{benchmark_table_rows}}`（数组：metric / before / after / improvement） |
| D. 用户量级 | `{{user_count}}`（如 "100M users / 700k developers"），渲染到 hero 副线或独立数字带 |
| E. 奖项 / 排行榜 | badge 行追加 + 可选独立 awards 段 |
| F. 暂无 | 不渲染相关 section（重要：**不允许伪造**） |

---

## SCAN 信号 → 模板变量

| SCAN 提取 | 模板变量 |
|---|---|
| `package.json` `name` | `{{project}}`, `{{package}}` |
| GitHub remote owner/repo | `{{owner}}`, `{{repo}}` |
| `LICENSE` SPDX | `{{license}}`（不存在时填 "TBD"，不写 broken link） |
| `package.json` `homepage` | `{{docs_url}}` 候选（用户可改） |
| 入口形态 | 决定 `{{quickstart_command}}`（见下表） |
| Manifest description | `{{auto_description}}`（用户答 Q3 前的兜底） |

---

## 入口形态 → 默认 quickstart command

| 入口形态 | `{{quickstart_command}}` 默认 |
|---|---|
| Node CLI | `npm install -g {{package}}` 或 `npx {{package}}` |
| Node Library | `npm install {{package}}` |
| Python Library | `pip install {{package}}` |
| Python CLI | `pip install {{package}}` 或 `pipx install {{package}}` |
| Rust CLI | `cargo install {{package}}` |
| Go CLI | `go install github.com/{{owner}}/{{repo}}@latest` |
| Web app | `git clone ... && cd ... && {{install_dep}} && {{dev_command}}` |
| Docker 项目 | `docker run {{image}}` |
| AI 模型 | 给两条：HF + ModelScope（如适用） |

---

## 用户答 = "暂无" 时的硬规则

- Q6 答 F（暂无信任锚）→ Adopters / Testimonials / Numbers 段全不渲染
- Adopters 不允许填 stripe/vercel/shopify 这类示例占位（避免伪信号）
- Testimonials 不允许写"占位引言 + 伪人名"
- Benchmark 数字不允许写"待补充" / "N/A"——直接不渲染该段

**如果生成结果检测到任何"占位伪信任信号"，自检阶段应自动删除并报告**。

---

## 模板变量命名规范

- 全部用 `{{snake_case}}` 双花括号
- 中英变体用 `_zh` / `_en` 后缀
- 数组类用 `_list` / `_rows` / `_paragraphs` 后缀
- URL 类用 `_url` 后缀
- 路径类用 `_path` 后缀

**禁止**：
- `{var}` 单花括号（与 Mustache 等冲突）
- `<var>` 角括号（与 HTML 冲突）
- `${var}` 美元（与 shell 冲突）

---

## 占位符在 URL 中的处理

URL 里的占位符必须 URL-encode：
- ❌ `https://placehold.co/1200x600?text={{project}}+demo`（空格未 encode）
- ✅ `https://placehold.co/1200x600?text={{project_url_encoded}}`（变量提前 encode）

或在生成时由 Skill 负责替换 + encode，不让模板里出现裸 `{{var}}` 在 URL query。
