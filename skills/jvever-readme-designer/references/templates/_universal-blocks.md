# 通用区块

可被任何 archetype 复用的标准块。

---

## 语言切换条

**重要规则**（避免 silent fail）：
- **当前语言的 badge 不是链接**——避免点了刷新本页或形成死循环
- **单语模式不放切换条**

中文版 README 顶部（中文当前 = 不带链接的 img；English 是链接）：
```markdown
<p align="center">
  <img alt="中文（当前）" src="https://img.shields.io/badge/lang-中文-red?style=flat-square">
  &nbsp;
  <a href="README_en.md"><img alt="English" src="https://img.shields.io/badge/lang-English-blue?style=flat-square"></a>
</p>
```

英文版 README 顶部（English 当前 = 不带链接的 img；中文是链接）：
```markdown
<p align="center">
  <a href="README.md"><img alt="中文" src="https://img.shields.io/badge/lang-中文-blue?style=flat-square"></a>
  &nbsp;
  <img alt="English (current)" src="https://img.shields.io/badge/lang-English-red?style=flat-square">
</p>
```

**单语模式**：`--zh-only` 或 `--en-only` 时整段切换条**不渲染**（避免链接到不存在的 README_en.md / README.md 造成 404）。

---

## Star History

```markdown
## Star History

[![Star History Chart](https://api.star-history.com/svg?repos={{owner}}/{{repo}}&type=Date)](https://star-history.com/#{{owner}}/{{repo}}&Date)
```

---

## Contributors

```markdown
## 贡献者

<a href="https://github.com/{{owner}}/{{repo}}/graphs/contributors">
  <img src="https://contrib.rocks/image?repo={{owner}}/{{repo}}" />
</a>
```

---

## Contributing

```markdown
## 参与贡献

我们欢迎任何形式的贡献！请先阅读 [CONTRIBUTING.md](CONTRIBUTING.md) 和 [Code of Conduct](CODE_OF_CONDUCT.md)。

**快速参与方式：**
- 🐛 报告 [Issue](https://github.com/{{owner}}/{{repo}}/issues)
- 💡 提交 Feature Request
- 📖 改进文档
- 💻 提交 Pull Request

加入 [Discord]({{discord}}) 与维护者交流。
```

---

## Domestic Community Block（国内社群）

```markdown
## 加入社区

<table>
<tr>
<td align="center" width="33%">
<b>微信群</b><br>
<img src="assets/wechat-group-qr.png" width="180"><br>
<sub>群满请加 <code>{{wx_id}}</code> 备注 GitHub</sub>
</td>
<td align="center" width="33%">
<b>飞书群</b><br>
<img src="assets/lark-group-qr.png" width="180">
</td>
<td align="center" width="33%">
<b>Discord</b><br>
<a href="{{discord}}">{{discord_short_url}}</a>
</td>
</tr>
</table>
```

---

## License

```markdown
## License

[{{license}}](LICENSE) © {{year}} {{author}}
```

---

## Used by

```markdown
## 谁在用

<p align="center">
  <a href="{{adopter_1_url}}"><img src="assets/adopters/{{adopter_1}}.svg" height="40" alt="{{adopter_1_name}}"></a>
  &nbsp;&nbsp;&nbsp;
  <a href="{{adopter_2_url}}"><img src="assets/adopters/{{adopter_2}}.svg" height="40"></a>
  &nbsp;&nbsp;&nbsp;
  <a href="{{adopter_3_url}}"><img src="assets/adopters/{{adopter_3}}.svg" height="40"></a>
</p>

完整名单：[ADOPTERS.md](ADOPTERS.md)。在用？欢迎 [PR 添加你的 logo]({{pr_url}})。
```

---

## Sponsors

```markdown
## 赞助 & 支持

{{project}} 由 [GitHub Sponsors](https://github.com/sponsors/{{owner}}) 与 [OpenCollective](https://opencollective.com/{{project}}) 支持。

特别鸣谢：

<p align="center">
  <a href="{{sponsor_1_url}}"><img src="assets/sponsor-1.svg" height="50"></a>
</p>
```

---

## Image Placeholder（图片占位）

如图片暂时不存在：

```markdown
> 🖼️ **[此处需 hero demo GIF — 见 docs/readme-image-plan.md 任务 #1]**
```

或用 placeholder（**统一用 placehold.co；via.placeholder.com 已停服**）：

```markdown
<img src="https://placehold.co/1200x600/2a2a2a/ffffff?text={{project_url_encoded}}" alt="{{project}} demo (placeholder)">
```
