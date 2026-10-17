# Clip Intelligence

AI-powered content intelligence for long-form creators.

## Current Skill

The Skill lives in [clip-intelligence/SKILL.md](clip-intelligence/SKILL.md). The v1.1 proposal focuses on Creator-Ready Clip Packages, Creator Goal Modes, transparent scoring, standalone clarity, evidence provenance, staged quality/cost controls, and broad opportunity inventory.

The default output contains up to five fully packaged primary recommendations, plus a compact inventory of all other distinct, credible opportunities found in the portions of the source actually analyzed. The five-item limit does not cap discovery or alternatives. The Skill reports coverage gaps and candidate counts rather than implying exhaustive coverage when source segments were skipped.

## Reference documents

- [Scoring framework](clip-intelligence/references/scoring.md)
- [Opportunity hook types](clip-intelligence/references/hook-types.md)
- [Visual intelligence and evidence provenance](clip-intelligence/references/visual-intelligence.md)
- [Creator Goal Modes](clip-intelligence/references/creator-goal-modes.md)
- [Quality verification and cost controls](clip-intelligence/references/cost-controls.md)
- [Automatic Video Intake architecture](clip-intelligence/references/automatic-video-intake.md)

## Important capability boundary

Automatic Video Intake is a prepared architecture, not an implemented downloader or transcription runtime. The Skill can analyze a URL only when the host runtime provides authorized access to the media and the required audio/transcription tools. Do not advertise link-to-clips as supported until the acceptance tests in the Automatic Video Intake reference have passed.

## Benchmarks

The benchmark fixtures are qualitative development aids, not statistical guarantees. Do not claim virality or production accuracy from them.
