# Benchmark Report — v0.3

This benchmark carries forward the functional Fields of Mistria live benchmark used during development. It is a qualitative regression fixture, not a statistically validated performance claim.

## Purpose

Verify that the Skill can preserve strong comedy detection while broadening discovery toward personality, progression, curiosity, story, community, and discovery opportunities.

## v0.3 evaluation criteria

- Does the output include multiple opportunity types rather than humor only?
- Are content and visual/edit potential kept separate?
- Are timestamps grounded in source evidence?
- Are duplicate moments clustered?
- Are boundaries tightened without removing necessary context?
- Are curiosity/open-loop moments allowed without an immediate punchline?
- Can the system explicitly return NO-CLIP?
- Is confidence separated from score?

## Known development lesson

The earlier blind benchmark showed strong detection of obvious humor but missed several non-comedy opportunities, including gameplay progression, curiosity, personality, discovery, and community moments. v0.3 therefore changes the product objective from generic highlight ranking to opportunity intelligence.

## Guardrail

Do not use this fixture to claim a percentage improvement in real-world virality, recall, or precision. It is intended for functional regression testing against known examples.
