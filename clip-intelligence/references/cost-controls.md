# Quality Verification and Cost Controls

These are reasoning and workflow rules for runtimes that support the required operations. They do not themselves create upload, download, transcription, frame extraction, or billing capabilities.

## Staged pipeline

1. **Check access first.** Confirm that the supplied transcript, media attachment, or link is actually accessible through a supported runtime tool. Do not perform expensive analysis against a URL that cannot be read.
2. **Reuse valid work.** If the current task already contains a valid transcript with timestamps, use it. Do not transcribe the same source again unless the user asks for a new language, improved quality, or a correction.
3. **Discover broadly and cheaply.** Build a broad text-based candidate pool from transcript segments and signal markers before generating detailed packages.
4. **Filter before enrichment.** Apply evidence, quality, context, and duplicate gates before spending effort on detailed packaging or visual inspection.
5. **Enrich only likely finalists.** Create title, hook, caption, optional hashtags, and detailed edit notes for primary recommendations, not every rejected candidate.
6. **Use selective visual review where supported.** Inspect frames around candidate boundaries, important events, and uncertain visual claims. Do not claim that selective sampling is continuous or exhaustive video review.
7. **Preserve timestamps across chunks.** Record each chunk's source offset; convert local timestamps back to original-video timestamps; deduplicate candidates that overlap chunk boundaries.
8. **Report limitations.** If any stage is skipped, failed, sampled, or inferred, disclose that in Quality & Evidence Notes.

## Quality gates

Before finalizing each primary recommendation, verify:
- Start/end timestamps are supported by source evidence.
- Duration matches the timestamps.
- The hook and payoff are represented by the source.
- Standalone Clarity and Required Context are consistent.
- Any visual instruction is based on observed video, not transcript-only inference.
- Suggested title/caption does not invent a quote, event, result, or claim.
- The candidate is not a duplicate of a stronger candidate.
- Score and confidence are not conflated.
- Goal mode is stated and applied consistently.

If the timestamp cannot be verified, mark it approximate and explain why. Never manufacture precision to make the output look complete.

## Cost discipline

- Avoid redundant calls, repeated transcription, and full candidate-by-candidate enrichment.
- Prefer a single source transcript reused for candidate discovery and packaging.
- Do not repeatedly process a long video to answer a small follow-up when the prior transcript/evidence is still available.
- Avoid defaulting to exhaustive visual analysis when a transcript-only answer can provide a useful first pass.
- Do not quote a fixed cost, runtime, maximum duration, or savings percentage unless it has been measured for the actual model, provider, media length, and runtime.
- If cost or runtime limits are unknown, recommend a small test and log input duration, bytes, token/audio usage, processing time, retries, and final candidate count.

## Operational fallback

If a stage is unsupported:
- Link unavailable: request a supported upload or transcript.
- Video visible but audio extraction unavailable: request an audio file or transcript.
- Transcript available but video inspection unavailable: proceed as transcript-only, mark Visual/Edit Potential evidence-limited, and do not describe unseen visuals.
- Chunk processing fails: report the covered time range and ask for a smaller or split source; do not imply full coverage.
- Output becomes too long: preserve the primary recommendations and concise alternatives; offer a separate detailed audit only if requested.

## Measurement

For each real test, where data is available, record:
- Source duration and size.
- Input method (transcript, upload, direct link).
- Model/provider and processing path.
- API cost and elapsed time.
- Number of candidates discovered, retained, and rejected.
- Human review of timestamp correctness, standalone clarity, evidence grounding, duplicate quality, and usefulness.

Do not claim the controls reduced cost or improved accuracy until measurements demonstrate it.