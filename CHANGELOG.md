# Changelog

## v3.0 — 2026-05-07

**架构层重构**——基于多轮真实使用反馈的设计哲学转向。

**命名统一**
- 整个项目从 `jvs-` 前缀改为 `jvever-`（用户身份对齐）
- GitHub 仓库重命名 / 触发命令 `/jvever-readme-designer` / 所有内部引用同步

**设计哲学转向：反模式驱动 → 正向原则驱动**
- 7 条原则收束为 **5 条核心原则**（principles.md）——主观设计判断的唯一信仰来源
- 每条原则下挂"反例锚"作为记忆点，不再单独成"反模式 #1-#16"
- 16 条反模式分流：
  - 主观判断（emoji 滥用 / 装饰 ASCII / hero 喧宾夺主 / 中英混杂用冷词等）→ 归入 5 条原则
  - 机械可检测（路径泄露 / broken link / 占位符未替换 / 黑名单替换字典等）→ 独立到 `auto-checks.md`
- `anti-patterns.md` 改为重定向薄壳，提供 v2 → v3 的查询表
- **新增 `auto-checks.md`**：A-F 六组机械检测（A 路径与隐私 / B 链接与文件 / C 占位符 / D 装饰物 / E 中英混杂黑名单 / F 模式一致性），每项 regex/字符串黑名单/文件存在性检查，对错明确

**访谈机制：配额驱动 → 信息驱动**
- 删除 `--quick` 上限 5 / `--full` 上限 7 的硬数字
- 没有固定数量、没有硬上限——基于"还有哪些信息缺失会让结果明显打折"动态决定
- 决策权两层分离：用户决定意愿强度（多答 / 只答关键 / 全跳过），模型决定问什么、问几个
- SKILL.md §2.2 加入"信息缺口评估闭环"——每答一批后重评估
- `interview-questions.md` 改名"候选问题清单"+ 加"信息缺口判断速查表"

**DRAFT 自检：合并为两层**
- 第一层：机械检测（`auto-checks.md`）——强制不可跳过
- 第二层：主观原则自检（`principles.md` 5 条）
- 删除原 §4.9 的 anti-patterns 引用，改为分流到上面两层

**README 措辞调整**
- 中英两版"最多 5 个问题"措辞改为"基于信息缺口动态决定，无固定上限"
- `Features` 段反映新结构（5 原则 + 机械检测分离）

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
