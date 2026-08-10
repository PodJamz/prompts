# Video production workflow

For video built from captured material (screen recordings, generated audio, footage) rather than slides: a structured process that adapts to content type but never breaks brand.

## The default order

```
1. PLAN       content type, audience, format (16:9 / 9:16), target duration
2. AUDIO      generated conversation audio OR scripted TTS OR an existing recording
3. STRIP      trim any platform intro/outro branding from captured audio (ffmpeg)
4. COMPOSITE  the composition: footage + audio + typography in a programmatic
              video framework (Remotion, HyperFrames, or your own)
5. CAPTION    captions synced to audio timestamps
6. EXPORT     render at every target format
7. DELIVER    to the surface the audience actually uses, then verify it plays
```

Steps 2-3 are optional depending on the audio source; every step runs independently.

## Audio sources, honestly ranked

- **AI-generated conversation audio** (podcast-style generators) produces genuinely surprising discussions that you would not script. Capture it, trim the platform's branded intro and outro, and composite it into your own template.
- **Scripted TTS**: local neural TTS for internal work; a premium cloud voice for anything public-facing. No robotic TTS on public content, ever.
- **Real recordings** beat both when you have them.

## Brand guardrails (define once, enforce always)

Write these into the skill so every pipeline applies them mechanically:

- **Palette**: your primary, your backgrounds, your text colors, stated as hex. And your FORBIDDEN ranges stated just as explicitly (banning a hue range outright is more enforceable than "prefer our colors").
- **Typography**: one display face, one body face, stated weights.
- **Motion language**: ease everything, no linear transitions; spring physics for reveals; fixed title-in and outro-out durations; caption style pinned (position, max width, background treatment).
- **Never**: third-party watermarks in your output, competitor mentions in any frame, punctuation and style patterns you have banned in your brand voice.

## Example invocations

```
"Make the onboarding tutorial video"
  -> PLAN: tutorial, new-user audience, 16:9 + 9:16 cuts
  -> AUDIO: generated conversation over the docs; STRIP branding
  -> COMPOSITE: screen recording + stripped audio + captions
  -> EXPORT both formats; DELIVER to the help page and verify

"60-second social clip of the new feature"
  -> PLAN: social, 9:16, no narration
  -> COMPOSITE: screen recording + music bed + caption overlays
  -> EXPORT vertical preset
```
