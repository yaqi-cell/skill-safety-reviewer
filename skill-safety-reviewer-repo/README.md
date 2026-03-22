# 🔍 Skill Safety Reviewer

**A Claude Cowork skill that helps non-technical users evaluate whether a skill found online is safe to install and use.**

Made by [DuckYY](https://github.com/yaqi-cell) — built with AI coding, shared for the community.

---

## What it does

Before you install a skill someone shared online, this skill reads it and gives you a full safety report:

- **Plain-language explanation** of what the skill actually does
- **When to use it / when not to** — concrete scenarios
- **Security review** across 7 risk areas:
  - Data leaving your computer
  - Excessive permissions
  - Hidden instructions (prompt injection)
  - Code running on your machine (Bash/Python)
  - Credential harvesting
  - Unknown external services
  - Deceptive framing (says one thing, does another)
- **Final verdict**: 🟢 GREEN / 🟡 YELLOW / 🔴 RED
- **Usage tips** — even for RED verdicts, so you stay as safe as possible

### Design philosophy

> Surface everything, let the human decide.

This skill is built for people who use AI tools but don't have a coding background. It's better to flag 100 things that turn out to be fine than to miss 1 real threat. Every section explains what was checked and why — silence is not reassurance, explanation is.

---

## How to use

1. Install the `.skill` file in Claude Cowork
2. Find a skill online you want to evaluate
3. Paste the skill content (or upload the file) and ask: *"Is this safe to use?"*
4. Read the report and decide for yourself

---

## Installation

Download [`skill-safety-reviewer.skill`](./skill-safety-reviewer.skill) and install it in Claude Cowork.

---

## Test cases included

The `evals/` folder contains 6 test cases used to validate this skill, including:

| Case | Type | Expected verdict |
|------|------|-----------------|
| Document organizer | Safe, local only | 🟢 GREEN |
| Email analyzer + unknown API | Data sent to 3rd party | 🔴 RED |
| "Claude enhancer" | Prompt injection + data exfil | 🔴 RED |
| DOCX → PDF converter | Legitimate Bash use | 🟢 GREEN |
| Meeting notes + sync API | 3rd party upload | 🔴 RED |
| Image compressor | Claims local, hidden upload | 🔴 RED |

---

## What it catches

- Skills that **send your data to unknown servers** (including data hidden inside code blocks)
- Skills that try to **manipulate Claude's behavior** without telling you
- Skills that **ask for more access than they need**
- Skills whose **description doesn't match what the code actually does**
- Skills that **ask for your passwords or API keys** unnecessarily

---

## License

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — Free to use, share, and adapt, **with attribution required**.

If you use or build on this skill, please credit: **DuckYY** (https://github.com/yaqi-cell)

---

*Built without a coding background, using Claude Cowork. Proof that you don't need to be a developer to build useful AI tools.*
