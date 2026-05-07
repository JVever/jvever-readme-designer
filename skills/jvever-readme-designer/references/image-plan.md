# 图片任务清单生成规则

Skill 输出 `docs/readme-image-plan.md` 给用户，列出 README 中所有需要的图片/视觉资产。

---

## 任务清单格式

```markdown
# README 图片任务清单

> 这是 jvever-readme-designer 为你的 README 生成的图片占位符清单。
> 完成后请把图片放到 `assets/` 目录，并删除 README 中的占位 HTML 注释。

## 必需

### 1. assets/hero.gif（首屏 demo）

**位置**：README 顶部 hero 区
**用途**：5 秒内让访客看到产品在做什么
**建议尺寸**：1200×600（16:9 或 2:1）
**建议时长**：≤30 秒
**建议内容**：
- 输入命令 `{{project}} {{example_arg}}`
- 显示输出过程
- 突出最有趣的能力（如 streaming / live preview）
**制作方式建议**：
- CLI 类：用 [asciinema](https://asciinema.org/) 录制 → [agg](https://github.com/asciinema/agg) 转 GIF
- GUI 类：用 [LICEcap](https://www.cockos.com/licecap/) / [Kap](https://getkap.co/) 录制
**完成后**：放到 `assets/hero.gif`，删除 README 中 `<!-- IMG: hero -->` 注释
**优先级**：⭐⭐⭐⭐⭐ 缺失会让首屏空荡

### 2. assets/logo.svg（logo）

**位置**：Hero 区 H1 之上
**建议尺寸**：宽 180px，矢量
**建议变体**：明色版 `logo-light.svg` + 暗色版 `logo-dark.svg`（用 `<picture>` 切换）
**完成后**：放到 `assets/`
**优先级**：⭐⭐⭐⭐ 缺失会让首屏不专业

## 推荐

### 3-N. assets/feature-{1..N}.png（功能截图）

每个 feature 对应 1 张：
- 路径：`assets/feature-{n}.png`
- 用途：feature bullet 后面的证据
- 尺寸：≤800×500
- 内容：单一功能的实际效果（不是 mockup）

## 可自动生成（无需用户操作）

### Star History
**自动 URL**：`https://api.star-history.com/svg?repos={{owner}}/{{repo}}&type=Date`
不需要任何操作。

### Contributors
**自动 URL**：`https://contrib.rocks/image?repo={{owner}}/{{repo}}`
不需要任何操作。

### Architecture（如启用）
**Mermaid 内联**：直接在 README 中用 ```mermaid ``` 渲染，无需图片文件。

## 国内特有（如适用）

### assets/wechat-group-qr.png
**用途**：微信群入群二维码
**注意**：群满后图片要更新，建议同时贴文字（"群满请加微信 xxx 拉你"）

### assets/lark-group-qr.png
飞书群二维码（同上）

### assets/bilibili-thumbnail.png
B 站演示视频缩略图，链接到 B 站视频
```

---

## Skill 在 README 里留占位的方式

每张图位置插入 HTML 注释 + 临时占位图：

```markdown
<p align="center">
  <img src="assets/hero.gif" alt="{{project}} demo" width="800">
  <!-- IMG: hero — 见 docs/readme-image-plan.md -->
</p>
```

如果图片暂时还不存在，使用 placeholder 服务（**统一用 placehold.co；via.placeholder.com 已停服**）：
```markdown
<img src="https://placehold.co/1200x600/2a2a2a/ffffff?text={{project_url_encoded}}+demo" alt="{{project}} demo (placeholder)">
```

或干脆放一个明显的占位标记（推荐，不依赖第三方）：
```markdown
> 🖼️ **[这里需要一张 hero demo GIF — 见 docs/readme-image-plan.md 任务 #1]**
```

---

## 图片任务清单的输出原则

1. **每张图都有"为什么需要"**：不仅说"放在哪"，还要说"读者从这张图获取什么信息"。
2. **每张图都有"怎么做"**：制作工具 + 推荐步骤。
3. **每张图都有"优先级"**：缺失影响多大。
4. **可自动的不让用户做**：Star History / contributors / mermaid 直接生成 URL 或代码。
5. **不超过 7 张需要手工的**：再多用户做不过来。多了的话考虑合并 / 砍掉次要的。

---

## 不同 archetype 的默认图片清单

| Archetype | 必需 | 推荐 | 国内特有（如适用） |
|---|---|---|---|
| **A 开发者工具型** | hero.gif（demo），logo | feature-1~3，benchmark.png | wechat-group-qr |
| **B 基础设施型** | hero.png（架构图或截图），logo | architecture.svg, adopters/*.svg | lark-group-qr |
| **C 消费/创作者工具型** | hero.png（视频缩略图或大截图），logo | feature-1~6（高密度网格） | bilibili-thumbnail |
| **D 新品类教育型** | hero（视频缩略图），logo | architecture.svg, capability-1~4 | wechat-group-qr |
| **E 第三方背书优先型** | hero（产品截图），logo | testimonial-avatar-1~3 | — |

---

## 一些可以 AI 直接生成的图

虽然 Skill 默认不直接生图，但可以在图片任务清单里告诉用户**哪些图可以让 AI 生成**：

- **Logo**：可用 logo-generator skill / Midjourney / DALL-E（建议人工把控终稿）
- **Banner**：可用 AI 生成意象画（但建议手工融入项目截图，纯 AI 生成的 banner 缺乏识别度）
- **Architecture 图**：直接用 mermaid（推荐）/ Excalidraw / draw.io
- **Placeholder 截图**：placehold.co 临时凑数（如 `https://placehold.co/1200x600?text=demo`）
