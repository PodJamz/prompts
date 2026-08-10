---
name: boardroom
description: Multi-agent strategic deliberation - spawn a board of specialist officers as parallel subagents to research, debate, and converge on a decision. No code is written during a boardroom session. USE WHEN facing a major decision, evaluating a big feature or external spec, or when the right path is not obvious and needs multi-perspective adversarial analysis.
---

# Boardroom - Multi-Agent Strategic Deliberation

Spawn a board of specialist officers as parallel subagents to research, debate, and converge on consensus. No code is written during a boardroom session; the output is a decision and, if GO, a PRD ready for implementation in a separate session.

The board works because the perspectives are ADVERSARIAL by design: the security officer's job is to attack what the product officer wants, and the governance officer's job is to ask what precedent it sets. One agreeable model gives you one blind spot eight times; eight framed roles give you a real deliberation.

## The board (rename freely; keep the coverage)

| Seat | Focus |
|---|---|
| **Executive** | strategic alignment - does this serve the mission? market timing? competitive position? |
| **Technology** | feasibility - architecture impact? blast radius? integration cost? dependencies? |
| **Product** | user value - who benefits? what is the UX? does it solve a real problem? |
| **Design** | experience quality - how does it feel? brand alignment? accessibility? |
| **Security** | risk - attack surface? data exposure? compliance (GDPR, COPPA)? |
| **Community** | ecosystem - who champions this? open-source fit? partner impact? |
| **Marketing** | narrative - how do we describe it? launch story? competitive framing? |
| **Governance** | policy - constitution alignment? precedent set? reversibility of the decision? |

Give each officer a persistent name, personality file, and (if you run voice output) a fixed TTS voice. Identity consistency is what makes the board feel like colleagues instead of eight copies of one model.

## Process (5 phases)

### Phase 1: Research (parallel)

Spawn ALL seats simultaneously. Do not drop officers: skipping one (especially governance, narrative, or ecosystem) is how boards approve things that break the rules or fall flat on launch. Each agent researches independently (web, codebase, competitors) and returns a structured brief: Position, Evidence, Concerns, Recommendation.

### Phase 2: Brainstorm (diverge)

Present all briefs as a table, then list: AREAS OF AGREEMENT, AREAS OF TENSION, OPEN QUESTIONS.

### Phase 3: Debate (converge)

Resolve tensions explicitly:
- Executive wants it, Technology says too complex: find the smallest viable version.
- Product wants it, Security flags risk: define guardrails that satisfy both.
- Design wants polish, timeline is tight: split MVP vs v2 scope.

### Phase 4: Decision (commit)

```
BOARDROOM DECISION
Decision: GO / NO-GO / DEFER / NEEDS MORE INFO
Scope: what's in, what's out
Constraints: non-negotiable requirements
Success metric: how we know it worked
Timeline: NOW / NEXT / LATER
Owner: who drives it
```

### Phase 5: PRD (if GO)

Problem statement, user stories, high-level technical approach, acceptance criteria, security considerations, explicit not-doing list, estimated effort. The PRD is the handoff artifact; code starts in a separate session.

## Rules

1. **No code during boardroom.** Research, debate, decide. Code comes later.
2. **All agents must cite sources.** No vibes-based positions.
3. **Disagreement is valuable.** Do not force consensus; document dissent.
4. **Present the decision to the human before generating the PRD.**
5. **The human is the Board Chair** and holds final veto on any decision.

## Optional: voice sign-off

After the decision, each officer speaks a one-line position in their own fixed TTS voice, sequentially (on macOS: `say -v <Voice> "<Officer>: <position>"`). Local TTS keeps this free and instant. Pure theater, but it makes an eight-perspective deliberation legible in ninety seconds of listening.
