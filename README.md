# cryptobot-publishing

Minimal Hugo site for publishing evidence-backed material from the closed `cryptobot-research` project.

## Current milestone

Milestone 002.2 is the final local polish pass before first deployment. It does not expand the site architecture.

Usable now:

- evidence-backed homepage with a restrained technical presentation;
- Benchmark 004 and Research 005 result panels with natural card heights;
- Research 005 acceptance metrics and terminal result in one compact 2×3 evidence grid;
- real methodology page;
- responsive, dependency-free presentation;
- keyboard-accessible skip link that stays out of the visual layout until focused;
- no JavaScript, analytics, CMS, database, external fonts, or paid services;
- public prose edited for a natural, concrete technical voice while remaining constrained by the final documented research handoff.

Not added yet:

- Research 005 long-form case study;
- detailed evidence/citation pages;
- custom domain;
- Cloudflare deployment configuration;
- analytics.

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
