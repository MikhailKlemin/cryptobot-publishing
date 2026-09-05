# Research 005 frozen strategy specification

## Parent mechanism

Research 005 inherits the **executed** Benchmark 004 channel-breakout semantics. Conflicting prose
from the external source is not used to modify executable behavior.

## Frozen universe

The exact universe is copied from the verified Benchmark 004A
`canonical/FROZEN_UNIVERSE.txt`.

It contains exactly 66 symbols and is frozen as of 2025-08-31.

**No full-panel availability re-filter is run in Research 005.** This is the single intentional
scientific correction relative to the external study: future 2025-09-01+ availability cannot affect
which symbols are admitted to the holdout.

## Data timeline

The evaluator operates on one continuous daily calendar:

- immutable pre-period history: 2021-01-01 through 2025-08-31, copied from the independently captured
  official Binance Benchmark 004B panel;
- protected Research 005 data: 2025-09-01 through 2026-08-31, captured only by the later frozen runner.

Canonical bar identity is `(symbol, UTC daily open)`.

Officially absent bars remain missing. They are not replaced by another venue, interpolated, or
back-filled.

## Entry channels

For each frozen asset and physical day:

- long-entry channel = highest **prior** 46 daily highs;
- short-entry channel = lowest **prior** 35 daily lows;
- LONG entry when current close is strictly above the long-entry channel;
- SHORT entry when current close is strictly below the short-entry channel.

The current day is excluded from both entry channels.

## Volume filter

- rolling window: prior 50 daily volume observations;
- quantile: `0.68`;
- pandas-linear quantile semantics as independently reproduced in Benchmark 004;
- entry is admitted only when current volume is strictly above the prior rolling quantile.

The executable value `0.68` is frozen. It is not changed to the source comment's "70th percentile."

## Price exits

- LONG exit: current close strictly below the prior 2-day lowest low;
- SHORT exit: current close strictly above the prior 40-day highest high.

Entries are applied before price exits, matching the reproduced executable state machine.

## Time-exit quirk

Preserve the external implementation exactly:

1. build the full raw position matrix by the event loop;
2. derive position age afterward;
3. age starts at 1 on opening or side flip;
4. age increments while the same non-zero raw side persists;
5. cells with age > 33 are masked to zero;
6. the post-hoc zero does **not** feed back into the raw event loop.

No "cleaner" recursive time-exit implementation is permitted.

## Portfolio construction

Across the frozen universe:

1. forward-fill closes for portfolio-return calculation;
2. compute simple daily returns;
3. compute 35-day rolling sample standard deviation (`ddof=1`, `min_periods=1`);
4. multiply the post-time-mask position by `sqrt(rolling_std)`;
5. normalize each day by the sum of absolute scaled positions;
6. do not apply EWMA smoothing.

This intentionally preserves the reproduced executable behavior even though it is not conventional
inverse-volatility scaling.

## Protected holdout slice

The strategy state is built continuously using pre-period history and protected holdout data.

Only after weights are constructed is the evaluated portfolio sliced to:

`2025-09-01` through `2026-08-31`, inclusive.

As in Benchmark 004, turnover is calculated **after** slicing. Therefore the first Research 005 day
is charged for moving from zero exposure to that day's portfolio weights.

## Returns and cost

- gross daily portfolio return = previous-day portfolio weights × current-day simple asset returns;
- turnover = sum of absolute day-to-day portfolio-weight changes after missing weights are treated as 0;
- frozen cost = turnover × `20e-4` (20 bps);
- net daily return = gross daily return − cost.

No fee/slippage/borrow/funding amendment is permitted after the holdout is opened.

## Important interpretation limit

The strategy may hold negative weights while the evidence source is Binance Spot OHLCV. Research 005
is therefore a research falsification test, not a live-execution qualification. Borrow, funding,
margin, liquidation and derivatives basis remain outside Research 005.
