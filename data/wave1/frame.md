# Who do AI assistants recommend when Singaporeans ask for a local business?

Frame written and frozen 5 October 2026, 23:20 SGT, before the first question was sent. Nothing in
this file changes after the run starts. Anything learned during the run goes in `NOTES.md`, dated.

## The question

When someone in Singapore asks an AI assistant to recommend a local service business, which
businesses get named, how stable is that answer if you ask again, do the assistants agree with each
other, and where do they get their information?

The study describes what the assistants return. It does not predict it, and nothing below encodes
an expected answer.

## Trades

The eleven trades in rankr's Singapore SME website benchmark (scans of 19 July and 30 August 2026),
kept so the two studies can sit side by side. They were chosen for that benchmark, not for this one.

## Questions

Five templates, applied identically to every trade. 11 trades x 5 templates = 55 questions.

| ID | Template |
|---|---|
| T1 | Can you recommend a good {provider} in Singapore? |
| T2 | What are the best {providers} in Singapore? |
| T3 | {keyword} |
| T4 | I need an affordable {provider} in Singapore. Who should I go to? |
| T5 | I live in Tampines. Which {provider} near me would you recommend? |

**T3 is a real search, verbatim.** Rule: the highest-volume keyword containing "singapore" among the
candidate keywords below, by Ahrefs Keywords Explorer Singapore volume, pulled 5 October 2026.
"singapore" is required because the assistants are queried with no location, so the location has to
be in the words, and Singaporeans do type it (the volumes show it).

| Trade | {provider} / {providers} | T3 keyword | SG volume |
|---|---|---|---|
| Aircon servicing | aircon servicing company / companies | aircon servicing singapore | 4,100 |
| Dental clinics | dental clinic / clinics | dental clinic singapore | 2,500 |
| Interior design and renovation | interior designer / designers | interior design singapore | 2,400 |
| Movers | moving company / companies | movers singapore | 2,400 |
| Aesthetic clinics | aesthetic clinic / clinics | aesthetic clinic singapore | 1,800 |
| Physiotherapy | physiotherapy clinic / clinics | physiotherapy singapore | 1,700 |
| Tuition centres | tuition centre / centres | tuition centre singapore | 1,400 |
| Maid agencies | maid agency / agencies | maid agency singapore | 1,100 |
| Accounting | accounting firm / firms | accounting services singapore | 1,100 |
| Lawyers | lawyer / lawyers | lawyer singapore | 700 |
| Car workshops | car workshop / workshops | car servicing singapore | 700 |

Candidate keywords checked (44): aircon servicing, aircon servicing singapore, aircon service, aircon
chemical wash, dentist, dental clinic, dentist singapore, dental clinic singapore, tuition centre,
tuition centre singapore, tuition, math tuition, movers singapore, movers, moving company singapore,
house movers, accounting firm singapore, accounting services singapore, accounting firm, corporate
secretarial services singapore, aesthetic clinic singapore, aesthetic clinic, aesthetics clinic,
renovation contractor singapore, interior design singapore, hdb renovation, interior designer
singapore, renovation singapore, lawyer singapore, law firm singapore, lawyer, law firm,
physiotherapy singapore, physiotherapist singapore, physiotherapy, physio singapore, car workshop
singapore, car workshop, car servicing singapore, car servicing, maid agency singapore, maid agency,
interior design, renovation.

T5 uses one fixed town for every trade. Tampines was picked because it is one of Singapore's
largest residential towns; it is a constant, not a variable.

## Engines

| Engine | How it is asked | Runs per question |
|---|---|---|
| ChatGPT (OpenAI) | OpenAI's `gpt-5.6-luna` through the OpenRouter API, with OpenAI's own web search on (`plugins: web, engine: native`) | 3 |
| Perplexity | `perplexity/sonar` through the OpenRouter API, which searches with Perplexity's own index | 3 |
| Google AI Overviews | Not asked. The AI Overview and organic results Google showed in Singapore for each T3 keyword, from Ahrefs SERP Overview, with Ahrefs' capture date per keyword | 1 snapshot |

Every question is sent alone, with no system prompt, no conversation history and no location. Runs
go in rounds: round 1 for all 55 questions on both engines, then round 2, then round 3, so a budget
stop leaves complete rounds rather than complete trades. Every raw response is saved before anything
is parsed.

**This is not the ChatGPT app.** The app adds its own instructions, memory and the user's location,
and may use a different model. The API with OpenAI's search is the closest version that can be
rerun by anyone with a key, which is why it is used. The same is true of Perplexity's app.

## What is coded, and how

**Named businesses.** A small model (`openai/gpt-5-nano`, no web access) lists every business the
answer names as an option, copying each name exactly as written. A name is kept only if that exact
string appears in the answer; anything else is dropped and counted. Directories, publishers, review
sites, platforms, government bodies and equipment brands are excluded unless the answer presents
them as the service provider. A sample of 20 answers is checked by hand against the model's list
and the agreement is published.

**Matching names across runs and engines.** Lowercase; drop "pte ltd", "pte. ltd.", "llp", "(s)",
"singapore", "sg", "the", punctuation and spacing; "&" and "and" removed. Two names match when the
cleaned strings are equal or one contains the other.

**Cited sources.** Every URL the engine cites, with tracking parameters removed, gets one label:

| Label | Rule |
|---|---|
| Best-of list | URL path or title contains "best" or "top" followed by a number or the trade, on any site |
| Business website | Domain belongs to a business offering the trade (lookup table, published) |
| Directory or review platform | Domain in the directory list (published) |
| News or magazine | Domain in the media list (published), and not a best-of list |
| Forum or social | reddit.com, hardwarezone.com.sg, facebook.com, instagram.com, youtube.com, tiktok.com |
| Government | Domain ends in gov.sg |
| Other | Anything left |

A best-of list is further split by who published it: a media or directory site, or a business that
offers the trade itself.

## What is reported

1. **Top-pick stability.** For each question and engine, whether the first business named was the
   same in all three runs.
2. **Repeat overlap.** For each question and engine, the share of businesses named in one run that
   were also named in another run of the same question.
3. **Engine agreement.** For each question, the share of businesses named by either engine (all runs
   pooled) that both engines named.
4. **Source mix.** Share of citations by label, per engine, and for Google's AI Overviews.
5. **Google overlap.** For each trade, the share of domains the two assistants cited for that trade
   that were in Google's top 10 organic results for its T3 keyword.

Every figure is published with its numerator and denominator. Answers that name no business are
counted and reported, not dropped.

## What this design still allows to be wrong

- The API is not the app. A customer using the ChatGPT or Perplexity app, logged in, with location
  on, can see different businesses.
- One date. Answers change; this is a snapshot of 5 and 6 October 2026.
- Per-trade figures rest on 5 questions x 3 runs and are descriptive only.
- Name matching can split one business into two (a nickname against a full name) or, more rarely,
  merge two. Split names push agreement and stability down. The hand check reports how often it
  happened.
- Ahrefs' Google snapshots are not all from the same day; each keyword's capture date is published.
- English only.
