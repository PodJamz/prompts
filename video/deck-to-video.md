# Deck to video

Any HTML slide deck on a simple convention becomes a narrated MP4, rendered entirely locally in a few minutes. This is the workhorse pipeline: agents write HTML fluently, so agents can produce broadcast-ready narrated video by writing a single file.

## The deck convention

One HTML file. Slides are sibling divs shown one at a time via an `.active` class; narration and voice are declared per slide as data attributes:

```html
<div class="slide" data-slide="0" data-voice="Daniel"
     data-voiceover="The narration for this slide, written to be SPOKEN - short sentences, no abbreviations, numbers written as words where they read better.">
  <div class="kicker">SECTION LABEL</div>
  <h1>The headline</h1>
  <div class="lede">Supporting line the viewer reads while listening.</div>
</div>
```

- `data-slide`: ordinal.
- `data-voiceover`: the spoken line. Write for the ear, not the eye.
- `data-voice`: narrator voice for this slide (maps to an installed TTS voice). Different speakers per slide gives you a multi-presenter deck for free.
- Author at a fixed canvas (1920x1080), dark background, big type. A tiny keyboard-nav script makes the same file a live presentation.

## The pipeline

```
for each slide:
  1. SCREENSHOT   headless Chrome renders a temp copy with that slide forced
                  .active, entrance animations killed, nav controls hidden
  2. NARRATE      local TTS speaks data-voiceover in data-voice -> wav
                  loudness-normalize to about -18 LUFS so voices match
  3. TIME         slide duration = narration duration (+ ~0.7s breathing room)
then:
  4. ASSEMBLE     ffmpeg: image sequence with 0.5s crossfades, narration track,
                  optional soft music bed (lowpassed, volume ~0.15, no pulse)
  5. DELIVER      MP4 to the folder your surfaces serve, then notify the human
```

The whole thing is one script of a few hundred lines: Python or TypeScript, headless Chrome (or Playwright), your OS TTS or a local neural TTS, ffmpeg. No cloud calls anywhere.

Useful flags to build in: `--no-voice` (silent music-only cut), `--rate` (speech WPM), `--max-slides` (fast preview renders).

## Gotchas learned the hard way

- **Narration drives length.** A 13-slide deck with generous voiceovers is six or seven minutes. Write tight lines.
- **Kill entrance animations in the screenshot copy** or half your slides capture mid-fade.
- **Normalize loudness per line.** Different TTS voices ship at wildly different levels; without normalization every speaker change is a volume jump.
- **Decks not on the convention should fail loudly.** Detect and exit with a clear message; a silent empty video is worse than an error.
- **A path in chat is not a deliverable.** The render is done when it has been opened on the human's screen (or delivered into their hand on the phone), not when the file exists.

## Rendering session reports automatically

Wire this into your harness's stop hook: when a session response is substantive (define a real gate: length floor, structural headings, a stated value block), render it into a deck and deliver it. Gate rules that matter, learned from silent failures:

- The hook's pre-gate and the renderer's gate must be THE SAME code or they drift apart and videos silently stop.
- Log every verdict (rendered or skipped, and why) to a file; a silent skip is indistinguishable from a broken pipeline.
- Detached spawns need their PATH set explicitly; hooks run in a thinner environment than your shell.
- Rate-limit (one video per N minutes, a daily cap) so the channel stays a signal.
