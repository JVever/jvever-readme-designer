# Changelog

## v2.1 — 2026-05-07

修复 v2 复审发现的 3 个真 bug：
- `archetype-A-dev-tool.md` 切换条 silent fail（中文当前仍是链接）
- `image-plan.md` 残留 `via.placeholder.com`（已停服）
- `references/*.md` 文件头注释豁免规则（在 `references/_INDEX.md` 显式声明）

复审打分：8.5/10，30 项问题中 27 项 ✅、3 项已补（v2.1）。

## v2 — 2026-05-07

基于 4 路独立 Reviewer Agent + skillofskills/skill-creator 元技能方法论的全面迭代：

**新增**
- `EXTEND.md` 用户偏好持久化模板
- `references/answer-to-template-map.md` 访谈答案 → 模板变量映射
- `references/scope-out.md` 不该用本 Skill 的场景
- 三维正交参数（流程 × 语言 × 图片）
- 5 阶段流程的 ⛔ BLOCKING 门控（SCAN / INTERVIEW / ARCHETYPE / REVIEW）
- `--rewrite` 完整流程（保留区 / 重写区 / 补漏区）
- `--patch` 差量补丁模式
- minimal-asset 模式（stars<100 / 无资产项目降级）
- archetype E 自动触发规则
- archetype 决策器信号优先级
- 反模式自检循环上限（≤2 轮）+ 自动可修 vs 必须升级分类

**修复**
- 双语切换条 silent fail（当前语言不带链接、单语模式删切换条）
- `via.placeholder.com` → `placehold.co`（前者已停服）
- 删除错误的 `shields.io.cn` 镜像建议
- adopters 模板硬编码（`stripe/vercel/shopify`）→ `{{adopter_n_*}}` 占位
- tagline 字数矛盾统一（中文 ≤30 汉字 / 英文 ≤120 字符）
- archetype 决策树死路径
- archetype-A 模板补 ⚠️ testimonial style 属性失效提示
- SCAN fallback（monorepo / mirror / 私有仓库 / 无 manifest）
- License 缺失时不写 broken link
- 信任信号 section 条件渲染规则

**改进**
- description 触发词中英扩展（GitHub 门面 / open-source launch / 双语 README 等）
- 默认从 `--full` 改为 `--quick`（降低认知负担）
- principles.md checklist 成为唯一真理源（去除 anti-patterns 重复）
- B/C/D/E archetype 模板补全英文版（v1 是"略"）

## v1 — 2026-05-07

首版。5 阶段流程 + 5 archetype + 6 tagline 套路 + 中英双语模板 + 国内特有元素。

基于 5 路并行 Sub-Agent 调研（60+ 开源项目 + 软件官网 + 设计方法论）。
