# Full-Live Audit — Fields of Mistria Live 002

## Scope

This is a qualitative full-live audit of the second user-provided Fields of Mistria livestream transcript against Clip Intelligence v0.3's Opportunity Intelligence design.

It is a manual source-grounded review, not an execution of the Skill runtime and not statistical validation.

## Evaluation question

After broadening candidate discovery beyond humor, does the v0.3 logic surface strong opportunities across different functions without simply promoting every unusual line?

## Candidate audit

| # | Approx. window | Candidate | Primary type | Assessment | Gold overlap |
|---|---|---|---|---|---|
| 1 | 00:05:09–00:05:20 | New growth spell / instant plant growth | Gameplay Progression | PRIORITY | Gold 11 |
| 2 | 00:05:29–00:06:05 | Returning memories / dragon portal mystery | Curiosity | STRONG | Gold 10 |
| 3 | 00:06:18–00:06:37 | Silver tools / “I make my own” | Personality | STRONG | Gold 9-adjacent |
| 4 | 00:13:13–00:13:38 | What the game lets you do | Discovery | TEST | Additional |
| 5 | 00:15:12–00:15:32 | Expected 3x3 watering vs energy limitation | Discovery | TEST | Additional |
| 6 | 00:21:25–00:22:33 | Fields of Mistria vs Stardew Valley | Discovery | STRONG | Additional |
| 7 | 00:26:51–00:27:13 | Silver artifact donated to museum | Personality | STRONG | Gold 9 |
| 8 | 00:27:34–00:28:05 | Mobile availability / platform comparison | Discovery | TEST; time-sensitive | Additional |
| 9 | 00:29:08–00:29:16 | Unexpected chest during exploration | Discovery | TEST | Additional |
| 10 | 00:34:58–00:35:19 | Why creator prefers Mistria to Stardew | Personality | STRONG | Additional; related to #6 |
| 11 | 00:35:19–00:36:00 | Skill-tree bonuses and crafting effects | Discovery | TEST | Additional |
| 12 | 00:37:31–00:38:13 | Forgotten memories / skill unlock discussion | Curiosity | STRONG | Additional |
| 13 | 00:38:33–00:39:07 | Silver smithing specialization | Gameplay Progression | STRONG | Additional |
| 14 | 00:39:39–00:40:45 | Check-up, amputation threat, grain-bag injury | Comedy | PRIORITY | Gold 1 |
| 15 | 00:45:50–00:45:58 | Frederick and the pantyhose comment | Comedy | PRIORITY | Additional |
| 16 | 00:46:08–00:46:20 | “Money doesn't buy happiness” / creator reaction | Personality | STRONG | Additional |
| 17 | 00:53:42–00:54:48 | Rooster / mortal fragility joke | Comedy | STRONG | Gold 12 |
| 18 | 00:59:40–01:01:39 | Creature refuses to die / combat escalation | Comedy | STRONG | Additional |
| 19 | 01:02:41–01:04:03 | Seriously square / round rocks | Comedy | STRONG | Additional |
| 20 | 01:14:19–01:15:31 | Staircase / swearing and frustration | Comedy | TEST | Additional |
| 21 | 01:15:58–01:16:31 | Fire seal broken / fire tablet | Gameplay Progression | STRONG | Gold 5 |
| 22 | 01:17:12–01:17:47 | Queen Maple succession and death threat | Story | PRIORITY | Gold 4 |
| 23 | 01:19:03–01:19:44 | Board game / flower piece / joke comment | Curiosity | STRONG | Gold 8 |
| 24 | 01:23:43–01:24:46 | Rare sealing scroll / “it's legal” | Discovery | STRONG | Gold 3 |
| 25 | 01:33:43–01:35:17 | Autumn clothes / personal color palette | Personality | STRONG | Gold 6 |
| 26 | 01:46:18–01:49:14 | Fruit competition / desire for first place | Community | STRONG | Gold 7 |
| 27 | 01:53:18–01:54:26 | Expensive scroll / kidney joke | Comedy | PRIORITY | Gold 2 |

## What this audit shows

### Strong additional opportunities outside the 12 gold cuts

The review found several credible candidates that were not part of the human-selected gold set, especially:

- Fields of Mistria vs Stardew Valley comparison.
- Frederick / pantyhose reaction.
- Money / happiness reaction.
- Creature combat escalation.
- Seriously square / round rocks running gag.
- Mobile/platform discussion, with a time-sensitive-claim flag.
- Silver smithing specialization.

This matters because a benchmark that only rewards the 12 known cuts can encourage overfitting to the gold list.

### Diversity

The candidate pool contains all seven v0.3 opportunity types:

- Comedy
- Personality
- Gameplay Progression
- Curiosity
- Story
- Community
- Discovery

The strongest candidates are not concentrated exclusively in Comedy. The source contains credible high-value opportunities in progression, story, personality, curiosity, community, and discovery.

### Duplicate / clustering observations

The Stardew comparison appears in more than one section of the live. These should be clustered when they serve the same hook, while preserving a later version if it adds a materially stronger opinion or payoff.

The pergaminho appears as a story/discovery setup around 01:23–01:26 and later as a price/comedy payoff around 01:53. These should NOT automatically be merged: they represent different hooks and different clip functions.

The silver-related moments also recur. Tool preference is personality-driven, while the museum artifact is a separate decision/reaction opportunity.

## Precision risk

The broadened detector must not treat every:

- game mechanic explanation,
- inventory decision,
- routine task,
- ordinary reaction,
- or factual platform statement

as a strong clip merely because it belongs to a supported opportunity type.

The strongest protection is the combination of opportunity-type fit, hook strength, specificity, context independence, editability, and explicit NO-CLIP behavior.

## Current conclusion

The v0.3 design appears materially better suited to this live than the previous highlight-centric approach. It can represent the 12 human-selected cuts while also surfacing credible additional opportunities.

The next quantitative step should be a real Agent execution producing a fixed ranked list, followed by blind matching against the 12 gold opportunities and a separate quality review of the non-gold candidates. Until that execution exists, no precision/recall improvement should be claimed as a measured result.
