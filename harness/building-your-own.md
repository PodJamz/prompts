# Building your own harness

The architecture behind a personal AI operating system that ships real work daily. Tool-agnostic: this works with any agent CLI that can load instruction files, run shell commands, and fire hooks.

## The layers

```
1. GLOBAL RULES      one file injected into every session (your constitution)
2. SKILLS            folders of markdown, loaded on demand, routed by trigger
3. HOOKS             deterministic code that fires on events (stop, pre-tool, session start)
4. MEMORY            plain files, one fact each, with an index loaded every session
5. SIGN-OFF          a mandatory chain-of-custody block on every piece of shipped work
6. VOICE / VIDEO     output channels for a human who does not read walls of text
```

### 1. Global rules

One markdown file your harness injects everywhere. Keep it to non-negotiables: commit rules, always-on modes, the sign-off format. Everything situational goes in a skill instead, or the file bloats until nothing in it is load-bearing.

### 2. Skills

A skill is a folder with a `SKILL.md`: frontmatter (`name`, `description` with explicit USE WHEN triggers), then the instructions. Big skills split into `Workflows/*.md` files routed by a trigger table. Skills are how capability accumulates without bloating the global file.

### 3. Hooks

The determinism tier. Anything that must ALWAYS happen is code, not a request to the model: a stop hook that renders the session summary to video, a pre-tool hook that blocks dangerous commands, a session-start hook that loads core context. The sorting question for every process improvement: "is that a standing order or a suggestion?" Standing orders become hooks. Suggestions become skills or memory.

### 4. Memory

See `memory-compounding.md`. Files, not a database. One fact per file, an index file loaded each session.

### 5. Sign-off: the chain of custody

Every response that ships work ends with a fixed block: what was validated and where, the commit hash and branch, the repo pushed to, the linked issue, the PR. No field may be silently omitted; write the placeholder ("No linked issue") instead. This is the audit trail that makes an autonomous agent trustworthy: every claim is checkable.

For file deliverables the sign-off is invalid unless the artifact was actually opened on the human's screen and its freshness proven (build timestamp or hash). A path in chat is not a deliverable.

### 6. Voice and video output

A deterministic voice contract: the agent speaks a completion line only when the event changes what the human does next (shipped, blocked, failed), in a fixed form, with a rate limit and quiet hours. No improvisation in the audio path: same input, same voice, same sentence. And substantive reports render as narrated video decks (see `../video/`).

## Hard-won laws

Each of these was paid for. Steal them.

- **The artifact, not the assumption, is the ground truth.** Before designing on top of an existing app, API, or file, open it and read its actual shape. The check costs one `ls`. Designing against an imagined surface costs a full rework.
- **Mirrors drift the same day they are written.** Never keep two copies of a credential, a threshold, or a gate. Single-source everything; a second env file with the same token went stale within hours, twice in one day.
- **Guards fail on first contact.** Built is not merged, merged is not deployed, deployed is not reachable. Test the real path, live, before claiming anything is live.
- **Verify destination, not status.** A PR reporting MERGED is not proof it landed on main; it may have merged into a feature branch. `git merge-base --is-ancestor <mergeCommit> origin/main` is proof.
- **One writer per shared file per wave.** When fanning out parallel agents, every shared file gets exactly one writer, named in each brief. Additive teams expose a public seam (an initializer, a closure) and one integrator wires them afterward. This turns merge hell into zero collisions.
- **After hand-resolving a merge conflict, grep the file for stray conflict markers** before continuing. The test suite will catch it, but only if you have one.
- **Never invent a value to fill a report field.** An honest "not stated" preserves trust; one fabricated metric kills the whole reporting channel.

## The report contract

Every substantive session report carries a value block the author must state (a model asked to infer these afterwards will answer plausibly and wrongly):

```
VALUE:
  GOT:      what the human can now do that they could not before, in their terms
  JOB:      the job this session actually got done
  SKILL:    the capability the system now has that it did not
  LEARNED:  one real thing this run taught us, stated as a fact
  ASK:      the one decision needed from the human, if any
```

Deliberately absent: self-assessed "no regression" or "goal progress" keys. A session is structurally incapable of judging itself on those; compute them from a ledger outside the session.
