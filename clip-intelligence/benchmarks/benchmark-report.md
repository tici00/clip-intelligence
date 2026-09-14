# Benchmark Report — v0.3

This directory contains qualitative regression fixtures for Clip Intelligence v0.3. They are not statistically validated performance claims.

## Purpose

Verify that the Skill identifies distinct opportunity types instead of over-prioritizing obvious humor, while preserving evidence grounding, boundary quality, and explicit NO-CLIP behavior.

## Fixtures

### Fictional regression fixture

`benchmarks/fields-of-mistria-live-001.json` was replaced with a fictional Everdawn fixture to avoid publishing user-provided livestream details. It covers Comedy, Personality, Gameplay Progression, Curiosity, Story, Community, Discovery, and NO-CLIP.

### Human-gold fixture

`benchmarks/human-gold/fields-of-mistria-live-002.json` contains 12 human-selected opportunities from the second Fields of Mistria live used during development review.

The gold set is curated, not exhaustive. Its numeric scores are estimated benchmark labels created during review, not scores supplied by the user.

## What the prior blind test revealed

The earlier v0.3 blind review produced approximately 60% precision@5 and 33% recall@10 against the 12 selected human cuts, using event/content overlap as the matching rule. These figures are development diagnostics for that single curated test, not general model metrics.

The main failure modes were:

- over-ranking immediate humor and punchlines;
- under-detecting gameplay progression and meaningful unlocks;
- under-detecting curiosity and open-loop moments;
- under-detecting personality-driven moments without a conventional joke;
- under-detecting community opportunities such as competitions;
- missing discovery and story opportunities that depend on more than a single punchline.

## v0.3 implementation response

The Skill was adjusted to:

1. detect opportunity signals before ranking candidates;
2. explicitly search for progression, curiosity, personality, community, discovery, and story signals;
3. preserve opportunity-type integrity rather than treating humor as a universal proxy;
4. perform a diversity check before final ranking;
5. apply duplicate, evidence, and context safeguards;
6. preserve valid NO-CLIP outcomes;
7. keep the scoring formula stable while improving candidate discovery and type-aware evaluation.

## Evaluation criteria

For a future run against the human-gold set, report:

- **Gold Match Rate:** proportion of gold opportunities represented by at least one output candidate, with the matching rule stated explicitly.
- **Top-K Gold Coverage:** gold opportunities represented within the first K ranked outputs.
- **Opportunity-Type Coverage:** which gold types were recovered or missed.
- **Ranking Quality:** whether recovered gold opportunities appear near the top.
- **NO-CLIP behavior:** whether explicit negatives are correctly identified without suppressing genuine opportunities.
- **Diversity:** distribution of ranked opportunities across types and source sections.

Do not claim statistical generalization, virality, engagement lift, or production accuracy from these fixtures.
