# 中国社区项目特有 README 元素

国内开源项目相比国际项目，README 里通常会多出一些"本地化生态对接"的元素。Skill 在识别项目面向国内用户时，会询问是否启用以下元素。

---

## 1. 社群入口（最高频）

### 微信群 / QQ 群 / 飞书群

```markdown
## 加入社区

<table>
<tr>
<td align="center" width="33%">
<b>微信群</b><br>
<img src="assets/wechat-group-qr.png" width="180"><br>
<sub>群满请加 <code>{{wx_id}}</code> 备注 GitHub 拉你进群</sub>
</td>
<td align="center" width="33%">
<b>飞书群</b><br>
<img src="assets/lark-group-qr.png" width="180">
</td>
<td align="center" width="33%">
<b>QQ 群</b><br>
<code>{{qq_group_id}}</code><br>
<sub><a href="{{qq_join_link}}">点击加入</a></sub>
</td>
</tr>
</table>
```

**关键约束**：
- 群二维码会过期 / 群会满，**必须同时给文字补救**
- 微信号建议放小字号（避免被刷）
- 飞书生态在国内开发者圈渗透率高，是 Discord 的国内对应

### 微信公众号

```markdown
关注公众号「{{name}}」获取更新：

<img src="assets/wechat-official-qr.png" width="180">
```

---

## 2. 模型镜像（AI 项目特有）

国内 AI 项目几乎必给多个模型仓库链接，因为 HuggingFace 国内访问慢：

```markdown
## 模型下载

| 平台 | 链接 | 适用 |
|---|---|---|
| 🤗 Hugging Face | [{{hf_link}}]({{hf_link}}) | 海外用户 |
| 🌐 ModelScope（魔搭） | [{{ms_link}}]({{ms_link}}) | 国内首选 |
| 📦 WiseModel | [{{wm_link}}]({{wm_link}}) | 国内备用 |
| 🔬 OpenXLab | [{{xlab_link}}]({{xlab_link}}) | 学术友好 |
| 🏛 ModelArts | [{{ma_link}}]({{ma_link}}) | 华为云 |
```

---

## 3. 国内云一键部署

```markdown
## 一键部署

<a href="{{aliyun_url}}"><img src="https://img.shields.io/badge/阿里云-计算巢一键部署-FF6A00" alt="阿里云"></a>
<a href="{{sealos_url}}"><img src="https://cdn.jsdelivr.net/gh/labring-actions/templates@main/Deploy-on-Sealos.svg" alt="Sealos"></a>
<a href="{{zeabur_url}}"><img src="https://zeabur.com/button.svg" alt="Zeabur"></a>
<a href="{{railway_url}}"><img src="https://railway.app/button.svg" alt="Railway"></a>
```

主要平台：
- **阿里云计算巢** — `https://computenest.console.aliyun.com/...`
- **Sealos** — `https://cloud.sealos.io/?openapp=...`
- **Zeabur** — `https://zeabur.com/templates/...`
- **腾讯云 / 火山引擎 / 华为云** — 看项目选择
- **1Panel** —（飞致云生态，常见于 MaxKB 这类）

---

## 4. 国内镜像仓库

```markdown
## 国内镜像

代码镜像（同步 GitHub）：
- [Gitee](https://gitee.com/{{owner}}/{{repo}})
- [GitCode](https://gitcode.com/{{owner}}/{{repo}})
- [Atomgit](https://atomgit.com/{{owner}}/{{repo}})

文档镜像：
- [Yuque（语雀）](https://www.yuque.com/{{owner}}/{{book}})
- [中文文档（自建域名）]({{docs_zh_cn}})
```

---

## 5. 演示视频

国内项目用 Bilibili 远多于 YouTube：

```markdown
## 演示视频

[![Bilibili 演示](assets/bilibili-thumbnail.png)](https://www.bilibili.com/video/{{bv}})

或观看 [YouTube 版](https://www.youtube.com/watch?v={{yt_id}})。
```

---

## 6. 整合包 / 一键启动

国内 AI 项目（特别是模型类）常提供 Windows 整合包：

```markdown
## Windows 整合包（一键启动）

无需配 Python 环境，下载即可双击运行：

| 版本 | 下载 | 大小 |
|---|---|---|
| v{{version}} (CUDA 12) | [百度网盘](xxx) / [HuggingFace](xxx) / [ModelScope](xxx) | 4.2 GB |
| v{{version}} (CPU only) | 同上 | 3.8 GB |

下载后解压，双击 `start.bat` 即可启动。
```

---

## 7. 商业版 / 商业咨询入口

国内开源 + 商业版双轨模式很常见：

```markdown
## 商业版

{{project}} 提供企业版（私有化部署 + 技术支持 + SLA），请联系：

- 商业邮箱：[business@{{domain}}](mailto:business@{{domain}})
- 商业咨询表单：[飞书表单]({{lark_form}})
- 微信：{{biz_wx}}
```

---

## 8. Trendshift / 国内排行榜 badge

```markdown
[![Trendshift](https://trendshift.io/api/badge/repositories/{{repo_id}})](https://trendshift.io/repositories/{{repo_id}})
```

国内类似的：
- HelloGitHub 月榜
- 开源中国（OSCHINA）热门
- 知乎技术榜

---

## 9. 情怀型开场（少用，但用对了很有感染力）

国内项目偶有用文化锚点的：

```markdown
> 毕昇活字印刷术启于宋，为汉字传播之利器。
> {{project}}，愿做大模型时代的"活字"。
```

或：

```markdown
> Proudly made by Chinese, for the world.
```

**注意**：情怀开场要有真实的文化共鸣。强行套用容易显得做作，反成减分项。

---

## 10. 知乎 / 掘金 链接

```markdown
## 阅读更多

- [项目设计哲学（知乎专栏）](https://zhuanlan.zhihu.com/p/{{id}})
- [技术细节（掘金）](https://juejin.cn/post/{{id}})
- [Bilibili 教学频道](https://space.bilibili.com/{{uid}})
```

---

## Skill 决策逻辑

什么时候启用国内特有元素？

```
默认 → 不启用（保持国际化）

启用条件（任一即触发询问）：
- 项目主要语言是中文（package.json 的 description / commit message 含中文）
- 已有 README_zh.md 或 README.md 是中文
- 用户在访谈中明确说"国内项目" / "面向国内用户"

启用后逐项问：
- 是否要放群二维码？（微信/QQ/飞书任选）
- 是否在 ModelScope 同步？（仅 AI 项目问）
- 是否提供国内云一键部署？
- 是否有 Bilibili 演示视频？
- 是否有商业版/商业咨询入口？
- 是否要 Gitee / GitCode 镜像？
```

---

## 反模式（国内项目特有）

详见 `anti-patterns.md` 的 CN-1 至 CN-5：
- 直接搬英文表达（机翻味）
- 群二维码失效不补救
- shields.io badge 加载慢
- utm_source 跟踪参数
- 截图全英文 UI
