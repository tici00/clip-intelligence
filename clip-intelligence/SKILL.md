---
name: clip-intelligence
description: Identify, rank, and optimize short-form content opportunities from long-form creator content.
---

# Clip Intelligence v0.3

## Purpose

Turn long-form content into an **opportunity map**, not just a list of obvious highlights. Analyze timestamped transcripts and, when available, video evidence to find moments worth turning into short-form content.

The system must optimize for **opportunity diversity, evidence quality, and usefulness**, not only immediate humor or punchlines.

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
2. Segment the content into a **broad candidate pool**. Do not rank while discovering.
3. Detect opportunity signals before ranking. Look for punchlines, strong reactions, opinions, specific observations, questions, reveals, unlocks, milestones, discoveries, conflicts, competitions, audience-facing statements, surprising outcomes, and narrative escalation.
4. Classify each candidate with one primary and optional secondary opportunity type.
5. Apply the **candidate quality gate** before scoring. Reject or mark NO-CLIP candidates that lack a usable hook, meaningful information/emotion/progression, or sufficient evidence.
6. Score **Content Potential** separately from **Visual/Edit Potential**.
7. Evaluate audience/goal fit, editability, context dependency, payoff or open loop, specificity, and comment potential as appropriate to the opportunity type.
8. Cluster overlapping candidates and avoid returning several versions of the same moment unless they have materially different hooks, payoffs, or clip functions.
9. Optimize boundaries: remove unnecessary setup, preserve enough context, and end after the punchline/reveal/result. Curiosity candidates may intentionally end on an open loop; progression candidates should include the meaningful unlock, reward, result, or consequence when needed.
10. Explicitly identify NO-CLIP moments when evidence does not support a worthwhile short-form opportunity.
11. Run a **diversity check before final ranking**. If one opportunity type dominates the top results, re-check the source for strong candidates from other types before finalizing. Do not force weak diversity merely to fill categories.
12. Produce the final ranking using the deterministic output rules below.

## Candidate quality gate

A candidate should normally satisfy **at least two** of these signal groups, with at least one being Hook, Value, or Change:

- **Hook:** immediate question, contradiction, strong opinion, surprising statement, reaction, or tension.
- **Value:** useful discovery, explanation, comparison, tip, or information viewers can understand.
- **Change:** unlock, milestone, reveal, consequence, outcome, or meaningful state change.
- **Emotion/Personality:** strong reaction, recognizable preference, unusual behavior, or creator-specific perspective.
- **Participation:** debate, choice, competition, vote, or explicit invitation for viewers to weigh in.

Do not promote a candidate merely because it contains an unusual sentence, a game mechanic, or a reaction. Routine actions, generic commentary, low-information explanations, and ordinary transitions should default to NO-CLIP unless a second strong signal makes them meaningfully useful.

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
Prioritize meaningful progress, hook, visual potential, discovery, relevance, and consequence.

### Curiosity
Prioritize hook, unanswered question/open loop, specificity, emotion, and comment potential. Do not require an immediate payoff.

### Story
Prioritize narrative completeness, escalation, emotion, hook, stakes, and context independence.

### Community
Prioritize participation, debate, competition, personality, relevance, specificity, and comment potential.

### Discovery
Prioritize discovery value, hook, specificity, visual support, usefulness, and relevance.

## Output contract

Return the following sections in this order:

1. **Source Summary**
2. **Opportunity Map** — one compact subsection per opportunity type with the strongest observed candidates, including types that do not make the final top ranking.
3. **Ranked Candidates** — default to the top 10 unless the user requests another K.
4. **NO-CLIP / Low-Value Findings** — include representative false-positive/routine moments when evidence supports them.
5. **Diversity Check**
6. **Benchmark Comparison** — only when a human-gold set is supplied.

For every ranked candidate, return exactly these fields:

- Rank
- Primary Type
- Secondary Type (if any)
- Timestamp
- Duration
- Hook
- Content Potential (0–100)
- Visual/Edit Potential (0–100 or `evidence-limited`)
- Audience/Goal Fit (0–100)
- Opportunity-Type Fit (0–100)
- Editability (0–100)
- Final Opportunity Score (0–100)
- Confidence (`high`, `medium`, or `low`)
- Why it works
- Required context
- Payoff or Open Loop
- Recommended edit
- Alternate shorter boundary
- Evidence note

Do not add invented engagement metrics or unsupported certainty.

## Ranking and tie-breaking

Use 0–100 scores. Treat scores as structured judgment, not guarantees of virality.

When candidates are within **2 points** of each other after scoring, prefer the candidate that:
1. has stronger evidence,
2. has lower context dependency,
3. adds distinct topic/type coverage,
4. has a cleaner boundary.

Do not use diversity as a reason to overtake a clearly stronger candidate.

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
2. **Signal gate:** Candidates failing the candidate quality gate should be NO-CLIP or low priority.
3. **Context penalty:** Penalize moments that require long unseen setup unless the setup is essential and compact.
4. **Duplicate penalty:** Cluster near-identical moments and keep the strongest version.
5. **Type concentration check:** If several top candidates are near-ties and represent the same type/topic, surface the strongest one and consider the best distinct candidate from another type.
6. **Opportunity-type integrity:** Do not relabel a candidate as Comedy simply because humor makes it easier to rank. Score it according to its actual primary opportunity.
7. **No forced diversity:** Diversity is a review step, not a license to promote weak candidates above clearly stronger ones.
8. **NO-CLIP is valid:** Routine actions, low-information filler, repetitive inventory management, or moments without a usable hook/payoff may be returned as NO-CLIP.
9. **Time-sensitive claims:** Flag claims whose truth may change over time, especially platform availability, pricing, releases, or product features.
10. **Transcript/video agreement:** When both are available, use the transcript for what was said and the video for what was visibly/aurally observable. Do not let one source silently invent evidence for the other.

## Benchmark mode

When a human-gold set is available, keep the model's ranked output fixed before comparing it to the gold set. Do not use the gold labels to retroactively improve the ranking in the same run.

Report matching using an explicit rule, such as semantic event overlap plus timestamp overlap where timestamps are available. Keep **gold recovery** separate from **non-gold candidate quality**.

Never claim benchmark precision, recall, or virality unless measured against an explicit evaluation set.

## Quality rules

- Prefer distinct opportunities over repetitive highlights.
- Separate factual claims from inference.
- Flag time-sensitive claims.
- Do not promise virality.
- Do not fabricate engagement metrics.
- Preserve creator voice without copying another creator's identity or scripts.
- If no strong opportunity exists, say NO-CLIP.
- Confidence reflects evidence quality; it is not another version of the score.
