<div align="center">

# jvever-readme-designer

**Write your README like a front door — it reads your code, decides for you, ships ZH + EN**

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC_BY--SA_4.0-lightgrey.svg)](LICENSE)

[中文](README.md)

</div>

> A portable README-writing Skill. Drop it into Claude Code / Cursor / Codex / Trae or similar AI editors — describe your intent in plain words; no command to memorize.

---

## What you get

- 🎯 **Above-the-fold sells** — name, one-line pitch, first command sit above the scroll. A visitor decides in 5 seconds whether to keep reading.
- 🧠 **It won't ask what it can read** — `package.json`, `Cargo.toml`, your file tree are inferred for free. It only opens its mouth when something genuinely affects the output and can't be inferred (which license, real customer logos, tone serious or warm).
- 🧱 **Different projects need different bones** — a CLI, a library, an infra platform, a desktop creator tool, a brand-new-category AI project — pick the wrong skeleton and the front door collapses. It picks per project.
- 🛡 **Mechanical errors get fixed, judgment calls get flagged** — path leaks like `/Users/yourname/...`, dead placeholder image hosts, language toggles that reload the same page — those it cleans up itself. Anything it can't decide cleanly is marked ⚠️ for you to settle in the review step.
- 🌏 **The Chinese version isn't translated** — both languages are written from scratch, the Chinese rewritten for Chinese reading habits, not machine-translated. Language switch lives in exactly one place, never duplicated.

## Quick start

Copy the `skills/jvever-readme-designer/` folder into your AI editor's skill directory (for Claude Code it's `~/.claude/skills/`; check your editor's docs otherwise). Then ask in plain words at your project root:

```
write me a README
redo the README
I'm open-sourcing this — design the GitHub front page
```

It scans the project, makes every design call itself, and hands you a draft. Your only job is the final review — say "ok" or "change that paragraph."

You end up with 3 files:

- `README.md` — Chinese, always
- `README_en.md` — English, default-on, can be turned off
- `docs/readme-image-plan.md` — image task list: each image gets a path, purpose, recommended size, and how to make it

**This repo is one of its outputs — the README you're reading was written by it.**

<details>
<summary>Invocation flags</summary>

```
/jvever-readme-designer                       # default: auto-decides whether to ask, ZH + EN
/jvever-readme-designer --full                # answer a few more, get a closer fit
/jvever-readme-designer --rewrite --en-only   # rewrite an existing README, English only
/jvever-readme-designer --patch --zh-only     # patch holes in an existing Chinese README
```

`--quick` / `--full` / `--rewrite` / `--patch` are mutually exclusive; combine freely with `--zh-only` / `--en-only` / `--bilingual`.

</details>

## License

[CC BY-SA 4.0](LICENSE) © 2026 JVever
