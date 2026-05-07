<!--
@input:    -
@output:   重定向薄壳。原"反模式集"已分流到 principles.md（主观判断）+ auto-checks.md（机械检测）
@rule:     **不要**继续往本文件添加新反模式。新规则按以下二分法归位：
           - 主观/需要判断 → principles.md（作为"反例锚"挂在对应原则下）
           - 机械可检测 → auto-checks.md（作为新的检测项）
-->

# 反模式集（已重构 — 不再使用）

> **历史版本（≤ v2）** 把 16 条反模式作为 skill 的主架构。
> **当前版本（v3 起）** 已彻底重构：

## 主观判断的设计反例

请见 [`principles.md`](principles.md)。

5 条核心原则，每条下挂"反例锚"——具体踩过的坑作为记忆锚点，但**不再单独成篇**。包括：
- emoji 满天飞 / HTML 滥用 / 装饰性 ASCII / TOC 必要性 → **原则 4：克制即专业**
- Hero 后塞展示性内容 / 装饰流程图 / 双语切换冗余 → **原则 1：首屏定生死** + **原则 4**
- 形容词堆砌 / feature dump / Marketing 喧宾夺主 → **原则 2** + **原则 3**
- Stale 命令 / 凭空捏造数字 / 假 testimonial → **原则 5：信任信号 + 鲜活维护**
- 中英混杂用冷词（archetype / claim / testimonial / adopter） → **原则 4** + auto-checks E

## 机械可检测的 lint 规则

请见 [`auto-checks.md`](auto-checks.md)。

DRAFT 阶段强制运行的检测器，每项满足"对/错明确 + 可机械检测"。包括：
- 路径泄露 / 用户身份信息 → A 组
- License 链接断裂 / 占位图服务停服 / 双语切换条规则 → B 组
- 占位符未替换 / adopters 未替换 → C 组
- Hero 后 ASCII 超长 / 标题 emoji → D 组
- 中英混杂黑名单（archetype / claim / testimonial 等） → E 组
- 模式一致性（`--zh-only` 不生成英文版等） → F 组

---

## 为什么这么改？

把"反模式"作为主架构有几个结构性问题：
1. **永远在防御**——只告诉模型"别这样"，没告诉它"该这样"
2. **覆盖率焦虑**——列了 16 条还是不够，新场景一来又得加
3. **冗余/重叠**——很多反模式本质是同一原则的不同表现
4. **认知污染**——给 LLM 一堆反例当输入，反而可能让它"被反例带偏"
5. **削弱判断力**——维护者会变成 checker，不是设计师

正向原则（少而精）+ 机械检测（多而准）的二分，比"散乱的反模式清单"更可持续。

---

## 给历史链接的兼容

如果你从外部进来，期望看到旧 v2 时代的"反模式 1-16"内容，请按下表跳转：

| 旧引用 | 新位置 |
|---|---|
| 反模式 1（项目名 + logo 没解释做什么） | principles.md 原则 1 |
| 反模式 2（Obvious to me 安装） | principles.md 原则 1 + 原则 4（唯一安装路径） |
| 反模式 3（跳过 Why 直接 Install） | principles.md 原则 2 |
| 反模式 4（形容词堆砌） | principles.md 原则 3 |
| 反模式 5（巨型一段式无 heading） | principles.md 原则 2 |
| 反模式 6（emoji 和 HTML 滥用） | principles.md 原则 4 |
| 反模式 7（Demo 缺失） | principles.md 原则 1 + 原则 3 |
| 反模式 8（Stale README） | principles.md 原则 5 |
| 反模式 9（Marketing 喧宾夺主） | principles.md 原则 1 + 原则 4 |
| 反模式 10（短 README 里的 TOC） | principles.md 原则 4 |
| 反模式 11（Contributing 占据黄金位） | principles.md 原则 1 + 原则 2 |
| 反模式 12（License 缺失） | auto-checks.md B1 |
| 反模式 13（hero 后装饰 ASCII） | principles.md 原则 1 + 原则 4 + auto-checks D1 |
| 反模式 14（双语切换重复） | auto-checks.md B5 + principles.md 原则 4 |
| 反模式 15（本地路径泄露） | auto-checks.md A1 |
| 反模式 16（中英混杂冷词） | auto-checks.md E + principles.md 原则 4 |
| CN-1 至 CN-5（中文项目特有） | principles.md 原则 5（鲜活维护：群补救、utm）+ 原则 4（中英混杂）+ 双语层 checklist |
