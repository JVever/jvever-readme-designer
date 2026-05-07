# Archetype E：第三方背书优先型 骨架

适用：已有强势对手的赛道 / 项目还小但有真实早期用户好评。

强调：用户引言当 H1、testimonials 高密度、第三方媒体引用。

**门槛**：必须有真实可验证的引言。**不要为了用 E 而伪造**。

---

## 中文版骨架（README.md）

> ⚠️ **关键修正**：archetype E 的 hero 是用引言**替代** H1，不是引言之上还有 H1。否则一份文档两个 H1 + 引用变 heading，渲染破坏。

```markdown
<p align="center">[lang switcher]</p>

<div align="center">

<!-- 项目名作为 H2/小字号或省略，引言作为视觉中心 -->
<sub>{{project}}</sub>

# "{{key_quote}}"

**— {{quote_author}}, {{quote_title}}**

[badges]

[下载]({{download}}) · [官网]({{site}}) · [Discord]({{discord}})

</div>

<p align="center">
<img src="assets/hero.png" alt="{{project}}" width="1000">
<!-- IMG: hero — 产品大截图 -->
</p>

## 更多用户怎么说

> "{{testimonial_2}}"
> — **{{name_2}}**, {{title_2}}

> "{{testimonial_3}}"
> — **{{name_3}}**, {{title_3}}

> "{{testimonial_4}}"
> — **{{name_4}}**, {{title_4}}

> "{{testimonial_5}}"
> — **{{name_5}}**

## 媒体报道

- [{{outlet_1}}]({{url_1}}) — "{{outlet_1_quote}}"
- [{{outlet_2}}]({{url_2}}) — "{{outlet_2_quote}}"
- [{{outlet_3}}]({{url_3}}) — "{{outlet_3_quote}}"

## {{project}} 是什么

{{short_definition_paragraph_zh — 简洁，因为前面已经被引言定调}}

## 功能截图

[5-8 张截图墙]

## 下载

[多平台下载]

## 加入社区

{{community_section}}

## License

[{{license}}](LICENSE)
```

---

## English version skeleton (README_en.md)

```markdown
<p align="center">[lang switcher with English current]</p>

<div align="center">

<sub>{{project}}</sub>

# "{{key_quote}}"

**— {{quote_author}}, {{quote_title}}**

[badges]

[Download]({{download}}) · [Website]({{site}}) · [Discord]({{discord}})

</div>

<p align="center">
<img src="assets/hero.png" alt="{{project}}" width="1000">
</p>

## More users say

> "{{testimonial_2}}"
> — **{{name_2}}**, {{title_2}}

> "{{testimonial_3}}"
> — **{{name_3}}**, {{title_3}}

> "{{testimonial_4}}"
> — **{{name_4}}**, {{title_4}}

## Press

- [{{outlet_1}}]({{url_1}}) — "{{outlet_1_quote}}"
- [{{outlet_2}}]({{url_2}}) — "{{outlet_2_quote}}"

## What is {{project}}

{{short_definition_paragraph_en — concise; the quote already set the tone}}

## Screenshots

[5-8 image grid]

## Download

[Multi-platform download]

## Community

{{community_section}}

## License

[{{license}}](LICENSE)
```

