---
title: "A published Bitcoin trend strategy reduced drawdown — but still failed"
description: "A subsequent out-of-sample test of a published BTC trend-following mechanism reduced drawdown at every lookback, but all four variants produced negative mean excess return versus the frozen benchmark."
date: 2026-09-14
lastmod: 2026-09-15
card_title: "A Bitcoin trend strategy reduced drawdown—but still failed"
card_summary: "All four published lookbacks reduced drawdown. None met the frozen excess-return criteria against buy-and-hold in this subsequent out-of-sample test."
layout: "case-study"
eyebrow: "Published strategy replication"
summary: "We tested all four published BTC trend-following horizons on a subsequent out-of-sample period. Every variant reduced maximum drawdown, but every mean excess-return estimate was negative. Under the frozen family rule, 0 of 4 variants survived."
status: "FALSIFIED"
period_label: "Evaluation period"
period: "1 Feb 2023 – 31 Aug 2026"
universe: "BTCUSDT · 20 / 65 / 150 / 200 days"
provider: "Binance Spot public daily klines"
publication:
  published: "14 Sep 2026"
  updated: "15 Sep 2026"
  evidence_state: "closed"
source_lineage:
  origin: "Published academic study"
  source: "Trend-following Strategies for Crypto Investors — Trinh Le and Ummul Ruthbah"
  source_url: "https://doi.org/10.2139/ssrn.4551518"
  source_id_label: "Publication source identity"
  source_id: "d185408c6c047a74f55f05868886deb46feaa6c37f4e51719ff6e904d4fa31c3"
  relationship: "The paper studies BTC and ETH trend following over 20, 65, 150 and 200-day lookbacks. This replication froze all four published BTC horizons rather than selecting the historically strongest one, then evaluated them on a subsequent period using official Binance BTCUSDT daily bars, next-open execution, a fixed transaction-cost model and a predeclared survival rule."
metric_guide:
  - term: "Annualized net return"
    explanation: "Geometric annualization: exp(mean daily net log return × 365) − 1. Unlike Research 005's arithmetic annualization, this expresses a compounded annual rate. Survival was based on excess return versus the benchmark, not this number alone."
  - term: "Net Sharpe"
    explanation: "Mean daily net log return × 365 divided by annualized daily log-return volatility, with a zero risk-free rate. A higher Sharpe can coexist with lower absolute return, as it did for some longer lookbacks here."
  - term: "Maximum drawdown"
    explanation: "The largest peak-to-trough decline in wealth. Every trend filter reduced this relative to the frozen buy-and-hold benchmark."
  - term: "Mean excess return"
    explanation: "Mean daily net log return minus the corresponding benchmark return, shown in basis points per day. The frozen rule required this value to be positive."
  - term: "HAC lower bound"
    explanation: "A one-sided 95% lower confidence bound for mean daily excess log return using Bartlett-HAC with lag 20. The rule required the lower bound itself to remain above zero."
  - term: "Family survival"
    explanation: "A lookback survived only if all three variant criteria passed. The four-horizon family survived only if at least three of the four published lookbacks independently survived."
metrics:
  - label: "Surviving variants"
    value: "0 / 4"
    note: "3 required for family survival"
  - label: "Benchmark annualized return"
    value: "+40.60%"
  - label: "Best variant annualized return"
    value: "+34.65%"
    note: "150-day; not a surviving strategy"
  - label: "Benchmark max drawdown"
    value: "52.97%"
  - label: "Lowest variant max drawdown"
    value: "25.59%"
    note: "150-day"
  - label: "Mean excess return"
    value: "Negative"
    note: "all four lookbacks"
criteria_title: "Three variant requirements, zero survivors"
criteria_summary: "Every lookback improved drawdown, but survival required all three conditions. Negative excess-return estimates prevented every variant from passing, so the 3-of-4 family rule could not be met."
criteria:
  - label: "Mean daily net excess log return > 0"
    result: "FAIL"
  - label: "One-sided 95% Bartlett-HAC(20) lower bound > 0"
    result: "FAIL"
  - label: "Maximum drawdown improved versus benchmark"
    result: "PASS"
  - label: "At least 3 of 4 published lookbacks survive"
    result: "FAIL"
evidence_note: "These two compact terminal artifacts expose the deterministic evaluation and final research verdict. The original paper is linked separately; raw market payloads and internal runner material are not republished here."
evidence_files:
  - label: "Deterministic evaluation"
    description: "Benchmark metrics, all four lookbacks, turnover, excess-return estimates, HAC results, drawdown flags and the frozen family decision rule."
    url: "/evidence/published-strategy-replication-001/published-strategy-replication-001-evaluation.json"
    sha256: "4e2700eb52bb549d6110e1ad5cc543eccc2f3e3d8437c2b4ef94373425f3bb70"
  - label: "Terminal research result"
    description: "The FALSIFIED outcome, terminal reason, core lineage identities and action counters."
    url: "/evidence/published-strategy-replication-001/published-strategy-replication-001-research-result.json"
    sha256: "329ef70346266423bec9377f07553cf89a3bacd7d5cf237d388a7630ede4624d"
editorial_update: "15 September 2026: clarified the historical evaluation period, implementation choices, geometric annualization, and log-return Sharpe. This was a before-capture freeze, not a live or forward-running test. The recorded metrics, evidence, and terminal outcome are unchanged."
---

## The result in one sentence

The published BTC trend-following family did something economically meaningful in our subsequent evaluation: every one of the four filters reduced maximum drawdown. None of them survived the frozen test, because every lookback also produced a **negative mean excess return versus buy-and-hold** and a negative one-sided 95% HAC lower bound.

The terminal result was therefore `FALSIFIED`, with **0 of 4** published variants surviving.

That tension is the useful part of the case. A strategy can make the ride less severe without producing excess return.

## What the published study tested

Trinh Le and Ummul Ruthbah's August 2023 paper, *Trend-following Strategies for Crypto Investors*, studies Bitcoin, Ether and a broader crypto index using trend horizons of **20, 65, 150 and 200 days**. Its historical BTC sample runs through 31 January 2023. The paper reports strong historical performance for trend-following portfolios and explicitly examines how transaction costs reduce those returns.

For the long-only momentum family, the basic idea is simple: compare the asset with a moving average over a published lookback, hold the crypto asset when the trend condition is active, and otherwise move out of the risky position. The paper compares those portfolios with buy-and-hold and reports particularly strong historical results for shorter horizons.

We did **not** take the historically strongest BTC horizon and call that the strategy. All four published lookbacks were carried forward as one frozen family.

## Replication is not copying the historical backtest

The purpose of this experiment was not to reproduce the paper's historical performance table from the same source data. It was to evaluate the published mechanism on a subsequent historical period, with the implementation and acceptance rules fixed before capture and evaluation. This was not a live or forward-running test.

That required several choices that are easy to leave vague in a research paper but cannot remain vague in a deterministic evaluator.

We used **BTCUSDT** daily bars from the official Binance Spot public API. Signals were calculated only after a completed UTC daily bar. If the target position changed, the new target became effective at the **following UTC daily open**. That next-open rule was frozen before capture as the conservative execution interpretation because the paper does not specify exchange execution timing precisely enough for a literal tradable implementation.

The cost was fixed at **0.1% per traded leg**, including initial entry and terminal liquidation where applicable. The benchmark was a cost-adjusted BTC buy-and-hold portfolio evaluated under the same frozen contract. Capital held flat earned zero.

There were material differences from simply copying the paper's results. The original BTC series was an S&P Bitcoin index backed by Lukka Prime; this test used Binance BTCUSDT. The paper's printed average formula also has an n-versus-n−1-term ambiguity. The frozen interpretation followed its prose: the arithmetic mean of exactly n completed daily closes, including the signal day's close. The target was LONG only when that close exceeded the average; equality meant FLAT.

The evaluation covered **1 February 2023 through 31 August 2026**, comprising 1,308 daily open-to-next-open holding intervals. The final interval ended at the **1 September 2026 UTC open**, when any remaining long position was liquidated with the specified exit cost.

The capture itself was bounded: warm-up began on 16 July 2022, the data request returned **1509 of 1509 expected daily bars**, and the entire public capture used **two provider requests**.

One wording point matters here. The paper is dated August 2023, while its historical BTC sample ends on 31 January 2023 and our evaluation period begins on 1 February 2023. The clean description is therefore a **subsequent out-of-sample / post-sample evaluation**. It would be inaccurate to describe every evaluation observation as post-publication data.

## What was frozen before the result

Each published horizon had to satisfy all three requirements independently:

1. positive mean daily **net excess log return** versus the frozen benchmark;
2. positive **one-sided 95% Bartlett-HAC(20) lower bound** on that excess return;
3. improved **maximum drawdown** versus the benchmark.

The family survived only if at least **three of the four** published horizons survived individually.

That final condition matters because it prevents a familiar form of hindsight selection. We could not inspect the four results, choose the nicest-looking row and promote it afterward. No winning lookback could be selected after evaluation.

## The result

The benchmark compounded to **+239.13%**, corresponding to a **40.60% annualized net return**, a Sharpe ratio of **0.736**, and a **52.97% maximum drawdown** under the frozen evaluator.

All four trend filters reduced drawdown. None beat the benchmark on mean daily excess return.

| Lookback | Annualized return | Sharpe | Max drawdown | Mean excess bps/day | Result |
| --- | ---: | ---: | ---: | ---: | --- |
| **Benchmark** | **40.60%** | **0.736** | **52.97%** | — | Benchmark |
| 20 days | 17.47% | 0.494 | 33.13% | −4.93 | FAIL |
| 65 days | 32.02% | 0.830 | 35.45% | −1.73 | FAIL |
| 150 days | 34.65% | 0.829 | 25.59% | −1.19 | FAIL |
| 200 days | 34.00% | 0.785 | 31.67% | −1.32 | FAIL |

The statistical confidence calculation did not turn otherwise-positive estimates into failures. The point estimates themselves were already negative: **−4.93, −1.73, −1.19 and −1.32 basis points per day** for the 20, 65, 150 and 200-day variants respectively.

Their one-sided 95% HAC lower bounds were also negative: **−11.91, −8.24, −7.35 and −7.48 bps/day**.

## Lower drawdown was real. It was not enough.

The **150-day** variant makes the distinction especially clear.

Its annualized net return was **34.65%**, below the benchmark's **40.60%**. Its Sharpe ratio was **0.829**, above the benchmark's **0.736**. Its maximum drawdown was **25.59%**, less than half the benchmark's **52.97%**.

Those are meaningful differences in risk characteristics. A reader who cared primarily about drawdown or return per unit of observed volatility could reasonably find that path more attractive than unfiltered BTC exposure.

But that was not the experiment we had declared.

The frozen rule required positive excess return, a positive dependence-aware lower confidence bound, and improved drawdown. The 150-day filter passed only the third condition. Calling it a success after seeing its Sharpe and drawdown would redefine the target after the result was known.

So the 150-day row is useful as a **post-result observation about risk management**, not as a promoted strategy.

## This was more than a confidence-bound failure

There is an important difference between these two statements:

- the estimated excess return was positive, but uncertainty was too large to establish it confidently;
- the estimated excess return itself was negative.

This experiment produced the second result for every horizon.

The HAC lower bounds matter because daily strategy returns are not safely assumed to be independent and identically distributed. But the terminal interpretation does not depend on statistical subtlety alone. Before looking at confidence intervals, all four observed mean excess-return estimates were already on the wrong side of zero.

## What this result says about the paper — and what it does not

It does **not** establish that the original paper was wrong.

The paper evaluated a different historical period and different source/index data. It reported the behavior of its strategies on that sample. Our experiment used Binance Spot BTCUSDT daily bars, a specific next-open execution convention, a fixed 0.1% per-leg cost, a frozen benchmark and a predeclared family-survival rule.

The supported conclusion is narrower:

**the published BTC trend-following mechanism did not survive this subsequent evaluation under our frozen data, timing, cost, benchmark and survival contract.**

That is a replication result, not a universal claim about trend following and not an accusation about the original authors' work.

## Why a negative replication is useful

Published strategies are unusually easy to evaluate badly after the fact. One can choose the best published parameter, adjust the execution convention, change costs, emphasize Sharpe instead of return, or decide that drawdown reduction was the real objective only after seeing the results.

Freezing the whole published parameter family removes much of that freedom.

Here it produced a result with more information than a simple "worked / did not work" label. The trend filters continued to behave like risk overlays: they spent substantial time flat and materially reduced drawdown. At the same time, they did not earn positive excess return over the benchmark in the frozen evaluation.

Both observations can be true. Keeping them separate is the discipline.

## Evidence and lineage

This page is derived from the preserved terminal research artifacts; the strategy was not rerun, retuned or re-evaluated for publication.

The deterministic lineage was:

`published paper → prospectively specified proposal → capability assessment → official-source admission → immutable experiment freeze → explicit authorization gate → bounded Binance capture → normalized dataset with provenance → deterministic four-horizon evaluation → FALSIFIED terminal result → immutable novelty-history registration`

The principal identities are:

- proposal: `48080d526ea006e31aafb25b250e59c3025ba5a309d3d4848200f94b5c35466f`
- experiment: `e8b616f494a35fe43ef16f46ef1fac1590189c1d9358a0304fa06202ec297315`
- dataset: `7ea7f981bedd01448579d14d76ebcdbc649da8657ab0c06c215ec790cc118173`
- signal manifest: `1ea305ddffd464380c64c007f05da0b2397947f57d061ac5536f37c0163715f0`
- evaluation: `4e2700eb52bb549d6110e1ad5cc543eccc2f3e3d8437c2b4ef94373425f3bb70`
- research result: `329ef70346266423bec9377f07553cf89a3bacd7d5cf237d388a7630ede4624d`
- novelty history: `f9fccc6394470b15213a5f0a4d8a32505ba2609cef246ed72ce6dcffbf3142aa`

No qualification occurred. No strategy was exported. No paper or live order was placed, and no integration with the separate trading runtime occurred.
