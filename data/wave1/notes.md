# Notes during the run

Observations made after the frame was frozen, all on 5 October 2026. Each one says whether it
changed anything. FRAME.md itself has not been edited since it was saved.

- **When things happened.** FRAME.md was saved at 23:18:09 SGT. The first question was sent at
  23:18:43 SGT and the last answer arrived at 23:28 SGT, so all 330 answers are from 5 October 2026.
  The frame's header says "23:20 SGT" and its limitations say "5 and 6 October 2026": both were
  estimates typed before the run. The file's own save time and the timestamps in `raw/` are the
  record; FRAME.md is left unedited so that its save time stays evidence that it came first.
- **No AI Overviews.** Ahrefs SERP Overview returned no `ai_overview` position for any of the 11 T3
  keywords (captures 11 August to 5 October 2026). Every one returned a local pack of three
  businesses. Checked live in a logged-in Chrome on google.com, Singapore, on 5 October 2026:
  "aircon servicing singapore", "dental clinic singapore" and "lawyer singapore" showed sponsored
  results and a business map, and the page text contained no "AI Overview". The frame's Google AI
  Overview source mix therefore has nothing to count. Reported as a finding, not dropped. Google's
  organic top 10 is classified with the same rules instead, as a comparison.
- **Name matching: "starts with" instead of "contains".** Containment let a generic name ("SG
  Interior Design", cleaned to "interiordesign") chain unrelated firms into one business. Every name
  result is also computed under the frame's containment rule and published as
  `sensitivity_contains_rule`. The headline figures move by at most 2 points between the two.
- **Rule precedence for citations,** which the frame's table left implicit: forum or social, then
  government, then best-of list, then the domain's label. A Reddit thread titled "best movers?"
  counts as forum, not as a best-of list.
- **Domain labels.** Domains that matched a business named in the same trade were labelled
  "Business website" by rule. The 280 the rules could not settle were drafted by
  `openai/gpt-5.4-mini` from domain, title and URL (`domain_labels_draft.json`). Every label was then
  read by hand; the corrections are listed in `label_final.py`. healthhub.sg and chas.sg are
  labelled Government by hand: both are Ministry of Health services on domains that do not end in
  gov.sg. 29 domains in Google's top 10 that no assistant cited were labelled by hand
  (`GOOGLE_ONLY` in `label_final.py`).
- **Hand check of name extraction.** 20 answers (every 16th coded file, listed in
  `handcheck_sample.json`), 10 per engine, read in full against the extracted list: 99 names, none
  missed, none invented. Three borderline names were kept because the answer offers them as the
  place to book: Helpling, "Motorist Authorised Workshops" and "SingHealth polyclinics". Outside the
  sample, checking the map-pack result surfaced one wrong name: "Carros Centre", a building, listed
  as a car workshop in one answer (openai car-T1 run 2).
- **Map pack check.** For each of the 15 map-pack businesses counted as never named, the raw answer
  text of all 30 answers in its trade was searched for its distinctive word. None appeared. Two
  near-hits were different businesses ("A.M Aesthetics" against "M-Aesthetic Clinic"; "Carros
  Centre" against "Carro Care").
- **Budget.** The three rounds cost US$5.02 through OpenRouter, the name extraction US$0.06 and the
  domain drafts under US$0.10. No round was stopped early; 330 of 330 answers were collected.
- **Wave 2 (6 Oct 2026).** FRAME-wave2.md saved 01:19:47 SGT; answers sent 01:20 to 01:41 SGT. Runs 4 to 10: 770 answers, 0 errors,
  US$12.02, US$5.45 left on the key. Names coded with extract.py (US$0.14). Ten-run figures in
  results_wave2.json: ChatGPT's most common first pick appeared in a median 5 of 10 answers, with a
  median 4 different first picks; Perplexity 9 of 10 and 2. Not yet on the published page, which
  still reports wave 1 (runs 1 to 3); analyze.py and publish.py are pinned to runs 1 to 3.
- **Wave 2 on the page (6 Oct 2026).** This supersedes the last sentence of the entry above.
  analyze.py is still pinned to runs 1 to 3, and every wave 1 file is published byte for byte as
  before. analyze_wave2.py keeps every figure it wrote and adds: same first pick every time and
  changed at least once, per engine; the median count out of ten behind the median share; one row
  per question; the most-named businesses split by engine; when runs 4 to 10 were sent and what
  they cost; the map-pack check below; and the worked example. publish.py adds
  answers-full-wave2.jsonl, answers-wave2.csv, results-wave2.json and frame-wave2.md.
- **"Same first pick every time" (6 Oct 2026).** A question counts when at least five of its ten
  answers named a business: 54 for ChatGPT (maid-T3 named one in three answers) and 55 for
  Perplexity. An answer that named no business has no first pick and is left out. On that rule
  ChatGPT kept one first pick for 4 of 54 questions and Perplexity for 20 of 55. One of Perplexity's
  20, lawyer-T2, has nine answers naming a business, all with Allen & Gledhill first, and one naming
  none; requiring all ten answers gives 4 and 19. The page prints the other side: the first pick
  changed at least once for 50 of 54 and 35 of 55.
- **Median share (6 Oct 2026).** FRAME-wave2.md defines the first-pick share out of "the ten
  answers"; analyze_wave2.py divides by the answers that named a business. The medians agree either
  way, 0.5 for ChatGPT and 0.9 for Perplexity, which the page prints as 5 and 9 of 10 answers.
- **Map pack over ten runs, a check added after FRAME-wave2.md was written (6 Oct 2026).** That
  frame does not list it. analyze.py's map-pack block, with the same matching (prefix clusters and
  names.same), rerun over all 1,100 answers: 14 of 33 never matched, against 15 in runs 1 to 3. The
  one that changed is M-Aesthetic Clinic, named by Perplexity in aesthetic-T3 in each of runs 4 to 10
  (7 answers). The wave 1 text search, repeated over all 100 answers in each trade, found two of the
  14 named in a form the matching cannot join. ChatGPT named "Emergency Dental by Ashford Dental" in
  dental-T3 runs 6 and 8, citing emergencydental.sg, whose footer reads Ashford Dental Centre and
  whose address, 215 Upper Thomson Rd, Thomson Ridge, is Ashford Dental Centre Thomson's. Perplexity
  named "Koh Management" in accounting-T4 run 4, citing shkoh.com.sg, Koh Management Pte Ltd; Ahrefs'
  6 September 2026 capture of that map pack titles the listing "Koh Mgmt | Affordable Corporate
  Secretarial Services Singapore | GST Bookkeeping Accounting Services". Neither appears in runs 1 to
  3, so wave 1's 15 of 33 stands. Counted by hand, 12 of 33 were never named in 1,100 answers. The
  only other text hits were "Carros Centre", the building noted above. The page prints both counts;
  every hit and verdict is in results_wave2.json under map_pack.text_check.
- **Citations from runs 4 to 10 (6 Oct 2026).** FRAME-wave2.md says new domains get the same rules
  and the same hand review. The hand review has not been done: 320 of the 9,142 citations in runs 4
  to 10 point at one of 186 domains that no rule settles and no hand pass has labelled.
  answers-full-wave2.jsonl marks them "Not labelled" so they do not fall through to "Other". No wave
  2 figure uses citation labels.
- **Worked example (6 Oct 2026).** The page shows ChatGPT's ten first picks for aircon-T1, one of
  seven ChatGPT questions where no business came first more than twice, and sets it beside the
  median question, whose most common first pick came first in 5 of 10 answers.
- **The twelve never-named map businesses, searched for everywhere (6 Oct 2026).** The text check above
  read each business's own trade, 100 answers. Searched again across the text of all 1,100 answers in
  every trade, none of the 12 is named. Two near-hits were other things: "Tembusu House", an interior
  design project in one ChatGPT answer, and "Carros Centre", the building noted above. Tembusu Law's own
  page "best lawyers in singapore" was cited as a source in 10 Perplexity answers, and none of those
  answers names the firm.
- **Google's first page over all ten runs (16 Oct 2026).** In neither frame. google_page_one_by_engine
  counts runs 1 to 3 only; analyze_page_one_all_runs.py applies the same rule (distinct websites per trade,
  domain_of, the unchanged google_serps.json top 10) to every coded answer, runs 1 to 10, and writes
  results_page_one_all_runs.json. ChatGPT: 39 of 601 (6.5%), against 29 of 338 in runs 1 to 3. Perplexity:
  46 of 459 (10.0%), against 43 of 445. A website counts once per trade, so the 601 is 535 distinct
  websites; the 39 on page one are 39 distinct websites either way. Aircon servicing, ChatGPT: 1 of 49.
  Aesthetic clinics, ChatGPT: 2 of 75 (0 of 37 in runs 1 to 3). Run for a LinkedIn post and the page's
  first-page section, which prints it beside the runs 1 to 3 table and says it came after both frames.
