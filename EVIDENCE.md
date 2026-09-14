# Editorial evidence map

This file is internal publishing guidance and is not rendered by Hugo.

Authoritative source used for the initial site:

- `cryptobot-research-final-documented-handoff-20260905T113648Z.tar.gz`
- final documented HEAD: `a4d22c3cfa15aee7cbe00fee794e8c693adb931a`
- final documented root tree: `82dc4a7b2d602c6a3801bceca9351384294c55ab`
- source documents: handoff `README_FIRST.md`, tracked-source root `README.md`, and `context/FINAL_VALIDATION.txt`

Initial claims mapped to source evidence:

- Research is closed; durable outcome is controlled research/reproducibility/falsification methodology: tracked-source `README.md`, "Project evolution and durable outcome".
- Benchmark 004 reached `FULL_REPLICATION_MATCH`: tracked-source `README.md`, "Final scientific state".
- Research 005 period, frozen 66-symbol universe, +20.50% annualized net return, ~0.368 Sharpe, negative one-sided 95% HAC lower bound, 3/4 positive folds, ~-29.59% max drawdown, terminal `FALSIFIED`: tracked-source `README.md`, "Final scientific state".
- No promotion into trading runtime; research repository is not a trading bot/runtime: tracked-source `README.md`, opening and "Scientific and authority boundaries".
- `DISCOVERY_RECLOSED=true` and zero provider/network/order actions during final validation: `context/FINAL_VALIDATION.txt`.

## Research record additions

The public research record uses selected preserved historical evidence in addition to the final closure summary. It deliberately distinguishes completed empirical falsifications from proposals that stopped before evaluation.

- A later stable-continuation research checkpoint records `completed_empirical_research: 16` and `completed_empirical_falsifications: 16`. Source artifact: `sol-proposal18-discovery-to-public-gate.log`. Publish this as a preserved checkpoint, not as a claim that every internal proposal or engineering iteration was a distinct strategy.
- Attention-shock example: Iteration 038 immutable terminal `e7dec1573dd81f5609734e5396b11ae94ce97af9c6e3772c6c028b53d8121462`; result `profile_complete_cycle_falsified`, decision `falsified`, 1,000 rows, one public-data request, one evaluator invocation, zero qualification/export/product/paper/live actions. Source artifacts: `iteration038-real-cycle.log` and its offline verification log.
- Reference-price-anchor example: Iteration 103 proposal family `spot_reference_price_anchor_adjustment`; deterministic evaluation produced 344 completed round trips and failed frozen aggregate cost-adjusted return and chronological-block criteria; terminal state `PROPOSAL_FALSIFIED`; no qualification. Source artifact: `iteration103-evaluation.log`.
- Source-budget feasibility example: Iteration 043 terminal `falsified_source_budget_incompatibility_before_capture`, reason `INSUFFICIENT_SOURCE_HISTORY_UNDER_FROZEN_BUDGET`; 100,000 required rows per symbol, 12,000 maximum total rows under the frozen budget, 4,000 planned rows per series, no public capture or evaluation. Source artifact: `cryptobot-research-iteration043-continuation-prompt.md`, which records the immutable terminal for continuation. Public wording uses `REJECTED BEFORE CAPTURE` rather than calling this an empirical falsification.
- Coinbase completeness example: Iteration 049 proposal `93da4e6f...` terminated because the real normalized capture contained 4,995 rows per symbol against the prospectively frozen 5,000-row minimum. The gap was not filled, the window was not extended, and the evaluator did not run. Source artifact: `cryptobot-research-post-iteration049-continuation-prompt.md`. Public wording uses `CLOSED BEFORE EVALUATION` rather than calling this an empirical falsification.

## Benchmark 004 detailed provenance

Authoritative uploaded bundle inspected for this publishing iteration:

- `benchmark-004b-result-20260905T085552Z.tar.gz`
- `RESULT_MANIFEST.sha256` contains 154 file entries; all 154 SHA-256 entries were independently checked against the uploaded bundle and matched.
- Benchmark 004B terminal result: `FULL_REPLICATION_MATCH`.
- External frozen source commit: `fdb17c13b81ca007bac8ac59b55f14d9088d5a28` in public GitHub repository `gm-clara/Stat-Arb-in-Crypto`.
- Exact source notebook used for the channel-breakout target: `Momentum/Momentum - Channel Breakout.ipynb` at that commit.
- The external repository describes a broader project named `Statistical Arbitrage in Cryptocurrencies`; Benchmark 004 reproduced only the channel-breakout target, not every strategy in the repository.
- `FROZEN_EXECUTABLE_SPEC.md` states that Benchmark 004A follows executed notebook code when explanatory prose conflicts with code. It records the independently reconstructed executable semantics, including 46/35 entry channels, asymmetric exits, 50-day volume quantile 0.68, reproduced 33-day post-hoc position mask, 35-day sample-volatility scaling, and turnover-based 20 bps cost.
- `PREDECLARED_AUDIT_FINDINGS.md` records methodology/documentation discrepancies before reproduction: full-sample availability filtering, prose/code disagreement on volatility scaling and smoothing, 0.68 versus "70th percentile" wording, spot-price shorting limitations, and "per trade" wording versus executable turnover cost. These findings must not be erased by the successful numerical match.
- Benchmark 004B capture contract freezes 66 Binance Spot symbols, 2021-01-01 through 2025-08-31, two requests per symbol, maximum 132 requests, zero automatic retries, no credentials, and no alternate-provider fallback.
- `CAPTURE_RECEIPT.json` records all 132 authorized requests executed successfully.
- `INPUT_COMPARISON.json` records 1,704 dates, 66 symbols, four fields per date/symbol, 449,856 compared field cells, zero missingness disagreements, zero numeric disagreements, zero differing rows, max absolute difference 0, and identical canonical SHA-256 values.
- The exact sealed Benchmark 004A evaluator binary was reused without rebuild against the independently captured canonical input.
- Benchmark 004A reproduced the source notebook's published display metrics; these are historical reproduction targets, not proof of future profitability or live executability.

The public source link points to the exact channel-breakout notebook at the frozen source commit rather than the moving default branch.

## Research 005 detailed case study

Authoritative terminal bundle inspected for the detailed public page:

- `research-005-result-20260905T093254Z.tar.gz`
- `RESULT_MANIFEST.sha256` lists 89 files; all 89 SHA-256 entries were independently checked against the uploaded bundle before drafting the case study and matched.
- `RESEARCH_005_RESULT.json` records terminal outcome `FALSIFIED`, reasons `hac_one_sided_95_lower_bound_positive` and `net_sharpe_at_least_0_50`, `discovery_reclosed=true`, 66 provider requests, one evaluator invocation, zero external-AI/qualification/export/product/paper/live-order actions, and complete capture.
- `EVALUATION.json` records: 365 rows; mean daily net return `0.0005616657171424867`; annualized net return `0.20500798675700765`; annualized net volatility `0.5573360727415418`; net Sharpe `0.3678354888255685`; gross cumulative return `0.28390069811311824`; net cumulative return `0.05258496063130158`; maximum drawdown `-0.2958996939666908`; maximum drawdown duration 207 days; average turnover `0.27154153337636683`; one-sided 95% HAC lower bound `-0.0010016019807964668`; HAC lag 33; 3/4 positive folds.
- Frozen fold mean daily net returns: fold 1 `0.0008886449401567116`, fold 2 `0.0014062885237440038`, fold 3 `-0.0014267178944449188`, fold 4 `0.0014003627864643373`.
- `FROZEN_DECISION_SPEC.md` defines `SURVIVED_RESEARCH` as all seven deterministic requirements passing: 365 rows, positive annualized net return, net Sharpe >= 0.50, positive one-sided 95% HAC lower bound, at least 3/4 positive folds, maximum drawdown > -0.50, and all required metrics finite. It explicitly prohibits post-result rescue via changed criteria, costs, parameters, universe, dates, provider, fold removal, alternate signal, or direction reversal.
- `FROZEN_STRATEGY_SPEC.md` records the exact reproduced executable semantics: prior 46-day long channel, prior 35-day short channel, prior 50-day volume window at quantile 0.68, asymmetric exit channels, reproduced 33-day post-hoc time mask, `sqrt(rolling_std)` portfolio scaling, and frozen cost `turnover × 20e-4`.
- `RESEARCH_005_EXPERIMENT.json` freezes a 66-symbol universe and protected holdout 2025-09-01 through 2026-08-31 with official Binance Spot public REST, maximum 66 requests, zero automatic retries, no credentials, and no alternate-provider fallback.
- `CAPTURE_RECEIPT.json` records 66/66 successful provider requests with zero retries and complete capture. 65 symbol responses contain 365 klines; `OMUSDT` contains 183. The frozen strategy/capture semantics already permit legitimate venue-bar absence as missing data, so this should not be described as an ad-hoc repair or post-hoc universe change.
- The public charts `research-005-gross-net.svg` and `research-005-fold-means.svg` are editorial renderings of values already present in `EVALUATION.json`; they are not a replay, optimization, or new empirical evaluation.

## Published Strategy Replication 001 — Le & Ruthbah BTC trend following

Authoritative publishing sources for this page:

- uploaded paper `Trend-following-Strategies-for-Crypto-Investors.pdf`, Trinh Le and Ummul Ruthbah, August 2023;
- uploaded terminal artifact `published-strategy-replication-001-evaluation.json`;
- uploaded terminal artifact `published-strategy-replication-001-research-result.json`.

Publication evidence and wording constraints:

- The paper's historical BTC source is an S&P Bitcoin index series backed by Lukka Prime, with the reported BTC sample ending 31 January 2023. The paper studies 20, 65, 150 and 200-day trend horizons and reports historically strong trend-following results, especially for shorter horizons. It separately evaluates transaction costs at 0.1%, 0.25% and 0.5%.
- The paper is dated August 2023, while the replication evaluation period begins 1 February 2023. Therefore the public article must describe the new period as subsequent out-of-sample / post-sample data, not claim that every evaluation observation is post-publication data.
- Replication source/data contract: BTCUSDT, official Binance Spot public daily klines, one-day frequency, LONG / FLAT semantics, 20/65/150/200-day published lookbacks, warm-up/capture beginning 16 July 2022, 1509/1509 expected bars, two public provider requests, 0.1% transaction cost per traded leg.
- Timing contract: signal only after a completed UTC daily bar; target changes effective at the following UTC daily open. This was the prospectively frozen conservative implementation because the paper does not specify exchange execution timing precisely enough for a literal tradable implementation.
- Benchmark: cost-adjusted BTC buy-and-hold under the frozen evaluation contract.
- Variant survival required all three conditions: positive mean daily net excess log return versus benchmark; positive one-sided 95% Bartlett-HAC(20) lower bound; improved maximum drawdown versus benchmark. Family survival required at least three of four published lookbacks to survive; no post-result lookback winner could be selected.
- Terminal outcome: `FALSIFIED`, reason `PUBLISHED_TREND_FAMILY_CRITERIA_NOT_SATISFIED`, surviving variants 0/4.
- Benchmark: +239.13% cumulative net return, 40.60% annualized net return, 46.32% annualized volatility, 0.736 annualized Sharpe, 52.97% maximum drawdown.
- 20-day: +78.05% cumulative, 17.47% annualized, Sharpe 0.494, max drawdown 33.13%, mean excess -4.93 bps/day, one-sided 95% HAC lower bound -11.91 bps/day, failed.
- 65-day: +170.62% cumulative, 32.02% annualized, Sharpe 0.830, max drawdown 35.45%, mean excess -1.73 bps/day, lower bound -8.24 bps/day, failed.
- 150-day: +190.43% cumulative, 34.65% annualized, Sharpe 0.829, max drawdown 25.59%, mean excess -1.19 bps/day, lower bound -7.35 bps/day, failed.
- 200-day: +185.45% cumulative, 34.00% annualized, Sharpe 0.785, max drawdown 31.67%, mean excess -1.32 bps/day, lower bound -7.48 bps/day, failed.
- All four variants improved drawdown, but all four observed mean excess-return estimates were already negative before considering the confidence bound. The 150-day variant's higher Sharpe and much lower drawdown are a risk-characteristic observation only and must not be reframed as a surviving or promoted strategy.
- Do not say that the original paper was wrong. The supported conclusion is that the published BTC mechanism did not survive this frozen subsequent evaluation under the Binance data, next-open timing, transaction-cost, benchmark and survival contract.
- Research result counters: external AI attempts 0; provider calls 2; public data requests 2; evaluator invocations 1; protected reads 0; qualification decisions 0; exports 0; product communications 0; paper orders 0; live orders 0.
- No qualification, export, paper trading, live trading or integration with the separate `cryptobot` runtime occurred.

Deterministic identities used on the page:

- publication source `d185408c6c047a74f55f05868886deb46feaa6c37f4e51719ff6e904d4fa31c3`
- proposal `48080d526ea006e31aafb25b250e59c3025ba5a309d3d4848200f94b5c35466f`
- experiment `e8b616f494a35fe43ef16f46ef1fac1590189c1d9358a0304fa06202ec297315`
- dataset `7ea7f981bedd01448579d14d76ebcdbc649da8657ab0c06c215ec790cc118173`
- signal manifest `1ea305ddffd464380c64c007f05da0b2397947f57d061ac5536f37c0163715f0`
- evaluation `4e2700eb52bb549d6110e1ad5cc543eccc2f3e3d8437c2b4ef94373425f3bb70`
- research result `329ef70346266423bec9377f07553cf89a3bacd7d5cf237d388a7630ede4624d`
- novelty history `f9fccc6394470b15213a5f0a4d8a32505ba2609cef246ed72ce6dcffbf3142aa`

Published excerpts:

- `static/evidence/published-strategy-replication-001/published-strategy-replication-001-evaluation.json` — exact uploaded evaluation; SHA-256 `4e2700eb52bb549d6110e1ad5cc543eccc2f3e3d8437c2b4ef94373425f3bb70`.
- `static/evidence/published-strategy-replication-001/published-strategy-replication-001-research-result.json` — exact uploaded terminal result; SHA-256 `329ef70346266423bec9377f07553cf89a3bacd7d5cf237d388a7630ede4624d`.

## Published evidence excerpts

PR #4 publishes only selected text artifacts with a direct explanatory benefit. Each public file was compared byte-for-byte with the corresponding artifact in the uploaded preserved bundle using Git blob identity before opening the PR; the listed SHA-256 value on the case-study page is the source bundle's manifest hash.

Benchmark 004 public excerpts:

- `static/evidence/benchmark-004/benchmark004b_result.json`
- `static/evidence/benchmark-004/INPUT_COMPARISON.json`
- `static/evidence/benchmark-004/benchmark004b_evaluation.json`
- `static/evidence/benchmark-004/FROZEN_EXECUTABLE_SPEC.md`
- `static/evidence/benchmark-004/DECISION_SPEC.md`
- `static/evidence/benchmark-004/PREDECLARED_AUDIT_FINDINGS.md`

Research 005 public excerpts:

- `static/evidence/research-005/RESEARCH_005_RESULT.json`
- `static/evidence/research-005/EVALUATION.json`
- `static/evidence/research-005/FROZEN_STRATEGY_SPEC.md`
- `static/evidence/research-005/FROZEN_DECISION_SPEC.md`
- `static/evidence/research-005/RESEARCH_005_EXPERIMENT.json`

## Editorial limitations

Do not publish raw provider payloads, private machine paths, binaries, or internal runner artifacts merely because they exist in an evidence bundle. Publish only what has a clear public explanatory benefit.

The broader historical lineage contains many proposal identities, mechanism families, rejected provider outputs, capability stops, and engineering iterations. Do not convert those counts into claims such as "number of strategies tested" unless the counting rule and exact evidence are first made explicit. The currently supported public quantitative statement is the preserved checkpoint of 16 completed empirical studies and 16 empirical falsifications.
