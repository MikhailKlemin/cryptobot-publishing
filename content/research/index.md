---
title: "Research record"
description: "A selective record of empirical falsifications, pre-evaluation stops, and the reproduction and prospective milestones that closed the project."
---

Cryptobot Research was not a single strategy test. The research lineage contains many candidate mechanisms and several different kinds of terminal outcome. A preserved checkpoint recorded **16 completed empirical studies and 16 empirical falsifications**. Other candidates stopped earlier because a frozen source requirement, data-admission rule, or capability boundary could not be satisfied.

This page is deliberately selective. It does not turn every internal iteration into a public article. The entries below are included because they show materially different ways controlled research can end.

## Empirical falsification

### Attention-shock cycle

**Stage:** real-data deterministic evaluation  
**Outcome:** `FALSIFIED`

A bounded Binance research cycle reached evaluation on 1,000 rows and terminated as falsified. One public-data request and one evaluator invocation were recorded; qualification, export, product communication, paper orders, and live orders remained at zero.

The important point is procedural: the completed negative result became part of the research history rather than a prompt to retune the tested rule.

### Reference-price anchor adjustment

**Stage:** deterministic evaluation  
**Outcome:** `FALSIFIED`

A later proposal in the reference-price-anchor family generated 344 completed round trips under its frozen evaluator. Its required aggregate cost-adjusted return criterion failed, as did required chronological-block return criteria. The proposal was registered as falsified and was not sent to qualification.

These examples are representative, not an exhaustive list of the empirical falsifications in the lineage.

## Stopped before empirical evaluation

### Source-budget feasibility

**Stage:** prospective experiment freeze  
**Outcome:** `REJECTED BEFORE CAPTURE`

One accepted proposal required 100,000 historical rows for each symbol series. Its already-frozen request budget could supply only 4,000 rows per series, 12,000 rows in total. Cross-symbol aggregation was not allowed to disguise the shortfall.

The experiment therefore stopped before a public-data request was made. No evaluator was invoked. That is a negative research result, but it is not an empirical falsification: the hypothesis never reached its intended data test.

### Coinbase history completeness

**Stage:** data admission  
**Outcome:** `CLOSED BEFORE EVALUATION`

Another frozen experiment required at least 5,000 normalized rows per symbol. The real Coinbase capture produced 4,995. The five-row shortfall was not filled, the window was not shifted, and replacement history was not requested after inspection.

Because the frozen admission rule was not satisfied, the evaluator did not run. The distinction matters: failing a predeclared data contract is different from observing market evidence against a hypothesis.

## Closure milestones

### Benchmark 004 — independent reproduction

**Outcome:** `FULL_REPLICATION_MATCH`

Before the final prospective experiment, Benchmark 004 tested whether independently implemented research machinery could reproduce an externally specified strategy against official public data. It matched completely. The benchmark was a reproducibility test, not evidence that the strategy itself should be promoted.

### Research 005 — final prospective evaluation

**Outcome:** `FALSIFIED`

The final Research 005 experiment was frozen before evaluation. It finished with a positive annualized net return of **20.50%**, but the complete acceptance rule also required stronger risk-adjusted performance, a positive dependence-aware confidence bound, and recurring evidence across chronological folds. Net Sharpe was about **0.368** against a required minimum of **0.50**, the one-sided 95% HAC lower bound was negative, only **3 of 4** frozen folds were positive, and maximum drawdown was about **−29.59%**.

The positive headline return therefore did not override the frozen terminal rule. The result remained `FALSIFIED`, and no strategy was authorized for promotion into the separate trading runtime.

## How to read these outcomes

`FALSIFIED` is reserved here for an empirical proposal that reached its frozen evaluation and failed the predeclared survival criteria. A pre-capture feasibility rejection or a data-admission failure is reported separately because no empirical strategy verdict was produced. `FULL_REPLICATION_MATCH` belongs to a different category again: it says the independent reproduction machinery matched the specified behavior, not that a trading strategy was profitable or deployable.

Keeping those categories separate is part of the research method. It prevents a source failure from being presented as market evidence, a reproduction benchmark from being presented as alpha, or a positive-looking metric from replacing the acceptance rule that was fixed in advance.

## Why the record is selective

The internal research history contains more proposals, capability checks, source constraints, rejected discoveries, and implementation iterations than belong on a useful public page. Publishing all of them would blur the distinction between engineering history and research evidence.

The public record will grow only when an additional case teaches something distinct and can be tied cleanly to preserved evidence. The aim is not to maximize the number of strategy names on the site. It is to make the research process inspectable without overstating what any individual experiment demonstrated.
