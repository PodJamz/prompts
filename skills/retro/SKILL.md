---
name: retro
description: Socratic retrospective over a session - find what can become deterministic, adopt at most one change. USE WHEN a session ends, when the same mistake happened twice, or nightly over the day's transcripts.
user_invocable: true
---

# /retro - Session Retrospective

Interview the human (or, if run unattended, interview the session transcript) using the Socratic method. The goal is NOT a summary. The goal is a table of things that can be made deterministic so they never cost a decision again.

## Interview (3-6 questions, one at a time, short)

Ask about THIS session specifically:

- Where did you correct me more than once for the same class of mistake?
- What did I re-derive that should have been written down already?
- Which interruption today did not change what you did next?
- What decision did you make today that you have made before?
- Where did I claim something was done - was every claim evidence-backed?

If running unattended, answer these yourself from the transcript, honestly, citing message references.

## Output - the determinism table

| Friction observed | Recurrence | Fix type | Where it lands |
|---|---|---|---|
| ... | first time / repeated / chronic | hook (deterministic) / command (forced ritual) / skill or memory (advisory) / policy | file path or issue |

## Rules

- Hook or command only for things that must ALWAYS happen. Advisory tier for everything else. "Is that a standing order or a suggestion?" is the sorting question.
- **Adopt at most ONE deterministic change per retro.** File the rest as issues (label them `standing-orders`) or memory entries so the backlog is durable. Perfectionism warning: retros generate infinite appetite; the cap is the feature.
- If a change alters governance or cross-project behavior, do not implement it in the retro - file a PROPOSED decision record for the human's morning queue instead.
- End with one line: what got adopted, what got filed.

## Scaling it

Run this nightly, unattended, over the day's transcripts, and pipe the PROPOSED changes into a morning approval queue. The system then improves every single day, and nothing changes itself ungoverned. This is the engine of compounding knowledge (see `harness/memory-compounding.md` in this repo).
