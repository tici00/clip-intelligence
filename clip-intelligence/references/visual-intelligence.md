# Visual Intelligence — v1.1

When video is available and the runtime can actually inspect it, review visual evidence before assigning Visual/Edit Potential.

Look for:
- visible reactions and facial expressions
- gameplay state changes, unlocks, rewards, failures, discoveries
- UI or scene changes that clarify the event
- objects entering, leaving, or changing state
- readable on-screen information when genuinely visible
- framing and composition that support a vertical short
- moments where a cut, zoom, caption, freeze frame, or replay would improve clarity

## Evidence provenance

For each meaningful visual claim, distinguish:
- **Observed in video:** directly inspected in the supplied media.
- **Present in transcript/audio:** established by words or sound, not necessarily by the image.
- **Inference:** plausible interpretation, not directly established.
- **Unverified:** cannot be checked with available evidence.

Do not infer a visual event solely because the transcript suggests it happened. If the video is unavailable or cannot be inspected reliably, state the limitation, mark Visual/Edit Potential as evidence-limited, and lower confidence.

A visually busy moment with weak content should not automatically rank highly. Visual evidence strengthens the content decision; it does not replace it.

## Selective inspection

If a runtime supports frame extraction or video viewing, inspect frames around candidate starts, key events, and ends, especially where a visual claim affects the recommendation. Do not imply that sampled frames constitute continuous video review. State when visual inspection was sampled or partial.

The Skill itself does not extract frames, download video, or transcribe audio. Those capabilities must be provided by the runtime or an external supported service. See references/automatic-video-intake.md.