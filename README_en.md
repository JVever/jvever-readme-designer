<div align="center">

# jvever-readme-designer

**Read your code, ask at most 3 questions, ship a marketing-grade bilingual README.**

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](LICENSE) [![Type: Skill](https://img.shields.io/badge/type-Skill-blue.svg)](skills/jvever-readme-designer/SKILL.md)

[SKILL.md](skills/jvever-readme-designer/SKILL.md) · [CHANGELOG](CHANGELOG.md) · [中文](README.md)

</div>

> Treat README as a **landing page**, not a doc dump. The KPI is keeping a visitor past five seconds and getting them to `git clone` — not enumerating every feature.

> Works as a Skill across Claude Code / Cursor / Codex and similar AI editors — Claude Code is used as the example below.

## What you get

- 🧭 **5 archetypes picked for you** — CLI tool / infrastructure / creator app / new category / endorsement-first each have their own structure; the decision tree reads your manifest and chooses, no one-size-fits-all
- ✍️ **0–3 questions, then it works** — anything inferable from code is not asked; license, real adopter names, and a few subjective tonal calls are the only things asked, in a single round
- 🌏 **Chinese and English drafted together** — not machine translation; each version follows its own language's conventions and may even reorder the selling points
- 🛡 **Auto-fixes the verifiable, escalates the judgement calls** — path leaks, broken links, unreplaced placeholders are silently fixed; tagline strength and section trims are surfaced for your review
- 📋 **Image task list as a side product** — `docs/readme-image-plan.md` lists hero / logo / screenshots with priority and recommended tooling

## Quick start

Drop the Skill folder into Claude Code's skills directory (`~/.claude/skills/` for global or `.claude/skills/` per project), then in any repo say:

```
/jvever-readme-designer
```

Under 30 seconds for a bilingual README plus the image plan.

<details>
<summary>Other modes / flow flags</summary>

```
/jvever-readme-designer --rewrite       # keep your gems, rewrite weak sections, fill gaps
/jvever-readme-designer --patch         # only patch the holes, leave the rest alone
/jvever-readme-designer --en-only       # English only
/jvever-readme-designer --full          # higher tolerance for questions (default quick is mostly 0)
```

Full flag reference and design principles in [`SKILL.md`](skills/jvever-readme-designer/SKILL.md).

</details>

## License

[CC BY-SA 4.0](LICENSE) © 2026 JVever
