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

承载 Skill 的设计原则、模式库、模板与条件渲染规则。SKILL.md 只描述流程，具体内容查这里。

## 文件清单

**信仰层（主观判断 / 机械检测）**：
- `principles.md` — **5 条核心原则**（所有主观设计判断的唯一来源；每条挂"反例锚"）
- `auto-checks.md` — **机械检测清单**（DRAFT 阶段强制运行的 lint，A-E 五组；只放对错明确、可机械检测的规则）

**执行层（archetype 决策 + section 拼装）**：
- `archetypes.md` — 5 种 archetype 详解 + 决策器（信号优先级）+ E 型自动触发规则 + Section 拼装契约（DRAFT 阶段直接按此契约从 section-library 拼装，不再加载预存骨架）
- `section-library.md` — **唯一真理源** — Section 模板库（§1-§16 含 hero / quickstart / features / why / use-cases / architecture / adopters / testimonials / numbers / star-history / contributors / sponsors / contributing / 国内特有元素 / license）
- `tagline-formulas.md` — 6 种 tagline 套路（中文 ≤30 汉字 / 英文 ≤120 字符）
- `trust-signals.md` — 信任信号清单 + **条件渲染规则** + 真实性硬规则 + Badges 最佳实践 + 反信号清单（具体模板在 section-library §8-§13、§15）
- `bilingual-patterns.md` — 4 种双语模式（M1 中文优先双文件为默认，含 silent fail 规避规则）
- `image-plan.md` — 图片任务清单生成规则（统一 placehold.co）
