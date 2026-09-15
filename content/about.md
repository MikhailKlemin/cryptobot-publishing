---
title: "About"
description: "What Backtest Discipline is, how the published evidence is handled, and where to raise corrections."
eyebrow: "About the publication"
---

I'm **Mikhail Klemin**. I built `cryptobot-research` to look for crypto trading strategies that could survive disciplined testing. That open-ended search ended. What I kept was the software and a more focused question: what happens when I independently test a strategy someone has already published?

Backtest Discipline is where I publish those individually scoped evaluations, alongside selected cases from the initial discovery phase. My aim is to understand what the evidence supports—not to find a winner for readers or prove that every strategy fails. I aim to publish roughly every two weeks, with timing depending on the work each case needs.

## What this site is for

The useful part of a trading experiment is not only the final return. It is also the chain of decisions that made the result interpretable: where the idea came from, what data were admitted, what executable behavior was frozen, what counted as success, and whether the same result could be reproduced independently.

That is the focus here. The [research record](/research/) shows concrete outcomes, [Methodology](/methodology/) explains the controls behind them, and the [engineering notes](/notes/) pull reusable lessons out of the preserved cases.

## What it is not

I build and use research software; that is different from operating a trading service. Backtest Discipline is not a trading-signal service, a managed fund, or a live trading bot. The research software is separate from the trading runtime, and publishing a result does not authorize a strategy to trade.

The site also does not treat historical backtest performance as evidence of guaranteed or deployable profitability. A reproduction can succeed while the underlying methodology still has limitations; a strategy can show a positive headline return and still fail the acceptance rule that was frozen before evaluation.

## Evidence policy

Concrete research claims published here are tied to preserved evidence. Where it helps a reader inspect a case directly, I publish selected frozen specifications, decision rules, deterministic evaluation outputs, hashes, and later publication reports. These are **selected artifacts, not a complete rerun package**: they let readers inspect parts of the evidence and decision process, but do not by themselves supply everything needed to reproduce a run.

Those publication reports are summaries created after the relevant experiments had closed. They are not presented as original runtime artifacts, and generating them did not replay, retune, recapture, or re-evaluate the experiments.

Raw provider payloads, private machine paths, binaries, credentials, and internal runner material are not published merely because they exist. The aim is useful transparency, not indiscriminate release of development artifacts.

## Maintainer and source

I maintain Backtest Discipline independently as a single-person publishing project.

The public publishing source is available on [GitHub](https://github.com/MikhailKlemin/cryptobot-publishing). The repository contains the Hugo site, editorial source, selected public evidence, and the publication-report provenance used by this website. The repository keeps its original `cryptobot-publishing` name so existing history and links remain intact; **Backtest Discipline** is the public publication name.

## Corrections and contact

For a factual correction, broken evidence link, question about a published claim, or other publication-related contact, email [contact@backtestdiscipline.com](mailto:contact@backtestdiscipline.com).

For corrections that benefit from public tracking, you can also [open an issue in the publishing repository](https://github.com/MikhailKlemin/cryptobot-publishing/issues). Referencing the page and the relevant evidence artifact or hash, when applicable, makes the issue easier to check.

A separate contact form is intentionally not part of the site at this stage. The project is kept small and static unless a real publishing need justifies additional infrastructure.

## The research boundary

New published-strategy evaluations continue in `cryptobot-research`, each with its own scope and frozen test. Completed experiments stay closed: an article does not silently change their data, parameters, holdouts, or verdicts. Additional empirical work requires explicit authorization in the research project, not an editorial change to this site.
