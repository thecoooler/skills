# skills

Personal agent skills by [@thecoooler](https://github.com/thecoooler). Skills are folders of
instructions (`SKILL.md`) that coding agents such as Claude Code, Gemini CLI, Codex, and
Cursor load on demand.

## Skills

| Skill | Description |
| --- | --- |
| [`pr-writing`](skills/pr-writing/SKILL.md) | How to write pull requests: Conventional Commits title, one problem per PR, Problem / Change / Verification body, honest verification notes, UI evidence. |

## Install

With the [`skills`](https://github.com/vercel-labs/skills) CLI:

```sh
npx skills add thecoooler/skills
```

To install a single skill:

```sh
npx skills add thecoooler/skills --skill pr-writing
```

Or manually: clone this repository and symlink the skill folder into your agent's skills
directory.

```sh
git clone https://github.com/thecoooler/skills.git ~/skills
ln -s ~/skills/skills/pr-writing ~/.claude/skills/pr-writing   # Claude Code
ln -s ~/skills/skills/pr-writing ~/.gemini/skills/pr-writing   # Gemini CLI
```

## Layout

```
skills/
  <skill-name>/
    SKILL.md      # frontmatter (name, description) + instructions
```

Each `SKILL.md` starts with YAML frontmatter. `name` matches the folder name;
`description` says what the skill does and when an agent should use it.

## Contributing

Add each new skill in its own folder under `skills/`, add a row to the table above, and
open one pull request per skill.

## License

[MIT](LICENSE)
