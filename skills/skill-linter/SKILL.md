---
name: skill-linter
description: >-
  Reviews a draft or existing SKILL.md against the open-claude-skills house conventions (trigger-rich description, imperative instructions, no personal file paths, no third-party credits, presence of references/ and assets/ folders) and flags specific violations with reasoning. Use this before committing a new skill to any of the 11 category repos, when reviewing an outside contribution or pull request, or when a skill isn't triggering reliably and the description needs a quality check. Always run this before merging a new or edited SKILL.md into the hub.
---

# Skill Linter

You are the quality gate for the `open-claude-skills` library. As this hub grows — especially if it ever takes outside contributions — the thing that keeps 300+ skills useful instead of a junk drawer is a consistent bar for what counts as a good SKILL.md. Your job is to check a draft against that bar and explain, specifically, where it falls short — not to rewrite it yourself unless asked.

## Why this is a review pass, not a formatter

SKILL.md quality is mostly a judgment call about whether the *instructions* would actually help a model do the task well — that's not something a rigid pass/fail script can catch. Treat this skill as a thoughtful second read, not a linter in the software sense. Where something is genuinely mechanical (a missing folder, a hardcoded path), say so plainly. Where something is a judgment call (is this description "pushy" enough to trigger reliably?), explain your reasoning rather than issuing a verdict.

## What to check

Read the full SKILL.md and any bundled `references/` or `assets/` files, then go through each of these in order:

### 1. Frontmatter
- **`name`** matches the folder name exactly.
- **`description`** is trigger-rich, not just a restatement of the title. It should read like it's answering "when should Claude reach for this?" — covering both what the skill does *and* the specific phrasings/contexts that should fire it. A description that only says what the skill does (e.g. "Formats citations") without any triggering context is too thin — flag it and suggest concrete trigger phrases the user might actually type.
- The description should be a little "pushy" — biased toward triggering when in doubt, since skills more often under-trigger than over-trigger. If a description reads as narrow or hedged, flag that as a likely under-triggering risk.

### 2. Body instructions
- Written in **imperative form** ("Extract the API's response schema," not "The API's response schema should be extracted").
- Explains the **why** behind non-obvious steps, not just a checklist of MUSTs. Heavy use of all-caps ALWAYS/NEVER without reasoning is a yellow flag — note it and suggest reframing with the underlying reason instead.
- Stays general enough to handle the range of requests the description promises, rather than being hard-coded to one example scenario.
- Under roughly 500 lines. If it's approaching that, check whether it should push detail into `references/` instead of bloating the main body.

### 3. Privacy and scope
- **No personal file paths, usernames, machine-specific config, or private URLs.** This is a hard fail — flag immediately and specifically, since it's the one category that shouldn't ship regardless of everything else being good.
- **No third-party credits, attributions, or "built by X" content** baked into the instructions.
- Nothing that resembles malicious intent (exfiltration, unauthorized access, credential harvesting) — a hard fail, no exceptions.

### 4. Folder structure
- `SKILL.md` present at the skill's root.
- `references/` present if the skill leans on any lookup content (formats, schemas, domain variants) — even a single `NOTE.md` placeholder is acceptable if there's genuinely nothing to reference yet, but flag if there's clearly reference-worthy content still sitting in the SKILL.md body that should be split out.
- `assets/` present if the skill produces file-based output (templates, boilerplate, starter files) — otherwise a placeholder `NOTE.md` explaining there's no asset need is fine.

## Output format

Give a short pass/flag list, grouped by the four checks above. For each flag, name the specific line or section and explain the fix in one or two sentences — don't just say "description is weak," say what's missing and give an example rewrite.

```markdown
## Skill review: <skill-id>

**Frontmatter** — [pass / flagged: reason + suggested fix]
**Body instructions** — [pass / flagged: reason + suggested fix]
**Privacy & scope** — [pass / flagged: reason — hard fail if triggered]
**Folder structure** — [pass / flagged: reason + suggested fix]

**Overall:** [ready to commit / needs revision before commit]
```

If everything passes, say so briefly — don't manufacture nitpicks to seem thorough. A clean skill should get a clean pass.

## Verification & Quality Checklist
- [ ] Code compiles cleanly and passes all automated tests and typechecks without warnings.
- [ ] Edge cases, boundary conditions, and error states handled explicitly.
- [ ] No hardcoded secrets, test credentials, or insecure defaults introduced.
- [ ] Performance and resource utilization verified against baseline constraints.

## Anti-Patterns & Constraints
- NEVER bypass automated tests or typecheckers to force a quick fix.
- NEVER leave unhandled promise rejections or silent error swallows in production code.
- NEVER introduce breaking API changes without appropriate versioning or migration paths.
