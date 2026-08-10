# Compounding knowledge

A harness that forgets what a session taught it re-buys the same lesson forever. The compounding loop is: capture friction, promote it up a determinism ladder, and let capability accumulate as files under version control.

## Memory is files

No database, no embeddings to start. One fact per markdown file, with frontmatter:

```markdown
---
name: short-kebab-slug
description: one-line summary used to decide relevance at recall time
metadata:
  type: user | feedback | project | reference
---

The fact. For feedback entries, follow with:
**Why:** the incident that taught it.
**How to apply:** the concrete behavior change.
Link related memories with [[their-slug]].
```

Types:
- `user` - who the human is: role, expertise, preferences.
- `feedback` - corrections and confirmed approaches, WITH the why. These are the crown jewels.
- `project` - ongoing work and constraints not derivable from the code or git history.
- `reference` - pointers to external resources.

An index file (`MEMORY.md`) holds one line per memory and loads into every session. Content stays in the individual files; the index is a table of contents, never a store.

Rules: check for an existing file before creating a duplicate; update rather than fork; delete memories that turn out to be wrong; never save what the repo already records (git history is memory too).

Organize the files by PARA (Projects, Areas, Resources, Archive) or anything stable; the layout matters less than the discipline of one-fact-one-file.

## The retro loop

Every session (or nightly, unattended over the transcript) run a retrospective whose goal is NOT a summary. The goal is a table of things that can be made deterministic so they never cost a decision again. See `../skills/retro/SKILL.md`.

The one rule that keeps it alive: **adopt at most ONE deterministic change per retro.** Retros generate infinite appetite; the cap is the feature. File the rest as issues so the backlog is durable.

## The determinism ladder

Every recurring piece of friction gets promoted exactly as high as it deserves, and no higher:

```
1. MEMORY NOTE   advisory: "remember this preference"        (cheap, fallible)
2. SKILL         reusable procedure the agent loads on trigger
3. COMMAND       a forced ritual the human can invoke (/retro, /no-bs)
4. HOOK          deterministic code on an event: ALWAYS happens (expensive, reliable)
5. POLICY        a decision record that changes governance across repos
```

The sorting question: "is that a standing order or a suggestion?" Standing orders climb to hook or policy. Suggestions stay advisory. Promoting a suggestion to a hook creates brittle ceremony; leaving a standing order as a memory note guarantees it gets violated on a busy day.

## Self-improvement at scale

Once the loop runs nightly, scale it:

- **Nightly retro, morning queue.** An unattended retro over the day's transcripts produces PROPOSED changes; the human approves them over coffee. The system improves daily without ever changing itself ungoverned.
- **Autonomous improvement loops** (see `../skills/autoresearch/SKILL.md`): run challenges against the harness, judge with a DIFFERENT model than the one being evaluated, apply at most one meta-change per round, gate on benchmarks, block regressions.
- **Skills are the compounding asset.** Models get swapped; your skills, memories, hooks, and rules survive every migration. That corpus IS the system. Version-control all of it.

## Anti-drift guards for any self-improvement loop

- No new files unless solving a specific measured problem
- No refactoring unless it fixes a measured problem
- No dependency additions from an autonomous loop
- All changes pass existing tests; benchmarks must not regress
- Max one meta-change per round, always reversible, always logged
