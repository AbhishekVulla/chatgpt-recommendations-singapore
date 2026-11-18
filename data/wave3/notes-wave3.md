# Notes during wave 3

Observations made after FRAME-wave3.md was saved, all on 18 November 2026 (Singapore time). FRAME-wave3.md
has not been edited since 01:46:19 SGT.

- **When things happened.** T3 volumes pulled 01:45:11 SGT. FRAME-wave3.md saved by 01:46:19. First
  question sent 01:47:16, last answer received 01:55:52. All 200 answers are from 18 November 2026.
- **Model ids.** Every response reports `gpt-5.6-luna` (200 of 200), through OpenAI's Responses API with
  `tools: [{"type": "web_search"}]` and nothing else. Coding: `gpt-5-nano` through Chat Completions,
  extract.py's instruction word for word.
- **Counts.** 4 trades x 5 questions x 10 runs = 200 answers, 200 collected, 0 errors, every response
  status `completed`. 349 web search calls (331 searches, 17 page opens, 1 find in page), 1,116 cited URLs.
  Per trade, 50 answers, ChatGPT only.
- **Refusals and empty answers.** No refusal in any answer. Five answers named no business, all
  property-T3 ("real estate agent singapore", runs 1, 2, 7, 8 and 9): ChatGPT asked whether the person
  wanted to buy, sell or rent and pointed to the CEA public register instead of naming an agency. They
  count in the 50 and name nobody. The exact-text check dropped one name in 200 answers (restaurant-T5
  run 5: the coder returned "Nando's" with a control character in place of the apostrophe, so it did not
  match the answer's text).
- **Leaders, out of 50 ChatGPT answers per trade** (results_wave3.json):

  | Trade | Leader | Answers naming it | Next |
  |---|---|---|---|
  | Property agents | PropNex | 33 | Huttons Asia 29 |
  | Cafes and restaurants | Candlenut | 26 | Burnt Ends 25 |
  | F&B suppliers | Wilmar Distribution | 27 | Bidfood Singapore 25 |
  | Corporate gift companies | Noel Gifts | 35 | Aquaholic Gifts 25 |

- **How firm the leaders are.** Under the frame's looser containment rule the counts barely move:
  PropNex 36, Candlenut 26, Noel Gifts 35, and F&B suppliers ties Bidfood Singapore and Wilmar
  Distribution at 27, so the F&B leader's name depends on the rule while its count, 27, does not.
  Candlenut leads Burnt Ends by one answer. A text search of the coded names finds PropNex in 36
  property answers and ERA in 35: ChatGPT sometimes names an individual agent with the agency
  ("Jeffrey Kwok - PropNex"), and the bare "ERA" is three letters, under names.py's five-letter minimum,
  so it never joins "ERA Realty". PropNex leads on every count. The page prints the study rule's number,
  the same rule as the other eleven trades.
- **What the coder counted as a business.** extract.py's instruction is unchanged, so it keeps what it kept
  in October: hawker centres in restaurant answers (Maxwell Food Centre, 20 answers) and a few supplier
  directories in F&B answers (FoodService.com.sg, FoodSupplier.sg). None of them leads a trade.
- **Concentration, per trade** (top three against all mentions; businesses named in one answer): property
  87 of 213 and 18 of 37; restaurants 73 of 418 and 46 of 92; F&B suppliers 72 of 359 and 41 of 97;
  corporate gifts 84 of 247 and 31 of 61.
- **Cost.** Answers US$4.209 and coding US$0.033, US$4.242 in all, computed from each response's token
  counts at OpenAI's list prices with every one of the 349 search calls priced at US$0.01. If only the 331
  search actions are billed, the answers cost US$0.18 less. The dearest single answer was US$0.048 and
  the dearest round US$0.456; the US$15 stop rule never came close. Volumes: two DataForSEO calls at
  US$0.09 each (the first response was lost to a missing output folder and the call was repeated), both in
  the DataForSEO ledger.
- **Not published as downloads.** On 18 November 2026 the four figures were wired onto rankrhq.com/for
  only, each labelled ChatGPT only and out of 50. The study page and its downloads still describe the
  October waves; nothing from wave 3 is in their totals.
- **Folded into the study page, later on 18 November 2026.** The page now reads as one study, with no
  separate wave 3 section. The four trades now sit in the page's per-trade tables beside the October eleven:
  ChatGPT columns carry their figures and Perplexity cells read "Not asked". Tables that compare the two
  assistants, label citation sources or check Google's results stay at the 11 October trades, because wave 3
  has no Perplexity answers, no hand-labelled domains and no Google captures. Totals rows say which trades
  they cover, and a ChatGPT line over all 15 trades is added where it says something new. The headline
  figures (title, hero, meta description) are unchanged. This replaces the bullet above: the wave 3 files are
  now downloads beside the October ones.
- **Ten-run figures for the four trades, in no frame.** analyze_wave3_full.py applies analyze_wave2.py's
  per-question rules to wave 3 and writes results_wave3_full.json (published as results-wave3.json). Its
  self-check reruns the same code over the October answers and stops unless it reproduces results_wave2.json
  for both assistants; it did. ChatGPT, four trades: first pick changed at least once for 15 of 20 questions
  (no question left out; property-T3 counts with exactly 5 of 10 answers naming a business), the most common
  first pick came first in a median 6 of 10 answers, a median 3 different first picks, and 57 of 421
  business and question pairs were named in 7 or more of the 10 answers. Median first-pick share by trade:
  corporate gifts 70%, the other three 60%. Pooled with ChatGPT's October rows, all 15 trades: changed for
  65 of 74 counted questions (75 asked; maid-T3 is still the one left out), median 5 of 10, median 4
  different first picks, 166 of 1,451 pairs in 7 or more of 10, median first-pick share 55%. The four
  trades' concentration pooled: the top three took 316 of 1,237 mentions, and 136 of 287 businesses were
  named once.
