---
title: "Research record"
description: "Independent evaluations of selected published strategies, alongside a historical archive of discovery tests, pre-evaluation stops, and reproduction milestones."
intro: |-
  I independently evaluate selected published strategies using `cryptobot-research`. Those individually scoped tests continue; the initial open-ended search for surviving strategies has ended. This record brings ongoing published-strategy evaluations together with selected cases from that historical archive.

  A preserved checkpoint from the initial discovery phase recorded **16 completed empirical studies and 16 empirical falsifications**. That is a historical checkpoint, **not a running count** of this publication's evaluations. Other candidates stopped earlier because a frozen source requirement, data-admission rule, or capability boundary could not be satisfied.

  The entries are deliberately selective. They show what particular tests established, not that all strategies fail or that a passing backtest would be ready to trade.
groups:
  - title: "Empirical falsification"
    note: "Representative completed evaluations that reached a frozen empirical verdict."
    records:
      - case: "Published Strategy Replication 001 — Le & Ruthbah BTC trend following"
        url: "/research/published-strategy-replication-001/"
        stage: "Published-strategy out-of-sample evaluation"
        outcome: "FALSIFIED"
        ended: "All four published BTC lookbacks reduced maximum drawdown, but all four had negative mean excess return versus the frozen buy-and-hold benchmark. Zero of four variants survived the predeclared family rule."
      - case: "Attention-shock cycle"
        stage: "Real-data deterministic evaluation"
        outcome: "FALSIFIED"
        ended: "Reached evaluation on 1,000 rows and failed. The negative result was preserved rather than used as a prompt to retune the tested rule."
      - case: "Reference-price anchor adjustment"
        stage: "Deterministic evaluation"
        outcome: "FALSIFIED"
        ended: "Generated 344 completed round trips, then failed its required aggregate cost-adjusted return and chronological-block criteria."
  - title: "Stopped before empirical evaluation"
    note: "Negative research outcomes where a frozen prerequisite failed before a strategy verdict could be produced."
    records:
      - case: "Source-budget feasibility"
        stage: "Prospective experiment freeze"
        outcome: "REJECTED BEFORE CAPTURE"
        ended: "Required 100,000 historical rows per symbol series, but the frozen request budget could supply only 4,000 per series. No public-data request or evaluator run followed."
      - case: "Coinbase history completeness"
        stage: "Data admission"
        outcome: "CLOSED BEFORE EVALUATION"
        ended: "Required at least 5,000 normalized rows per symbol; the real capture produced 4,995. The five-row shortfall was not filled or worked around after inspection."
  - title: "Initial discovery phase: closure milestones"
    id: "closure-milestones"
    note: "These two scientific milestones closed the initial discovery phase with different kinds of result, not all subsequent published-strategy evaluation."
    records:
      - case: "Benchmark 004 — independent reproduction"
        url: "/research/benchmark-004/"
        stage: "Reproduction benchmark"
        outcome: "FULL_REPLICATION_MATCH"
        ended: "Independent research machinery reproduced the externally specified executable behavior and independently recaptured the frozen official-data panel exactly. This established reproducibility, not profitability."
      - case: "Research 005 — final prospective evaluation"
        url: "/research/research-005/"
        stage: "Prospective evaluation"
        outcome: "FALSIFIED"
        ended: "The frozen rule failed because net Sharpe was about 0.368 versus 0.50 required and the one-sided 95% HAC lower bound was negative. The 3-of-4 positive-fold criterion and the −50% drawdown boundary both passed."
---

## Detailed case studies

[Published Strategy Replication 001: a Bitcoin trend strategy reduced drawdown — and still failed →](/research/published-strategy-replication-001/)

All four published BTC lookbacks were frozen as a family and evaluated on a subsequent out-of-sample period. Every variant reduced drawdown, but every mean excess-return estimate was negative versus the frozen buy-and-hold benchmark.

[Benchmark 004: reproduce the result before trusting it →](/research/benchmark-004/)

Independent reimplementation and official-data recapture established that the external channel-breakout result was reproducible, while preserving the audit findings that reproduction did not resolve.

[Research 005: why a positive return still failed →](/research/research-005/)

The final experiment of the initial discovery phase shows the next step in the lineage: the reproduced executable strategy was frozen for evaluation on a new 365-day holdout and failed two of its seven predeclared survival criteria. A before-evaluation freeze is not a claim of forward monitoring or live trading.

## How to read these outcomes

`FALSIFIED` is reserved here for an empirical proposal that reached its frozen evaluation and failed the predeclared survival criteria. A pre-capture feasibility rejection or a data-admission failure is reported separately because no empirical strategy verdict was produced. `FULL_REPLICATION_MATCH` belongs to a different category again: it says the independent reproduction machinery matched the specified behavior, not that a trading strategy was profitable or deployable.

Keeping those categories separate is part of the research method. It prevents a source failure from being presented as market evidence, a reproduction benchmark from being presented as alpha, or a positive-looking metric from replacing the acceptance rule that was fixed in advance.

## Why the record is selective

The internal research history contains more proposals, capability checks, source constraints, rejected discoveries, and implementation iterations than belong on a useful public page. Publishing all of them would blur the distinction between engineering history and research evidence.

The public record grows through individually scoped evaluations of published strategies and selected historical cases tied to preserved evidence. Results are reported against each test's fixed criteria, whether they pass or fail; evidence limitations and pre-evaluation stops remain separate. The aim is to make the research process inspectable without overstating what any individual experiment demonstrated.
