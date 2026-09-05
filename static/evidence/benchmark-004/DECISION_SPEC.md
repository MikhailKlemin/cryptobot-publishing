# Benchmark 004B decision specification

Frozen before provider execution.

## Input-data comparison

Compare the independently captured Binance Spot daily `high`, `low`, `close`, and `volume` fields
against the Benchmark 004A canonical archived panel over the exact 66-symbol universe and daily
calendar 2021-01-01 through 2025-08-31.

- Date grid must match exactly.
- Symbol grid must match exactly.
- Missing/non-missing state must match exactly for every field cell.
- Finite values are parsed as IEEE-754 float64 and must compare exactly.
- Canonical serialization uses the same 17-significant-digit formatting as Benchmark 004A.
- The canonical CSV SHA-256 is also compared directly.

No numeric tolerance may be relaxed after observation.

## Strategy-result comparison

Run the exact evaluator binary sealed in the Benchmark 004A result directory against the independent
canonical input. The evaluator's published display-target rules are unchanged.

## Outcomes

`FULL_REPLICATION_MATCH`
: canonical inputs match exactly and published strategy metrics match.

`METRICS_MATCH_WITH_INPUT_DIFFERENCES`
: at least one input field differs, but the published strategy display metrics still match.

`DATA_MISMATCH`
: input fields differ and the independent-data strategy metrics do not fully match.

`METRIC_MISMATCH`
: canonical inputs match exactly but the evaluator does not reproduce the published metrics.

`INCOMPLETE_CAPTURE`
: the frozen provider evidence could not be captured or interpreted completely.
