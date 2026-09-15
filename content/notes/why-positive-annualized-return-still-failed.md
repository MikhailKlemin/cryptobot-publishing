---
title: "Why a +20.5% annualized return still failed our strategy test"
description: "A frozen holdout test finished with positive headline returns and still failed. Return was only one part of a decision rule fixed before evaluation."
lead: "The protected holdout recorded a +5.26% compounded net return and a +20.50% arithmetic annualized mean return. It still finished FALSIFIED because two required acceptance criteria did not pass."
eyebrow: "Lesson from a frozen holdout test"
summary: "A positive return describes one dimension of a backtest. It does not override a multi-criterion acceptance rule that was fixed before the result was known."
date: 2026-09-14
lastmod: 2026-09-15
source_case: "/research/research-005/"
source_label: "Research 005 — frozen holdout case study"
editorial_update: "15 September 2026: clarified that the experiment was frozen before capture/evaluation, which does not by itself establish a forward-running test. The recorded metrics and terminal outcome are unchanged."
---

At first glance, the result looks contradictory.

[Research 005](/research/research-005/) ended its protected one-year evaluation with a **+5.26% compounded net return**. The evaluator also reported a **+20.50% annualized net return**. Yet the terminal verdict was `FALSIFIED`.

Nothing was wrong with the arithmetic. The apparent contradiction comes from treating two different questions as if they were the same:

> Did the strategy make money in this holdout?

and

> Did the frozen experiment satisfy the conditions required to survive?

For this test, the answer to the first question was yes. The answer to the second was no.

That distinction is more useful than the headline return.

## The 20.5% number needs a label

The first thing to clarify is what **+20.50% annualized net return** actually means in this experiment.

It was not a 20.5% increase in portfolio value over the protected period. The frozen evaluator defined annualized net return as:

`mean daily net return × 365`

The actual compounded change in wealth over the 365 evaluation rows was **+5.26%**.

Those numbers are not supposed to be equal. One is an arithmetic annualization of the average daily return; the other is the compounded path actually recorded by the evaluator. Volatility and the sequence of daily gains and losses separate the two.

So the clean reading of the result is not “the strategy made 20.5%.” It is:

- compounded net return over the holdout: **+5.26%**;
- arithmetic annualized mean net return: **+20.50%**.

That already makes the headline less dramatic. It still leaves a positive result, but it describes the result accurately.

The difference between gross and net performance matters too. Before the frozen turnover cost, cumulative return was **+28.39%**. After the fixed cost model, it was **+5.26%**. The frozen evaluation did not respond to that gap by lowering the cost assumption after seeing the result. The cost rule was part of the experiment.

## Positive return was necessary, not sufficient

Before the holdout was evaluated, the experiment defined seven survival criteria. `SURVIVED_RESEARCH` required **all seven** to pass.

The strategy passed five:

- exactly 365 evaluation rows;
- annualized net return greater than zero;
- at least three of four chronological folds with positive mean net return;
- maximum drawdown better than −50%;
- all required deterministic metrics finite.

It failed two:

- net Sharpe had to be at least **0.50**;
- the one-sided 95% Bartlett-HAC lower bound on mean daily net return had to be above zero.

The recorded Sharpe was about **0.368**. The HAC lower bound was about **−0.1002% per day**.

Once those numbers existed, there was no extra clause saying “unless cumulative return is positive.” Positive return was already represented by its own criterion. It could not be counted twice and used to erase failures elsewhere.

This is what freezing the decision rule before evaluation changes. If the rule is written only after the result appears, almost any attractive number can become the reason to accept the strategy. If the rule is frozen first, the result has to meet the rule rather than negotiate with it.

Freezing before capture and evaluation does not by itself mean the historical market observations occurred after commitment. This should not be read as evidence of a forward-monitored or live-traded strategy.

## Why the Sharpe failure mattered

The Sharpe criterion asked a different question from cumulative return.

A positive cumulative return tells us where the compounded path ended relative to where it started. Sharpe relates average return to observed variability. The experiment used its own frozen definition and threshold: annualized net return divided by annualized net volatility, with survival requiring a value of at least **0.50**.

The result was **0.368**.

That does not mean 0.50 is a universal boundary between a good and bad strategy. It was simply the boundary this experiment committed to in advance. A different research program could reasonably choose a different threshold, provided it made that choice before looking at the protected result.

Here, the failure says something narrower: the amount of return recorded in the holdout was not high enough relative to its observed variability to satisfy the experiment's predeclared requirement.

That is important because a modest positive terminal gain can coexist with a rough path. The evaluation recorded a maximum drawdown of about **−29.59%**. The drawdown criterion itself passed because the frozen boundary was −50%, but the path still helps interpret the +5.26% net gain: the experiment reached that gain while experiencing a peak-to-trough decline of nearly thirty percent.

Passing the drawdown gate did not make that path disappear, and it did not compensate for the failed Sharpe gate.

## What the negative HAC lower bound actually says

The second failure is easier to overstate.

The frozen evaluation used a one-sided 95% Bartlett-HAC lower confidence bound on mean daily net return. The calculation was fixed in advance, including a **33-day lag** and the requirement to use all 365 physical daily returns. HAC was used so that the uncertainty calculation could account for serial dependence and changing variance rather than treating the daily observations as independent with constant variance.

The resulting lower bound was approximately **−0.1002% per day**.

Under the frozen decision rule, survival required that lower bound to be strictly above zero. It was not, so the criterion failed.

What does that mean?

It means the experiment did **not establish the required positive lower confidence bound** on mean daily net return under its chosen estimator and confidence rule.

It does **not** mean the calculation proved that the strategy's true expected return is negative. It does not convert a positive sample mean into proof of negative profitability. It says that, given the variability and dependence present in this sample, the experiment's required level of statistical support for a positive mean was not reached.

That difference matters. “The lower bound crossed zero” is a statement about uncertainty under a specified procedure. “The true return is negative” would be a much stronger claim, and this result does not establish it.

## Three positive folds were encouraging — and still not enough

The 365-day holdout was also split into four frozen chronological blocks.

Their mean daily net returns were approximately:

- fold 1: **+8.89 basis points/day**;
- fold 2: **+14.06 bps/day**;
- fold 3: **−14.27 bps/day**;
- fold 4: **+14.00 bps/day**.

Three of the four were positive, so the fold criterion passed exactly as specified.

That is useful evidence. Positive performance was not confined to a single short interval. But the folds were never designed to override the other tests. They were one component of a multi-criterion decision.

The negative third fold also prevents an overly smooth story about persistence. The experiment showed positive means in most blocks, one materially negative block, a positive full-period return, weak risk-adjusted performance relative to its threshold, and a confidence bound that did not clear zero.

Those facts can all be true at the same time.

## The experiment was designed to prevent the obvious rescue

After seeing the result, there are several tempting arguments one could make:

“0.368 is not that far from 0.50.”

“Three of four folds were positive.”

“The strategy made money after costs.”

“The HAC rule may be too conservative.”

“The drawdown limit passed.”

Any of those observations can motivate a later discussion about research design. None of them can change the verdict of this experiment.

The frozen decision specification explicitly prohibited post-result rescue by changing the criteria, costs, parameters, universe, dates, provider, fold selection, direction, or signal. If valid evidence existed and any required survival criterion failed, the terminal outcome was `FALSIFIED`.

That rule is what gives the result meaning.

Without it, “acceptance criteria” are easily reduced to a menu from which the favorable metrics are selected afterward. With it, an attractive number remains evidence, but it loses the power to rewrite the question.

## Describing a result is not the same as accepting it

This case is a useful example of a distinction that is easy to blur in backtesting.

A descriptive statement can be completely true:

> The strategy produced a positive net return over this holdout.

A decision statement can also be completely true:

> The strategy failed the experiment's frozen survival rule.

There is no paradox unless “made money” is treated as synonymous with “passed.” The test deliberately did not use that definition.

It was not asking whether at least one metric looked favorable. It was asking whether one frozen executable strategy, on one frozen 66-symbol universe, over the protected period from **1 September 2025 through 31 August 2026**, satisfied all seven conditions committed to before evaluation.

It did not.

The terminal result was therefore `FALSIFIED`, and no strategy was authorized for promotion into a trading runtime. The experiment involved neither paper nor live orders.

## What a backtest developer can borrow from this

The most reusable part of this case is not its channel-breakout logic. It is the separation between measurement and decision.

Before opening a holdout, write down what would count as survival. Include more than the metric you expect to look best. Define transaction costs, data handling, risk metrics, uncertainty treatment and any stability checks before the result can influence those choices.

Then keep the outputs descriptive. A positive return is a positive return. A failed confidence criterion is a failed confidence criterion. A passing drawdown gate is a passing drawdown gate. Do not collapse them into a single story until the predeclared decision rule has been applied.

Most importantly, allow the process to end with a result you would not have chosen after seeing the numbers.

That is what happened here. The +5.26% cumulative net return remains part of the record. So does the +20.50% arithmetic annualization. Neither was deleted or dismissed because the experiment failed.

But neither was allowed to overrule the two failed conditions either.

For the complete experiment record, see [Research 005](/research/research-005/). The broader workflow is described in [Methodology](/methodology/). The frozen rules and terminal outputs are available directly in the public evidence files: [decision specification](/evidence/research-005/FROZEN_DECISION_SPEC.md), [deterministic evaluation](/evidence/research-005/EVALUATION.json), [experiment definition](/evidence/research-005/RESEARCH_005_EXPERIMENT.json), and [terminal result](/evidence/research-005/RESEARCH_005_RESULT.json).

A concise six-page version is also available as the [Research 005 frozen holdout evaluation report](/reports/research-005-prospective-evaluation-report.pdf).

No research was replayed, retuned or extended for this article. It is an editorial explanation of already-preserved evidence from the completed Research 005 experiment.
