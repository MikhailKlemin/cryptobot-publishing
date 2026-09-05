---
title: "When the prose and the code disagree"
description: "A reproduction problem from Benchmark 004: what should count as the strategy when comments, documentation, and executed notebook behavior do not line up?"
eyebrow: "Reproducibility"
summary: "Benchmark 004 reproduced an external channel-breakout notebook exactly enough to expose a harder question: when the written explanation and the executed program differ, which object are you actually testing?"
date: 2026-09-05
lastmod: 2026-09-05
source_case: "/research/benchmark-004/"
source_label: "Benchmark 004 reproduction case study"
---

Reproducing a trading strategy sounds straightforward until the source contains more than one version of the strategy.

A paper, README or notebook narrative may describe one rule. A nearby comment may describe a slightly different parameter. The code that actually produced the displayed result may do something else again. At that point, “reproduce the strategy” stops being a purely numerical task. You first have to decide **what the object of reproduction is**.

Benchmark 004 ran into exactly this problem while reproducing the public *Statistical Arbitrage in Cryptocurrencies* channel-breakout notebook. The source was pinned to a specific Git commit before reproduction. The audit then recorded disagreements between the explanatory text and the executed notebook path **before** the independent result was known.

That ordering mattered. A successful numerical match was not allowed to make the discrepancies disappear.

## The executable result is an object, not a story

For Benchmark 004, the reproduction target was the behavior that actually generated the published display metrics. That meant following the executed notebook code where prose, comments and code conflicted.

This is not the same as saying the code was necessarily the *best* interpretation of the author's intent. It is a narrower claim: if the goal is to reproduce an existing numerical result, silently “correcting” the implementation would create a different experiment.

The distinction is easy to miss because small discrepancies can look editorial rather than scientific. In this case, several of them changed portfolio behavior.

## A 30-day description became a 35-day calculation

The explanatory material described volatility using a 30-period rolling standard deviation. The executed holdout path used a **35-day sample standard deviation**.

Five days may not sound dramatic, but volatility enters portfolio sizing. Changing the lookback changes the sequence of weights, turnover, costs and returns. A reproducer who follows the prose has already stopped reproducing the executed result.

Benchmark 004 therefore preserved the 35-day behavior in its frozen executable specification and separately recorded the documentation mismatch.

## “Lower exposure to high volatility” was not what the notebook executed

The prose described volatility scaling in the familiar direction: reduce exposure as volatility rises, with additional EWMA smoothing.

The executed holdout path did something materially different. It multiplied positions by **the square root of rolling standard deviation**, then normalized the portfolio, and did not apply the described EWMA smoothing in that path.

That is not a cosmetic difference. It changes relative asset weights and therefore changes the strategy being evaluated.

The tempting response would be to implement what the prose appears to have intended. That might produce a more conventional strategy. It would not reproduce the result that was actually published.

## A “70th percentile” comment executed as 0.68

The notebook contained an inline description of a 70th-percentile volume threshold. The executable parameter was **0.68**.

This is a smaller discrepancy, but it illustrates the same problem. Comments are evidence about intent; they are not necessarily evidence about execution. If the displayed backtest was generated with 0.68, reproducing it with 0.70 changes the target.

The audit kept both facts visible: the code used 0.68, while the nearby wording said 70th percentile.

## “20 bps per trade” was actually a turnover formula

The source documentation summarized transaction cost as 20 basis points “per trade.” The executable portfolio calculation charged **20 bps multiplied by daily portfolio turnover**.

Those two descriptions are not automatically equivalent. In a multi-asset portfolio with continuous weight changes, turnover is a specific quantitative object. A vague “per trade” interpretation leaves room for several incompatible implementations.

Again, Benchmark 004 reproduced the formula that generated the result and recorded the wording discrepancy instead of resolving it after the fact.

## Not every ambiguity is a documentation typo

The source universe also depended on information that was difficult to reconstruct historically. The executable notebook required sufficient non-null close coverage over the full panel through August 2025 before evaluating the portfolio from 2024 onward. Later data availability could therefore influence which symbols appeared in an earlier evaluation period.

There was a second practical problem: the original data-selection path depended on then-current CoinGecko and Binance listings plus an older hourly file. Historical snapshots of that discovery process were not available in a form that could be recreated honestly later.

Benchmark 004 did not invent a substitute universe and call it equivalent. It froze the 66-symbol universe already present in the archived source, then asked a narrower question: could the underlying market fields for that frozen panel be independently recaptured from the official provider?

They could. The independent comparison covered **449,856 high/low/close/volume field cells with zero numeric and zero missingness disagreements**. That established reproducibility of the frozen input. It did not retroactively remove the universe-selection limitation.

## Why not fix the source before reproducing it?

Because reproduction and repair answer different questions.

A reproduction asks:

> Can an independent implementation recover the result produced by this defined object?

A repair asks:

> What should the strategy have been if we change something we now consider mistaken, ambiguous or unrealistic?

Both can be legitimate projects. Combining them is dangerous. Once a reproducer starts choosing the “better” interpretation of each discrepancy, the exercise quietly becomes strategy design.

That was the practical reason for the Benchmark 004 rule: **follow executed behavior for the reproduction target, but preserve disagreements as audit findings rather than laundering them into the reconstructed specification.**

## A useful reproduction discipline

The worked example suggests a compact set of rules for reproducing computational research:

1. **Pin the source.** A moving repository branch is not an immutable specification.
2. **Identify the path that actually produced the reported result.** Documentation alone may not be sufficient.
3. **Record prose/code/data disagreements before running the independent reproduction.** A successful match should not erase criticism.
4. **Reimplement independently rather than merely rerunning the original notebook.** Otherwise you mostly prove that the original environment can execute itself.
5. **Separate input reproduction from strategy reproduction.** Matching calculations against an archived dataset is different from independently recovering the dataset.
6. **Do not convert reproduction into repair.** Proposed corrections belong in a new experiment with a new specification.
7. **State what the match does not prove.** Reproducibility is not evidence of future profitability, realistic execution or methodological soundness.

## Why the distinction mattered later

Benchmark 004 ended with `FULL_REPLICATION_MATCH`. The executable behavior and the frozen data panel were reproducible, including the oddities documented by the audit.

That success still did not answer the question that mattered for future evidence: would the same frozen executable behavior survive a new period that had not been used to produce the historical result?

Research 005 took that next step. It carried the reproduced semantics into a new prospectively frozen 365-day holdout. The result was positive on some headline measures, but it failed two predeclared acceptance criteria and finished `FALSIFIED`.

That sequence is useful precisely because the two verdicts are not contradictory:

**Benchmark 004:** we can reproduce what this strategy did historically.  
**Research 005:** that reproduced object did not satisfy our later prospective survival rule.

Reproducibility made the second statement more meaningful. It did not make the strategy good.

## Inspect the worked example

The detailed [Benchmark 004 case study](/research/benchmark-004/) explains the two-stage reproduction and links the exact upstream notebook at its frozen commit.

The publication also exposes selected preserved evidence used for this note:

- [Predeclared audit findings](/evidence/benchmark-004/PREDECLARED_AUDIT_FINDINGS.md)
- [Frozen executable specification](/evidence/benchmark-004/FROZEN_EXECUTABLE_SPEC.md)
- [Independent input comparison](/evidence/benchmark-004/INPUT_COMPARISON.json)
- [Benchmark 004 evaluation](/evidence/benchmark-004/benchmark004b_evaluation.json)

No research was replayed for this article. It is an editorial explanation of already-preserved evidence from the closed research program.
