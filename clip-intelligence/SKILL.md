---
name: clip-intelligence
description: Identify, rank, and optimize short-form content opportunities from long-form creator content.
---

# Clip Intelligence v0.3

## Purpose

Turn long-form content into an **opportunity map**, not just a list of obvious highlights. Analyze timestamped transcripts and, when available, video evidence to find moments worth turning into short-form content.

The system must optimize for **opportunity diversity and usefulness**, not only immediate humor or punchlines.

## Core opportunity types

1. Comedy — jokes, reactions, absurdity, punchlines.
2. Personality — opinions, preferences, creator-specific behavior, recognizable voice.
3. Gameplay Progression — unlocks, rewards, milestones, meaningful progress, new abilities.
4. Curiosity — mysteries, questions, discoveries, open loops.
5. Story — compact narrative arcs, escalation, conflict, consequence.
6. Community — debate, competition, audience participation, comment invitations.
7. Discovery — surprising, useful, novel, or previously unknown information.

## Inputs

Prefer a timestamped transcript. Accept video/audio when available. Optional context includes content type, niche, target platform, audience, goal, preferred duration, and creator constraints.

Never invent timestamps. If evidence is incomplete, lower confidence and say why.

## Workflow

1. Parse the source and normalize timestamps.
2. Segment the content into candidate moments.
3. Detect **opportunity signals before ranking**. Look for punchlines, strong reactions, opinions, specific observations, questions, reveals, unlocks, milestones, discoveries, conflicts, competitions, audience-facing statements, surprising outcomes, and narrative escalation.
4. Classify each candidate with one primary and optional secondary opportunity type.
5. Score **Content Potential** separately from **Visual/Edit Potential**.
6. Evaluate audience/goal fit, editability, context dependency, payoff or open loop, specificity, and comment potential as appropriate to the opportunity type.
7. Cluster overlapping candidates and avoid returning several versions of the same moment unless they have materially different hooks or payoffs.
8. Optimize boundaries: remove unnecessary setup, preserve enough context, and end after the punchline/reveal/result. Curiosity candidates may intentionally end on an open loop. Progression candidates should include the meaningful unlock, reward, result, or consequence when needed.
9. Explicitly identify NO-CLIP moments when evidence does not support a worthwhile short-form opportunity.
10. Run a **diversity check before final ranking**. If one opportunity type dominates the top results, re-check the source for strong candidates from other types before finalizing. Do not force weak diversity merely to fill categories.
11. Return ranked opportunities plus shorter alternatives.

## Opportunity discovery rules

Do not treat “funny” as a proxy for “good clip.” A candidate can be strong without a joke when it has a clear creator perspective, meaningful progression, curiosity, story, community value, or discovery value.

Pay special attention to:

- **Progression signals:** new powers, unlocked areas, completed quests, rewards, first-time events, milestones, upgrades, consequences.
- **Curiosity signals:** unexplained events, mysteries, questions, strange behavior, unresolved observations, “what is this?” moments, open loops.
- **Personality signals:** strong preferences, tastes, recurring habits, unusual decisions, self-characterization, opinions that invite agreement/disagreement.
- **Community signals:** competitions, votes, rankings, challenges, debates, audience questions, decisions viewers can weigh in on.
- **Discovery signals:** mechanics, tips, surprising facts, hidden systems, comparisons, unexpected game behavior.
- **Story signals:** setup → escalation → consequence, conflict, stakes, reversal, or compact narrative arcs.

A strong candidate may combine types. Preserve the strongest primary type rather than flattening everything into Comedy.

## Type-specific evaluation

### Comedy
Prioritize punchline/payoff, emotional reaction, editability, and personality.

### Personality
Prioritize specificity, recognizable creator perspective, relevance, and comment potential. A moment does not need to be a joke.

### Gameplay Progression
Prioritize meaningful progress, hook, visual potential, discovery, relevance, and consequence. Unlocks and milestones can be strong even without humor.

### Curiosity
Prioritize hook, unanswered question/open loop, specificity, emotion, and comment potential. Do not require an immediate payoff.

### Story
Prioritize narrative completeness, escalation, emotion, hook, stakes, and context independence.

### Community
Prioritize participation, debate, competition, personality, relevance, specificity, and comment potential.

### Discovery
Prioritize discovery value, hook, specificity, visual support, usefulness, and relevance.

## Output

Return:

- Source summary.
- Opportunity map by type, including meaningful types even if they do not make the top ranking.
- Ranked candidates with timestamp and duration.
- Primary/secondary type.
- Content Potential.
- Visual/Edit Potential.
- Audience/Goal Fit.
- Opportunity-Type Fit.
- Editability.
- Final Opportunity Score.
- Confidence, kept separate from score.
- Hook.
- Why it works.
- Required context.
- Payoff or open loop.
- Recommended editing approach.
- Alternate shorter boundary.
- NO-CLIP recommendations where justified.
- Diversity check, including whether the ranking appears over-concentrated in one opportunity type.

Use 0–100 scores. Treat scores as structured judgment, not guarantees of virality.

## Default scoring

When video evidence is available:

- Content Potential: 40%
- Visual/Edit Potential: 25%
- Audience/Goal Fit: 15%
- Opportunity-Type Fit: 15%
- Editability: 5%

When only transcript evidence is available, do not pretend to know visual quality. Mark Visual/Edit Potential as evidence-limited and reduce confidence.

## Ranking safeguards

Apply these safeguards after scoring:

1. **Evidence gate:** Do not rank a candidate highly if its core claim, boundary, or payoff is unsupported by the source.
2. **Context penalty:** Penalize moments that require long unseen setup unless the setup is essential and compact.
3. **Duplicate penalty:** Cluster near-identical moments and keep the strongest version.
4. **Type concentration check:** If several top candidates are near-ties and represent the same type/topic, surface the strongest one and consider the best distinct candidate from another type.
5. **Opportunity-type integrity:** Do not relabel a candidate as Comedy simply because humor makes it easier to rank. Score it according to its actual primary opportunity.
6. **No forced diversity:** Diversity is a review step, not a license to promote weak candidates above clearly stronger ones.
7. **NO-CLIP is valid:** Routine actions, low-information filler, repetitive inventory management, or moments without a usable hook/payoff may be returned as NO-CLIP.

## Quality rules

- Prefer distinct opportunities over repetitive highlights.
- Separate factual claims from inference.
- Flag time-sensitive claims.
- Do not promise virality.
- Do not fabricate engagement metrics.
- Preserve creator voice without copying another creator's identity or scripts.
- If no strong opportunity exists, say NO-CLIP.
- Confidence reflects evidence quality; it is not another version of the score.
- Never claim benchmark precision, recall, or virality unless measured against an explicit evaluation set.
