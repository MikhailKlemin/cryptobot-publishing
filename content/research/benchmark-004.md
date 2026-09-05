---
title: "Benchmark 004: reproduce the result before trusting it"
description: "An independent reproduction of an external channel-breakout notebook, including a fresh official-data recapture and exact input comparison."
layout: "case-study"
eyebrow: "Independent reproduction case study"
summary: "Benchmark 004 asked a deliberately narrow question before any prospective extension: could independent machinery recover the same executable strategy behavior and the same underlying market-data panel? The terminal answer was FULL_REPLICATION_MATCH."
status: "FULL_REPLICATION_MATCH"
period_label: "Reproduction data"
period: "1 Jan 2021 – 31 Aug 2025"
universe: "66 frozen Binance Spot symbols"
provider: "Binance Spot official public REST"
publication:
  published: "5 Sep 2026"
  updated: "5 Sep 2026"
  evidence_state: "closed"
source_lineage:
  origin: "External public research repository"
  source: "Statistical Arbitrage in Cryptocurrencies — Momentum / Channel Breakout"
  source_url: "https://github.com/gm-clara/Stat-Arb-in-Crypto/blob/fdb17c13b81ca007bac8ac59b55f14d9088d5a28/Momentum/Momentum%20-%20Channel%20Breakout.ipynb"
  commit: "fdb17c13b81ca007bac8ac59b55f14d9088d5a28"
  relationship: "Benchmark 004A independently reimplemented the executed notebook behavior in Go against the commit-pinned archived input. Benchmark 004B then recaptured the frozen 66-symbol panel from official Binance data and reused the sealed 004A evaluator without rebuilding it."
metrics:
  - label: "Input cells compared"
    value: "449,856"
    note: "1,704 dates × 66 symbols × 4 fields"
  - label: "Numeric disagreements"
    value: "0"
  - label: "Missingness disagreements"
    value: "0"
  - label: "Provider requests"
    value: "132 / 132"
    note: "zero automatic retries"
  - label: "Canonical input hash"
    value: "MATCH"
  - label: "Published display metrics"
    value: "MATCH"
criteria_title: "Exact input and metric reproduction"
criteria_summary: "FULL_REPLICATION_MATCH required the independently captured panel to match the archived canonical input exactly and the sealed evaluator to reproduce the published display metrics."
criteria:
  - label: "Date grid matches exactly"
    result: "PASS"
  - label: "Symbol grid matches exactly"
    result: "PASS"
  - label: "Missing / non-missing state matches for every field cell"
    result: "PASS"
  - label: "Finite high, low, close and volume values match exactly"
    result: "PASS"
  - label: "Canonical CSV SHA-256 matches"
    result: "PASS"
  - label: "Published strategy display metrics match"
    result: "PASS"
evidence_note: "These six files are byte-for-byte text artifacts selected from the preserved Benchmark 004B terminal bundle. The upstream notebook and archived market dataset are not redistributed here. Raw provider payloads, binaries, and runner material are also omitted."
evidence_files:
  - label: "Terminal result"
    description: "Benchmark 004B terminal outcome and action counters."
    url: "/evidence/benchmark-004/benchmark004b_result.json"
    sha256: "98f968533312722e705fdf8441d2df40ad84614f1d44785610f6c6b72745f635"
  - label: "Independent input comparison"
    description: "Field-cell comparison and canonical input hashes."
    url: "/evidence/benchmark-004/INPUT_COMPARISON.json"
    sha256: "263e0652a7197ceea7be26f183a78fdb234f179da3ec563eea5379626c05d9e9"
  - label: "Reproduced evaluation"
    description: "Benchmark 004A strategy parameters and matched historical display metrics."
    url: "/evidence/benchmark-004/benchmark004b_evaluation.json"
    sha256: "f036a3631231ace778195203064d190b4562618fab186c7296535816ef34fdb2"
  - label: "Frozen executable specification"
    description: "The code-level semantics the independent implementation was required to reproduce."
    url: "/evidence/benchmark-004/FROZEN_EXECUTABLE_SPEC.md"
    sha256: "4ce2e6571b1ca1241798966bcf45500eb8875dacb614a6c39779984fc6f9442e"
  - label: "Frozen decision specification"
    description: "The exact-match rules and possible terminal outcomes frozen before provider execution."
    url: "/evidence/benchmark-004/DECISION_SPEC.md"
    sha256: "fbcc7fc0762f287bc1e87ba884a319728cc67a92b0573f91788a3634c16c8853"
  - label: "Predeclared audit findings"
    description: "Methodology and documentation issues recorded before the reproduction result was known."
    url: "/evidence/benchmark-004/PREDECLARED_AUDIT_FINDINGS.md"
    sha256: "622c37e4d04dfc875d836af96d9e91aca24a470b5f5a73dae1a3f418a3932a49"
lineage_nav:
  - direction: "Next in lineage"
    title: "Research 005 — prospective evaluation"
    note: "The reproduced executable strategy was frozen into a new 365-day holdout."
    url: "/research/research-005/"
---

## What Benchmark 004 was trying to establish

Before using an external strategy as the basis for a new prospective experiment, the research program first asked whether the claimed object was reproducible at all.

The source was the public **Statistical Arbitrage in Cryptocurrencies** repository, frozen at commit `fdb17c13b81ca007bac8ac59b55f14d9088d5a28`, specifically its **Momentum / Channel Breakout** notebook. The source repository reported strong historical performance for this and several other strategies. Benchmark 004 did not begin by asking whether those returns would continue. It asked something more basic:

**Can we independently recover what the notebook actually executed, and can we reproduce its result without silently substituting our own interpretation?**

That distinction matters because a written strategy description, a notebook's executable code, and the data that happened to be available when it ran can all differ in consequential ways.

## 004A: reproduce the executable behavior

Benchmark 004A independently reimplemented the channel-breakout holdout path in Go. The specification followed the **executed notebook code**, even where explanatory prose or comments disagreed with it.

Among the reproduced details were:

- prior 46-day highs for long entries and prior 35-day lows for short entries;
- a prior 50-day volume filter at the executable 0.68 quantile;
- asymmetric 2-day long and 40-day short price exits;
- the notebook's 33-day post-hoc position-age mask, including its non-recursive behavior;
- rolling 35-day sample volatility and the executed `sqrt(std)` scaling before normalization;
- transaction cost as **20 bps × daily portfolio turnover**;
- out-of-sample portfolio evaluation from 1 January 2024.

The independent evaluator reproduced the notebook's published display metrics. For context, the reproduced historical target included **+287.34% net cumulative return** and a **1.430 net Sharpe** over the source holdout. Those are reproduction targets from a historical backtest, not prospective evidence of future profitability.

## 004B: independently recapture the market data

Matching a strategy against the author's archived input is useful, but it still leaves open whether the archived panel itself can be independently recovered.

Benchmark 004B therefore froze the exact 66-symbol universe produced by 004A and captured the required daily `high`, `low`, `close`, and `volume` fields directly from the official Binance Spot public REST API. It did not query a current universe and pretend that it represented the historical selection process.

The frozen capture executed **132 of 132 provider requests**, with zero automatic retries and no alternate-provider fallback. The comparison then covered:

**1,704 dates × 66 symbols × 4 fields = 449,856 field cells.**

There were **zero missingness disagreements** and **zero numeric disagreements**. The canonical serialized input SHA-256 matched as well.

Finally, 004B reused the evaluator binary sealed by 004A rather than rebuilding or changing it after seeing the newly captured data. The independently sourced input reproduced the same published display metrics, producing the terminal result `FULL_REPLICATION_MATCH`.

## The audit findings were frozen before the match

A perfect reproduction does not make every methodological choice good. Several limitations and specification discrepancies were recorded **before** the independent reproducer was run, specifically so that a successful numerical match could not erase them afterward.

### Future availability influenced the historical universe

The executable notebook required at least 90% non-null close coverage over the full panel through August 2025 before evaluating the portfolio from 2024 onward. That means later availability information can influence which symbols appear in an earlier evaluation period. Benchmark 004 reproduced this behavior because the immediate question was reproducibility, not methodological repair.

### Written volatility scaling and executed scaling differed

The explanatory prose described a 30-period rolling standard deviation, lower exposure to higher-volatility assets, and EWMA smoothing. The executed holdout path instead used a 35-day sample standard deviation, **multiplied** positions by `sqrt(std)`, and did not apply the described EWMA smoothing. Reproduction followed the executable path.

### A parameter comment did not match the executed value

The executable volume threshold was the **68th percentile** (`0.68`), while an inline comment described the 70th percentile. The executable value was treated as authoritative for reproduction.

### Spot OHLCV did not provide a complete short-execution model

The source data were Binance Spot prices while the portfolio could take negative weights. Borrow availability and cost, funding, derivatives basis, margin, liquidation and venue-specific short implementation were outside the published backtest. Exact historical reproduction therefore did not qualify the strategy for live trading.

### The cost wording and executable formula differed

The source README summarized a 20 bps transaction cost "per trade." The executable backtest charged **20 bps × daily portfolio turnover**. Benchmark 004 reproduced the executable formula.

### The original dynamic universe could not be recreated honestly after the fact

The source data-collection path used a then-current CoinGecko top-300 set, then-current Binance USDT pairs and symbols from an older hourly file. Without historical snapshots, reconstructing that discovery process later would require guesswork. Benchmark 004B instead froze the exact 66-symbol result produced by the archived source and tested whether its underlying market fields could be recaptured.

### Parameter-selection evidence was mixed

The source notebook reported that every examined parameter set had at least one validation window with negative Sharpe, then selected the final choice using validation information-ratio comparisons before the held-out execution test. This did not prevent reproduction, but it remains relevant when judging model-selection uncertainty.

## What FULL_REPLICATION_MATCH means — and what it does not

The result is strong evidence for a narrow claim: **the specified executable behavior was independently recoverable, and its frozen market-data panel could be independently recaptured from the official provider with exact agreement.**

It does **not** mean that every design choice was sound, that the historical return was free of selection effects, that short-side execution was realistic, or that the strategy should be traded.

That boundary is important. Reproducibility answers **"can we get the same result from the same defined object?"** It does not answer **"will this make money in the future?"**

The latter question required a new, prospectively frozen experiment. That became [Research 005](/research/research-005/), which carried the reproduced executable semantics into a new 365-day holdout and ultimately returned `FALSIFIED`.

## Evidence basis

This page is derived from the preserved `benchmark-004b-result-20260905T085552Z` terminal bundle. Its SHA-256 manifest contains 154 listed files, all of which were checked against the uploaded archive before publication and matched.

The selected artifacts below are published so that readers can inspect the terminal result, input comparison, evaluation, executable specification, decision rule, and predeclared audit findings directly. The public page does not redistribute the upstream notebook or archived dataset; the original notebook remains linked at its frozen public commit.
