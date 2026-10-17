---
name: clip-intelligence
description: Identify, rank, and package short-form content opportunities from long-form creator content.
---

# Clip Intelligence v1.1 — Creator-Ready Intelligence

## Purpose

Turn long-form content into an opportunity map and practical editing brief, not just a list of obvious highlights. Analyze timestamped transcripts and, when available, verified video/audio evidence to find moments worth turning into short-form content.

Optimize for opportunity diversity, evidence quality, standalone clarity, usefulness to the creator, and efficient use of analysis. Do not promise virality or fabricate engagement metrics.

## Core opportunity types

1. Comedy — jokes, reactions, absurdity, punchlines.
2. Personality — opinions, preferences, creator-specific behavior, recognizable voice.
3. Gameplay Progression — unlocks, rewards, milestones, meaningful progress, new abilities.
4. Curiosity — mysteries, questions, discoveries, open loops.
5. Story — compact narrative arcs, escalation, conflict, consequence.
6. Community — debate, competition, audience participation, comment invitations.
7. Discovery — surprising, useful, novel, or previously unknown information.

Use one primary type and add a secondary type only when it contributes a genuinely different, useful interpretation. Do not add secondary labels merely to make a candidate look richer.

## Inputs and source capability

Prefer a timestamped transcript. Accept video/audio or a video link only when the runtime actually makes the source accessible and provides the tools needed to inspect it. A link in a user message does not prove the video can be downloaded or analyzed.

Optional context: content type, niche, target platform, audience, creator goal, preferred duration, language, and creator constraints.

Never invent timestamps. If source access, audio, transcript, or visual evidence is incomplete, state the limitation and lower confidence. Do not claim to have downloaded, listened to, transcribed, or watched material unless the runtime actually did so.

For link-based intake, follow references/automatic-video-intake.md. If the URL cannot be accessed through an authorized, supported method, ask the user for a supported upload or timestamped transcript instead. Do not bypass authentication, paywalls, DRM, platform restrictions, or access controls.

## Creator Goal Modes

If the user specifies a goal, apply the relevant mode in references/creator-goal-modes.md. If no goal is specified, use Balanced Discovery.

- Growth / Discovery: emphasize clear hooks, novelty, accessibility, and low-context openings.
- Community: emphasize opinions, choices, debates, competitions, audience prompts, and identity.
- Personality / Connection: emphasize distinctive preferences, reactions, habits, storytelling, and creator voice.
- Evergreen / Value: emphasize useful discoveries, explanations, comparisons, and durable information.
- Balanced Discovery: balance the seven opportunity types according to source evidence; do not force equal representation.

Goal mode changes prioritization, not the evidence or the meaning of a score. Never guarantee reach, engagement, or virality.

## Workflow

1. Confirm source and scope. Identify what source evidence is available, its duration/time range if known, language, and any user-provided goal or platform. Ask one concise question only if a missing choice materially changes the result.
2. Normalize evidence. Preserve source timestamps and distinguish transcript timestamps, source-video timestamps, and any derived offsets. Never silently reset timestamps when processing chunks.
3. Build a broad candidate pool. Discover before ranking. Search for all opportunity types supported by the source, not only obvious jokes.
4. Classify candidates. Assign one primary type and an optional meaningful secondary type.
5. Apply the quality gate. Reject or mark NO-CLIP candidates that lack a usable hook, meaningful information/emotion/progression, or sufficient evidence.
6. Score content and evidence separately. Evaluate Content Potential and Visual/Edit Potential independently. Never infer visuals from a transcript alone.
7. Apply the requested Creator Goal Mode. Adjust relevance and ordering without changing source facts or inflating scores.
8. Check standalone clarity and context dependency. Determine whether an unfamiliar viewer can understand the clip, what minimum setup is required, and whether an on-screen caption or brief lead-in would resolve the gap.
9. Optimize boundaries. Remove unnecessary setup but preserve enough context; include the payoff, reveal, result, or consequence. Curiosity clips may end on a meaningful open loop.
10. Cluster duplicates. Keep one strongest version unless candidates have materially different hooks, payoffs, or clip functions.
11. Run evidence, quality, and diversity checks. Use references/cost-controls.md to stage expensive analysis only when supported by runtime tools.
12. Return ranked recommendations plus alternatives. Do not fill the primary list with weak candidates to reach a quota. Include the number of strong candidates actually found.
13. Create a Creator-Ready Clip Package for each primary recommendation, following the Output Contract.

## Candidate quality gate

A candidate should normally satisfy at least two of these signal groups, with at least one being Hook, Value, or Change:

- Hook: immediate question, contradiction, strong opinion, surprising statement, reaction, or tension.
- Value: useful discovery, explanation, comparison, tip, or information viewers can understand.
- Change: unlock, milestone, reveal, consequence, outcome, or meaningful state change.
- Emotion/Personality: strong reaction, recognizable preference, unusual behavior, or creator-specific perspective.
- Participation: debate, choice, competition, vote, or explicit invitation for viewers to weigh in.

Do not promote a candidate merely because it contains an unusual sentence, game mechanic, or reaction. Routine actions, generic commentary, low-information explanations, and ordinary transitions should default to NO-CLIP unless another strong signal makes them meaningfully useful.

## Opportunity discovery rules

Do not treat “funny” as a proxy for “good clip.” A candidate can be strong without a joke when it has a clear creator perspective, meaningful progression, curiosity, story, community value, or discovery value.

Pay special attention to:
- Progression: new powers, unlocked areas, completed quests, rewards, first-time events, milestones, upgrades, consequences.
- Curiosity: unexplained events, mysteries, questions, strange behavior, unresolved observations, “what is this?” moments, open loops.
- Personality: strong preferences, tastes, recurring habits, unusual decisions, self-characterization, opinions that invite agreement/disagreement.
- Community: competitions, votes, rankings, challenges, debates, audience questions, decisions viewers can weigh in on.
- Discovery: mechanics, tips, surprising facts, hidden systems, comparisons, unexpected behavior.
- Story: setup → escalation → consequence, conflict, stakes, reversal, or compact narrative arcs.

A strong candidate may combine types. Preserve the strongest primary type rather than flattening everything into Comedy.

## Type-specific evaluation

- Comedy: punchline/payoff, reaction, editability, personality.
- Personality: specificity, recognizable creator perspective, relevance, comment potential.
- Gameplay Progression: meaningful progress, hook, visual potential, discovery, consequence.
- Curiosity: hook, unanswered question/open loop, specificity, emotion, comment potential; an immediate payoff is not required.
- Story: narrative completeness, escalation, emotion, hook, stakes, context independence.
- Community: participation, debate, competition, personality, relevance, specificity, comment potential.
- Discovery: discovery value, hook, specificity, visual support, usefulness, relevance.

## Output Contract

Use the following sections in this order:

1. Source & Scope — source type actually analyzed, known duration/time range, language if known, evidence limitations, and chosen goal mode.
2. Top Clip Recommendations — default target is up to 5 primary recommendations, not a quota. Return fewer if fewer strong candidates exist. If the user asks for 10, return up to 10 strong candidates.
3. Alternative Opportunities — a separate, shorter shortlist of credible lower-priority or goal-specific candidates. Do not repeat the primary list or imply alternatives are equally strong.
4. Opportunity Coverage — briefly identify which of the seven opportunity types were found and which had no credible candidates. Do not force every type to appear.
5. NO-CLIP / Low-Value Findings — concise summary with at most 2–3 representative examples when useful. Do not dump a long list of routine moments unless the user explicitly asks for an audit.
6. Quality & Evidence Notes — note timestamp uncertainty, missing video evidence, context dependency, and any unverified assumptions.
7. Benchmark Comparison — only when a human-gold set is supplied.

### Required fields for each primary recommendation

- Rank and label.
- Primary type and optional secondary type only when meaningful.
- Timestamp and duration, using source-video time where available.
- Opportunity scores, following Scoring Transparency below.
- Confidence (high, medium, or low), representing evidence quality rather than predicted performance.
- Hook, grounded in the source; suggested packaging may be added separately.
- Why it works: the strongest evidence-backed reason.
- Standalone Clarity (high, medium, low): how well a new viewer can follow the moment without prior context.
- Required context: minimum setup that must remain or be added.
- Payoff / Open Loop: what resolves or intentionally remains unresolved.
- Recommended boundaries: why the start and end timestamps are appropriate.
- Alternate shorter boundary: timestamps plus what is lost or preserved by shortening.
- Evidence note: transcript, audio, video, or combination; clearly separate observed facts from inference.

### Creator-Ready Clip Package

For each primary recommendation, add a compact package with:

1. Suggested title — specific and faithful to the moment; avoid clickbait claims unsupported by the source.
2. Opening hook — a short source-grounded quote or a clearly labeled editorial suggestion. Never present invented wording as an actual quote.
3. Caption draft — adapt to the requested platform or use a platform-neutral version if none was specified.
4. Hashtags — optional and relevant; do not force a long generic list. If platform limits are known from the user's request, respect them.
5. Editing plan — concrete notes such as where to preserve a reaction, remove dead air, add a zoom, subtitle a key line, or show a relevant visual. Do not suggest an edit requiring visual evidence that was not observed.
6. Packaging rationale — one short sentence explaining how the title/hook/caption supports the moment's actual value.

Do not claim to generate or export an actual video file unless a supported tool performed that operation. This package is an editing brief, not a rendered clip.

### Scoring transparency

Use 0–100 structured judgment scores, not probabilities. A score of 90 does not mean a 90% chance of going viral or succeeding. Scores are comparative prioritization aids for this source and goal, not measured engagement predictions.

When video evidence is available, the default formula is:
- Content Potential: 40%
- Visual/Edit Potential: 25%
- Audience/Goal Fit: 15%
- Opportunity-Type Fit: 15%
- Editability: 5%

When only transcript evidence is available, mark Visual/Edit Potential as evidence-limited and do not pretend to know visual quality. Do not manufacture a precise visual score from transcript-only evidence. If a numeric final score is still requested, state that the score is transcript-only and not directly comparable to a video-verified score.

Interpretation guide for adequately evidenced candidates:
- 90–100: Priority
- 80–89: Strong
- 70–79: Test
- 60–69: Secondary
- Below 60: usually NO-CLIP unless a user-specific goal gives a supported reason to review it

These bands are prioritization guidance, not predictions of virality. Do not imply that scores have been empirically calibrated unless a documented evaluation supports that claim.

## Boundary and standalone clarity rules

For each recommended start, explain why that point is the earliest useful moment (for example, it introduces the question, reaction, conflict, or decision). For each end, explain why it preserves the payoff, result, or intentional open loop without unnecessary tail.

The alternate shorter boundary must state the trade-off: what context or payoff it preserves, and what it sacrifices compared with the main cut.

Standalone Clarity:
- High: the core situation and payoff are understandable to a new viewer with no more than minimal framing.
- Medium: understandable if a short lead-in, caption, or key visual is retained.
- Low: depends on earlier unseen context; recommend keeping setup or do not prioritize as a short unless the user wants serialized/context-dependent clips.

Do not treat a low-context clip as automatically better if the removed context contains the emotional or narrative payoff.

## Evidence and visual provenance

When video is available, inspect visual evidence before assigning Visual/Edit Potential. Look for reactions, gameplay state changes, unlocks, scene changes, readable UI, framing, and useful edit opportunities.

Label evidence explicitly:
- Observed in video: directly visible or audible in the supplied media.
- Present in transcript: words represented by the supplied/generated transcript.
- Inference: a plausible interpretation that is not directly established.
- Unverified: cannot be checked with available evidence.

Do not describe facial expressions, game events, on-screen text, or camera framing as observed unless they were actually inspected. If the video cannot be inspected, say so and lower confidence. Transcript/audio evidence can establish what was said, not what appeared on screen.

## Ranking and tie-breaking

Use 0–100 scores as structured judgments, not guarantees. When candidates are within 2 points, prefer stronger evidence, lower context dependency, distinct topic/type coverage, and cleaner boundaries—in that order. Do not let diversity overtake a clearly stronger candidate.

After scoring:
1. Apply evidence and context gates.
2. Apply the candidate quality gate and clipability check.
3. Cluster duplicates and overlapping versions.
4. Run the goal-fit and type-concentration checks.
5. Return a primary shortlist and separate alternatives.
6. Never force a weak candidate into the primary list to satisfy a count or diversity target.

## Quality and cost controls

Follow references/cost-controls.md. In brief:
- Use a staged pipeline: broad, economical discovery first; detailed packaging only for the strongest candidates.
- Do not transcribe or analyze the same source twice when a valid transcript/result is already available in the current task.
- Avoid generating full title/caption/hashtag packages for rejected candidates.
- For long media split into chunks, preserve offsets and deduplicate candidates crossing chunk boundaries.
- Do not assume a link is accessible. Check source availability before spending substantial analysis effort.
- If the source cannot be accessed, explain the blocker and ask for a supported upload or transcript.
- Do not promise cost savings or a processing limit without measured runtime data.

## Ranking safeguards

1. Evidence gate: do not rank a candidate highly if its core claim, boundary, or payoff is unsupported.
2. Signal gate: candidates failing the quality gate should be NO-CLIP or low priority.
3. Context penalty: penalize moments that require long unseen setup unless that setup is essential and compact.
4. Duplicate penalty: cluster near-identical moments and keep the strongest version.
5. Type integrity: do not relabel a candidate as Comedy merely because humor makes it easier to rank.
6. NO-CLIP is valid: routine actions, low-information filler, repetitive inventory management, or moments without a usable hook/payoff may be returned as NO-CLIP.
7. Time-sensitive claims: flag claims whose truth may change over time, including platform availability, pricing, releases, and product features.
8. Transcript/video agreement: when both are available, use transcript for words and video for visible events. Neither source silently invents evidence for the other.
9. Creator voice: preserve the creator's actual tone and meaning. Do not imitate another creator or invent quotes.
10. No unsupported promises: never promise virality, fabricate engagement metrics, or claim measured accuracy without a documented evaluation.

## Benchmark mode

When a human-gold set is available, freeze the ranked output before comparing it with the gold set. Do not use gold labels to retroactively improve the ranking in the same run.

Report matching with an explicit rule, such as semantic event overlap plus timestamp overlap. Keep gold recovery separate from non-gold candidate quality. Report opportunity-type coverage, ranking position, boundary quality, NO-CLIP behavior, and false positives when possible.

Never claim benchmark precision, recall, statistical generalization, virality, engagement lift, or production accuracy unless measured against an explicit evaluation set.
