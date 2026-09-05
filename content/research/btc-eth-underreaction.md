---
title: "When a positive effect failed after costs"
description: "A frozen BTC-to-ETH underreaction strategy showed a positive pre-cost effect, then failed every economic survival test that mattered."
layout: "case-study"
eyebrow: "Case study · BTC → ETH cross-asset underreaction"
verdict: "FALSIFIED"
verdict_reason: "POST_COST_MEAN_NOT_POSITIVE"
claim: "After an extreme completed BTCUSDT hourly shock, ETHUSDT may initially underreact relative to its prior BTC sensitivity, leaving a same-direction four-hour continuation large enough to remain profitable after realistic transaction costs."
metrics:
  - label: "Executed hypothetical trades"
    value: "204"
  - label: "LONG / SHORT"
    value: "116 / 88"
  - label: "Gross mean"
    value: "+4.58 bps"
  - label: "Frozen round-trip cost"
    value: "20.00 bps"
  - label: "Net mean"
    value: "−15.42 bps"
  - label: "Positive frozen folds"
    value: "0 / 4"
charts:
  - src: "/images/btc-eth-gross-vs-net.svg"
    alt: "Gross mean return of positive 4.58 basis points and net mean return of negative 15.42 basis points after a frozen 20 basis point round-trip cost."
    caption: "The apparent effect was positive before costs. The cost assumption was frozen before evaluation and reversed the economic conclusion."
  - src: "/images/btc-eth-fold-means.svg"
    alt: "All four frozen chronological folds had negative mean net return."
    caption: "The failure was not confined to one period: every prospectively frozen chronological fold was negative."
---

## The claim was plausible enough to test

The hypothesis was simple: after an unusually large completed BTC hourly move, ETH might lag the response implied by its recent sensitivity to BTC. If that underreaction was large enough, a same-direction position held for four hours might capture the delayed adjustment.

The rule was intentionally specific. It used the previous 720 paired hourly observations, excluded the current hour from the historical threshold and beta estimate, triggered only on a Q99 BTC shock, and required ETH to be at least 40 bps behind the beta-implied response. LONG and SHORT conditions were symmetric. The strategy entered at the exact ETH five-minute open beginning five minutes after the decision and exited four hours later.

None of those choices were changed after the result was observed.

## What was frozen before evaluation

The research contract fixed the lookback, shock definition, beta formula, 40 bps underreaction threshold, four-hour holding period, five-minute entry latency, 20 bps round-trip transaction cost, missing-data behavior, minimum sample counts, chronological folds, HAC specification, and survival criteria.

The strategy had to satisfy all of the following, not merely show a positive average move:

- complete exact entry and exit evidence for every emitted signal;
- at least 100 total trades, 25 LONG, 25 SHORT, and 15 trades in every frozen fold;
- positive mean return after exactly 20 bps round-trip cost;
- a positive one-sided 95% physical-time Bartlett-HAC lower bound using a 30-day lag;
- at least three positive chronological fold means, with no fold below −20 bps.

This matters because the headline result and the acceptance rule were not the same thing.

## The signal existed before costs

The registered closed evaluation produced 204 signals and 204 executed hypothetical trades: 116 LONG and 88 SHORT. Mean gross log return was **+4.5839 bps per trade**.

That is the kind of number that can tempt a researcher to keep going. It is positive, it comes from a concrete mechanism, and it can be narrated easily.

But the frozen round-trip cost was **20 bps**. Applying it exactly as specified changed mean net log return to **−15.4161 bps**. The experiment therefore failed the first economic survival criterion: post-cost mean return was not positive.

## The failure also persisted across time

The four chronological folds contained 31, 61, 52, and 60 trades. Their mean net results were **−22.15**, **−10.84**, **−9.80**, and **−21.46 bps** respectively.

The recurrence rule required at least three positive fold means and no fold below −20 bps. The result had zero positive folds, and two folds were below −20 bps.

The dependence-aware inference was no kinder. The one-sided 95% physical-time Bartlett-HAC lower bound was **−41.04 bps**, with a HAC standard error of about **15.58 bps**.

No later metric could rescue the result because the strategy had already failed the mandatory positive post-cost mean criterion.

## Data and causality controls

The experiment used official public Binance Spot evidence. The preserved verification record bound BTCUSDT predictor history and ETHUSDT target history to immutable source evidence.

ETH data was admitted fail-closed. An hourly ETH observation existed only when all twelve constituent five-minute candles were present. Missing slots were not interpolated, compressed, bridged, or silently replaced. Every hypothetical trade also required exact entry and exit five-minute opens.

The causal boundary was explicit: the current hour was excluded from historical estimation, signals were formed only after completed hourly returns were known, and entry was delayed by a complete five-minute interval. Trades crossing a frozen fold boundary were suppressed rather than reassigned after the fact.

## What this result does — and does not — say

The conclusion is narrow: **this exact frozen BTC-to-ETH underreaction rule did not demonstrate positive post-cost expectancy under the defined evidence and execution model.**

It does not establish that every BTC-to-ETH relationship is unprofitable. It does not rule out different horizons, different execution models, or different mechanisms. Those would be different experiments and would need their own prospective rules.

The experiment also modeled symmetric hypothetical SHORT payoff on spot price movement. Actual short borrow, derivatives funding, liquidity, financing, and venue availability were outside this research stage.

## Why this is the useful result

The interesting part is not that a strategy lost money after costs. That happens constantly.

The useful part is that the research process made the tempting interpretation difficult to preserve. The pre-cost effect was positive. The frozen cost assumption erased it. The chronological folds were all negative. The confidence bound was negative. And none of the rules were changed to produce a more attractive ending.

That is what prospective falsification is supposed to do: turn "this looks promising" into a decision that can survive contact with costs, timing, missing data, and predeclared rejection criteria.

### Evidence note

This page packages a previously closed internal experiment. It is not a new client engagement and this publishing step did not replay the omitted large immutable runtime payloads. The terminal result, aggregate metrics, source-boundary status, and evidence identities were preserved in the closed handoff used for publication.
