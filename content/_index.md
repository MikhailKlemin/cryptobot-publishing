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
results_title: "What the research established"
results_intro: "Two closure tests ended differently. One showed that specified executable behavior could be reproduced independently. The other showed why a good-looking return is not enough to pass a frozen test."
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

A failed frozen test can tell you more than another attractive equity curve. Research 005 matters because the decision rule was not rewritten after the numbers arrived, even when one headline metric looked appealing.

The material here is aimed at readers interested in:

- prospective freezes as a practical guard against backtest overfitting;
- deterministic evaluation and the role it plays in reproducibility;
- provenance and immutable evidence as limits on retrospective storytelling;
- what an independent reproduction test actually establishes;
- the boundary between research software and a trading runtime.

## What this site is for

The site will turn that record into a small set of readable case studies and technical notes. A reader should be able to inspect the method without knowing the development history of the project.

The research result is not a trading product. No Research 005 strategy was authorized for promotion into a trading runtime.
