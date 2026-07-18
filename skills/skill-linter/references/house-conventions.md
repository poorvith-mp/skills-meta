# open-claude-skills house conventions (v0.2)

Source of truth: the hub `README.md`. Reproduced here so the linter has it in context without re-fetching the README every run.

```
skill-id/
├── SKILL.md
├── references/NOTE.md   (or real reference files)
└── assets/NOTE.md        (or real asset files)
```

- Trigger-rich `description` frontmatter — err toward "pushy" wording that biases the model toward triggering when the task genuinely matches, since under-triggering is the more common failure mode.
- Imperative instructions in the body.
- No third-party credits or personal file paths baked into any skill.
- Keep SKILL.md under ~500 lines; push detail into `references/` past that.
