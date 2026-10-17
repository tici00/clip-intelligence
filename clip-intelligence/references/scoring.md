# Scoring Framework — v1.1

Clip Intelligence uses structured comparative scores, not a single generic highlight score and not probabilities of success.

## Components

### Content Potential
Measures whether the moment has a compelling idea, emotion, payoff, tension, specificity, progression, discovery, or useful information.

### Visual/Edit Potential
Measures observable visual action, reactions, screen changes, game events, framing opportunities, and ease of editing. Do not infer visuals from transcript alone.

### Audience/Goal Fit
Measures fit with the requested audience, platform, niche, and Creator Goal Mode. If no goal is provided, use Balanced Discovery.

### Opportunity-Type Fit
Measures how strongly the candidate matches its selected opportunity type. This prevents generic humor from automatically outranking strong non-comedy opportunities.

### Editability
Measures whether the moment can be turned into a coherent short clip without excessive setup or missing context.

### Standalone Clarity (separate diagnostic)
Rate how well a viewer unfamiliar with the source can understand the candidate:
- High: situation and payoff are understandable with minimal framing.
- Medium: a short lead-in, caption, or key visual is needed.
- Low: substantial unseen context is required.

Standalone Clarity is a diagnostic, not an extra hidden weight. Use it to explain context requirements and compare otherwise similar candidates.

## Default formula

When video evidence exists:

Final = 0.40 Content + 0.25 Visual/Edit + 0.15 Audience/Goal + 0.15 Type Fit + 0.05 Editability

All numeric components use a 0–100 scale.

When only transcript evidence is available, Visual/Edit Potential must be marked evidence-limited. Do not invent a numeric visual score from transcript-only evidence. If a numeric final score is requested, label it transcript-only and not directly comparable to a video-verified score.

The formula is intentionally stable. Do not change weights without a controlled comparison.

## Score transparency

Scores are structured judgments for ranking candidates within the source and goal. They are not calibrated probabilities, virality predictions, or measured engagement forecasts. A score of 90 does not mean a 90% chance of success.

Labels:
- 90–100: PRIORITY
- 80–89: STRONG
- 70–79: TEST
- 60–69: SECONDARY
- Below 60: usually NO-CLIP unless a user-specific goal gives a supported reason to review it

These bands are prioritization guidance, not empirically calibrated thresholds unless an evaluation explicitly demonstrates that.

## Candidate quality gate

Before calculating the final score, test whether the candidate has at least two strong signal groups, including at least one of Hook, Value, or Change:

- Hook: question, contradiction, strong opinion, surprise, reaction, or tension.
- Value: useful discovery, explanation, comparison, tip, or information.
- Change: unlock, milestone, reveal, consequence, or meaningful outcome.
- Emotion/Personality: strong reaction, recognizable preference, unusual behavior, or creator-specific perspective.
- Participation: debate, choice, competition, vote, or invitation to comment.

A candidate with only a single weak signal should not become a strong clip simply because one score dimension was generous. Mark it NO-CLIP or low priority.

## Anti-false-positive adjustment

After component scoring, perform a separate clipability check:
- Is there a clear hook within the first practical seconds?
- Does the viewer gain information, emotion, progression, story, curiosity, or participation value?
- Can the moment stand alone with limited context?
- Is there a meaningful payoff or intentional open loop?
- Is it more than routine gameplay, filler, or an isolated sentence?

If mostly no, downgrade or mark NO-CLIP even when raw component scores are moderate. Confidence is separate: confidence measures evidence quality; clipability measures whether the moment is worth clipping.

## Type-specific scoring emphasis

| Type | Strongest signals |
|---|---|
| Comedy | punchline, reaction, payoff, editability, personality |
| Personality | specificity, creator perspective, relevance, comment potential |
| Gameplay Progression | meaningful progress, hook, visual evidence, discovery, consequence |
| Curiosity | hook, open loop, specificity, emotion, comments |
| Story | narrative completeness, escalation, emotion, stakes, context independence |
| Community | participation, debate, competition, personality, comment potential |
| Discovery | discovery value, hook, specificity, visual support, usefulness |

A candidate should not score highly merely because it is funny if another type better describes its value.

## Ranking safeguards

After scoring:
1. Apply evidence and context gates.
2. Apply the candidate quality gate and clipability check.
3. Cluster duplicates and overlapping versions.
4. Apply the selected goal mode.
5. Review type concentration without forcing weak diversity.
6. Prefer stronger evidence, lower context dependency, distinct topic/type coverage, and cleaner boundaries for near-ties.
7. Never force a weak candidate into the primary shortlist solely to satisfy a requested count.

## Boundary optimization

For each primary recommendation, explain why the start is the earliest useful point and why the end preserves the payoff, result, or intentional open loop without unnecessary tail. Alternate shorter boundaries must describe what is preserved and what is sacrificed.

## Benchmarking

When a human-gold set is available, report:
- Gold Match Rate with an explicit matching rule.
- Top-K Gold Coverage.
- Opportunity-Type Coverage.
- Ranking Quality.
- Boundary and Standalone Clarity quality.
- NO-CLIP behavior and non-gold candidate quality.

Keep gold recovery and non-gold quality separate. Do not claim statistical generalization, virality, engagement lift, or production accuracy from curated fixtures.