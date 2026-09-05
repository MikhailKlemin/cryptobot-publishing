---
title: "Cryptobot Research"
description: "What remains useful after controlled crypto strategy research does not produce a deployable strategy."
eyebrow: "Controlled strategy research"
headline: "A backtest is not the result. The process is."
summary: "A closed crypto-strategy research project built around a simple constraint: decide what counts as success before seeing the result."
intro_title: "What this project is"
intro: |-
  Trading ideas can look convincing after enough historical exploration. The harder part is finding out whether they still hold up once the rules are fixed **before** the result is known.

  That was the point of Cryptobot Research. Experiments were frozen prospectively, evaluated deterministically, and tied back to preserved data and execution provenance. Independent reproduction came before trust in novel results. When a frozen test failed, the failure stood. The research phase is now closed; what remains useful is the method and the evidence it left behind.
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
    body: "Benchmark 004 took an externally defined channel-breakout strategy and reproduced it independently against official public data. This was not a search for a better breakout rule. It was a check that the research machinery could recover specified executable behavior before it was asked to evaluate something novel."
  - label: "Research 005"
    kind: "Prospective evaluation"
    title: "A positive headline return still failed"
    status: "FALSIFIED"
    url: "/research/research-005/"
    body: "Research 005 was frozen in advance for 2025-09-01 through 2026-08-31, over a fixed 66-symbol universe and using the exact Benchmark 004 executable semantics. The annualized return looked encouraging. The complete acceptance rule did not pass, so the terminal classification stayed FALSIFIED."
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

## Why publish a failed experiment?

Because the failure contains more information than another optimized equity curve.

Research 005 finished with a positive annualized net return. If that number had been treated as the objective, it would have been easy to call the result promising and continue tuning. But the acceptance criteria were frozen before the evaluation. They also required stronger risk-adjusted performance, a positive dependence-aware lower confidence bound, and recurring evidence across chronological folds. Those conditions were not all met.

The important part is not that one strategy failed. It is that the procedure made it difficult to quietly redefine success after seeing the answer.

## What remains useful

The durable output of the project is a practical research workflow:

- bind data and transformations to explicit provenance;
- freeze the strategy, costs, timing, and acceptance rule before evaluation;
- make the evaluator deterministic enough to reproduce exactly;
- test independent reproduction before trusting novel results;
- preserve negative results instead of retuning them away;
- keep research authority separate from any trading runtime.

That workflow is useful even when the strategy under test is not.

## What this site will cover

The first pages focus on the parts worth carrying forward: the research record, prospective experiment design, deterministic evaluation, provenance, reproduction, realistic execution assumptions, and the failure modes that ordinary backtests make easy to hide. The goal is not to turn a closed experiment into a trading signal. It is to make the method understandable enough to inspect, criticize, and reuse.