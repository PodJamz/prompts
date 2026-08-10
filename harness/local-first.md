# Local first

Free and local by default. Cloud is an opt-in upgrade, never a dependency of the daily loop. This is a principle about an ADAPTIVE ladder, not a single provider.

## Why

- **No API keys to start.** The out-of-box experience must work on day one with zero accounts.
- **No rate limits, no surveillance, no per-token anxiety** on routine work.
- **Latency.** A local text-to-speech line speaks in under a second. A local transcription never queues.
- **Resilience.** When the cloud is down, revoked, or expensive, the system still runs.

## The model ladder

Wire a failover chain, best-first, and let the router pick:

```
1. local primary        (your tuned local model via Ollama / LM Studio / llama.cpp)
2. local fallback       (a second local model, different family)
3. free cloud tier      (e.g. an OpenRouter :free model, dynamically chosen)
4. paid cloud           (opt-in via API key, for the hardest work only)
```

Rules that make it work:

- Every provider behind one client interface, so the agent code never knows which rung answered.
- The free-tier rung should pick its model dynamically (query what is currently available and good, do not hardcode a model name that will be deprecated).
- Paid rungs activate only when a key is present. Their absence is a normal state, not an error.
- Platform-native accelerators (an on-device foundation model, a neural engine bridge) auto-enable when the host qualifies and silently stay off otherwise.

## Local speech, both directions

**Speech to text: whisper.cpp.** Download a model once (`ggml-base.en.bin` is fine for commands), then:

```bash
ffmpeg -y -i input.ogg -ar 16000 -ac 1 input.wav
whisper-cli -m ~/.models/whisper/ggml-base.en.bin -f input.wav -nt -np
```

No cloud STT fallback. If a voice note arrives and transcription fails, say so honestly; never ship audio to a third party as a silent fallback.

**Text to speech, in quality tiers:**

| Tier | Engine | Use |
|---|---|---|
| 0 | OS built-in (`say` on macOS, `espeak-ng`/`piper` on Linux) | always available, dev and internal |
| 1 | Small local neural TTS (KittenTTS, Supertonic and similar, CPU-friendly) | daily driver voices, per-agent identity |
| 2 | Cloud TTS (ElevenLabs and similar) | public-facing polish only, opt-in |

Give each agent persona a fixed voice mapping and never randomize it. Voice is declared identity: same speaker, same voice, every time.

## Credentials

- One env file is the single source of truth (for example `~/.claude/.env`). Never a second copy: a mirrored env file drifted within hours of being created, twice in one day.
- Code reads keys from the env file or a secret manager. Literal fallback values in code are banned.
- Never print a token. Compare secrets by hash when you must verify parity between environments.
- When a token leaks into any transcript or log, treat it as burned: rotate at the source, update the single env file, verify with a read-only API call.

## What local-first is not

It is not a purity test. Cloud models are the right tool for frontier reasoning; the point is that the SYSTEM keeps running without them, and that the routine 95 percent (transcription, narration, summaries, classification, rendering) costs nothing and leaks nothing.
