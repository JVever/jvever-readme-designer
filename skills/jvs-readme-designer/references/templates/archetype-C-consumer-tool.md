# Archetype C：消费 / 创作者工具型 骨架

适用：桌面 app（Tauri/Electron）/ 视频/音频/图像编辑工具 / 写作笔记白板 / 终端用户应用。

强调：强视觉、功能截图密集、用例分人群、多平台下载。

---

## 中文版骨架（README.md）

```markdown
<p align="center">[lang switcher]</p>

<div align="center">
[logo]

# {{project}}

**{{tagline_zh — 推荐"身份共鸣型"}}**

[badges ≤ 5 — 突出 download 量]

[官网]({{site}}) · [下载]({{download}}) · [Discord]({{discord}}) · [Bilibili]({{bilibili}})
</div>

<p align="center">
<img src="assets/hero.png" alt="{{project}}" width="1000">
<!-- IMG: hero — 大屏截图或视频缩略图 -->
</p>

> {{one_sentence_definition_zh}}

## 谁在用

[Logo 墙或一句话："已被 {{adopter_count}}+ 团队 / 创作者使用"]

## 功能一览

|  |  |  |
|---|---|---|
| ![]({{f1_img}})<br>**{{f1_name}}**<br>{{f1_desc}} | ![]({{f2_img}})<br>**{{f2_name}}**<br>{{f2_desc}} | ![]({{f3_img}})<br>**{{f3_name}}**<br>{{f3_desc}} |
| ![]({{f4_img}})<br>**{{f4_name}}**<br>{{f4_desc}} | ![]({{f5_img}})<br>**{{f5_name}}**<br>{{f5_desc}} | ![]({{f6_img}})<br>**{{f6_name}}**<br>{{f6_desc}} |

## 适合谁用

### 给设计师
{{designer_use_case}}

### 给创作者
{{creator_use_case}}

### 给团队
{{team_use_case}}

## 下载

| 平台 | 链接 | 备注 |
|---|---|---|
| macOS | [下载 .dmg]({{dmg}}) | Apple Silicon / Intel |
| Windows | [下载 .exe]({{exe}}) | 支持 Win10+ |
| Linux | [下载 .AppImage]({{appimage}}) | x86_64 / arm64 |
| iOS | [App Store]({{ios}}) | iOS 16+ |
| Android | [Google Play]({{android}}) | Android 10+ |

或包管理器：

```bash
brew install {{project}}      # macOS
winget install {{project}}    # Windows
```

## 价格 / 商业版

{{pricing_section_or_omit}}

## 用户怎么说

{{testimonials}}

## 加入社区

{{community_section_with_qr_codes_if_domestic}}

## 演示视频

[![Bilibili 演示](assets/bilibili-thumbnail.png)]({{bilibili_url}})

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

**{{tagline_en — identity-resonance formula recommended}}**

[badges ≤ 5 — emphasize downloads]

[Website]({{site}}) · [Download]({{download}}) · [Discord]({{discord}}) · [YouTube]({{youtube}})
</div>

<p align="center">
<img src="assets/hero.png" alt="{{project}}" width="1000">
</p>

> {{one_sentence_definition_en}}

## Trusted by creators

[Logo wall or one-liner: "Used by {{adopter_count}}+ teams / creators"]

## Features

|  |  |  |
|---|---|---|
| ![]({{f1_img}})<br>**{{f1_name}}**<br>{{f1_desc_en}} | ![]({{f2_img}})<br>**{{f2_name}}**<br>{{f2_desc_en}} | ![]({{f3_img}})<br>**{{f3_name}}**<br>{{f3_desc_en}} |
| ![]({{f4_img}})<br>**{{f4_name}}**<br>{{f4_desc_en}} | ![]({{f5_img}})<br>**{{f5_name}}**<br>{{f5_desc_en}} | ![]({{f6_img}})<br>**{{f6_name}}**<br>{{f6_desc_en}} |

## Who it's for

### For designers
{{designer_use_case_en}}

### For creators
{{creator_use_case_en}}

### For teams
{{team_use_case_en}}

## Download

| Platform | Link | Notes |
|---|---|---|
| macOS | [Download .dmg]({{dmg}}) | Apple Silicon / Intel |
| Windows | [Download .exe]({{exe}}) | Win10+ |
| Linux | [Download .AppImage]({{appimage}}) | x86_64 / arm64 |
| iOS | [App Store]({{ios}}) | iOS 16+ |
| Android | [Google Play]({{android}}) | Android 10+ |

Or via package manager:

```bash
brew install {{project}}
winget install {{project}}
```

## Pricing / Pro version

{{pricing_section_or_omit}}

## What users say

{{testimonials_en}}

## Community

{{community_section}}

## Demo video

[![YouTube demo](assets/youtube-thumbnail.png)]({{youtube_url}})

## License

[{{license}}](LICENSE)
```

