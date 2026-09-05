---
title: "Methodology"
description: "The controlled workflow used to keep crypto strategy research reproducible, prospective, and falsifiable."
---

Research becomes unreliable when the hypothesis, data treatment, execution assumptions, and success criteria can all move after results are visible. The methodology used in Cryptobot Research was designed to make those degrees of freedom explicit and progressively close them.

## The workflow

The final research implementation evolved toward this sequence:

1. **Define a mechanism.** Start with an economically or behaviorally interpretable candidate, not an unexplained parameter search.
2. **Assess capability.** Determine what data and executable semantics are actually required to test it.
3. **Admit an official public source.** Data-source access is explicit rather than silently interchangeable.
4. **Capture immutable data.** Preserve the observations used by the experiment instead of relying on a future provider response.
5. **Normalize with provenance.** Transformations remain traceable to their source material and deterministic rules.
6. **Freeze the experiment prospectively.** The hypothesis, universe, evaluation period, executable semantics, and acceptance criteria are fixed before evaluation.
7. **Evaluate deterministically.** The same admitted evidence and evaluator should produce the same result.
8. **Falsify or replicate.** Failure is a terminal scientific result, not an invitation to quietly alter the test.
9. **Independently reproduce when appropriate.** A separate reproduction path can check whether the claimed executable semantics are recoverable from the specification and evidence.
10. **Separate research from deployment authority.** Passing research would still require separate qualification and review before any runtime use.

## Prospective freezing

A prospective freeze changes the question from:

> "Can I find a version of this idea that looks good?"

into:

> "Did the version I committed to in advance satisfy the criteria I committed to in advance?"

This does not eliminate every source of bias. It does remove one especially powerful source: changing the experiment after seeing its result while continuing to describe the outcome as if it had been the original test.

## Deterministic evaluation

Reproducibility requires more than keeping source code in Git. The evaluation must also constrain the evidence and executable semantics that produced the result.

The final implementation therefore treated provenance, content-addressed evidence, deterministic calculations, and frozen evaluator identities as part of the scientific record rather than incidental engineering details.

## Falsification is a product feature

Research 005 is the clearest closure-stage example. The experiment reported a positive headline annualized net return, but it did not satisfy the complete predeclared acceptance criteria. Its terminal state remained `FALSIFIED`.

That outcome is not a defect to be optimized away. It is evidence that the process could reject an attractive-looking result instead of moving the goalposts.

## Independent reproduction

Benchmark 004 reached `FULL_REPLICATION_MATCH` for an externally defined channel-breakout strategy. The value of that benchmark was not that channel breakout was "discovered." It demonstrated that the research machinery could independently reproduce a specified strategy against official public data before novel claims were trusted.

## Research software is not a trading runtime

The closed research repository does not own exchange credentials, portfolio risk, runtime signals, paper trading, or live execution. Those responsibilities were deliberately kept outside the research application.

This distinction matters because evidence that a research experiment passed would not, by itself, authorize capital deployment. Research validity and operational trading authority are separate decisions.

## Evidence basis

The statements on this page are based on the final documented `cryptobot-research` handoff captured on **2026-09-05**, including its authoritative README and closure validation. Benchmark 004 and Research 005 are closure-stage results whose detailed immutable runtime evidence remains in the research archive/history rather than being reconstructed as active source modules.

Where future articles make more granular numerical or experiment-specific claims, they should cite the corresponding authoritative closure evidence directly rather than infer missing details from this summary.
