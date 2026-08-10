# prompts

A field-tested pack of operating rules, agent skills, and video pipeline patterns for anyone building their own AI agent harness and infrastructure.

Everything here was extracted from a working personal AI operating system: a daily-driven setup where agents ship real code, report progress as narrated video, run adversarial boardrooms on their own plans, and improve themselves through nightly retrospectives. None of it is theoretical. Each file states the failure it was born from.

## How to use this

Drop any skill folder into your agent's skills directory (`~/.claude/skills/`, `.claude/skills/`, or wherever your harness loads instruction files from). Put the rules into your global instructions file (the file your harness injects into every session). The harness guide explains the architecture that ties it together.

## Map

| Section | What is in it |
|---|---|
| `harness/` | How to build the system itself: architecture, local-first stack, compounding memory |
| `rules/` | Always-on operating rules: No-BS Mode, Boil the Ocean, No Hardcoded Data |
| `skills/` | Drop-in skills: git workflow, wayfinding, retro, boardroom, boardroom-your-weaknesses |
| `video/` | The video stack: deck-to-video pipeline, two-deck decision protocol, production workflow, HyperFrames |
| `prompts/` | The original community prompt collection (cursor rules, custom instructions). |

## The core ideas, in one paragraph each

**Local first.** Your agent should work with no API keys, no rate limits, and no cloud dependency for its daily loop. Local models for routine work, local speech-to-text and text-to-speech for the voice loop, cloud as an opt-in upgrade. See `harness/local-first.md`.

**Compounding knowledge.** A session that teaches you something and forgets it was a waste. Memory is files, retros mine every session for friction, and each piece of friction gets promoted up a ladder: memory note, then skill, then deterministic hook. The system gets better every day it runs. See `harness/memory-compounding.md`.

**Wayfinding.** Work bigger than one session is a map of decision tickets, not a plan document. Clear the fog one decision at a time; bind every worktree to a ticket so ambition does not become sprawl. See `skills/wayfinding/`.

**No BS.** Crisp problem statements, hard constraints, explicit tradeoffs, no fabricated facts, no padding, no agreeing to be agreeable. See `rules/no-bs-mode.md`.

**Boil the Ocean.** Scope is bounded by the request; completeness within that scope is non-negotiable. Finish what was asked. See `rules/boil-the-ocean.md`.

**Boardroom.** Big decisions get eight adversarial perspectives, not one agreeable one. And periodically, the board convenes on the system's own weaknesses. See `skills/boardroom/` and `skills/boardroom-your-weaknesses/`.

**Video as a first-class deliverable.** Humans do not read walls of text; they watch and decide. Progress reports, proposals, and validations render as narrated video decks through a local pipeline. See `video/`.

## License

MIT. Take it, adapt it, build your own.
