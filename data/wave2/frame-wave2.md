# Wave 2: seven more asks of every question

Written and saved 6 October 2026 before the first wave 2 question is sent. FRAME.md is unchanged;
this file only adds runs. Anything learned during wave 2 goes in NOTES.md, dated.

## Why

Wave 1 asked each of the 55 questions three times per engine. Three asks can show that the first
pick moves, but not how often any one business comes up. Ten asks can: "named in 7 of 10 asks" is a
share a business owner can track over time. That share is the measure wave 2 adds.

## What changes

- Runs 4 to 10 for the same 55 questions, on the same two engines, with the same models and request
  bodies as wave 1 (`run.py`, unchanged except a `--first` argument so it starts at run 4).
- Rounds as before: all 55 questions on both engines per round, so a budget stop leaves whole rounds.
- Stop rule unchanged: do not start a round with less than US$2.40 of credit left. Budget for wave 2
  is about US$12 of the US$16.40 left on the key on 6 October 2026.
- Coding unchanged: `extract.py`, the same exact-text check, the same name matching, the same
  domain labels (new domains get labelled by the same rules and the same hand review).

## What is reported

Wave 1 figures stay as published; they describe runs 1 to 3. Wave 2 adds, over all ten runs:

1. **First-pick share.** For each question and engine, the share of the ten answers whose first
   business is the most common first business for that question. Reported per engine as the median
   across questions, with the full distribution.
2. **Distinct first picks.** For each question and engine, how many different businesses were named
   first across ten asks.
3. **Share of asks per business.** For each question and engine, how many of the ten answers named
   each business. Reported as the number of business and question pairs named in at least 7 of 10
   asks, in 4 to 6, and in 1 to 3.
4. **Concentration.** The wave 1 concentration figure (top three per trade against all mentions,
   businesses named once) recomputed over all ten runs, so the two can be compared.

## What this still allows to be wrong

- Wave 2 runs about an hour after wave 1, on the same night. It is not a test of change over days.
- Ten asks is still a small sample per question; per-question shares are descriptive.
- Everything in FRAME.md's limits still applies: API, not the app; English only; one city town.
