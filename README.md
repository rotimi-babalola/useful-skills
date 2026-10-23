# useful-skills

Agent skills I use locally.

## Install

Install everything:

```bash
npx skills add rotimi-babalola/useful-skills
```

Install one skill:

```bash
npx skills add rotimi-babalola/useful-skills@git-commit-messages
npx skills add rotimi-babalola/useful-skills@technical-writing
npx skills add rotimi-babalola/useful-skills@full-code-review
npx skills add rotimi-babalola/useful-skills@thermo-nuclear-code-quality-review
```

Add `-g` for a global (user-level) install, or `--copy` to copy instead of symlink.

## Skills

- **git-commit-messages** — Conventional Commits subject lines and commit bodies.
- **technical-writing** — Documentation and explanations in Simplified Technical English plus the Google developer docs style.
- **full-code-review** — Runs the standard multi-axis review and the strict thermo-nuclear review, then merges the findings.
- **thermo-nuclear-code-quality-review** — Extremely strict maintainability review: structural simplification, the 1k-line rule, and spaghetti growth.

## Dependencies

`full-code-review` runs two other skills. Install them before using it:

```bash
npx skills add addyosmani/agent-skills@code-review-and-quality
npx skills add rotimi-babalola/useful-skills@thermo-nuclear-code-quality-review
```

## Attribution

- **thermo-nuclear-code-quality-review** is adapted from the [Thermos plugin by Cursor](https://github.com/cursor/plugins/tree/main/thermos), MIT licensed. The original is a Cursor plugin; this copy only adapts its frontmatter for other agents. See the skill's `LICENSE`.
- **full-code-review** is my own orchestration skill, but it depends on Addy Osmani's [code-review-and-quality](https://github.com/addyosmani/agent-skills/tree/main/skills/code-review-and-quality) (MIT). That skill is not redistributed here; install it from upstream.

## Manual install

Copy a skill folder into your agent's skills directory, for example
`~/.claude/skills/`, `~/.config/opencode/skills/`, or `.agents/skills/`.
Each skill is a folder containing a `SKILL.md`.
