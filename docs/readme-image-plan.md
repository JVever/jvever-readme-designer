# README 图片任务清单

> 由 `jvever-readme-designer` 在 minimal-asset 模式下生成。当前项目极早期（12 commits、无 logo、无截图、单人维护、CC BY-SA 4.0），所有任务都是 `nice-to-have`——不让 TODO 吓跑你。

按优先级实现即可，做完后把对应文件放到 `assets/`，回 README 加引用即可。

---

## Nice-to-have（建议但不阻塞发布）

### 1. `assets/logo.svg`

**位置**：Hero 区 H1 之上（中英版各一处）
**为什么**：minimal-asset 模式下 logo 不强求，但有 logo 能让首屏更专业
**建议尺寸**：宽 180px，矢量
**建议变体**：明色 `logo-light.svg` + 暗色 `logo-dark.svg`，用 `<picture>` 切换
**主题建议**：
- 「放大镜 + 文档」暗喻"先扫描后决策"
- 「多面体 / 棱镜」暗喻 5 种 archetype
- 「检测点 + 笔尖」暗喻"两层自检 + 文案"
**制作工具**：[`logo-generator` skill](https://github.com/anthropics/skills) / Midjourney / DALL-E 起草，Figma 收尾
**完成后**：在 README hero 区加：
```markdown
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/logo-light.svg">
  <img alt="jvever-readme-designer logo" src="assets/logo.svg" width="180">
</picture>
```

---

### 2. `assets/hero-demo.gif`（流程演示）

**位置**：当前 README 在 minimal-asset 模式下未放 hero 视觉块；做出来后插在 features 之上，或替代 features 上方那条 blockquote
**为什么**：直接看 3 阶段流程跑起来比文字描述快 10 倍——尤其能展示「0 个追问」这个最反常识的卖点
**建议尺寸**：1200×600（16:9）
**建议时长**：≤ 30 秒
**建议剧本**：
1. 在一个真实项目里启动 Claude Code
2. 输入 `/jvever-readme-designer`
3. 录到 SCAN 报告 → 自动决策播报 → DRAFT 开始为止
4. 重点展示「无任何追问、模型直接动手」的体感
**制作工具**：
- macOS：[Kap](https://getkap.co/) 或 [LICEcap](https://www.cockos.com/licecap/) 录屏 → 导出 GIF
- 终端友好：[asciinema](https://asciinema.org/) → [agg](https://github.com/asciinema/agg) 转 GIF
**完成后**：
```markdown
<p align="center">
  <img src="assets/hero-demo.gif" alt="jvever-readme-designer demo" width="800">
</p>
```

---

### 3. `assets/before-after.png`（对比截图）

**位置**：「为什么用它」第一段之后
**为什么**：show, don't tell——一张对比图胜过任何"你的 README 会变好"的承诺
**建议尺寸**：≤ 1600×900（左右分屏）
**建议内容**：
- 左：某真实项目重写前的 README（截屏，遮 logo / 项目名）
- 右：跑过本 Skill 后的 README（同位置）
- 高亮差异：hero 区结构 / tagline 力度 / trust signals 占位 / 双语切换
**制作工具**：Figma / Photoshop / Pixelmator 拼图

---

### 4. `assets/archetype-decision-tree.svg`（决策树可视化，可选）

**位置**：「5 种 archetype」表格之后
**为什么**：表格已说清楚，但决策**树**能进一步展示「自动选择」的机制感
**建议尺寸**：1200×800
**制作工具**：mermaid（如果嵌入 README，无需图片）/ excalidraw / tldraw

> 如果用 mermaid，可直接写在 README 里，不需要 png：
> ```mermaid
> flowchart TD
>   start[扫描 manifest + 入口形态] --> q1{是 CLI/SDK/库?}
>   q1 -->|是| A[A 开发者工具型]
>   q1 -->|否| q2{是 DB/云/API?}
>   ...
> ```

---

## 可自动生成（无需操作）

以下信号当前**不渲染**（项目阶段未达阈值），项目长大后会自动激活：

| 信号 | 触发条件 | 模板位置 |
|---|---|---|
| Star History 图 | ≥1k stars | `references/section-library.md` §11 |
| Contributors 头像墙 | ≥10 contributors | `references/section-library.md` §12 |
| Adopters logo 墙 | 用户提供 ≥3 个真实采用方 | `references/section-library.md` §8 |
| Testimonials | 用户提供 ≥2 条真实引言 | `references/section-library.md` §9 |
| Numbers 表 | 提供可验证 benchmark | `references/section-library.md` §10 |
| Sponsors 区 | 有 GitHub Sponsors / OpenCollective | `references/section-library.md` §13 |

到达条件后跑 `/jvever-readme-designer --patch`，Skill 会自动加上对应段。

---

## 后续维护提醒

每次 release / 每 3 个月 / star 数翻倍时跑：

```
> /jvever-readme-designer --rewrite
```

让 Skill 重新评估 archetype / hero 力度 / trust signals 状态。README 是活的产品页，半年不更新会显死。
