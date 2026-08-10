---
name: autoresearch
description: Overnight autonomous improvement loop for an agent harness - run challenges, judge with a different model, apply bounded meta-improvement, report on a heartbeat. USE WHEN running overnight loops, benchmarking the harness, or building a self-improvement cycle.
---

# AutoResearch

An autonomous improvement loop with meta-improvement: the agent runs challenges, judges results, improves the harness, then improves how it improves. Bounded hard, or it becomes a drift machine.

## The loop

```
1. SELECT CHALLENGE   (mix of coding + tool-use + research + real-world)
2. ATTEMPT            (the agent works the challenge)
3. JUDGE              (a DIFFERENT model scores impartially, 0-10, against a rubric)
4. REFLECT            (what worked, what failed, why)
5. IMPROVE            (apply the learning to harness code)
6. META-IMPROVE       (improve the improvement process itself - max 1 change)
7. REPORT             (heartbeat message to the human every 30 minutes)
8. REPEAT
```

## Challenge mix

| Category | Examples | Weight |
|---|---|---|
| Coding | real issues from your tracker, refactoring, test writing, bug fixes | 40% |
| Tool use | file operations, git workflows, multi-step tasks | 20% |
| Research | read docs, extract patterns, summarize findings | 15% |
| Real-world | API integration, data processing, config management | 15% |
| Meta | improve own prompts, optimize tool selection, memory tuning | 10% |

## Judge configuration

- **Never the same model as the one being evaluated.** A cheap fast model from a different family works fine.
- Score 0-10 on: correctness, efficiency, code quality, resourcefulness.
- The judge prompt includes the rubric, the expected output, and the actual output.

## Meta-improvement protocol

After each round: review performance vs previous rounds, propose AT MOST ONE change to the loop's own config, run the benchmark suite against it. Improvement: keep, bump version, write a changeset. Regression: block, log the reason. Everything to an append-only history log.

## Anti-drift guards (the part that matters)

- No new files unless solving a specific challenge
- No refactoring unless it fixes a measured problem
- No dependency additions
- No scope expansion beyond the challenge
- All changes must pass existing tests
- Benchmark scores must not regress
- Max 1 meta-config change per round
- A policy engine (deny-by-default) between the loop and the filesystem/network

## Reporting

Every 30 minutes to your messaging channel: rounds completed, challenges attempted/passed/failed, benchmark vs baseline, meta-config version, any meta-improvements applied, top insight of the period. Morning summary waits for the human; overnight output never demands attention.
