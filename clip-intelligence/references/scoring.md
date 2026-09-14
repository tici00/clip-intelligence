# Scoring Framework

Clip Intelligence v0.3 uses structured scores rather than a single generic highlight score.

## Components

### Content Potential
Measures whether the moment has a compelling idea, emotion, payoff, tension, specificity, progression, discovery, or useful information.

### Visual/Edit Potential
Measures observable visual action, reactions, screen changes, game events, framing opportunities, and ease of editing. Do not infer visuals from transcript alone.

### Audience/Goal Fit
Measures fit with the requested audience, platform, niche, and content goal.

### Opportunity-Type Fit
Measures how strongly the candidate matches its selected opportunity type. This prevents generic humor from automatically outranking strong non-comedy opportunities.

### Editability
Measures whether the moment can be turned into a coherent short clip without excessive setup or missing context.

## Default formula

When video evidence exists:

`Final = 0.40 Content + 0.25 Visual/Edit + 0.15 Audience/Goal + 0.15 Type Fit + 0.05 Editability`

All components use a 0–100 scale.

The formula is intentionally stable in v0.3. The main improvement is **better candidate discovery and type-aware evaluation**, not arbitrary weight changes.

## Candidate quality gate

Before calculating the final score, test whether the candidate has at least two strong signal groups, including at least one of Hook, Value, or Change:

- Hook: question, contradiction, strong opinion, surprise, reaction, or tension.
- Value: useful discovery, explanation, comparison, tip, or information.
- Change: unlock, milestone, reveal, consequence, or meaningful outcome.
- Emotion/Personality: strong reaction, recognizable preference, unusual behavior, or creator-specific perspective.
- Participation: debate, choice, competition, vote, or invitation to comment.

A candidate with only a single weak signal should not become a strong clip simply because one score dimension was generous. Mark it NO-CLIP or low priority.

## Anti-false-positive adjustment

After component scoring, perform a separate **clipability check**:

- Is there a clear hook within the first practical seconds?
- Does the viewer gain information, emotion, progression, curiosity, story, or participation value?
- Can the moment stand alone with limited context?
- Is there a meaningful payoff or intentional open loop?
- Is the candidate more than routine gameplay, filler, or an isolated sentence?

If the answer is mostly no, downgrade the candidate or mark NO-CLIP even when raw component scores are moderate.

This check is intentionally separate from confidence: confidence measures evidence quality; clipability measures whether the moment is actually worth clipping.

## Type-specific scoring emphasis

The components remain the same, but their interpretation changes by opportunity type:

| Type | Strongest signals |
|---|---|
| Comedy | punchline, reaction, payoff, editability, personality |
| Personality | specificity, creator perspective, relevance, comment potential |
| Gameplay Progression | meaningful progress, hook, visual evidence, discovery, consequence |
| Curiosity | hook, unanswered question, specificity, emotion, comments |
| Story | narrative completeness, escalation, emotion, stakes, context independence |
| Community | participation, debate, competition, personality, comment potential |
| Discovery | discovery value, hook, specificity, visual support, usefulness |

A candidate should not receive a high score merely because it is funny if another type better describes its value.

## Confidence

Confidence is separate from the score. High confidence requires strong source evidence and clear boundaries. A high-scoring transcript-only candidate can still have medium or low confidence when visual evidence is unavailable.

## Interpretation

- 90–100: PRIORITY
- 80–89: STRONG
- 70–79: TEST
- 60–69: SECONDARY
- Below 60: NO-CLIP candidate unless a user-specific goal justifies further review

These labels are prioritization guidance, not predictions of virality.

## Candidate discovery vs. ranking

Do not use the final score as the only mechanism for discovering candidates. First build a broad candidate pool from opportunity signals, then score and rank it.

The candidate pool should include plausible moments for all seven opportunity types when the source provides evidence for them. This is especially important for progression, curiosity, personality, community, and discovery moments that may lack an immediate punchline.

## Ranking safeguards

After scoring:

1. Apply evidence and context gates.
2. Apply the candidate quality gate and clipability check.
3. Cluster duplicates and overlapping versions.
4. Run the type concentration check.
5. If multiple candidates are close in score, prefer the candidate that adds distinct opportunity/topic coverage when quality remains strong.
6. Never force a weak candidate into the ranking solely to satisfy diversity.

## Boundary optimization

Start at the minimum setup needed to understand the moment. End after the punchline, reveal, result, or meaningful progression. For curiosity, ending at the open loop is acceptable when the unanswered question is the hook. For progression, preserve the meaningful unlock/reward/consequence when it is required to understand why the moment matters.

## Benchmarking

When a human-gold set is available, report at minimum:

- Gold Match Rate: proportion of gold opportunities represented by at least one output candidate, using an explicitly stated matching rule.
- Top-K Gold Coverage: gold opportunities represented within the first K ranked outputs.
- Opportunity-Type Coverage: which gold types were recovered or missed.
- Ranking Quality: whether recovered gold opportunities appear near the top.
- NO-CLIP behavior: whether explicit negatives are avoided or correctly marked.
- Non-gold Quality: whether additional candidates are genuinely clip-worthy rather than merely unusual.

Keep gold recovery and non-gold quality separate. Do not optimize against the gold set during the same evaluation run.

Do not describe these as model performance guarantees. They are benchmark measurements for the supplied evaluation set.
