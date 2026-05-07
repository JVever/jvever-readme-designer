# 不该用本 Skill 的场景

本 Skill 的范畴是"为 software 项目设计 README 作 landing page"。以下场景请绕道。

---

## 场景 1：单点改动

**例**："改个错字"、"修一个链接"、"加一行说明"

**原因**：本 Skill 流程 5 阶段，对单点改动是过度设计。

**替代**：直接 Edit / 让用户手改。

---

## 场景 2：项目没有 software

**例**：纯 dotfiles 仓库 / awesome-list / 个人收藏链接库 / 文学创作仓库

**原因**：本 Skill 假设有 software 可介绍（archetype A-E 全是软件类型），无 software 时 archetype 决策树会走死路径。

**替代**：用普通 markdown 编辑工具，参考 awesome-* 类项目的简明结构（H1 + 简介 + 分类列表）。

---

## 场景 3：你不维护这个项目

**例**：用户在别人的 fork 上想改 README

**原因**：重写别人的项目门面是越界。

**替代**：fork 后改自己 fork 的，但不要 PR 回原仓库（除非作者请求）。

---

## 场景 4：要生成的不是 README

**例**：CHANGELOG / API docs / wiki / 学术论文 / 产品营销文案

**原因**：CHANGELOG 是结构化变更记录（用 keep-a-changelog 标准）；API docs 是技术文档（用 typedoc / sphinx）；wiki 是面向贡献者的；本 Skill 都不擅长。

**替代**：用对应的专门工具或 Skill。

---

## 场景 5：完全私人 / 内部 reference

**例**：个人脚本仓库（只有自己看）/ 公司内部工具（只有 5 个同事用）

**原因**：本 Skill 设计哲学是"对外 marketing 漏斗入口"，对内部项目是过度营销。

**替代**：写最简结构（一句话说明 + install + usage），不需要 hero / archetype / trust signals。可用 `--patch` 模式只补缺失的段。

---

## 场景 6：项目还没启动

**例**：刚 `git init`，没写一行代码

**原因**：本 Skill 依赖 SCAN 阶段读取 manifest 和现有结构，空仓库 SCAN 拿不到任何信号。

**替代**：先写最小可运行版本，再回来跑本 Skill。或用 `--quick` 模式接受"完全靠用户口述"。

---

## 场景 7：高度敏感的项目

**例**：安全研究项目（漏洞 PoC）/ 不希望被广泛推广的内部工具 / 法律灰色地带项目

**原因**：本 Skill 优化目标是"提高 conversion"。如果项目特意要低调，本 Skill 反向做功。

**替代**：手写最简 README，故意 plain，不放 demo / 不写卖点。

---

## 自动检测建议

Skill 在 SCAN 阶段如检测到下列信号，应**主动询问是否走 scope-out**：

- 仓库无 manifest 文件（可能是 docs / awesome-list / dotfiles）
- 仓库代码量 < 100 行（可能未启动）
- README 含 "internal use only" / "do not distribute" / "for security research"
- 仓库在 Gitignore 中（不公开）

---

## 边界外但近似场景

| 你想做 | 推荐工具 |
|---|---|
| 写 CONTRIBUTING.md | doc-coauthoring skill |
| 写 product landing page | frontend-design skill |
| 写技术博客文章 | create-content skill |
| 写 API 文档 | typedoc / sphinx / 自动生成 |
| 写 commit message | commitizen / conventional commits |
| 写 PR 描述 | 项目自带的 PR template |
| 一键生成简单 README | readme.so（不深度访谈，但够轻量）|
