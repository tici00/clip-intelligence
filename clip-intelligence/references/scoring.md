# Scoring Framework

Clip Intelligence v0.3 uses structured scores rather than a single generic highlight score.

## Components

### Content Potential
Measures whether the moment has a compelling idea, emotion, payoff, tension, specificity, or useful information.

### Visual/Edit Potential
Measures observable visual action, reactions, screen changes, game events, framing opportunities, and ease of editing. Do not infer visuals from transcript alone.

### Audience/Goal Fit
Measures fit with the requested audience, platform, niche, and content goal.

### Opportunity-Type Fit
Measures how strongly the candidate matches its selected opportunity type.

### Editability
Measures whether the moment can be turned into a coherent short clip without excessive setup or missing context.

## Default formula

When video evidence exists:

`Final = 0.40 Content + 0.25 Visual/Edit + 0.15 Audience/Goal + 0.15 Type Fit + 0.05 Editability`

All components use a 0–100 scale.

## Confidence

Confidence is separate from the score. High confidence requires strong source evidence and clear boundaries. A high-scoring transcript-only candidate can still have medium or low confidence when visual evidence is unavailable.

## Interpretation

- 90–100: PRIORITY
- 80–89: STRONG
- 70–79: TEST
- 60–69: SECONDARY
- Below 60: NO-CLIP candidate unless a user-specific goal justifies further review

These labels are prioritization guidance, not predictions of virality.

## Boundary optimization

Start at the minimum setup needed to understand the moment. End after the punchline, reveal, result, or meaningful progression. For curiosity, ending at the open loop is acceptable when the unanswered question is the hook.
