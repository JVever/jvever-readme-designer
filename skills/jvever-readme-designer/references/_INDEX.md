# references/

> Skill 参考库。本目录结构或子文件职责变化时，必须更新此文件。

## 元规则豁免

CLAUDE.md V4.0 §2.4 要求每个代码文件有 @input/@output/@rule 头注释。**本目录下的 `.md` 文件统一豁免**——理由：
- 全部都是 Skill 的内部参考文档（不是代码文件）
- @input 统一为 SKILL.md（被 SKILL.md 调用读取）
- @output 统一为 README 生成的输入材料（结构化知识 / 模板 / checklist）
- @rule 统一适用：本目录任一文件职责变化时，必须更新本 `_INDEX.md`

如果未来某个 reference 转为可执行 script（如 SCAN 自动化脚本），该文件需补头注释。

## 职责

承载 Skill 的设计原则、模式库、模板与反模式清单。SKILL.md 只描述流程，具体内容查这里。

## 文件清单

**核心信仰层（v3 重构）**：
- `principles.md` — **5 条核心原则**（所有主观设计判断的唯一来源；每条挂"反例锚"）
- `auto-checks.md` — **机械检测清单**（DRAFT 阶段强制运行的 lint，A-F 六组）
- `anti-patterns.md` — **重定向薄壳**（v2 时代的 16 条反模式已分流到上面两份；保留为外部链接兼容）

**执行层**：
- `interview-questions.md` — 候选问题清单（模型按"信息缺口评估闭环"按需取，不全问、不固定数量）
- `answer-to-template-map.md` — INTERVIEW 答案 → 模板变量映射表（含命名规范）
- `archetypes.md` — 5 种 archetype 详解 + 决策器（信号优先级）+ E 型自动触发规则 + 混搭契约
- `tagline-formulas.md` — 6 种 tagline 套路（中文 ≤30 汉字 / 英文 ≤120 字符）
- `section-library.md` — Section 模板库（**唯一真理源** — 所有 archetype 拼装时都从这里取）
- `trust-signals.md` — 14 种信任信号 + badges / logo 墙 / star history 模板（含条件渲染规则）
- `bilingual-patterns.md` — 4 种双语模式（M1 中文优先双文件为默认，含 silent fail 规避规则）
- `image-plan.md` — 图片任务清单生成规则（统一 placehold.co）
- `domestic-elements.md` — 中文社区特有元素（飞书/微信群/ModelScope/Bilibili/国内一键部署）
- `scope-out.md` — 不该用本 Skill 的场景 + 推荐替代

## 子目录

- `templates/` — 5 种 archetype 骨架模板（中英双版均完整）+ universal-blocks（通用区块）
