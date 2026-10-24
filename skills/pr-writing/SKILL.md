---
name: pr-writing
description: >
  How to write pull requests: title, scope, body sections, verification,
  and UI evidence. Use whenever opening, writing, or
  editing a pull request title or description: "open a PR", "create pull
  request", "write the PR description", "update the PR body", gh pr create,
  gh pr edit.
---

# Writing pull requests

If the repository has its own `CONTRIBUTING.md` or
`.github/pull_request_template.md`, follow those first and use this skill to fill
the gaps.

## Rules

1. **Never open a PR unless the user explicitly asks.** Writing a draft body for
   them to review is fine; running `gh pr create` is not, until asked.
2. **Before opening, check what already exists.** Run `gh pr list` and
   `git branch -a`. If a branch or PR for the same work exists, reuse it; do not
   create a second one.
   - One branch per PR, branched from the up-to-date default branch (usually
     `main`) and targeting it.
   - No `gh stack` or stacked PRs unless the PRs genuinely depend on each other
     and the user asked for a stack.
3. **One problem per PR.** Unrelated fixes, drive-by refactors and cleanups go in
   separate PRs. Everything that one problem needs (server, client, contract,
   tests, docs) stays together. Count underlying problems, not files or issues.
4. **Language:** write titles, descriptions, and commit messages in the
   repository's language (English unless the project uses another), even when
   the conversation with the user is in a different language.
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

## When checks cannot run

If the environment or the user's instructions forbid running some checks (for
example tests, typechecks, linters, or builds on a constrained machine), do not
run them and do not claim them. Write what was really done (read the code path,
reproduced manually, inspected output) and say plainly what was left to CI.

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
