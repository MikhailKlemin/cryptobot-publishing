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

Important limitation:

Benchmark 004 and Research 005 detailed immutable runtime evidence is outside the active source tree. Before publishing a granular case study, use the corresponding authoritative closure/history evidence rather than reconstructing or extrapolating missing details.

The broader historical lineage contains many proposal identities, mechanism families, rejected provider outputs, capability stops, and engineering iterations. Do not convert those counts into claims such as "number of strategies tested" unless the counting rule and exact evidence are first made explicit. The currently supported public quantitative statement is the preserved checkpoint of 16 completed empirical studies and 16 empirical falsifications.
