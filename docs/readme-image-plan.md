# README 图片任务清单

> 由 `jvever-readme-designer` 在 minimal-asset 模式下生成。当前项目极早期（5 个 commit、无 logo、无截图），所有任务都是 `nice-to-have` —— 不让你被 TODO 吓跑。

按优先级实现即可，做完后把对应文件放到 `assets/`，README 会自动展示。

---

## Nice-to-have（建议但不阻塞发布）

### 1. `assets/logo.svg`

**位置**：Hero 区 H1 之上（中英版各一处）
**为什么**：minimal-asset 模式下 logo 不强求，但有 logo 能让首屏更专业
**建议尺寸**：宽 180px，矢量
**建议变体**：明色 `logo-light.svg` + 暗色 `logo-dark.svg`，用 `<picture>` 标签切换
**制作建议**：
- 用 `logo-generator` Skill（如已安装）/ Midjourney / DALL-E 生成草稿
- 也可手绘——主题可考虑"放大镜 + 文档"暗喻"先扫描后写"，或"多面体"暗喻 5 种 archetype
**完成后**：放到 `assets/`，回 README 把 H1 上方加：
```markdown
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="assets/logo-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="assets/logo-light.svg">
  <img alt="jvever-readme-designer logo" src="assets/logo.svg" width="180">
</picture>
```

---

### 2. `assets/hero-demo.gif`（流程演示）

**位置**：Hero 区一句定义之后、Quickstart 之前
**为什么**：直接看 5 阶段流程跑起来是什么样，比文字描述快 10 倍
**建议尺寸**：1200×600（16:9）
**建议时长**：≤ 30 秒
**建议内容**：
- 在一个真实项目（如本 Skill 仓库自身）里启动 Claude Code
- 输入 `/jvever-readme-designer`
- 录到 SCAN 报告 → INTERVIEW 第一个问题为止
**制作工具**：
- macOS：[LICEcap](https://www.cockos.com/licecap/) 或 [Kap](https://getkap.co/) 录屏 → 导出 GIF
- 也可用 [asciinema](https://asciinema.org/) 录终端 → [agg](https://github.com/asciinema/agg) 转 GIF
**完成后**：在 README hero 区加：
```markdown
<p align="center">
  <img src="assets/hero-demo.gif" alt="jvever-readme-designer demo" width="800">
</p>
```

---

### 3. `assets/before-after.png`（对比截图）

**位置**：Why this Skill 段第一条之后
**为什么**：show, don't tell —— 一张对比图胜过段落"你的 README 会变好"
**建议尺寸**：≤ 1600×900（左右分屏）
**建议内容**：
- 左：某个真实项目重写前的 README（截屏，遮住名字）
- 右：跑过本 Skill 后的 README（同项目同位置）
- 高亮关键差异（hero 区结构 / tagline 力度 / trust signals 占位）
**制作工具**：Figma / Photoshop / Pixelmator 拼图
**完成后**：替换 README 中"5 秒能看清产品 → 30 秒愿意试用"那段，附上图片

---

## 可自动生成（无需操作）

以下信号当前**不渲染**（项目阶段未到门槛），项目长大后自动激活：

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

每次 release / 每 3 个月 / star 数翻倍时，跑一遍：

```
> /jvever-readme-designer --rewrite
```

让 Skill 重新评估 archetype / hero 力度 / trust signals 状态，保持鲜活。
