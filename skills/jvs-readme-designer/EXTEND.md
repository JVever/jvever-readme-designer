# EXTEND.md — 用户偏好持久化

本文件让你为 `jvs-readme-designer` 设置永久默认值，避免每次都用命令行参数覆盖。Skill 在启动时会读这个文件覆盖默认设置。

> **使用说明**：复制本文件到使用 Skill 的项目根（与 `.git/` 同级），按需调整。Skill 找不到该文件时使用内置默认值。

---

## 流程默认值

```yaml
# 每次默认走哪个流程：quick / full / rewrite / patch
default_flow: quick

# 用户问句出现下列关键词时改用 full：
# 比如「重做 / 详细一点 / 高保真 / 我想做认真的 README」
upgrade_to_full_keywords:
  - 详细
  - 高保真
  - 认真
  - 重做
  - polished
  - thorough
```

---

## 输出语言默认值

```yaml
# bilingual / en-only / zh-only
default_output: bilingual

# 双语模式选哪种 pattern：
# M1 = 中文优先双文件（README.md + README_en.md）
# M2 = 英文优先双文件（README.md + README.zh-CN.md）
# M3 = 多语言子目录（README.md + i18n/README.<lang>.md）
# M4 = 单文件中英对照
bilingual_pattern: M1

# 自动检测语种并切换默认（推荐打开）：
# 如检测到 commits/manifest 主语种为英文且无中文 README，自动改 default_output 为 en-only
auto_detect_language: true
```

---

## Archetype 偏好

```yaml
# 当 SCAN+INTERVIEW 都不能强决定时，用哪个 archetype 兜底：
# A / B / C / D / E
default_archetype: A

# 强制 archetype（即使决策器判别不同也用这个）：
# 慎用——大多数情况让决策器选更好
force_archetype: null  # null = 不强制
```

---

## 视觉风格

```yaml
# Feature 列表风格：emoji / checkbox / cards
features_style: emoji

# Feature emoji 池（顺序使用）：
emoji_pool:
  - "⚡"
  - "🔒"
  - "🌍"
  - "🛠"
  - "📦"
  - "🎯"
  - "✨"
  - "🚀"

# 是否在标题里使用 emoji（默认 false，遵循"克制"原则）：
emoji_in_headings: false

# Logo 使用 picture 标签明暗双版本：
dual_logo: true

# Hero 视觉默认形态：gif / screenshot / video-thumbnail / ascii-art
hero_visual: gif
```

---

## Badge 偏好

```yaml
# 顶部 badge 数量上限：
max_badges: 6

# 默认 badge 组合：generic / ai-model / infrastructure / minimal
badge_preset: generic

# 国内项目额外 badges：
include_chinese_badges: false  # auto-detect 语种时会自动覆盖
```

---

## 国内特有元素

```yaml
# 是否启用国内特有元素（飞书/微信群、ModelScope、Bilibili、阿里云一键部署）：
# auto = 根据 SCAN 检测中文优先时启用
# always = 总启用（询问用户具体内容）
# never = 不启用
domestic_elements: auto

# 默认询问哪些国内元素：
domestic_questions:
  - wechat_group
  - lark_group
  - bilibili_video
  - one_click_deploy
  - modelscope_mirror  # AI 项目时
  - business_contact
```

---

## 文件命名约定

```yaml
# 中文 README 文件名：README.md / README_zh.md / README_CN.md
chinese_filename: README.md  # M1 默认

# 英文 README 文件名（仅 bilingual M1 模式）：README_en.md / README.en.md
english_filename: README_en.md
```

---

## 自检循环

```yaml
# 反模式自检最大循环轮数：
max_self_check_rounds: 2

# 自检发现问题后的策略：
# auto_fix = 直接改不打扰
# warn_only = 列出来等用户决定
# hybrid = 安全的自动改，主观的等用户（推荐）
self_check_strategy: hybrid
```

---

## 信任信号阈值

```yaml
# Star History section 渲染阈值（stars 数）：
star_history_min_stars: 1000

# Contributors 头像墙渲染阈值（独立 author 数）：
contributors_min_authors: 10

# Adopters 段渲染阈值（用户提供的 adopter 数）：
adopters_min_count: 3

# Testimonials 段渲染阈值：
testimonials_min_count: 2
```

---

## Skill 与其他工具的协作

```yaml
# 自动调用 logo-generator skill 生成 logo（仅当用户没有 logo 时询问）：
auto_invoke_logo_generator: false

# 自动建议 image-plan 中可用 AI 生图的项：
suggest_ai_image_generation: true
```

---

## 维护提醒

```yaml
# 生成完后是否在 README 末尾加注释提醒下次更新时机：
add_maintenance_reminder: true

# 提醒频率：每次 release / 每 3 个月 / star 翻倍
maintenance_trigger: every-release
```

---

## 自定义模板路径

```yaml
# 如果你想用自己的 archetype 模板覆盖内置：
custom_templates_dir: null  # 例如 "./my-templates/"

# 自定义 banner 占位 URL（替代 placehold.co）：
custom_placeholder_service: null  # 例如 "https://my-cdn.com/placeholder/{w}x{h}"
```
