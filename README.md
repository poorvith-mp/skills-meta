# skills-meta

Claude / Agent **skills** library by **Poorvith M P**.

- Version: **v0.1**
- Last updated: **July 2026**
- License: **MIT**
- Skills in this repo: **2**

Part of the **[open-claude-skills](https://github.com/prvthmpcypher/open-claude-skills)** multi-repo hub.

Unlike the other 11 category repos, `skills-meta` holds skills that operate on the library itself rather than on a domain — they help keep the other ~340 skills consistent and easy to find.

## Install

### Claude Code
```bash
# copy one skill
cp -R skills/<skill-id> ~/.claude/skills/<skill-id>
# or project-local
cp -R skills/<skill-id> .claude/skills/<skill-id>
```

### Claude.ai
Zip a single `skills/<skill-id>` folder and upload via **Settings → Capabilities → Skills**.

## Skill index

| Skill ID | Title |
|----------|-------|
| `skill-linter` | Skill Linter |
| `skill-router` | Skill Router |

## What these skills do

- **skill-router** — finds the right skill + repo for a described task, and gives the exact install command.
- **skill-linter** — checks a draft `SKILL.md` against house conventions before it's committed.

## Author

Copyright (c) 2026 Poorvith M P · MIT License
Follow the build: [@poorvith_mp](https://x.com/poorvith_mp)
