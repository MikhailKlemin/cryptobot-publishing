# Backtest Discipline

Public Hugo source for **Backtest Discipline**, Mikhail Klemin's independent publication testing selected published trading strategies and explaining their evidence, implementation, and limitations.

Mikhail built `cryptobot-research` to find strategies that survived disciplined testing. That open-ended discovery phase has ended; individually scoped evaluations of published strategies continue in the research project. This site publishes those results alongside selected historical cases, without a preferred pass/fail outcome. The publishing aim is roughly one new evaluation every two weeks, not a guaranteed schedule.

The repository keeps its original `cryptobot-publishing` name so existing history and links remain intact. **Backtest Discipline** is the public publication name.

Public site: https://backtestdiscipline.com/

## Public state

Usable now:

- evidence-backed homepage and selective research record covering ongoing evaluations and historical cases;
- published BTC trend-following out-of-sample evaluation (Published Strategy Replication 001);
- detailed Benchmark 004 independent-reproduction case study;
- detailed Research 005 frozen-holdout falsification case study;
- selected inspectable evidence artifacts with hashes, not a complete research rerun package;
- practical methodology page;
- engineering notes grounded in preserved cases;
- downloadable publication reports for Benchmark 004 and Research 005;
- About page with maintainer, evidence policy, source, and correction route;
- custom domain on Cloudflare Workers + Static Assets;
- canonical and social metadata tied to the public domain;
- responsive static presentation with no CMS, database, external fonts, or application backend.

## Run locally

Requires Hugo.

```bash
hugo server -D
```

Build production output:

```bash
hugo --minify --panicOnWarning
```

The generated site will be in `public/`. Deploy that directory only, not the repository root.

Research articles use an ISO `date` for the original publication date; the homepage automatically features the newest research article by that date. Optional `card_title` and `card_summary` provide concise homepage wording. Editorial revisions must not change the original date. The RSS feed includes research articles and engineering notes, not undated information pages.

## Publishing boundary

Do not turn positive historical metrics into claims of a deployable or guaranteed profitable strategy. Research 005 remains `FALSIFIED`, and no strategy in the published record was authorized for trading-runtime promotion. Historical closure refers to the initial discovery phase, not the end of individually scoped published-strategy testing.

Publishing changes may improve explanation, layout, evidence access, and provenance. They do not replay, retune, or silently extend completed experiments. Building or publishing this site grants no automatic authority to capture market data, run evaluations, change research criteria, or operate the separate trading runtime. New empirical work requires its own explicit scope and authorization in `cryptobot-research`.
