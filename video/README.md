# Video as a first-class deliverable

If the human behind your system does not read walls of text (most do not), video is not a nice-to-have; it is the reporting channel. Everything substantive the system produces should be able to land as a short narrated video: proposals, progress reports, validations, explainers, launches.

## The channels

| Channel | Artifact | File |
|---|---|---|
| **Decisions** | proposal deck + validation deck, narrated | `two-deck-protocol.md` |
| **Progress reports** | the session summary rendered as a narrated deck by a stop hook | `two-deck-protocol.md` |
| **Explainers, launches, social** | full production pipeline | `production-workflow.md`, `hyperframes.md` |
| **Anything from HTML slides** | the local deck-to-video renderer | `deck-to-video.md` |

## Principles

1. **Local-first rendering.** Headless browser screenshots, local TTS, ffmpeg. The whole pipeline runs free, offline, in minutes. Cloud TTS is a polish upgrade for public-facing output only.
2. **Voice-first pacing.** Narration length drives slide duration, never the reverse. A slide stays up exactly as long as its line takes to say.
3. **Deterministic audio identity.** Each narrator persona maps to one fixed voice. Same speaker, same voice, every render.
4. **Honest content or no video.** A deck field the author did not state renders as "not stated", never as an invented value. One fabricated metric in one deck kills the human's trust in the entire channel.
5. **Brand is enforced, not remembered.** Define palette, typography, and motion language once; every pipeline applies them. Ban the colors and patterns you never want; a rule that lives in a file gets applied, a preference that lives in your head does not.
6. **Music is a bed, not a voice.** Low, lowpassed, quiet (around -20 dB under narration), no loops that pulse or ping. Silence beats a distracting bed.
7. **Ship every video where the human actually is.** Rendering to a folder nobody opens is not delivery. Push to the phone, the chat channel, the dashboard; then confirm it opened.

## Choosing a pipeline

- **You have HTML slides** (or your agent can write them, which it can): `deck-to-video.md`. This is the workhorse; 90 percent of system-generated video is this.
- **You need designed motion** (animated explainers, launch videos, captions on footage, beat-synced cuts): `hyperframes.md`, an HTML-to-video framework with skills for each format.
- **You have captured audio or screen recordings** to build around: `production-workflow.md`.
