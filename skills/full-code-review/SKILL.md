---
name: full-code-review
description: Run both the thermo-nuclear code quality review and the standard code review-and-quality skill, then merge findings. Use when the user wants a full review, strict review plus broad review, or asks to run both review skills.
metadata:
  opencode/slash: "true"
---

# Full Code Review

Run both reviews, then merge. No shortcuts — both always run.

## Requires

This skill is orchestration only. Install both dependencies first:

- `code-review-and-quality` by Addy Osmani (MIT):
  `npx skills add addyosmani/agent-skills@code-review-and-quality`
  <https://github.com/addyosmani/agent-skills/tree/main/skills/code-review-and-quality>
- `thermo-nuclear-code-quality-review` (in this repo):
  `npx skills add rotimi-babalola/useful-skills@thermo-nuclear-code-quality-review`

If either skill is missing, stop and tell the user which one to install. Do
not invent a substitute rubric.

## Process

1. Load and run `code-review-and-quality` first (five axes: correctness, readability, architecture, security, performance). Follow its SKILL.md exactly, including its output format and severity labels.
2. Load and run `thermo-nuclear-code-quality-review` second. Follow its SKILL.md exactly — ambitious structural lens, code-judo moves, 1k-line rule, spaghetti-growth flags.
3. Merge into one report:
   - `## code-review-and-quality` — findings verbatim, ordered by that skill's leverage rule (correctness/security first).
   - `## thermo-nuclear` — findings verbatim, ordered by that skill's priority list.
   - `## Merged verdict` — one line: total findings per skill, worst issue per skill. If they conflict (one approves, one blocks), the thermo-nuclear blocker wins and is stated explicitly. Do not rerank across axes beyond that.
