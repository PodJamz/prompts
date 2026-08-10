# HyperFrames

For designed motion video (animated explainers, launch videos, motion graphics, captioned footage, beat-synced edits), HyperFrames renders video from HTML: a composition is an HTML file whose DOM declares timing with `data-*` attributes, whose animation runtime is seekable, and whose media playback is owned by the framework. If your agent writes HTML, your agent makes video.

## Getting it

```bash
npx hyperframes skills update <workflow-name>   # installs/refreshes a workflow's agent skills
npx hyperframes check                            # validate a project's compositions
```

The CLI ships agent skills for each workflow, so your agent gets the authoring contract, motion rules, and diagnostics as loadable instructions rather than folklore.

## Routing by deliverable

Match the requested deliverable, not a word mentioned in passing:

| You want | Workflow |
|---|---|
| a presentation, pitch deck, or navigable interactive deck | `slideshow` |
| plain captions/subtitles on existing talking-head footage | `embedded-captions` |
| designed graphic overlays on interview/podcast footage, footage untouched | `talking-head-recut` |
| a beat-synced video driven by a music track | `music-to-video` |
| a short unnarrated motion-first unit, typically under 10s | `motion-graphics` |
| explain a pull request or code change | `pr-to-video` |
| market a website/product from a URL | `product-launch-video` |
| explain a topic with invented visuals, no product capture | `faceless-explainer` |
| anything else custom | `general-video` |

Notes that save routing arguments: length pushes long pieces (over ~3 minutes) to `general-video`; music as a bed does not make it `music-to-video` (only a beat-grid-driven piece does); "I want a storyboard" changes the review process, not the workflow.

## Why an HTML-native framework is the right call for agent video

- The composition is TEXT. Agents diff it, review it, version it, and regenerate it deterministically.
- Seekable animation means renders are reproducible frame-for-frame: no flaky captures.
- The same brand system (CSS tokens) that styles your product styles your video.
- It composes with the local-first stance: author locally, render locally, no per-render cloud cost.

## Discipline

- Pin the framework version in each project so renders stay reproducible; upgrade deliberately (`npx hyperframes@latest upgrade --project . --check` before, `npx hyperframes check` after) and name the version bump in the run summary.
- Read the framework's authoring contract before writing composition HTML; seek-safety rules are what keep renders deterministic, and guessing them produces videos that drift between renders.
