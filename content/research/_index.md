---
title: "Research record"
description: "A selective record of empirical falsifications, pre-evaluation stops, and the reproduction and prospective milestones that closed the project."
intro: |-
  Cryptobot Research was not a single strategy test. The research lineage contains many candidate mechanisms and several different kinds of terminal outcome. A preserved checkpoint recorded **16 completed empirical studies and 16 empirical falsifications**. Other candidates stopped earlier because a frozen source requirement, data-admission rule, or capability boundary could not be satisfied.

  This page is deliberately selective. It does not turn every internal iteration into a public article. The entries below are included because they show materially different ways controlled research can end.
groups:
  - title: "Empirical falsification"
    note: "Representative completed evaluations that reached a frozen empirical verdict."
    records:
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
  - title: "Closure milestones"
    note: "The two final scientific milestones closed the project with different kinds of result."
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
        ended: "Annualized net return was +20.50%, but the complete frozen rule failed: Sharpe was about 0.368 versus 0.50 required, the one-sided 95% HAC lower bound was negative, only 3 of 4 folds were positive, and maximum drawdown was about −29.59%."
---

## Detailed case studies

[Benchmark 004: reproduce the result before trusting it →](/research/benchmark-004/)

Independent reimplementation and official-data recapture established that the external channel-breakout result was reproducible, while preserving the audit findings that reproduction did not resolve.

[Research 005: why a positive return still failed →](/research/research-005/)

The final prospective experiment shows the next step in the lineage: the reproduced executable strategy was frozen into a new 365-day holdout and failed two of its seven predeclared survival criteria.

## How to read these outcomes

`FALSIFIED` is reserved here for an empirical proposal that reached its frozen evaluation and failed the predeclared survival criteria. A pre-capture feasibility rejection or a data-admission failure is reported separately because no empirical strategy verdict was produced. `FULL_REPLICATION_MATCH` belongs to a different category again: it says the independent reproduction machinery matched the specified behavior, not that a trading strategy was profitable or deployable.

Keeping those categories separate is part of the research method. It prevents a source failure from being presented as market evidence, a reproduction benchmark from being presented as alpha, or a positive-looking metric from replacing the acceptance rule that was fixed in advance.

## Why the record is selective

The internal research history contains more proposals, capability checks, source constraints, rejected discoveries, and implementation iterations than belong on a useful public page. Publishing all of them would blur the distinction between engineering history and research evidence.

The public record will grow only when an additional case teaches something distinct and can be tied cleanly to preserved evidence. The aim is not to maximize the number of strategy names on the site. It is to make the research process inspectable without overstating what any individual experiment demonstrated.
