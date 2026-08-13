# Contributing to `skills-meta`

Maintainer: **Poorvith M P** · v0.1 · last updated July 2026

## What belongs here

`skills-meta` is different from the other 11 category repos: skills here operate on the
**skillary library itself** (routing, linting, house-style checks), not on an
external domain like marketing or finance. Only add a skill here if it is about
maintaining, navigating, or quality-checking the library.

## Skill format (skill-creator)

Every skill lives at:

```text
skills/<skill-id>/
├── SKILL.md
├── references/NOTE.md
└── assets/NOTE.md
```

Rules:
1. Folder name must equal frontmatter `name` (kebab-case).
2. `description` must include **what** the skill does and **when** to use it (trigger phrases).
3. Body uses imperative instructions; explain **why** for critical rules.
4. Keep `SKILL.md` lean; put large docs in `references/` only when needed.
5. `assets/` is for templates and media used in outputs — not instructions.
6. **No credits, personal handles, machine paths, or third-party source URLs** in skill bodies.
7. License is MIT under Poorvith M P.
8. Any skill counts referenced inside a meta-skill's description (e.g. total library size)
   should be updated whenever the hub's total skill count changes.

## Pull request checklist

- [ ] New/changed skill has `SKILL.md` + empty `references/` + `assets/` notes
- [ ] Description is trigger-rich and under ~1024 characters
- [ ] No duplicate skill-id in this repo
- [ ] CHANGELOG.md updated under Unreleased or a version heading
- [ ] No personal data or secrets

## Local install (Claude Code)

Copy a skill folder into `~/.claude/skills/<skill-id>/` or `.claude/skills/<skill-id>/`.
