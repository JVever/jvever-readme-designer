<div align="center">

# jvever-readme-designer

**Design your README as a landing page, not a doc dump.**

[![License](https://img.shields.io/badge/license-TBD-lightgrey)](#license) [![Claude Code Skill](https://img.shields.io/badge/Claude_Code-Skill-orange)](https://docs.claude.com/en/docs/claude-code/skills) ![Bilingual](https://img.shields.io/badge/lang-zh%20%2B%20en-blue)

[SKILL](skills/jvever-readme-designer/SKILL.md) · [CHANGELOG](CHANGELOG.md) · [中文](README.md)

</div>

---

## What is this

A Claude Code Skill: when you say "write me a README", it **reads your project code first**, makes every design call itself (archetype, tagline formula, section order, what to highlight), runs two layers of self-check, and ships a **bilingual marketing-grade README**.

The only thing it leaves to you: **the review**.

> Skill is a portable format supported by Claude Code, Cursor, Codex, and other AI editors — install once, use anywhere.

---

## Quickstart

```bash
git clone https://github.com/JVever/jvever-readme-designer.git
cp -r jvever-readme-designer/skills/jvever-readme-designer ~/.claude/skills/
```

Open Claude Code in your project and say:

```
> /jvever-readme-designer
```

Or trigger in plain language:

```
> Rewrite this project's README as a landing page
> My README is bland, give it a real front door
```

The Skill scans, decides, drafts, and only stops to ask when it's time to review.

---

## Why this Skill

### 1. Reads your code by default — doesn't ask what it can infer

Most README tools open with "please answer these 7 questions". This Skill opens with a **scan** — manifests (package.json / Cargo.toml / pyproject.toml / go.mod / pubspec.yaml …), entry shape (CLI / library / web app / mobile / desktop / AI model / Skill), primary language, visual assets, trust signals state.

**If the code can tell, it won't ask you.** The model only asks when missing information would noticeably degrade the result, and **never** kicks design questions like "which tagline formula" or "what section order" back to the user.

For most projects, the answer is **0 follow-up questions**.

### 2. 5 archetypes, auto-decided

Different products need different README skeletons. The Skill picks for you:

| Archetype | Fits | Hero formula |
|---|---|---|
| A Dev tool | CLI / SDK / library / IDE plugin | Category-defining + asciinema |
| B Infrastructure | DB / BaaS / cloud / API gateway | Outcome promise + adopters wall |
| C Consumer tool | Desktop app / AV / writing | Identity resonance + heavy visual |
| D New-category | LLM agent / brand-new concept | Metaphor / persona + video demo |
| E Endorsement-first | Crowded space, strong incumbents | User quote as H1 |

The decision tree picks based on manifest + entry shape, with mixing allowed (e.g. an A-type CLI borrowing D's "What is X" block). Every section template comes from one source: [section-library.md](skills/jvever-readme-designer/references/section-library.md). **Single source of truth**, no copies.

### 3. Subjective + mechanical self-checks, kept separate

After DRAFT, two passes:

- **5 core principles** ([principles.md](skills/jvever-readme-designer/references/principles.md)) handle subjective calls — First screen decides life or death / Job-driven not feature-list / Show don't tell / Restraint is professional / Trust signals + alive maintenance. Each principle anchors a real anti-example as a memory hook.
- **Mechanical lint** ([auto-checks.md](skills/jvever-readme-designer/references/auto-checks.md)) handles right-vs-wrong — local path leakage (`/Users/<x>/`), broken license link, `via.placeholder.com` (defunct), bilingual switcher silent fail, unfilled placeholders, oversized decorative ASCII, emoji-in-headings … each item is a regex or string blacklist; matches get auto-fixed or block REVIEW.

**Judgment calls vs. lookup calls — never mixed.** That separation is the heart of the v3 refactor.

### 4. Bilingual by default, China ecosystem ready

Bilingual demand is high among Chinese open-source projects. The default is **M1 Chinese-first dual-file** (`README.md` Chinese + `README_en.md` English), **not machine-translated** — each version is rewritten in its own idiom.

Chinese projects auto-enable a bundle of **conditionally rendered** China-specific sections (silent for international projects): Lark / WeChat / QQ groups, ModelScope / WiseModel mirrors (AI projects), Aliyun / Sealos / Zeabur one-click deploys, Bilibili demos, Gitee / GitCode mirrors, Trendshift / HelloGitHub badges.

### 5. Trust signals are thresholded — never look poor

A 50-star project showing a Star History chart screams weakness. The Skill renders by threshold:

| Section | Renders when |
|---|---|
| Star History | ≥1k stars |
| Contributors wall | ≥10 contributors |
| Adopters wall | User supplies ≥3 real adopters |
| Testimonials | User supplies ≥2 real quotes |

Below threshold, nothing renders. Your README **shows what's strong, hides what isn't**.

---

## How it works

```
READ+DECIDE  →  DRAFT  →  ⛔ REVIEW
```

| Stage | What happens |
|---|---|
| **READ+DECIDE** | Local scan (manifests / assets / existing README / LICENSE / CI), **no network, no fabrication**. Auto-decides archetype, bilingual pattern, tagline formula, section order. Asks 0-3 real unknowns in one round if any. |
| **DRAFT** | Generates `README.md` + `README_en.md` + `docs/readme-image-plan.md`. Two-layer self-check loops ≤2 rounds, auto-fixing what's safe. |
| **⛔ REVIEW** | The only block. Shows "auto-fixed" + "⚠️ defaulted fields", waits for your read. 1-2 iterations to ship. |

---

## Modes (3-dimensional orthogonal)

```bash
/jvever-readme-designer                          # quick + bilingual + with-images (default)
/jvever-readme-designer --full                   # broader interview tolerance
/jvever-readme-designer --rewrite --en-only      # rewrite existing, English only
/jvever-readme-designer --patch --zh-only        # patch missing sections, Chinese only
```

| Dimension | Options | Default |
|---|---|---|
| Flow | `--quick` / `--full` / `--rewrite` / `--patch` | `--quick` |
| Output language | `--bilingual` / `--en-only` / `--zh-only` | `--bilingual` |
| Image plan | `--with-images` / `--no-images` | `--with-images` |

Persistent overrides: copy `skills/jvever-readme-designer/EXTEND.md` into your project root.

---

## When *not* to use

| Situation | Better path |
|---|---|
| One typo / one broken link | Just Edit |
| Pure dotfiles / awesome-list (no code) | Plain markdown |
| Someone else's project (you don't maintain) | Don't run — not your front door |
| You want CHANGELOG / API docs / wiki | Use the right tool |
| Personal reference (not public) | Minimal structure is fine |

---

## Project structure

```
jvever-readme-designer/
├── README.md                                # Chinese
├── README_en.md                             # English (this file)
├── CHANGELOG.md
├── docs/
│   └── readme-image-plan.md                 # Image task plan
├── research/
│   └── synthesis.md                         # 60+ project survey
├── assets/                                  # Visual asset placeholders
└── skills/
    └── jvever-readme-designer/
        ├── SKILL.md                         # Main entry, 3-stage workflow
        ├── EXTEND.md                        # User preference template
        └── references/
            ├── principles.md                # 5 core principles
            ├── auto-checks.md               # Mechanical lint
            ├── archetypes.md                # 5 archetypes + decision tree
            ├── tagline-formulas.md          # 6 tagline formulas
            ├── section-library.md           # Section templates (single source)
            ├── trust-signals.md             # Trust signal catalog
            ├── bilingual-patterns.md        # Bilingual patterns
            └── image-plan.md                # Image plan generation rules
```

---

## How it was built

5 parallel sub-agents surveyed **60+ open source READMEs** (Cursor, Aider, OpenHands, LangChain, Vercel, Supabase, PostHog, ChatTTS, FastGPT, Dify, Lobe Chat, MaxKB …) and product landing pages (Linear, Stripe, Raycast, Notion, Arc, Warp …), plus 7 design methodology sources (Standard README spec, Tom Preston-Werner's RDD, StoryBrand SB7, Jobs-to-be-Done, NN/G F-pattern research …).

Then iterated through 4 independent reviewer agents (design rationality / real-world simulation / anti-pattern audit / trigger & naming review) + one verification round. Full trace in [research/synthesis.md](research/synthesis.md).

Key design influences:
- **Standard README spec** — Richard Litt
- **README Driven Development** — Tom Preston-Werner (2010)
- **StoryBrand SB7** — Donald Miller
- **Jobs-to-be-Done** — Tony Ulwick / Christensen
- **Cognitive science** — F-pattern reading (NN/G), choice overload (Iyengar/Lepper), peak-end rule (Kahneman)

---

## Maintenance

Every release / every 3 months / star count doubling — run:

```
> /jvever-readme-designer --rewrite
```

Re-evaluates archetype / hero strength / trust signal state. A README is a living product page; six months without an update reads as dead.

---

## License

TBD — please add a `LICENSE` file (MIT / Apache-2.0 / BSD-3 are reasonable choices).
