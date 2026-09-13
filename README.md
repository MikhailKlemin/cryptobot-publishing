# Backtest Discipline

Public Hugo source for **Backtest Discipline**, a technical publication about controlled trading-strategy evaluation, reproducibility, prospective freezing, provenance, and falsification.

The repository keeps its original `cryptobot-publishing` name so existing history and links remain intact. The underlying `cryptobot-research` program is closed; this repository publishes from that preserved record rather than continuing strategy discovery.

Public site: https://backtestdiscipline.com/

## Public state

Usable now:

- evidence-backed homepage and selective research record;
- detailed Benchmark 004 independent-reproduction case study;
- detailed Research 005 prospective-falsification case study;
- selected inspectable evidence artifacts with hashes;
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
hugo --minify
```

The generated site will be in `public/`.

## Publishing boundary

Do not turn positive historical metrics into claims of a deployable or guaranteed profitable strategy. Research 005 remains `FALSIFIED`, and no strategy was authorized for trading-runtime promotion.

Publishing changes may improve explanation, layout, evidence access, and provenance. They do not replay, retune, or silently extend the closed research program.
