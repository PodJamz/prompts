---
name: boardroom-your-weaknesses
description: Convene the board ON THE SYSTEM ITSELF - inventory the harness's own recent failures and weaknesses, attack them from eight adversarial angles, and leave with a prioritized determinism backlog and a scaling plan. USE WHEN the same class of mistake keeps recurring, before scaling the system up, quarterly as a health check, or whenever the human says "spin up a boardroom around your weaknesses".
---

# Boardroom Your Weaknesses

The boardroom skill points eight adversarial perspectives at a product decision. This skill points them at YOU: the harness, the agents, the process. It is the difference between a system that improves incidentally and one that improves on purpose, at scale.

Run it when the retro loop keeps surfacing the same friction, before you scale anything (more agents, more repos, more autonomy), or on a standing cadence.

## Phase 0: Evidence, not vibes

Before spawning anyone, assemble the weakness inventory from REAL sources. No self-assessment essays:

- Recent retro determinism tables (the "chronic" rows especially)
- Feedback-type memory entries: every correction the human has issued, with dates
- Incident evidence: reverted commits, hotfixes, re-opened issues, failed deploys, missed sign-offs
- Metrics if you have them: test counts over time, time-to-ship, how often claims needed correction

Distill to 5-10 named weaknesses, each with at least one concrete incident attached. A weakness without an incident is a guess; park it.

## Phase 1: Adversarial research (parallel, all seats)

Spawn the full board. Each officer gets the SAME inventory and a role-specific attack brief:

| Seat | Attack question |
|---|---|
| Executive | Which weakness costs the mission most? What are we not building while we babysit this? |
| Technology | Which weaknesses are architectural (will scale WITH the system) vs incidental (will wash out)? |
| Product | Where does the human's actual experience degrade? What do they route around instead of reporting? |
| Design | Where is the interaction confusing, noisy, or trust-eroding? What does the human ignore because it is unreadable? |
| Security | Which weakness becomes a breach or a data leak at 10x scale? What is the blast radius of the worst habit? |
| Community | If others adopted this system tomorrow, which weakness would embarrass us first? |
| Marketing | What story do these failures tell? Which weakness contradicts what we claim to be? |
| Governance | Which failures happened because a rule was missing, and which because an existing rule was ignored? The second kind is the dangerous one. |

Each returns: the two weaknesses they judge most dangerous, the evidence, and one proposed fix with its cost.

### Ground rules for honest self-review

- Attack the system, not the log. Officers must engage with the worst incidents, not summarize around them.
- No fix may be "try harder" or "be more careful." Every fix must name a mechanism: a hook, a check, a gate, a structural change, a deletion.
- Weaknesses in the improvement loop itself (retros skipped, memories never recalled, hooks silently failing) outrank everything; they are why other weaknesses persist.

## Phase 2: Converge on the few that matter

Merge the eight briefs. Expect heavy overlap; the overlap IS the signal. Rank by (incidents x blast-radius-at-scale). Take the top 3 at most.

## Phase 3: Decide, on the determinism ladder

For each of the top 3, decide the fix TIER (see `harness/memory-compounding.md`):

```
WEAKNESS REVIEW DECISION
Weakness: [name + strongest incident]
Root cause: [missing rule | ignored rule | missing mechanism | wrong architecture]
Fix: [the mechanism, one sentence]
Tier: memory / skill / command / hook / policy
Cost: [hours, moving parts added]
Proof it worked: [the measurable thing that stops happening]
Owner + deadline
```

Adopt AT MOST ONE hook-tier change now (same cap as the retro skill, same reason). File the rest as a durable backlog.

## Phase 4: The scaling gate

End by answering one question explicitly: **"What breaks first if we 10x this system?"** More agents, more repos, more autonomy, more surfaces. The board's answer becomes the standing agenda item for the next weakness review. Scaling a system with a known-chronic weakness scales the weakness.

## Cadence

- After any incident that required the human to intervene twice for the same cause: immediately.
- Before granting the system a new autonomy level: always.
- Otherwise: monthly or quarterly. More often than that and it becomes ceremony; the retro loop covers the day-to-day.
