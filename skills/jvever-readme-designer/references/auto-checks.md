<!--
@input:    DRAFT 阶段生成的 README / EXTEND.md / 图片任务清单 / 模板渲染结果
@output:   一组可机器执行的检测规则。每项要么"对/错明确"，要么有具体可检测的 regex/字符串模式
@rule:     新增检测时确保它真的"对/错明确"——主观判断的规则归入 principles.md，不放本文件
-->

# 机械检测清单（DRAFT 阶段强制运行）

**这是一份 lint 规则**，不是设计指引。每项规则都满足两个条件：
1. **对/错明确**——要么命中要么不命中，没有"看情况"
2. **可机械检测**——有 regex 模式、字符串黑名单、或文件存在性检查

主观判断（hero 是否克制、tagline 是否吸引、文案是否过营销）见 [`principles.md`](principles.md)。

---

## 运行时机

```
DRAFT 完成 → [本文件] 机械检测 → 命中 → 自动修复 / 阻断进入 REVIEW
                                  ↓
                               未命中
                                  ↓
                       原则层主观自检（principles.md）
                                  ↓
                              REVIEW
```

**任何机械检测命中都不可跳过**——必须修到通过才能进入 REVIEW。

---

## 检测项

### A. 路径与隐私

#### A1. 本地家目录路径泄露
**检测**：以下 regex 命中即失败——
- `/Users/[^/]+/`
- `/home/[^/]+/`
- `C:\\Users\\[^\\]+\\`
- `~/[A-Z][a-zA-Z]*/[0-9]+-`（个人编号目录习惯，如 `~/Code/18-My_Skills/`）

**修法**：替换为通用占位——
- skill 安装：`~/.claude/skills/<name>` 或 `<your-code-dir>/<name>`
- 一般项目：`<your-projects-dir>/<name>`

**严禁**：在 INTERVIEW 阶段问用户"想装到哪里"——这是把问题转嫁给用户，不解决根因。

#### A2. 当前用户标识泄露
**检测**：以下字符串出现即失败（除非项目 owner 本身就是该用户）——
- `git config user.name` / `user.email` 的值
- 当前用户的 SSH host alias
- 私有 fork URL（含当前 user 的 owner 段，但项目实际 owner 不是该 user）

**修法**：用 `<owner>` / `<your-name>` 占位，或不出现。

---

### B. 链接与文件

#### B1. License 链接
**检测**：
- 如果 README 中出现 `[MIT](LICENSE)` / `[Apache 2.0](LICENSE)` / `[License](LICENSE)` 等链接 → 检查项目根是否存在 `LICENSE` / `LICENSE.md` / `LICENSE.txt`
- 文件不存在 → 失败

**修法**：
- 不存在 → 改写"License: TBD（建议补 LICENSE 文件）"
- 不允许 broken link

#### B2. 占位图服务
**检测**：URL 中出现 `via.placeholder.com` → 失败（该服务已停服）

**修法**：替换为 `https://placehold.co/` 同尺寸 URL。

#### B3. 当前语言切换条不指向自己
**检测**：
- 中文版 README 中，当前语言 badge / 链接含 `href="README.md"` 或 `(README.md)` → 失败（点击会刷新本页）
- 英文版同理：当前语言不能链接 `README_en.md`

**修法**：当前语言 badge / 链接不带 `href`，仅作视觉标识。

#### B4. 单语模式不带切换条
**检测**：用户启用 `--zh-only` 或 `--en-only` 但 README 中出现切换条 → 失败

**修法**：删除整个切换条段落。

#### B5. 双语切换只放一处
**检测**：
- 顶部存在 `<p align="center">...lang-中文.../...lang-English...</p>` 切换条
- **同时** Hero nav 行包含 `[English](...)` 或 `[中文](...)` 链接
- → 失败（重复信息）

**修法**：保留 nav 行内嵌切换（推荐），删除顶部 badge 条；或仅保留顶部 badge 条删除 nav 内的语言链接。

#### B6. GitHub URL 与 git remote 一致性
**检测**：
- README 中出现 `github.com/<owner>/<repo>` 形式的链接（含 clone 命令、徽章 URL、issue 链接等）
- 与 `git remote get-url origin` 解析出的 owner/repo 不一致 → 失败

**修法**：
- 若仓库已配置 remote → 用 remote 的 owner/repo 替换
- 若仓库无 remote（本地仓库）→ 不写绝对 GitHub URL，改用相对路径或占位符 `<owner>/<repo>`
- 不允许 README 命令里的 clone URL 是不存在或臆造的仓库（这是原则 5"鲜活的硬规则"）

#### B7. install / 首屏命令的包名/版本真实性
**检测**：README 中的 install 命令（如 `pip install X` / `npm install Y` / `cargo install Z` / `brew install W` / `pip install X==1.2.0`）含具体包名 / 版本号 → 必须基于 SCAN 推断的真实值：

- 包名 ≠ manifest 实际 name（`package.json`/`pyproject.toml`/`Cargo.toml` 中读到的）→ 失败
- 写死的版本号（如 `pip install xx==1.2.0`）+ 与最新 release / manifest version 不一致 → 失败（除非用户明确说"锁版本"）
- 命令引用 dmg / 二进制下载链（`Project-0.1.3.dmg`）含具体版本号 + 与最新 release 不同步 → 失败

**修法**：
- 包名一律从 manifest 读取（不臆造）
- 版本号能用 shields.io 自动 badge 反映就别写死字面量
- 必须写死的（dmg 链接 / 锁版本场景）→ 在 image-plan / maintenance reminder 加一条"每次发版同步替换"

---

### C. 占位符与模板渲染

#### C1. 模板变量未替换
**检测**：README / EXTEND.md / image-plan 中残留 `{{` 或 `}}` → 失败

**修法**：所有 `{{var}}` 必须替换为实际值；找不到的值用 INTERVIEW 默认值后备（详见 SKILL.md §2.4）。

#### C2. URL 中的占位符未编码
**检测**：badge URL / 链接 URL 中含未 URL-encode 的中文 / 空格 / 特殊字符 → 失败

**修法**：URL-encode（如 `中文` → `%E4%B8%AD%E6%96%87`）。

#### C3. Adopters / Testimonials 占位符未替换
**检测**：以下硬编码的"模板示例公司名"出现在 adopters / testimonials 段 → 失败——
- `Stripe` / `Vercel` / `Shopify` / `Notion` / `Linear`（除非用户在 INTERVIEW 阶段确认这些**真的**是项目的 adopter）

**修法**：用户没提供真实名单 → **不渲染**该 section（条件渲染规则见 trust-signals.md）。

---

### D. 装饰物检测（细化原则 4 中可机械识别的部分）

#### D1. Hero 后过长的 ASCII 块
**检测**：
- Hero 区（H1 + tagline + badge + nav 行）之后、第二个 `---` 或第二个 `##` 之前出现 ` ``` ` 代码块
- 代码块行数 > 6 → 失败

**修法**：
- 如果是真实命令演示但行数过多 → 拆分，hero 只留 ≤6 行核心 input/output
- 如果是装饰性流程图（含 ⛔ ✅ 🔥 等 emoji + 大量 ─ 框线）→ 删除整块；hero 视觉应该用占位符 + image-plan，或直接空着

#### D2. Hero 视觉占位符服务一致性
**检测**：README 中所有占位图 URL 必须用 `placehold.co`（详见 B2）

#### D3. 标题里的 emoji
**检测**：H1 / H2 / H3 行包含 emoji（不是 ✓ ✗ — · 这类符号，是 🚀 ✨ 🔥 这类装饰）→ 失败

**修法**：移除标题里的 emoji。emoji 仅允许出现在 feature bullet 前缀（且全篇统一风格）。

#### D4. README 段落数 / 长度上限（克制即专业）
**检测**：
- A 型（开发者工具型）minimal-asset 模式下 `##` 段总数 > 7 → 警告
- README 总行数 > 200（不含代码块） → 警告
- 任意单 `##` 段含 ≥3 个 `###` 子标题 → 警告（features 段不应该用 H3 切分卖点，应该用 emoji bullet）

**修法**：每个超额段过 principles §4 段落必要性 sweep——"删掉这段读者损失什么具体能帮他做决策的信息？"答不出 → 删整段。

#### D5. 自我引用一致性（产品类别词全篇统一）
**检测**：README 中产品**类别词**（如 "Skill" / "Claude Code Skill" / "Agent" / "插件" / "工具"）出现矛盾性混用——
- Hero 区写 X，正文却说 X 其实是 Y
- 同一概念前后用不同词指代（如前面叫 "Skill"，后面叫 "插件"）

**修法**：选定一个**最准确的类别词**，全文统一；如果担心受众不熟悉，就用最通用的（"Skill"），用 1 行 note 说明覆盖面，不要在 hero 用窄词后又改口。

---

### E. 触发条件 / 模式一致性

#### E1. 单语模式不生成另一语言文件
**检测**：用户启用 `--zh-only` 但生成了 `README_en.md` → 失败（反之亦然）

**修法**：尊重用户的语言模式选择，不"额外送一个英文版"。

#### E2. `--no-images` 不生成 image-plan
**检测**：用户启用 `--no-images` 但生成了 `docs/readme-image-plan.md` → 失败

**修法**：根据 flag 严格控制生成。

---

## 修复机制

每项检测命中后的处理：

| 严重度 | 处理 |
|---|---|
| **可自动修**（A1 / B1 / B2 / B5 / C1 / C2 / D1 装饰类 / D3） | DRAFT 阶段直接修，不打扰用户。修复记录写入 REVIEW 报告的"已自动修复" |
| **需用户决策**（B1 中"是否真的有 LICENSE 文件"、C3 中"用户是否真有这些 adopter"） | 升级到 REVIEW，列出选项让用户选 |

**循环上限**：自动修循环 ≤ 2 轮；2 轮后剩余必须升级到 REVIEW。

---

## 与 principles.md 的边界

| 这里（auto-checks） | principles.md |
|---|---|
| 路径里有 `/Users/<x>/` | "Hero 是不是太满" |
| LICENSE 文件不存在 | "Tagline 够不够吸引人" |
| via.placeholder.com 已停服 | "feature 选了对的几条吗" |
| `{{var}}` 没替换 | "证据载体选哪个最合适" |
| ASCII 块超过 6 行 | "这一段是不是太营销" |
| 占位符未替换、broken link | "中英混杂是否影响理解、中英版结构是否对称" |

**判断标准**：能写成 regex / 字符串黑名单 / 文件存在性检查 → 这里。需要语义理解或主观判断 → principles.md。
