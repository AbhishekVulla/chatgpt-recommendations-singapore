# Wave 3: four more trades, ChatGPT only

Written and saved 18 November 2026 (Singapore time) before the first wave 3 question is sent. FRAME.md
and FRAME-wave2.md are unchanged; this file only adds trades. Anything learned during wave 3 goes in
NOTES-wave3.md, dated.

## Why

rankrhq.com/for lists four trades that were not in the study: property agents, cafes and restaurants,
F&B suppliers and corporate gift companies. Their rows show no study number. Wave 3 asks the same five
questions for each of them, ten times, so each row can carry the same figure the other rows carry: how
many of the trade's answers named its most-named business. "Clinics and AI search" is also on /for but
is not a trade, so it is left out.

## What is the same

- The five templates T1 to T5 from FRAME.md, word for word, Tampines as the fixed town in T5.
- The ChatGPT model, `gpt-5.6-luna`, with OpenAI's own web search on, asked alone: no system prompt, no
  conversation history, no location.
- Ten asks of every question (runs 1 to 10), sent in rounds: every question once per round, so a budget
  stop leaves whole rounds.
- Coding: `gpt-5-nano` with extract.py's instruction, word for word, and extract.py's exact-text check, so
  the model can drop a name but never add one.
- Analysis: names.py's matching (prefix rule) and analyze_wave2.py's leader rule: for each trade, the
  business named in the most answers, out of all the trade's answers.

## What is different, and why

- **ChatGPT only.** No Perplexity key exists on 18 November 2026, so each trade has 5 questions x 10 asks =
  50 answers, not 100. Every place these numbers appear says ChatGPT only and out of 50. They are never
  added to the 11-trade totals or the headline figures.
- **OpenAI's API directly, not OpenRouter.** The OpenRouter key on hand is free tier and cannot reach these
  models. Request: Responses API, `{"model": "gpt-5.6-luna", "tools": [{"type": "web_search"}], "input":
  <question>}`, nothing else, so search settings stay at OpenAI's defaults, as OpenRouter's `plugins: web,
  engine: native` left them. Extraction: Chat Completions, `gpt-5-nano`, `reasoning_effort: low`,
  `response_format: json_object`, as extract.py sent it.
- **T3 volumes from DataForSEO, not Ahrefs.**
  Google Ads search volume, Singapore, pulled through DataForSEO on 18 November 2026 at 01:45 SGT
  (`volumes_wave3.py`, `wave3/volumes.json`). Same rule as FRAME.md: the highest-volume candidate that
  contains "singapore". Google Ads reports close variants with one shared volume, so ties happen; a tie
  goes to the form the trade's rankr article quotes as a search most often, then to the form closest to
  {provider}.
- **One date, six weeks later.** The original trades were asked on 5 and 6 October 2026. Wave 3 is asked
  on 18 November 2026. The model id is the same; what it finds on the web may not be.

## Trades

{provider} wording comes from the trade's rankr article and, where the article uses two words for the
trade, from what Singapore searchers type (the volumes below).

| Trade (/for row) | {provider} / {providers} | T3 keyword | SG volume |
|---|---|---|---|
| Property agents | property agent / property agents | real estate agent singapore | 720 |
| Cafes and restaurants | restaurant / restaurants | restaurant singapore | 22,200 |
| F&B suppliers | food supplier / food suppliers | food supplier singapore | 170 |
| Corporate gift companies | corporate gift supplier / corporate gift suppliers | corporate gifts singapore | 4,400 |

Why each wording:

- **Property agents.** The article (/blog/seo-for-property-agents-singapore) says "property agent"
  throughout. "property agent singapore" has 50 searches a month; "real estate agent singapore" has 720,
  tied with "real estate agency singapore". The article quotes neither; "agent" is closer to {provider}.
- **Cafes and restaurants.** The article (/blog/seo-for-cafes-restaurants-singapore) is titled "Restaurant
  SEO in Singapore" and says restaurant 38 times to cafe 5. "restaurant singapore" and "restaurants
  singapore" tie at 22,200; the article quotes neither, and the singular is {provider}'s form.
- **F&B suppliers.** The article (/blog/seo-for-fnb-suppliers-singapore) says "F&B suppliers" in its
  title and "food supplier", "wholesaler" and "distributor" in its body. Searchers type "food supplier
  singapore" (170) far more than "f&b supplier singapore" (10), so {provider} is "food supplier". "food
  supplier singapore", "food suppliers singapore" and "food distributor singapore" tie at 170; the
  article quotes none of them, and "food supplier singapore" is {provider}'s form.
- **Corporate gift companies.** The article (/blog/seo-for-corporate-gift-companies-singapore) calls the
  trade "corporate gift suppliers" in its body (supplier 13 times, company twice), and "corporate gift
  supplier singapore" (390) beats "corporate gift company singapore" (30). "corporate gifts singapore"
  and "corporate gift singapore" tie at 4,400; the article quotes the plural three times and the
  singular once.

Candidate keywords checked (36), with volumes, are in `wave3/volumes.json`.

## Budget and stop rule

At most US$15 on the OpenAI key for answers and coding together. Cost is computed from each response's
token counts at OpenAI's published prices for 18 November 2026 (gpt-5.6-luna US$0.20 input, US$0.02
cached input, US$1.20 output per million tokens; web search US$10 per thousand calls; gpt-5-nano US$0.05,
US$0.005 and US$0.40) and logged after every answer. A round is not started if the spend so far plus
the most expensive round so far (US$1.50 before the first one) would pass US$15.

## What is reported

Per trade, out of its 50 answers: the business named in the most answers (the leader), how many answers
named it, the runner-up counts, the number of distinct businesses, and answers that named no business,
counted and kept. Also per trade: the businesses' share of all mentions (top three against all), and
businesses named once.

## What this still allows to be wrong

- Everything in FRAME.md's limits: the API is not the app, English only, one fixed town.
- 50 answers from one assistant is half the original trades' sample, and the original rows' 100 includes
  Perplexity's 50. The two kinds of row are not a like-for-like comparison and are not presented as one.
- DataForSEO's volumes are Google Ads ranges, not Ahrefs' clickstream estimates; a different source could
  have picked a different T3 keyword.
