---
title: "Methodology"
description: "How selected published strategies are independently evaluated: source selection, reproduction, out-of-sample tests, frozen rules, and evidence limits."
---

I use `cryptobot-research` to independently evaluate selected published trading strategies. The open-ended discovery phase has ended; individually scoped evaluations continue. The question is what a specified test supports, not how to find winners or accumulate failures.

A backtest becomes difficult to trust when its data, executable rules, cost model, and definition of success can all move after the result is visible. The controls below keep those choices explicit and fixed, whether the outcome is favorable, unfavorable, or insufficient to support a conclusion.

## The controlled research loop

Each evaluation follows a controlled loop:

1. **State the hypothesis and its origin.** Record whether the idea came from an external publication, an internal mechanism, or another source. Do not blur inspiration, reproduction, and original research.
2. **Define the evidence contract.** Specify the market, fields, resolution, provider, history requirement, request budget, and missing-data behavior needed to test the hypothesis.
3. **Freeze the executable experiment.** Fix the universe, dates, strategy semantics, costs, transformations, and acceptance criteria before capture and evaluation. Record the freeze timing and any prior exposure to the data; do not imply that historical observations were still in the future.
4. **Capture and preserve the admitted evidence.** Keep the observations actually used, together with provenance and content identities, rather than assuming a future provider response will be identical.
5. **Evaluate deterministically.** The same frozen evidence and evaluator should produce the same result.
6. **Apply the predeclared verdict.** Report whether the frozen criteria pass or fail, without changing the rule to favor either result. A source or data-admission failure is not an empirical strategy verdict.
7. **Preserve the result and stop changing it.** A negative result is not permission to retune the same experiment. Any materially different question would require a newly frozen experiment.

This is not a claim that the workflow eliminates every form of research bias. It is a way to remove several particularly easy forms of hindsight.

## Source selection and lineage {#source-lineage-comes-before-performance}

I select published strategies with an identifiable source, rules specific enough to implement or clarify explicitly, and data requirements that can be met within a bounded test. The claim must be testable against a stated benchmark or decision rule. Selection is not a representative survey of all strategies, nor an endorsement of the source's performance claims.

If an essential rule or input cannot be established, that limitation must be reported rather than filled in after seeing the result. A strategy should not appear on the site as if it emerged from nowhere.

When a case is based on external work, the public record should identify the original source, the exact frozen version when possible, and the relationship between that source and the experiment being discussed: **reproduced**, **derived**, or merely **inspired by**.

Benchmark 004 is the clearest example. Its target was the public `Momentum - Channel Breakout.ipynb` notebook in the `gm-clara/Stat-Arb-in-Crypto` repository at commit `fdb17c13b81ca007bac8ac59b55f14d9088d5a28`. The benchmark independently reimplemented the executed notebook behavior in Go rather than copying the notebook runtime.

That distinction exposed an important problem: written explanations and executable behavior can disagree. The audit found differences in volatility scaling, an inline volume-percentile description, transaction-cost wording, and other details. Benchmark 004 reproduced the **executed code** and recorded the discrepancies instead of silently choosing the cleaner description.

## Original-result reproduction versus out-of-sample extension {#independent-reproduction-before-novel-claims}

**Reproduction** asks whether an independent implementation can match a specified original result using the original period and inputs. **Out-of-sample extension** asks how a published mechanism behaves on a different period under an explicitly defined test. An extension is not evidence that the original performance table was reproduced; changes in data, execution assumptions, or costs must be visible.

[Published Strategy Replication 001](/research/published-strategy-replication-001/) is a subsequent out-of-sample evaluation, not a reproduction of the paper's historical table. Benchmark 004, by contrast, had two reproduction layers.

First, Benchmark 004A asked whether an independent implementation could reproduce the published display metrics from the commit-pinned archived input. Then Benchmark 004B replaced that archived input with independently captured official Binance Spot data over the same frozen 66-symbol panel.

The second step compared 449,856 high/low/close/volume field cells. The independently normalized panel matched the archived canonical panel exactly: no missingness disagreements, no numeric disagreements, and the same canonical SHA-256. The sealed evaluator then reproduced the target metrics, producing `FULL_REPLICATION_MATCH`.

That result established reproducibility of the specified executable object and its input evidence. It did **not** establish future profitability or live executability.

## Freeze timing is not a forward-test timeline {#prospective-freezing-changes-the-question}

Freezing rules before capture and evaluation limits opportunities to change a test after inspecting its result. It does **not** mean the market observations occurred after the freeze. A truly forward test fixes the rules before the tested observations occur; live trading additionally involves actual order execution. A historical post-sample evaluation establishes neither.

Each case should distinguish the original sample dates, source publication date, evaluation period, and freeze/capture timing where documented. In Published Strategy Replication 001, the evaluation begins after the paper's sample ends but before the paper's publication date, so not all observations are post-publication.

The controlled question is:

> “Did the fixed version satisfy the fixed criteria on the specified evidence?”

Research 005 applied that logic to the reproduced Benchmark 004 strategy. The universe, one-year protected period, executable semantics, transaction-cost rule, data provider contract, and survival criteria were fixed before the holdout was evaluated.

The return was positive, but two required conditions failed. The terminal classification therefore stayed `FALSIFIED`. The before-evaluation freeze should not be read as a claim that the strategy was monitored forward or traded live.

## Data quality is part of the experiment

A strategy test is not only a formula applied to prices. Source completeness and provenance can determine whether the experiment is admissible at all.

The broader research record includes examples that stopped **before** empirical evaluation because a frozen source budget could not supply the required history, or because a real capture returned fewer rows than the prospectively required minimum. Those are not strategy falsifications. They are evidence-contract failures.

Keeping that distinction matters. Otherwise an engineering or source problem can be presented as market evidence, or quietly repaired after inspection.

## Deterministic evaluation is more than a Git commit

Keeping source code in version control is necessary but insufficient. Reproduction also depends on the exact input evidence, normalization rules, floating-point semantics, evaluator identity, and sometimes subtle ordering or missing-data behavior.

The research implementation therefore treated content hashes, immutable capture receipts, frozen specifications, and evaluator identities as part of the scientific record rather than incidental build metadata.

The objective is not ceremony. It is to make the question “what exactly produced this number?” answerable later.

## The outcome is not the objective {#falsification-must-be-allowed-to-win}

A useful test must allow a strategy to pass or fail its stated criteria. Inconclusive evidence and inability to evaluate also need honest descriptions; neither establishes that a strategy works or that it cannot work.

Research 005 produced a +5.26% compounded net return over its 365-day holdout and a +20.50% arithmetic annualized mean return, yet failed the frozen Sharpe and dependence-aware confidence requirements. Calling it a success because one number looked attractive would have replaced the experiment's decision rule after the fact.

`FALSIFIED` remained the correct outcome for that frozen test, not a verdict on every possible implementation or market period. A passing result would likewise support only the claim actually tested.

## Research software is not a trading runtime

The research system was deliberately separated from exchange credentials, runtime portfolio state, paper trading, and live execution. It could capture public evidence and evaluate research experiments, but a research result did not authorize capital deployment.

That boundary prevents two different questions from being conflated:

- **Is the research claim supported by its evidence?**
- **Should this strategy control real capital?**

Even a strategy that survived a research gate would still need separate execution, risk, market-structure, and operational qualification.

## What readers can inspect {#what-this-publication-will-use-the-methodology-for}

New published-strategy evaluations and selected historical cases use these distinctions to explain what was tested, what happened, and what remains uncertain. Engineering notes explore the implementation choices behind those results.

The site publishes selected evidence artifacts, not a complete rerun package. A deterministic internal evaluation does not mean the public excerpts alone are sufficient to reproduce it. Later publication reports explain completed work; they do not rerun or amend the experiment.
