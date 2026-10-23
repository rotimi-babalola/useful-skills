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
```

Add `-g` for a global (user-level) install, or `--copy` to copy instead of symlink.

## Skills

- **git-commit-messages** — Conventional Commits subject lines and commit bodies.
- **technical-writing** — Documentation and explanations in Simplified Technical English plus the Google developer docs style.

## Manual install

Copy a skill folder into your agent's skills directory, for example
`~/.claude/skills/`, `~/.config/opencode/skills/`, or `.agents/skills/`.
Each skill is a folder containing a `SKILL.md`.
