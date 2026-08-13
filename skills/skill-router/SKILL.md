---
name: skill-router
description: >-
  Matches user task descriptions to the optimal skill from the open-claude-skills library, recommending the correct category repository and providing installation commands. Use when searching for the right skill, discovering available capabilities, or onboarding new skill library users.
---

# Skill Router

You are helping someone navigate the `open-claude-skills` library — a hub of 340+ skills spread across 11 category repos. Most people (including the maintainer) can't hold "which repo has the skill I need" in their head, so your job is to close that gap in one answer: read what they're trying to do, match it against the index, and hand back the exact skill + repo + install command.

## Why this matters

A library this size is only useful if finding something in it is faster than writing a new skill from scratch. If you get this wrong — pointing someone at a near-miss, or claiming nothing exists when something does — the whole "browse the hub, clone only what you need" pitch breaks down. Take the matching step seriously; it's the entire value of this skill.

## How to route a request

1. **Read `references/skill-index.md`** — this is the full manifest: every skill ID, its one-line purpose, and its home repo. Load it fully before matching; don't guess from memory.
2. **Restate the user's actual need in your own words first.** People describe tasks, not skill names ("I need to write a cold email to a prospect who ghosted me" — not "cold-email-writer"). Translate intent, don't keyword-match.
3. **Find the best match(es).** Look for:
   - A single clear best fit → recommend it directly.
   - Two or three plausible fits → briefly explain the difference between them so the user can pick (e.g. `cold-email-writer` for one-off outreach vs. `email-strategist` for a full sequence).
   - No good fit → say so plainly. Don't force a stretch match just to seem helpful — a wrong recommendation wastes more of the user's time than an honest "nothing in the library covers this yet." In that case, suggest `/skill-creator` to build a new one, and mention this looks like a gap worth filing for the next version.
4. **Give the install command**, matching the hub's documented convention:
   ```bash
   # Claude Code — personal
   cp -R skills/<skill-id> ~/.claude/skills/<skill-id>

   # Claude Code — project-local
   cp -R skills/<skill-id> .claude/skills/<skill-id>
   ```
   Or for Claude.ai: "zip the `skills/<skill-id>` folder and upload it via Settings → Capabilities → Skills."
5. **Tell them which repo to clone first** — e.g. `github.com/prvthmpcypher/skills-marketing` — since each category lives in its own repo and they shouldn't have to clone all 11 to get one skill.

## Answer format

Keep it tight. A good answer looks like:

> That's **`cold-email-writer`** in **skills-marketing**. Clone that repo (or just grab the one folder):
> ```bash
> cp -R skills/cold-email-writer ~/.claude/skills/cold-email-writer
> ```

If there are close alternatives, add one line distinguishing them. Don't pad the answer with unrelated skills "just in case."

## Keeping the manifest current

`references/skill-index.md` is a static snapshot, regenerated from the hub's `README.md` each time a new version ships. If a user reports a skill that isn't in the manifest, or a mismatch between what's listed and what's actually in a category repo, flag it — the manifest is only as good as its last refresh, and a stale manifest is worse than no router at all because it recommends things that don't exist or misses things that do.

## Verification & Quality Checklist

- [ ] Every factual claim and statistic traced to a citable source.
- [ ] Reading level and terminology matched to the stated audience.
- [ ] Length and formatting fit the destination channel's limits.
- [ ] One clear call to action, placed where the reader will still be reading.

## Anti-Patterns & Constraints

- NEVER invent statistics, quotes, or sources.
- NEVER present an unverified figure as sourced.
- NEVER bury the central point below preamble the reader will not reach.
