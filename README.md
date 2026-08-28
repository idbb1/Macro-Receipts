# Macro-Receipts

# Macro Scoreboard — Project Brief

> A public, methodology-backed scoreboard of macro forecasters' track records, plus a weekly synthesis of what the tracked voices currently think about markets and why. Built to grow an X audience first; the web app is the destination.

---

## 1. The problem

Investors drown in commentary: podcasts, YouTube, Substacks, Fed communications, X threads, mainstream press. Nobody has time to consume it all, and nobody keeps score. Forecasters bury misses and tout hits, so investors have no way to know whose views deserve weight.

## 2. The product (two halves, one data model)

### A. The Scoreboard (acquisition)
A ranked, public table of named macro forecasters scored on **falsifiable, time-bound calls only**, with every graded call linked to the exact source and quote.

### B. The Briefing (retention)
A weekly (later daily) synthesis of what the tracked voices currently think: consensus, disagreements, who changed their mind, and the reasoning behind each view — every claim linked to source. Designed to be read in under five minutes.

Both are generated from the same underlying dataset of extracted **stances** and **calls**.

## 3. Strategy

- **X first.** The scoreboard is the viral hook. Weekly post in a fixed format, tag forecasters ranked in the top tier, link to full profiles on the web.
- **Play the top half.** Lead with who has been right. The bottom of the table is visible on the site but nobody is tagged into it. High-ranked forecasters have a commercial reason to retweet.
- **Monetise the audience, not the summary.** Sponsorship, affiliate links on forecaster profiles (their paid services), X revenue share. Do not plan on subscriptions early.
- **The moat is the dataset.** Twelve-plus months of clean, quoted, mechanically resolved calls on ~30 people. Start logging calls before building any UI. Backfill from the last 12 months of source material with original timestamps.

## 4. Non-negotiable principles

1. **Only score what is falsifiable.** "Gold to $4,000 by year end" is a call. "We are in fiscal dominance" is a view — log it, never grade it.
2. **Every graded call carries the exact quote, source URL and timestamp.** This is the defence when a ranking is challenged.
3. **Resolution is mechanical.** Price data and published rules decide, not editorial judgement. Rules are public.
4. **Show more than hit rate.** Call count, average horizon, directional bias, boldness-adjusted score. A permabull at 70% in a bull market is not a forecaster.
5. **Summarise, attribute, link. Never republish.** Transcripts are inputs, not outputs.
6. **Same rigour for everyone.** The top of the table is only a compliment if the bottom of the table cannot dismiss the method.

## 5. What we want the agents to design

Explore and propose the best approach for each of the following. Argue for a recommendation; do not just list options.

### 5.1 Stickiness — why does someone come back?
- What is the smallest daily/weekly unit that creates a check-in habit?
- What changes week to week that is worth noticing? (rank moves, calls resolving, "flipped" alerts, streaks)
- Notification / email / X cadence that informs without spamming.
- Personal layer: follow forecasters, get alerted when one of yours makes a new call or a call resolves.

### 5.2 Catchiness — what spreads on X?
- Fixed weekly post format (table image + top 5 + biggest mover + link). Propose the exact template.
- Which single stats are the most shareable? (e.g. "X is 68% accurate but has never made a bearish call")
- Forecaster profile cards designed to be screenshotted and shared by the forecaster themselves.
- Event-driven posts: a big call resolves, a forecaster flips, consensus breaks.
- Tagging etiquette that maximises retweets and minimises hostility.

### 5.3 Informativeness — is it actually useful to an investor?
- Briefing structure: Consensus / Disagreements / Who changed their mind / What it implies. Propose the layout and length limits.
- How to surface *reasoning*, not just direction, so the reader learns the argument.
- Weighting views by track record: should the briefing say "the forecasters with the best records lean X"?
- Consensus over time: show when the crowd is unusually aligned (historically a contrarian signal).

### 5.4 Extraction and grading
- Structured extraction schema for stances and calls (see §7).
- Detecting whether a statement is a new call, a repeat, or a reversal versus the forecaster's prior stances.
- Grading rules: hit / miss / partial / void, deadlines, thresholds, boldness weighting, minimum call count before a grade is shown.
- Handling hedged calls ("could", "likely", "if X then Y"). Propose a confidence taxonomy.
- A human review step before anything is published, with an audit trail.

### 5.5 Credibility and defensibility
- Public methodology page. Propose its contents.
- Appeal process for forecasters who dispute a grade.
- Legal posture: public statements, exact quotes, objective grading, no editorialising about competence.

### 5.6 Pipeline and stack
- Ingestion for v1 sources: YouTube (transcripts), podcast RSS (transcription), Substack/RSS, Fed speeches/minutes/SEP, free news RSS. Defer X and paywalled press.
- Cost model per source per week.
- Storage for stances, calls, resolutions, and source snapshots.
- Image generation for the weekly table post.

## 6. Sources — initial roster (v1)

Macro voices to track. Adjust after feasibility check on source availability.

| Voice | Primary channels |
|---|---|
| Lyn Alden | Newsletter, podcasts |
| Luke Gromen | FFTT, podcasts |
| Jim Bianco | Podcasts, YouTube |
| Ray Dalio | LinkedIn, interviews |
| Jeremy Grantham | GMO letters, interviews |
| Michael Burry | 13F, rare interviews |
| Mohamed El-Erian | Columns, interviews |
| Tom Lee | Interviews, YouTube |
| David Rosenberg | Newsletter, interviews |
| Jeff Gundlach | Webcasts, interviews |
| Stanley Druckenmiller | Interviews |
| Howard Marks | Memos |
| Federal Reserve | Statements, minutes, SEP, speeches |
| WSJ / FT / Bloomberg | Headlines only (paywalled) |
| Yahoo Finance | Free articles and video |

Add 10–15 more after checking transcript availability. Prefer voices who make concrete calls.

## 7. Draft data model (starting point — improve it)

```
Forecaster
  id, name, handle_x, channels[], affiliate_url, bio

SourceItem
  id, forecaster_id, type (podcast|youtube|article|tweet|fed_doc), url,
  published_at, ingested_at, transcript_ref, snapshot_ref

Stance                      # a view, never graded
  id, forecaster_id, source_item_id, asset_or_theme, direction,
  horizon, reasoning_summary, quote, confidence, is_change_from_prior,
  extracted_at, reviewed_by

Call                        # falsifiable, graded
  id, forecaster_id, source_item_id, asset, direction,
  target_value | threshold, deadline, quote, confidence,
  boldness_score, status (open|hit|miss|partial|void),
  resolved_at, resolution_evidence, reviewed_by

Resolution rules (public)
  price source, evaluation window, partial-credit rules,
  void conditions, minimum calls for a published grade
```

## 8. Weekly output — v1 targets

- **X post:** fixed template, table image, top 5, biggest mover, one-line "consensus this week", link.
- **Web:** scoreboard table (sortable), forecaster profile pages (grade, calls list with quotes, open calls, affiliate link), methodology page, weekly briefing page.

## 9. Success metrics

- X: follower growth, retweets by tracked forecasters, link click-through.
- Web: weekly returning visitors, briefing read-completion, profile page shares.
- Data: calls logged per week, % resolved mechanically without dispute, dispute count.

## 10. Out of scope for v1

Per-user source selection, mobile app, X ingestion via API, full-text paywalled press, subscriptions.

## 11. Deliverables requested from the agents

1. Recommended product design for stickiness, catchiness and informativeness (§5.1–5.3), with rationale and trade-offs.
2. Final extraction schema and grading rulebook (§5.4), including worked examples of tricky cases.
3. Methodology page draft (§5.5).
4. Pipeline architecture and cost estimate (§5.6).
5. Backfill plan: how to log the last 12 months of calls for the v1 roster.
6. A 90-day launch plan sequenced around the first public scoreboard post.
