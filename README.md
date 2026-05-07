<div align="center">

# jvs-readme-designer

**Interview-driven, marketing-grade README designer for code projects.**

Treat your README as a landing page, not a doc dump.

![type](https://img.shields.io/badge/type-Claude_Code_Skill-7C3AED?style=flat-square)
![status](https://img.shields.io/badge/status-v2.1_production-green?style=flat-square)
![bilingual](https://img.shields.io/badge/output-中文+English-orange?style=flat-square)
![license](https://img.shields.io/badge/license-MIT-blue?style=flat-square)

[Install](#installation) · [Usage](#usage) · [Modes](#modes) · [Why](#why-this-exists) · [中文文档](README_CN.md)

</div>

---

A Claude Code Skill that interviews you, picks an archetype for your project, and generates a product-marketing-grade README — bilingual, with an image task plan.

---

## Why this exists

Most open source READMEs are doc dumps: install command + feature list + license. Visitors leave in 5 seconds.

The good ones — Linear, Cursor, Vercel, Supabase, FastGPT, Lobe Chat — treat README as a product landing page:

- A hero that answers "what / for whom / how to start" in 5 seconds
- Show-don't-tell evidence for every claim (GIF / benchmark / code / before-after)
- Trust signals (adopters, testimonials, real numbers, last release date)
- Structure tuned to the product's archetype, not a one-size-fits-all template

This Skill captures that craft. You answer 3 questions; it picks the right archetype, runs an anti-pattern self-check, and ships bilingual output.

---

## Features

- **5 archetypes** — A Dev tool / B Infrastructure / C Consumer tool / D New-category / E Endorsement-first. Auto-decision tree based on SCAN + interview signals.
- **6 tagline formulas** — Category-defining, outcome-promise, identity-resonance, third-party endorsement, metaphor, hard-numbers.
- **17-point self-check** — Single source of truth in `references/principles.md`. Runs automatically before showing the draft. Auto-fixes safe issues; escalates judgment calls.
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
| **Flow** | `--quick` (3 Qs) / `--full` (7 Qs) / `--rewrite` (preserve gold, fix weak, fill gaps) / `--patch` (gaps only, no interview) | `--quick` |
| **Output language** | `--bilingual` / `--en-only` / `--zh-only` | `--bilingual` |
| **Image plan** | `--with-images` / `--no-images` | `--with-images` |

```bash
/jvs-readme-designer                       # quick + bilingual + with-images
/jvs-readme-designer --full                # deep interview, 7 questions
/jvs-readme-designer --rewrite --en-only   # rewrite existing, English only
/jvs-readme-designer --patch               # fill gaps only, no interview
```

Persistent overrides → `EXTEND.md` in your project root.

---

## Installation

```bash
# Clone this repo
git clone <this-repo-url> ~/Code/18-My_Skills/12-jvs-readme-designer

# Symlink the skill into Claude Code's skills directory
ln -s ~/Code/18-My_Skills/12-jvs-readme-designer/skills/jvs-readme-designer \
      ~/.claude/skills/jvs-readme-designer

# Verify
ls ~/.claude/skills/jvs-readme-designer
# → SKILL.md  EXTEND.md  _INDEX.md  references/
```

Restart Claude Code. The skill auto-loads on next session.

---

## Usage

In Claude Code, trigger by saying any of these (English or Chinese):

- "Write a marketing-grade README for this project"
- "Polish my README"
- "我的 README 太朴素了，重做一下"
- "帮这个项目设计 README"
- "GitHub 项目首页要发布了，做一下门面"

The Skill auto-engages and walks you through 5 stages, pausing at each ⛔ for your confirmation.

To trigger explicitly: `/jvs-readme-designer` (with optional flags).

---

## How it works

```
SCAN → ⛔ INTERVIEW → ⛔ ARCHETYPE → DRAFT → ⛔ REVIEW
```

| Stage | What happens |
|---|---|
| **SCAN** | Reads project locally (manifests, assets, existing README, LICENSE, CI). **No network calls, no fabricated data.** Reports a "project profile" for confirmation. |
| **⛔ INTERVIEW** | 3 questions (quick) or 7 (full). Batched via `AskUserQuestion`. Skips questions already answered by SCAN. |
| **⛔ ARCHETYPE** | Decision tree picks 1 of 5 archetypes; you can override. Section order is proposed concretely (not abstract template). |
| **DRAFT** | Generates `README.md` + `README_en.md` + `docs/readme-image-plan.md`. Self-check loop runs ≤2 rounds; auto-fixes safe issues. |
| **⛔ REVIEW** | Shows what was auto-fixed, what was escalated, and subjective decision points (tagline alternatives). Iterates 1–2 rounds on your feedback. |

---

## Project structure

```
12-jvs-readme-designer/
├── README.md                          # English (this file)
├── README_CN.md                       # 中文
├── CHANGELOG.md
├── research/
│   └── synthesis.md                   # 60+ project / site survey, 17 insights
└── skills/
    └── jvs-readme-designer/           # The actual Claude Code skill
        ├── SKILL.md                   # Main entry, 5-stage workflow (404 lines)
        ├── EXTEND.md                  # User preferences template
        ├── _INDEX.md
        └── references/
            ├── principles.md          # 7 core principles + single-source checklist
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

See [scope-out.md](skills/jvs-readme-designer/references/scope-out.md) for the full list. Quick check:

- Single-line edits → just edit, don't run a 5-stage workflow
- Pure dotfiles / awesome-list / non-software repos → use plain markdown
- Internal tools you don't market → minimal structure is fine
- README for someone else's project → don't rewrite other people's storefront

---

## Status & roadmap

- **v2.1** (current) — Production-ready. Passed 4-reviewer audit + verification round.
- **v3** (planned) — Quantitative evals: run the Skill on a fixture set of real open source projects, score outputs against the 17-point checklist programmatically.

Known limitations:
- The E archetype (endorsement-first) requires real testimonials and **will not fabricate** — by design.
- SCAN does not call GitHub API (kept local to avoid `hallucinated` star/version numbers); badges that need fresh data use shields.io URLs that resolve at render time.

---

## License

[MIT](LICENSE) © 2026 jvs
