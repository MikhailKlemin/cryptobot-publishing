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

## Research 005 detailed case study

Authoritative terminal bundle inspected for the detailed public page:

- `research-005-result-20260905T093254Z.tar.gz`
- `RESULT_MANIFEST.sha256` lists 89 files; all 89 SHA-256 entries were independently checked against the uploaded bundle before drafting the case study and matched.
- `RESEARCH_005_RESULT.json` records terminal outcome `FALSIFIED`, reasons `hac_one_sided_95_lower_bound_positive` and `net_sharpe_at_least_0_50`, `discovery_reclosed=true`, 66 provider requests, one evaluator invocation, zero external-AI/qualification/export/product/paper/live-order actions, and complete capture.
- `EVALUATION.json` records: 365 rows; mean daily net return `0.0005616657171424867`; annualized net return `0.20500798675700765`; annualized net volatility `0.5573360727415418`; net Sharpe `0.3678354888255685`; gross cumulative return `0.28390069811311824`; net cumulative return `0.05258496063130158`; maximum drawdown `-0.2958996939666908`; maximum drawdown duration 207 days; average turnover `0.27154153337636683`; one-sided 95% HAC lower bound `-0.0010016019807964668`; HAC lag 33; 3/4 positive folds.
- Frozen fold mean daily net returns: fold 1 `0.0008886449401567116`, fold 2 `0.0014062885237440038`, fold 3 `-0.0014267178944449188`, fold 4 `0.0014003627864643373`.
- `FROZEN_DECISION_SPEC.md` defines survival as all seven listed deterministic requirements passing and explicitly prohibits post-result rescue via changed criteria, costs, parameters, universe, dates, provider, fold removal, alternate signal, or direction reversal.
- `FROZEN_STRATEGY_SPEC.md` records the exact reproduced executable semantics: prior 46-day long channel, prior 35-day short channel, prior 50-day volume window at quantile 0.68, asymmetric exit channels, reproduced 33-day post-hoc time mask, `sqrt(rolling_std)` portfolio scaling, and frozen cost `turnover × 20e-4`.
- `RESEARCH_005_EXPERIMENT.json` freezes a 66-symbol universe and protected holdout 2025-09-01 through 2026-08-31 with official Binance Spot public REST, maximum 66 requests, zero automatic retries, no credentials, and no alternate-provider fallback.
- `CAPTURE_RECEIPT.json` records 66/66 successful provider requests with zero retries and complete capture. 65 symbol responses contain 365 klines; `OMUSDT` contains 183. The frozen strategy/capture semantics already permit legitimate venue-bar absence as missing data, so this should not be described as an ad-hoc repair or post-hoc universe change.
- The public charts `research-005-gross-net.svg` and `research-005-fold-means.svg` are editorial renderings of values already present in `EVALUATION.json`; they are not a replay, optimization, or new empirical evaluation.

Important limitation:

Benchmark 004 detailed immutable runtime evidence is outside the active source tree. Research 005 now has a separate uploaded terminal bundle supporting a granular case study, but the public site should still avoid publishing raw provider payloads or internal runner artifacts without a specific public benefit and release review.

The broader historical lineage contains many proposal identities, mechanism families, rejected provider outputs, capability stops, and engineering iterations. Do not convert those counts into claims such as "number of strategies tested" unless the counting rule and exact evidence are first made explicit. The currently supported public quantitative statement is the preserved checkpoint of 16 completed empirical studies and 16 empirical falsifications.
