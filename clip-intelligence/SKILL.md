---
name: clip-intelligence
description: Identify, rank, and optimize short-form content opportunities from long-form creator content.
---

# Clip Intelligence v0.3

## Purpose

Turn long-form content into an **opportunity map**, not just a list of obvious highlights. Analyze timestamped transcripts and, when available, video evidence to find moments worth turning into short-form content.

## Core opportunity types

1. Comedy — jokes, reactions, absurdity, punchlines.
2. Personality — opinions, preferences, creator-specific behavior.
3. Gameplay Progression — unlocks, rewards, milestones, meaningful progress.
4. Curiosity — mysteries, questions, discoveries, open loops.
5. Story — compact narrative arcs and escalation.
6. Community — debate, competition, audience participation.
7. Discovery — surprising, useful, or previously unknown information.

## Inputs

Prefer a timestamped transcript. Accept video/audio when available. Optional context includes content type, niche, target platform, audience, goal, preferred duration, and creator constraints.

Never invent timestamps. If evidence is incomplete, lower confidence and say why.

## Workflow

1. Parse the source and normalize timestamps.
2. Segment the content into candidate moments.
3. Classify each candidate with one primary and optional secondary opportunity type.
4. Score **Content Potential** separately from **Visual/Edit Potential**.
5. Evaluate audience/goal fit, editability, context dependency, payoff or open loop, specificity, and comment potential as appropriate to the opportunity type.
6. Cluster overlapping candidates and avoid returning several versions of the same moment unless they have materially different payoffs.
7. Optimize boundaries: remove unnecessary setup, preserve enough context, and end after the punchline/reveal/result. Curiosity candidates may intentionally end on an open loop.
8. Explicitly identify NO-CLIP moments when evidence does not support a worthwhile short-form opportunity.
9. Run a diversity check across opportunity types, topics, and sections of the source.
10. Return ranked opportunities plus shorter alternatives.

## Type-specific evaluation

### Comedy
Prioritize punchline/payoff, emotional reaction, editability, and personality.

### Personality
Prioritize specificity, recognizable creator perspective, relevance, and comment potential. A moment does not need to be a joke.

### Gameplay Progression
Prioritize meaningful progress, hook, visual potential, discovery, and relevance. Unlocks and milestones can be strong even without humor.

### Curiosity
Prioritize hook, unanswered question/open loop, specificity, emotion, and comment potential. Do not require an immediate payoff.

### Story
Prioritize narrative completeness, escalation, emotion, hook, and context independence.

### Community
Prioritize participation, debate, competition, personality, relevance, and specificity.

### Discovery
Prioritize discovery value, hook, specificity, visual support, and relevance.

## Output

Return:

- Source summary.
- Opportunity map by type.
- Ranked candidates with timestamp and duration.
- Primary/secondary type.
- Content Potential.
- Visual/Edit Potential.
- Opportunity Fit.
- Final Opportunity Score.
- Confidence, kept separate from score.
- Hook.
- Why it works.
- Required context.
- Payoff or open loop.
- Recommended editing approach.
- Alternate shorter boundary.
- NO-CLIP recommendations where justified.
- Diversity check.

Use 0–100 scores. Treat scores as structured judgment, not guarantees of virality.

## Default scoring

When video evidence is available:

- Content Potential: 40%
- Visual/Edit Potential: 25%
- Audience/Goal Fit: 15%
- Opportunity-Type Fit: 15%
- Editability: 5%

When only transcript evidence is available, do not pretend to know visual quality. Mark Visual/Edit Potential as evidence-limited and reduce confidence.

## Quality rules

- Prefer distinct opportunities over repetitive highlights.
- Separate factual claims from inference.
- Flag time-sensitive claims.
- Do not promise virality.
- Do not fabricate engagement metrics.
- Preserve creator voice without copying another creator's identity or scripts.
- If no strong opportunity exists, say NO-CLIP.
- Confidence reflects evidence quality; it is not another version of the score.
