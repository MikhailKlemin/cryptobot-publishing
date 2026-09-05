---
title: "Methodology"
description: "A practical workflow for making trading-strategy research reproducible, prospective, and capable of saying no."
---

A backtest becomes difficult to trust when the hypothesis, source data, executable rules, cost model, and definition of success can all move after the result is visible. Cryptobot Research evolved toward a simpler goal: **close those degrees of freedom before they can rescue a disappointing experiment.**

The research program is now closed. This page describes the controls that remain useful beyond it.

## The controlled research loop

The final workflow can be reduced to seven steps:

1. **State the hypothesis and its origin.** Record whether the idea came from an external publication, an internal mechanism, or another source. Do not blur inspiration, reproduction, and original research.
2. **Define the evidence contract.** Specify the market, fields, resolution, provider, history requirement, request budget, and missing-data behavior needed to test the hypothesis.
3. **Freeze the executable experiment.** Fix the universe, dates, strategy semantics, costs, transformations, and acceptance criteria before the evaluation result is known.
4. **Capture and preserve the admitted evidence.** Keep the observations actually used, together with provenance and content identities, rather than assuming a future provider response will be identical.
5. **Evaluate deterministically.** The same frozen evidence and evaluator should produce the same result.
6. **Apply the predeclared verdict.** A strategy survives only if the criteria fixed in advance say it survives. A failed source gate, failed data-admission rule, or failed empirical criterion remains a distinct terminal outcome.
7. **Preserve the result and stop changing it.** A negative result is not permission to retune the same experiment. Any materially different question would require a newly frozen experiment.

This is not a claim that the workflow eliminates every form of research bias. It is a way to remove several particularly easy forms of hindsight.

## Source lineage comes before performance

A strategy should not appear on the site as if it emerged from nowhere.

When a case is based on external work, the public record should identify the original source, the exact frozen version when possible, and the relationship between that source and the experiment being discussed: **reproduced**, **derived**, or merely **inspired by**.

Benchmark 004 is the clearest example. Its target was the public `Momentum - Channel Breakout.ipynb` notebook in the `gm-clara/Stat-Arb-in-Crypto` repository at commit `fdb17c13b81ca007bac8ac59b55f14d9088d5a28`. The benchmark independently reimplemented the executed notebook behavior in Go rather than copying the notebook runtime.

That distinction exposed an important problem: written explanations and executable behavior can disagree. The audit found differences in volatility scaling, an inline volume-percentile description, transaction-cost wording, and other details. Benchmark 004 reproduced the **executed code** and recorded the discrepancies instead of silently choosing the cleaner description.

## Independent reproduction before novel claims

Benchmark 004 had two layers.

First, Benchmark 004A asked whether an independent implementation could reproduce the published display metrics from the commit-pinned archived input. Then Benchmark 004B replaced that archived input with independently captured official Binance Spot data over the same frozen 66-symbol panel.

The second step compared 449,856 high/low/close/volume field cells. The independently normalized panel matched the archived canonical panel exactly: no missingness disagreements, no numeric disagreements, and the same canonical SHA-256. The sealed evaluator then reproduced the target metrics, producing `FULL_REPLICATION_MATCH`.

That result established reproducibility of the specified executable object and its input evidence. It did **not** establish future profitability or live executability.

## Prospective freezing changes the question

Without a freeze, research easily becomes:

> “Can I find a version of this idea that looks good?”

With a prospective freeze, the question becomes:

> “Did the version I committed to in advance satisfy the criteria I committed to in advance?”

Research 005 applied that logic to the reproduced Benchmark 004 strategy. The universe, one-year protected period, executable semantics, transaction-cost rule, data provider contract, and survival criteria were fixed before the holdout was evaluated.

The result was awkward in exactly the useful way a prospective test should be awkward: the return was positive, but two required conditions failed. The terminal classification therefore stayed `FALSIFIED`.

## Data quality is part of the experiment

A strategy test is not only a formula applied to prices. Source completeness and provenance can determine whether the experiment is admissible at all.

The broader research record includes examples that stopped **before** empirical evaluation because a frozen source budget could not supply the required history, or because a real capture returned fewer rows than the prospectively required minimum. Those are not strategy falsifications. They are evidence-contract failures.

Keeping that distinction matters. Otherwise an engineering or source problem can be presented as market evidence, or quietly repaired after inspection.

## Deterministic evaluation is more than a Git commit

Keeping source code in version control is necessary but insufficient. Reproduction also depends on the exact input evidence, normalization rules, floating-point semantics, evaluator identity, and sometimes subtle ordering or missing-data behavior.

The research implementation therefore treated content hashes, immutable capture receipts, frozen specifications, and evaluator identities as part of the scientific record rather than incidental build metadata.

The objective is not ceremony. It is to make the question “what exactly produced this number?” answerable later.

## Falsification must be allowed to win

A process that can only produce “promising” results is not much of a test.

Research 005 produced a +5.26% compounded net return over its 365-day holdout and a +20.50% arithmetic annualized mean return, yet failed the frozen Sharpe and dependence-aware confidence requirements. Calling it a success because one number looked attractive would have replaced the experiment's decision rule after the fact.

The useful property of the workflow is that `FALSIFIED` remained a legitimate final state.

## Research software is not a trading runtime

The research system was deliberately separated from exchange credentials, runtime portfolio state, paper trading, and live execution. It could capture public evidence and evaluate research experiments, but a research result did not authorize capital deployment.

That boundary prevents two different questions from being conflated:

- **Is the research claim supported by its evidence?**
- **Should this strategy control real capital?**

Even a strategy that survived a research gate would still need separate execution, risk, market-structure, and operational qualification.

## What this publication will use the methodology for

Future pages will apply these controls in three ways: case studies of completed research outcomes, explanations of individual methodological choices, and engineering notes about reproducibility and evidence handling.

No new strategy discovery is implied by publishing those pages. The evidence base is the completed research program; the publishing work is to make its useful lessons inspectable without rewriting the experiments after the fact.
