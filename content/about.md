---
title: "About"
description: "What Cryptobot Research is, how the published evidence is handled, and where to raise corrections."
eyebrow: "About the publication"
---

Cryptobot Research is an independent technical publication built from a completed crypto strategy-research program. The research program itself is closed; this site turns the preserved work into case studies, methodology, engineering notes, and selected evidence that can be inspected without reopening strategy discovery.

## What this site is for

The useful part of a trading experiment is not only the final return. It is also the chain of decisions that made the result interpretable: where the idea came from, what data were admitted, what executable behavior was frozen, what counted as success, and whether the same result could be reproduced independently.

That is the focus here. The [research record](/research/) shows concrete outcomes, [Methodology](/methodology/) explains the controls behind them, and the [engineering notes](/notes/) pull reusable lessons out of the preserved cases.

## What it is not

Cryptobot Research is not a trading-signal service, a managed fund, a live trading bot, or an ongoing strategy-discovery project. No strategy from the closed research program was authorized for promotion into the separate trading runtime.

The site also does not treat historical backtest performance as evidence of guaranteed or deployable profitability. A reproduction can succeed while the underlying methodology still has limitations; a strategy can show a positive headline return and still fail the acceptance rule that was frozen before evaluation.

## Evidence policy

Concrete research claims published here are tied to preserved evidence. Where it helps a reader inspect a case directly, the site exposes selected frozen specifications, decision rules, deterministic evaluation outputs, hashes, and later publication reports.

Those publication reports are summaries created after research closure. They are not presented as original runtime artifacts, and generating them did not replay, retune, recapture, or re-evaluate the experiments.

Raw provider payloads, private machine paths, binaries, credentials, and internal runner material are not published merely because they exist. The aim is useful transparency, not indiscriminate release of development artifacts.

## Maintainer and source

Cryptobot Research is maintained independently by **Mikhail Klemin** as a single-person publishing project.

The public publishing source is available on [GitHub](https://github.com/MikhailKlemin/cryptobot-publishing). The repository contains the Hugo site, editorial source, selected public evidence, and the publication-report provenance used by this website.

## Corrections and contact

For a factual correction, broken evidence link, or question about a published claim, please [open an issue in the publishing repository](https://github.com/MikhailKlemin/cryptobot-publishing/issues). Referencing the page and the relevant evidence artifact or hash, when applicable, makes the issue easier to check.

A separate contact form is intentionally not part of the site at this stage. The project is kept small and static unless a real publishing need justifies additional infrastructure.

## The research boundary

Publishing can explain the closed record more clearly, but it does not silently extend it. If a future article would require new market data, new strategy parameters, a new holdout, or another empirical test, that would be a proposal to reopen research work explicitly rather than an editorial update to this site.
