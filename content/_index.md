---
title: "Cryptobot Research"
description: "A technical publication about controlled trading-strategy evaluation, built from a completed crypto research program."
eyebrow: "Controlled strategy evaluation"
headline: "Trading research is easy to optimize. Harder to falsify."
summary: "A technical publication built from a closed crypto-strategy research program: real case studies, methods, and engineering lessons about deciding whether a backtest deserves trust."
intro_title: "What this site is for"
intro: |-
  A backtest can be made more attractive in many small ways: change a parameter, move a date, choose another cost assumption, discard an awkward period, or reinterpret the success criterion after seeing the result. The difficult part is building a process that can still say **no** when the numbers look tempting.

  Cryptobot Research documents that process using preserved work from a completed research program. Strategy discovery is closed. The site is not a source of trading signals; it is a record of how hypotheses were reproduced, frozen, evaluated, rejected, or stopped before evaluation when the evidence contract could not be satisfied.
lanes_title: "Three ways into the work"
lanes_intro: "The publication is broader than one experiment. Research 005 is the most complete case today, while the same evidence base supports future case studies, methodological explanations, and engineering notes."
lanes:
  - label: "Case studies"
    title: "What happened to actual research ideas"
    body: "Completed falsifications, reproduction benchmarks, and experiments that stopped at source or data-admission gates. Each case should answer what was fixed in advance, what happened, and why the recorded outcome stood."
    url: "/research/"
    link: "Browse the research record"
  - label: "Methodology"
    title: "How to make a backtest harder to fool"
    body: "Prospective freezing, deterministic evaluation, transaction costs, chronological folds, provenance, and falsification — explained as practical controls rather than abstract research ceremony."
    url: "/methodology/"
    link: "Read the methodology"
  - label: "Engineering lessons"
    title: "What the research machinery taught us"
    body: "Reproducibility, market-data quality, immutable evidence, executable-vs-written specifications, and why research software should not quietly become a trading runtime."
    url: "/methodology/#research-software-is-not-a-trading-runtime"
    link: "See the current engineering boundary"
record_title: "Selected research outcomes"
record_intro: "The project tested more than one candidate mechanism. A preserved checkpoint already recorded 16 completed empirical studies and 16 falsifications; other candidates stopped earlier at feasibility or data-admission gates. These examples show several ways a controlled research cycle can end."
record:
  - title: "Attention-shock cycle"
    stage: "Real-data evaluation"
    outcome: "FALSIFIED"
    summary: "A bounded Binance cycle reached deterministic evaluation and terminated as falsified. The result was preserved rather than retuned after the outcome was known."
  - title: "Reference-price anchor adjustment"
    stage: "Deterministic evaluation"
    outcome: "FALSIFIED"
    summary: "A later frozen proposal failed its required return criteria and was registered as falsified rather than being passed forward for qualification."
  - title: "Source-budget feasibility"
    stage: "Pre-capture gate"
    outcome: "REJECTED BEFORE CAPTURE"
    summary: "One proposal required more history per symbol than its frozen request budget could supply. It stopped before any public-data capture or evaluation."
  - title: "Coinbase history completeness"
    stage: "Data admission"
    outcome: "CLOSED BEFORE EVALUATION"
    summary: "A real capture returned 4,995 rows per symbol against a prospectively frozen 5,000-row minimum. The shortfall was not filled or worked around after inspection."
results_title: "Closure milestones"
results_intro: "The final closure work ended with two different scientific outcomes: independent reproduction succeeded, while the final prospective strategy evaluation did not satisfy its complete frozen acceptance rule."
results:
  - label: "Benchmark 004"
    kind: "Independent reproduction"
    title: "Reproduction worked"
    status: "FULL_REPLICATION_MATCH"
    body: "Benchmark 004 independently reimplemented an external channel-breakout notebook and then reproduced it using independently captured official Binance data. The point was reproducibility, not an endorsement of the historical return."
  - label: "Research 005"
    kind: "Prospective evaluation"
    title: "A positive headline return still failed"
    status: "FALSIFIED"
    url: "/research/research-005/"
    body: "Research 005 froze the reproduced executable semantics for 2025-09-01 through 2026-08-31 over a fixed 66-symbol universe. The annualized return looked encouraging. The complete acceptance rule did not pass, so the terminal classification stayed FALSIFIED."
    metrics:
      - label: "Annualized net return"
        value: "+20.50%"
      - label: "Net Sharpe"
        value: "0.368"
        note: "required ≥ 0.50"
      - label: "95% HAC lower bound"
        value: "Negative"
      - label: "Positive frozen folds"
        value: "3 / 4"
      - label: "Maximum drawdown"
        value: "−29.59%"
---

## Why publish negative results?

Because a controlled failure can be more informative than another optimized equity curve.

Research 005 is the clearest example, but it is not the whole publication. Other cases show different failure modes: a hypothesis can fail empirically, a source budget can make an experiment impossible before capture, a real dataset can miss a frozen admission requirement, or an independent reproduction can succeed without saying anything about future profitability.

Those distinctions are useful because they stop very different events from collapsing into the same vague label of "the backtest did not work."

## What remains useful

The durable output of the project is a practical research workflow and the evidence left by applying it:

- bind data and transformations to explicit provenance;
- distinguish an external idea from the executable object actually tested;
- freeze the strategy, costs, timing, and acceptance rule before evaluation;
- make the evaluator deterministic enough to reproduce exactly;
- test independent reproduction before trusting novel results;
- preserve negative results instead of retuning them away;
- keep research authority separate from any trading runtime.

The publication will grow by explaining those lessons through a small number of evidence-backed cases and technical notes — not by restarting strategy discovery.
