<div align="center">

# jvever-readme-designer

**Design your README as a landing page, not a doc dump.**

[![License: CC BY-SA 4.0](https://img.shields.io/badge/license-CC%20BY--SA%204.0-lightgrey)](LICENSE) ![Bilingual](https://img.shields.io/badge/lang-zh%20%2B%20en-blue)

[SKILL](skills/jvever-readme-designer/SKILL.md) · [CHANGELOG](CHANGELOG.md) · [中文](README.md)

</div>

---

A Skill: tell it "write me a README", it reads your project code, makes every design call itself, and ships a bilingual marketing-grade README. **All you do is review.**

> Skill is a portable format supported across Claude Code, Cursor, Codex, and other AI editors — examples below use Claude Code.

---

## What it does for you

- 🔍 **Zero follow-ups by default** — reads your manifests, commits, and entry shape; never asks what code can tell. For most projects, 0 questions.
- 🎯 **5 archetypes, auto-picked** — CLI / infrastructure / consumer tool / new-category / endorsement-first, each with its own hero formula. No one-size-fits-all.
- 🛡 **Auto-fixes what's wrong, flags what's debatable** — path leakage, broken links, decorative ASCII, emoji-in-headings get fixed silently; subjective calls surface as ⚠️ for your review.
- 🌏 **Bilingual + China ecosystem on auto** — Lark / ModelScope / one-click deploys / Bilibili etc. render only when the project is actually Chinese-facing; silent for international projects.

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

It scans, decides, drafts `README.md` + `README_en.md` + `docs/readme-image-plan.md`, and **only stops to ask when it's time to review**.

<details>
<summary>Other modes / persistent preferences</summary>

```bash
/jvever-readme-designer --full               # broader interview tolerance
/jvever-readme-designer --rewrite --en-only  # rewrite existing, English only
/jvever-readme-designer --patch --zh-only    # patch missing sections, Chinese only
```

Copy `skills/jvever-readme-designer/EXTEND.md` into your project root to override defaults permanently.

For Cursor / Codex / other AI editors, check their docs for the Skill install path — the mechanism is the same.

</details>

---

## License

[CC BY-SA 4.0](LICENSE) — free to use, modify, and ship commercially; **derivatives must credit and stay open under the same license**.
