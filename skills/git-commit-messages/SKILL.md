---
name: git-commit-messages
description: Write Conventional Commits subject lines and well-formed commit bodies following tpope's and cbeams' commit message conventions. Use this skill whenever you are about to run `git commit`, whenever the user asks for a commit message, asks you to commit, stage and commit, amend a message, squash commits, or reword history — and also when writing PR titles, since they follow the same subject-line rules. Use it even when the user just says "commit this" without mentioning messages.
---

# Git commit messages

A diff shows *what* changed. Only the message can explain *why*. Write for the person
running `git blame` on this line in eighteen months — quite possibly you.

## Format

```
<type>(<scope>): <imperative summary>

<body: what changed and why, wrapped at 72 characters>

<footers>
```

The subject line is the whole message for most commits. Get it right first.

## Subject line rules

**Target 50 characters, treat 72 as the hard limit.** This includes the `type(scope):`
prefix. GitHub truncates past 72. If you cannot fit the change into 50 characters, that is
usually a signal the commit is doing more than one thing — consider splitting it.

**Use the imperative mood.** Not past tense, not third person. The test: the subject must
complete the sentence *"If applied, this commit will ___"*.

| Write | Not |
|---|---|
| `fix(auth): reject expired refresh tokens` | ~~`fixed expired token bug`~~ |
| `refactor(upload): extract useFileUpload hook` | ~~`extracting the upload hook`~~ |
| `feat(search): add pinnedAt sort for paid datasets` | ~~`sweet new sort option`~~ |

This is not arbitrary — git itself writes in the imperative when it generates messages
(`Merge branch 'x'`, `Revert "Add the thing"`), so your commits read consistently with the
ones the tooling creates.

**Lowercase the description, no trailing period.** `feat(api): add rate limiting`, not
`feat(api): Add rate limiting.`. Keep the original casing of identifiers and proper nouns:
`fix(r2): handle missing Bucket param`.

Note this is the one place Conventional Commits departs from cbeams' rule 3 ("capitalize
the subject line"). The `type:` prefix takes that slot instead.

## Types

| Type | Use for |
|---|---|
| `feat` | A new capability visible to a user or caller |
| `fix` | A bug fix |
| `refactor` | Restructuring with no change in behaviour |
| `perf` | A change made specifically for performance |
| `docs` | Documentation only |
| `test` | Tests only |
| `build` | Build system, bundler, or dependency changes |
| `ci` | Pipeline and workflow configuration |
| `style` | Formatting, whitespace, lint fixes with no logic change |
| `chore` | Housekeeping that fits nothing above |
| `revert` | Reverting a previous commit |

Choose by intent, not by which files changed. Adding a test *for a new feature* that ships
in the same commit is `feat`. Adding a missing test for existing code is `test`.

**Scopes:** read `git log --oneline -20` first and reuse the scopes the repository already
uses. Inventing a parallel vocabulary of scope names makes the log harder to filter, which
defeats the point. Omit the scope rather than guess.

## When to write a body

Skip it when the subject says everything. `docs: fix typo in contributing guide` needs no
elaboration — if the reader wonders what the typo was, they can read the diff.

Write a body when any of these hold:

- The reason for the change is not obvious from the code
- You chose this approach over an obvious alternative
- There are side effects, or consequences a reader would not predict
- The change works around a bug, a platform limitation, or an upstream constraint
- The commit reverts or partially undoes earlier work

Then structure it as: what was happening before, what was wrong with it, and why you solved
it this way. Leave out *how* — the diff covers that, and if the code needs prose to be
legible, that belongs in a source comment.

**Wrap the body at 72 characters manually.** Git never wraps for you, and `git log` indents
by four columns, so 72 keeps everything inside 80 on a standard terminal.

**Always leave a blank line between subject and body.** Git treats everything up to the
first blank line as the title. Without it, `log --oneline`, `shortlog`, `rebase -i`, and
`format-patch` all misbehave.

## Footers

Put references at the bottom, after a blank line:

```
Refs: #412
Closes: #398
BREAKING CHANGE: uploadLogo now requires an orgId argument
```

`BREAKING CHANGE:` in a footer (or a `!` after the type, as in `feat(api)!:`) marks a
breaking change. Preserve any footer convention already present in the repository's log,
including trailers added by tooling.

## Workflow

1. Run `git diff --staged` to see exactly what is being committed. If nothing is staged,
   run `git diff` and `git status`, then ask what should go in before writing a message.
2. Run `git log --oneline -20` to pick up the repository's scope names and prefix habits.
3. Identify the single logical change. If the staged diff contains two unrelated changes,
   say so and offer to split it rather than writing a vague subject that covers both.
4. Draft the message. Show it before committing.

## Worked examples

Trivial change, subject only:

```
fix(nav): clear stale session state after verification
```

Change with a non-obvious rationale:

```
refactor(upload): redirect with window.location after verify

router.replace kept the client-side navigation state intact, so the
nav bar continued to render the unauthenticated menu after email
verification succeeded. A full document load is heavier but forces
the nav bar to re-read the session.

Revisit once the session lives in a context provider rather than
being read at mount.

Refs: #287
```

## Anti-patterns

| Problem | Example |
|---|---|
| Describes the contents, not the change | `chore: more fixes for broken stuff` |
| Past tense | `fix: fixed the pagination bug` |
| Restates the diff in prose | A body that lists every renamed variable |
| Explains *how* instead of *why* | "Adds a useEffect that calls the API and sets state" |
| No blank line before the body | Breaks every tool that reads the subject |
| One subject covering several changes | `feat: add sorting, fix upload, bump deps` |
