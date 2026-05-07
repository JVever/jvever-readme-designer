<div align="center">

# jvever-readme-designer

**Interview-driven, marketing-grade README designer for code projects.**

Treat your README as a landing page, not a doc dump.

![type](https://img.shields.io/badge/type-Claude_Code_Skill-7C3AED?style=flat-square)
![status](https://img.shields.io/badge/status-v2.1_production-green?style=flat-square)
![bilingual](https://img.shields.io/badge/output-中文+English-orange?style=flat-square)
![license](https://img.shields.io/badge/license-MIT-blue?style=flat-square)

[Install](#installation) · [Usage](#usage) · [Modes](#modes) · [Why](#why-this-exists) · [中文文档](README_CN.md)

</div>

---

A skill that scans your project, lets you choose how much time you want to spend answering (more / only the critical few / skip with all defaults), and lets the model decide *what* to ask and *how many* based on the information gaps it sees. No fixed quota. Final output: a product-marketing-grade bilingual README plus an image task plan.

> Skill is a portable format supported by Claude Code, Cursor, Codex, and other AI editors — install once, use anywhere.

---

## Why this exists

Most open source READMEs are doc dumps: install command + feature list + license. Visitors leave in 5 seconds.

The good ones — Linear, Cursor, Vercel, Supabase, FastGPT, Lobe Chat — treat README as a product landing page:

- A hero that answers "what / for whom / how to start" in 5 seconds
- Show-don't-tell evidence for every claim (GIF / benchmark / code / before-after)
- Trust signals (adopters, testimonials, real numbers, last release date)
- Structure tuned to the product's archetype, not a one-size-fits-all template

This Skill captures that craft. It scans your project first, lets you set the interview depth, then asks only what it actually needs based on detected gaps. Picks the right format, runs a two-layer self-check (mechanical lint + 5 positive principles), and ships bilingual output.

---

## Features

- **5 archetypes** — A Dev tool / B Infrastructure / C Consumer tool / D New-category / E Endorsement-first. Auto-decision tree based on SCAN + interview signals.
- **6 tagline formulas** — Category-defining, outcome-promise, identity-resonance, third-party endorsement, metaphor, hard-numbers.
- **5 positive principles + mechanical lint, separated** — Subjective judgment lives in [`principles.md`](skills/jvever-readme-designer/references/principles.md) (5 principles, each with anchor anti-examples). Mechanical checks (path leakage, broken links, placeholder leftovers, mixed-language blacklist, etc.) live in [`auto-checks.md`](skills/jvever-readme-designer/references/auto-checks.md). Both run before draft is shown.
- **Bilingual by default** — Chinese-first (M1: `README.md` + `README_en.md`) with proper i18n switching (current-language badge is not a link → no silent fail).
- **Image task plan** — Separate `docs/readme-image-plan.md` with priority, dimensions, and how-to-make guidance. Auto-generated assets (Star History, contributors, mermaid) skip the plan.
- **Conditional trust signals** — Star History only renders ≥1k stars, contributors wall only ≥10 authors, adopters only when user provides real names. No "displaying poor" with 50-star projects.
- **Domestic elements for Chinese projects** — WeChat / Lark / QQ groups, ModelScope mirror, Bilibili demo, Aliyun / Sealos one-click deploy.
- **`EXTEND.md` for persistent preferences** — Override default archetype, bilingual pattern, emoji style, render thresholds.
- **Scope-out boundary** — Explicit "when NOT to use this Skill" list to avoid mis-triggering on dotfiles / single-line edits / private references.

---

## Modes (3-dimensional orthogonal)

Three independent dimensions, freely composable:

| Dimension | Options | Default |
|---|---|---|
| **Flow** | `--quick` (default; model decides count from gaps + your willingness) / `--full` (broader candidate pool, leans toward asking more) / `--rewrite` (preserve gold, fix weak, fill gaps) / `--patch` (gaps only, no interview) | `--quick` |
| **Output language** | `--bilingual` / `--en-only` / `--zh-only` | `--bilingual` |
| **Image plan** | `--with-images` / `--no-images` | `--with-images` |

Question count is **not fixed and has no hard cap**. At the start of every interview you choose your willingness — answer more, answer only the critical, or skip with all defaults. Within that boundary, the model evaluates "what missing information would meaningfully degrade the result" and asks only those.

```bash
/jvever-readme-designer                       # default: bilingual + image plan + targeted interview
/jvever-readme-designer --full                # deeper interview
/jvever-readme-designer --rewrite --en-only   # rewrite existing, English only
/jvever-readme-designer --patch               # fill gaps only, no interview
```

Persistent overrides → `EXTEND.md` in your project root.

---

## Installation

Simplest path — clone directly into Claude Code's skills folder:

```bash
git clone https://github.com/<owner>/jvever-readme-designer.git \
  ~/.claude/skills/jvever-readme-designer

# Verify
ls ~/.claude/skills/jvever-readme-designer/skills/jvever-readme-designer
# → SKILL.md  EXTEND.md  _INDEX.md  references/
```

> Replace `<owner>` with the actual GitHub owner.

If you'd rather keep the repo in your own code directory and symlink it:

```bash
# Clone wherever you keep your code
git clone https://github.com/<owner>/jvever-readme-designer.git <your-code-dir>/jvever-readme-designer

# Symlink
ln -s <your-code-dir>/jvever-readme-designer/skills/jvever-readme-designer \
      ~/.claude/skills/jvever-readme-designer
```

Cursor / Codex / other AI editors: see their respective docs for registering `skills/jvever-readme-designer` as a skill.

Restart your editor. The skill auto-loads on next session.

---

## Usage

In your AI editor, trigger by saying any of these (English or Chinese):

- "Write a marketing-grade README for this project"
- "Polish my README"
- "我的 README 太朴素了，重做一下"
- "帮这个项目设计 README"
- "GitHub 项目首页要发布了，做一下门面"

The Skill auto-engages and walks you through 5 stages, pausing at each ⛔ for your confirmation.

To trigger explicitly: `/jvever-readme-designer` (with optional flags).

---

## How it works

```
SCAN → ⛔ INTERVIEW → ⛔ FORMAT PICK → DRAFT → ⛔ REVIEW
```

| Stage | What happens |
|---|---|
| **SCAN** | Reads project locally (manifests, assets, existing README, LICENSE, CI). **No network calls, no fabricated data.** Reports a "project profile" for confirmation. |
| **⛔ INTERVIEW** | Opens with a willingness choice (more / only critical / skip with defaults). Within that boundary, the model picks what to ask and how many based on detected information gaps — **no fixed count**. Skips anything SCAN already answered. |
| **⛔ FORMAT PICK** | Decision tree picks 1 of 5 README formats; you can override. Section order is proposed concretely (not abstract template). |
| **DRAFT** | Generates `README.md` + `README_en.md` + `docs/readme-image-plan.md`. Self-check loop runs ≤2 rounds; auto-fixes safe issues. |
| **⛔ REVIEW** | Shows what was auto-fixed, what was escalated, and subjective decision points (tagline alternatives). Iterates 1–2 rounds on your feedback. |

---

## Project structure

```
jvever-readme-designer/
├── README.md                          # English (this file)
├── README_CN.md                       # 中文
├── CHANGELOG.md
├── research/
│   └── synthesis.md                   # 60+ project / site survey, 17 insights
└── skills/
    └── jvever-readme-designer/           # The actual skill
        ├── SKILL.md                   # Main entry, 5-stage workflow
        ├── EXTEND.md                  # User preferences template
        ├── _INDEX.md
        └── references/
            ├── principles.md          # 5 core principles (single source for subjective design)
            ├── auto-checks.md         # Mechanical lint (mandatory, runs in DRAFT)
            ├── interview-questions.md
            ├── answer-to-template-map.md
            ├── archetypes.md          # 5 archetypes + decision tree
            ├── tagline-formulas.md
            ├── section-library.md     # Section templates (single source)
            ├── trust-signals.md
            ├── bilingual-patterns.md
            ├── image-plan.md
            ├── anti-patterns.md
            ├── domestic-elements.md
            ├── scope-out.md           # When NOT to use
            └── templates/
                ├── archetype-A-dev-tool.md
                ├── archetype-B-infrastructure.md
                ├── archetype-C-consumer-tool.md
                ├── archetype-D-new-category.md
                ├── archetype-E-endorsement-first.md
                └── _universal-blocks.md
```

---

## How it was built

5 parallel research agents surveyed **60+ open source READMEs** (Cursor, Aider, OpenHands, LangChain, Vercel, Supabase, PostHog, ChatTTS, FastGPT, Dify, Lobe Chat, MaxKB …) and product landing pages (Linear, Stripe, Raycast, Notion, Arc, Warp …), plus 7 design methodology sources (Standard README spec, Tom Preston-Werner's RDD, StoryBrand SB7, JTBD, NN/G F-pattern research …).

The Skill was then iterated through **4 independent reviewer agents** (design-rationality, real-world-simulation, anti-pattern audit, trigger/naming review) and one verification round. Final score: **8.5 / 10**, 27 of 30 issues fully resolved.

Full process traceable in [research/synthesis.md](research/synthesis.md).

Key design influences:
- **Standard README spec** — Richard Litt
- **README Driven Development** — Tom Preston-Werner (2010)
- **StoryBrand SB7** — Donald Miller
- **Jobs-to-be-Done** — Tony Ulwick / Christensen
- **Cognitive science** — F-pattern reading (NN/G), choice overload (Iyengar/Lepper jam study), peak-end rule (Kahneman)

---

## When NOT to use

See [scope-out.md](skills/jvever-readme-designer/references/scope-out.md) for the full list. Quick check:

- Single-line edits → just edit, don't run a 5-stage workflow
- Pure dotfiles / awesome-list / non-software repos → use plain markdown
- Internal tools you don't market → minimal structure is fine
- README for someone else's project → don't rewrite other people's storefront

---

## Status & roadmap

- **v2.1** (current) — Production-ready. Passed 4-reviewer audit + verification round.
- **v3.0** (current, 2026-05-07) — Architectural refactor: rename `jvs` → `jvever`; design philosophy shift from anti-pattern-driven to principle-driven (5 principles + mechanical lint); interview shifts from quota-driven to information-gap-driven (no fixed count, no hard cap).
- **v4** (planned) — Quantitative evals: run the Skill on a fixture set of real open source projects, score outputs against principles + auto-checks programmatically.

Known limitations:
- The endorsement-first format requires real testimonials and **will not fabricate** — by design.
- SCAN does not call GitHub API (kept local to avoid hallucinated star / version numbers); badges that need fresh data use shields.io URLs that resolve at render time.

---

## License

[MIT](LICENSE) © 2026 jvever
