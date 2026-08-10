# The two-deck decision protocol

How a human who does not read walls of text stays in genuine control of an autonomous system: every bulk of work is decided via a narrated video deck, and validated via a second one. Nothing merges in between.

## The protocol

```
1. PROPOSE     the system renders a proposal deck: numbered points, one decision
               per point, narrated. Sent to wherever the human actually is
               (their phone, their chat app).
2. ANSWER      the human replies to each numbered point ("1 yes, 2 yes, 3 no,
               4 - do it this other way"). Voice notes count; transcribe locally.
3. BUILD       the system executes exactly the approved points. Unapproved
               points do not get built "while we're in there".
4. VALIDATE    a second deck: what was built, the evidence (test counts, live
               probes, screenshots), what changed from the proposal, what
               remains. Honest failures included.
5. PROCEED     only after the validation deck does anything merge, deploy, or
               ship. The human's go on the validation is the gate.
```

## Why decks and not text

Numbered points force decisions to be enumerable; a wall of prose hides the seventh decision inside the fourth paragraph. Narration means the human can decide from their phone, walking, in ninety seconds. And a validation deck that must show EVIDENCE (numbers, probe output, screenshots) is much harder to hand-wave than a chat message saying "done".

## The value block

Every deck-worthy report states its own value honestly, because these four fields are judgements only the author can make; a model asked to infer them later will answer plausibly and wrongly:

```
VALUE:
  GOT:      what the human can now do that they could not before, in their terms
  JOB:      the job this session actually got done for them
  SKILL:    the capability the system now has that it did not
  LEARNED:  one real thing this run taught us - "everything went well" is not a learning
  ASK:      at most ONE decision needed from the human; omit if none
```

Rules that keep the channel alive:

- **Never invent a field to fill a slide.** An honest "not stated" is the designed value.
- **No self-graded fields.** Deliberately absent: "regression: none", "goal progress: 80%". A session cannot audit itself; compute those from an external ledger.
- **ASK is at most one decision.** Filler asks train the human to ignore the field.
- Skip the block (and the deck) on conversational replies and trivial fixes. The gate scales with the work.

## Failure modes to design against

- **Per-response gates cannot see a wave.** If ten parallel agents each ship a small piece, no single response crosses the "substantive" threshold and the milestone gets no deck. Add milestone triggers (a merge train completing, an install landing) alongside the per-response gate.
- **A missed deck is a trust incident.** When the human asks "where is my video?", treat it as a sev: find the silent exit path, log all verdicts, fix the gate. Twice is chronic.
- **Voice replies must reach the session.** If the human answers the deck by voice note in their chat app, the transcription must land in the working session's context, not in a bridge nobody reads.
