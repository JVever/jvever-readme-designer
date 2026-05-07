<div align="center">

# jvever-readme-designer

**Designs your README as a landing page — not a doc dump.**

[![License](https://img.shields.io/badge/license-TBD-lightgrey)](#license) [![Claude Code Skill](https://img.shields.io/badge/Claude_Code-Skill-orange)](https://docs.claude.com/en/docs/claude-code/skills) [![Bilingual](https://img.shields.io/badge/lang-zh%20%2B%20en-blue)](README.md)

[SKILL.md](skills/jvever-readme-designer/SKILL.md) · [CHANGELOG](CHANGELOG.md) · [中文](README.md)

</div>

> A Claude Code Skill: when you say "rewrite my README," it scans your codebase first, runs a **gap-driven interview** (skipping anything it can infer), picks an archetype automatically, runs a **two-layer self-check** (5 principles + mechanical lint), then ships a bilingual marketing-grade README.

```bash
git clone https://github.com/JVever/jvever-readme-designer.git
cp -r jvever-readme-designer/skills/jvever-readme-designer ~/.claude/skills/
# Then open Claude Code in your project and say /jvever-readme-designer
```

---

## What is jvever-readme-designer?

**Short version**: a methodology pack that makes Claude Code design your README **like a PM + designer + copywriter** — not like a docs writer.

**Long version**:

It's not a template generator (no fill-in-the-blank like readme.so), and it's not a single prompt. It's a Claude Code Skill carrying a **structured methodology**:

- **Reads your code first** — manifest, commit history, existing README, entry shape, visual assets, trust signals — anything inferable is not asked
- **Interviews you only when something is genuinely missing** (gap-driven, not a fixed questionnaire; you choose the willingness level, the model decides what to ask)
- **Picks an archetype automatically** based on your project type (5 archetypes: developer tool / infrastructure / consumer tool / new-category education / endorsement-first)
- **Subjective judgment** runs through **5 core principles** (first-screen decides life-or-death / job over feature list / show don't tell / restraint is professional / trust signals + alive maintenance)
- **Objective checks** run through a **mechanical lint** (path leakage / broken links / dead placeholder hosts / bilingual silent-fail / unreplaced placeholders, etc.)
- Default output: **bilingual** (`README.md` zh + `README_en.md` en) + a `docs/readme-image-plan.md` checklist

**Result**: your README goes from "100 lines of doc-style noise" to "5 seconds to grok the product → 30 seconds to want to try → 1 minute of trust building" — i.e. a real landing page.

---

## Quickstart

```bash
# 1. Install the Skill
git clone https://github.com/JVever/jvever-readme-designer.git
cp -r jvever-readme-designer/skills/jvever-readme-designer ~/.claude/skills/

# 2. In your project, open Claude Code and say:
> /jvever-readme-designer

# Or trigger it in natural language:
> Rewrite my README as a landing page
```

<details>
<summary>Modes (three orthogonal axes)</summary>

```
/jvever-readme-designer                          # quick + bilingual + with-images (default)
/jvever-readme-designer --full                   # answer more questions, prioritize quality
/jvever-readme-designer --rewrite --en-only      # rewrite existing README, English only
/jvever-readme-designer --patch --zh-only        # patch holes in an existing Chinese README
```

Full reference in [SKILL.md](skills/jvever-readme-designer/SKILL.md).

</details>

<details>
<summary>Persistent preferences (EXTEND.md)</summary>

Copy `skills/jvever-readme-designer/EXTEND.md` into your project root and tweak defaults (always-`--full`, always-`--zh-only`, fixed emoji style, etc.).

</details>

---

## Why this Skill

### 1. Reads your code first; only asks what it can't infer

Most README generators open with "answer these 7 questions." This Skill opens with a **scan**:

- manifest files (`package.json` / `Cargo.toml` / `pyproject.toml` / `go.mod` / `Gemfile` / `pubspec.yaml` / ...)
- entry shape (CLI / Library / Web app / Mobile / Desktop / AI Model — 11 inferred categories)
- commit-message language, existing-README highlight phrases, trust-signal status (`LICENSE` / CI / `CHANGELOG` / `SECURITY`)

**If it's inferable from code, it doesn't ask.** It only asks things that are "still genuinely unknown after reading code AND would visibly degrade README quality if skipped." With the dual-layer "dynamic gap eval × 3-tier willingness" decision, the interview is typically 0-5 questions — not a fixed 7.

### 2. 5 archetypes, automatic decision, no one-size-fits-all

Different product types deserve different README skeletons:

| Archetype | Fits | Hero pattern |
|---|---|---|
| **A Developer Tool** | CLI / SDK / library / IDE plugin | Category-defining + asciinema |
| **B Infrastructure / Platform** | DB / BaaS / cloud / API gateway | Outcome promise + adopters wall |
| **C Consumer / Creator Tool** | Desktop app / video-audio / writing | Identity-resonance + strong visuals |
| **D New-Category Education** | LLM agents / novel concepts | Persona / metaphor + video demo |
| **E Endorsement-First** | Categories with strong incumbents | User quote as H1 |

The decision tree picks one based on manifest + entry shape + your answers, with mixing allowed (e.g. an A-type CLI can borrow D's architecture mermaid). All section templates come from [`section-library.md`](skills/jvever-readme-designer/references/section-library.md) — **single source of truth**, no duplicates.

### 3. Principle-driven judgment + mechanical lint

**Subjective judgment** lives in [5 core principles](skills/jvever-readme-designer/references/principles.md): first-screen decides life-or-death / job over feature list / show don't tell / restraint is professional / trust signals + alive maintenance. Each principle ships with concrete "anti-anchors" as memory hooks.

**Objective checks** live in [mechanical lint rules](skills/jvever-readme-designer/references/auto-checks.md): local path leakage (`/Users/<x>/`), broken license links, the dead `via.placeholder.com`, bilingual silent-fail, unreplaced placeholders, oversized post-hero ASCII, emoji in headings — every rule is unambiguous, auto-fixable or hard-blocking.

> Subjective and mechanical rules **stay separate** — the v3 refactor's core insight is "judgment problems vs. lookup problems" don't belong in the same checklist. Let the model judge where it should judge; let the rules check where they can check.

### 4. Bilingual by default + Chinese ecosystem ready

Open-source projects from China usually need bilingual READMEs, but most generators only know English. This Skill defaults to **M1 Chinese-first dual-file** (`README.md` zh + `README_en.md` en) and ships a set of "domestic" sections (**conditionally rendered** — they don't show up for non-Chinese projects):

- Lark / WeChat / QQ community entries
- ModelScope / WiseModel / OpenXLab model mirrors (for AI projects)
- Aliyun ComputeNest / Sealos / Zeabur / 1Panel one-click deploy
- Bilibili demo video embeds
- Gitee / GitCode / Atomgit code mirrors
- Trendshift / HelloGitHub / OSCHINA leaderboard badges

---

## Core features

- 🔍 **Scan first, ask only the gap** — manifest / commit / entry shape inferred up front; questions are project-specific, not template-fixed
- 🎯 **5 archetypes auto-decided** — decision tree by entry shape + your answers, cross-archetype mixing allowed
- 📐 **section-library as single source of truth** — 16 section templates in one file, no duplicates, no drift
- 🛡 **Principles + lint, two layers of self-check** — judgment vs. lookup kept separate, neither contaminates the other
- 🌏 **Bilingual default + Chinese ecosystem built-in** — M1 Chinese-first, Lark / ModelScope / one-click deploy conditionally rendered
- 📦 **Image task plan generated alongside** — `docs/readme-image-plan.md` lists each image's location / purpose / dimensions / priority / making tool
- ⚡ **`--rewrite` / `--patch` incremental modes** — never black-box rewrite. Outputs a diff report first (keep X / rewrite Y / add Z), then regenerates after your approval

---

## Contributing

This is an early-stage project. Feedback welcome:

- 🐛 **Issues** — wrong archetype decisions / missed lint rules / template defects
- 💡 **Feature requests** — new archetypes / new section templates / new lint rules
- 📖 **References improvements** — any file under `references/`
- 💻 **PRs** welcome

Change log: [CHANGELOG.md](CHANGELOG.md).

---

## License

License: TBD (suggest adding a `LICENSE` file, MIT recommended).
