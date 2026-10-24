---
name: pr-writing
description: >
  How to write pull requests in the user's repositories: title, scope, body
  sections, verification, and UI evidence. Use whenever opening, writing, or
  editing a pull request title or description: "open a PR", "create pull
  request", "write the PR description", "update the PR body", gh pr create,
  gh pr edit.
---

# Writing pull requests

Applies to every repository the user owns or works in. If the repository has its
own `CONTRIBUTING.md` or `.github/pull_request_template.md`, follow those first and
use this skill to fill the gaps.

## Rules

1. **Never open a PR unless the user explicitly asks.** Writing a draft body for
   them to review is fine; running `gh pr create` is not, until asked.
2. **Before opening, check what already exists.** Run `gh pr list` and
   `git branch -a`. If a branch or PR for the same work exists, reuse it; do not
   create a second one.
   - One branch per PR, branched from an up-to-date `main`, targeting `main`.
   - No `gh stack` or stacked PRs unless the PRs genuinely depend on each other
     and the user asked for a stack.
3. **One problem per PR.** Unrelated fixes, drive-by refactors and cleanups go in
   separate PRs. Everything that one problem needs (server, client, contract,
   tests, docs) stays together. Count underlying problems, not files or issues.
4. **English** for PR titles, PR descriptions, and commit messages, even when the
   conversation with the user is in another language.
5. **Title:** Conventional Commits, plain language, describing the user-visible
   outcome rather than the code edit.
   - Good: `fix(web): new threads no longer spike CPU`
   - Bad: `fix: refactor useThread hook memo deps`
6. **Body:** use the template below. Keep each section short and concrete.
   - **Problem**: one or two sentences. Add expected behavior, repro steps, and
     environment when relevant.
   - **Change**: how it is fixed. If it spans components or clients, say why
     they belong to the same fix.
   - **Verification**: what was actually checked and what was observed, plus
     what could not be checked. "Tests pass" alone is not enough. Never claim a
     check you did not run.
   - End with the model and harness that did the work, when an agent did it.
7. **UI changes need evidence:** before/after screenshots; a short recording when
   motion, timing, transitions, or interaction matter. Upload evidence to the PR
   on GitHub and embed or link it. Never commit PR-only screenshots or assets.

## Verification on the user's VPS

On the user's VPS, agents must not run heavy checks for T3 Code: tests,
typechecks, linters, formatters, builds. Do not claim them. Write what was
really done (read the code path, reproduced manually, inspected output) and say
plainly: "Tests, typecheck and lint left to CI."

## Body template

```markdown
## Problem

<One or two sentences. Expected vs actual behavior; repro steps / environment if relevant.>

## Change

<How this fixes it. If it touches several components, why they are part of the same fix.>

## Verification

- <Check performed> → <what was observed>
- <Before/after screenshots or recording, for UI changes>
- Not checked: <what and why, e.g. "tests, typecheck and lint left to CI">

<Model and harness, e.g. "Written by Claude Opus 5.5 in Claude Code.">
```
