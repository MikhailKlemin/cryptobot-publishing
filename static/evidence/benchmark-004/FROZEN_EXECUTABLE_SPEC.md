# Benchmark 004A frozen executable specification

This specification follows the **executed notebook code**, not conflicting explanatory prose.
Nothing below may be altered after Benchmark 004A output is observed in order to obtain a match.

## Data preprocessing

Starting from the commit-pinned `binance_1D_crypto_data.pkl`:

1. Parse `open_time` as pandas datetime.
2. Remove every row whose `open_time.date()` equals the maximum date in the pickle.
3. `drop_duplicates(keep='first')` using pandas' default all-column duplicate definition.
4. For close prices, pivot by `open_time x symbol`, cast to float, and reindex to a continuous daily
   calendar from the first to last pivot timestamp.
5. Slice through `2025-08-31` (`.loc[:'2025-08']`).
6. Keep symbols whose close series is non-null on at least 90% of that **full** panel.
7. Use exactly those columns for high, low and volume panels, through the same end date.
8. Out-of-sample start: `2024-01-01`.

The notebook display indicates 66 selected symbols. A different extracted count is recorded as a
source surprise; it is not repaired by manually editing the universe.

## Signals and state

For each asset and day:

- Long-entry channel: prior 46 daily highs.
- Short-entry channel: prior 35 daily lows.
- Long entry when current close is strictly above the prior 46-day highest high.
- Short entry when current close is strictly below the prior 35-day lowest low.
- Volume filter: current volume must be strictly above the **prior** rolling 50-day 0.68 quantile.
  Pandas linear quantile semantics are reproduced.
- Long exit: current close strictly below the prior 2-day lowest low.
- Short exit: current close strictly above the prior 40-day highest high.
- Raw state carries forward day by day; entries are applied before price exits.

## Time exit - preserve upstream implementation quirk

After the complete raw position matrix is built, a position-age matrix is calculated. Age begins at
1 on opening/side-flip and increments while the same non-zero raw side persists. Cells with age > 33
are then masked to zero.

This is a **post-hoc mask**. The resulting zero does not feed back into the raw event loop. Benchmark
004A preserves this exact behavior.

## Portfolio construction - executable code wins

1. Compute simple returns from forward-filled closes over the full panel.
2. Compute rolling **35-day sample standard deviation** (`ddof=1`, `min_periods=1`).
3. Multiply the post-time-mask position by `sqrt(rolling_std)`.
4. Normalize each day by the sum of absolute scaled positions.
5. Slice the resulting portfolio from `2024-01-01` onward.

No EWMA smoothing is applied in the executed holdout path.

## Backtest

For OOS prices only:

- forward-fill closes;
- simple daily percent change;
- gross portfolio return = previous-day portfolio weights times current-day returns;
- turnover = sum absolute day-to-day portfolio-weight changes after treating missing weights as 0;
- cost = turnover x `20 bps` (`20e-4`);
- net return = gross return - cost.

Because the portfolio is sliced before turnover calculation, the first OOS day is charged for moving
from zero exposure to that day's portfolio weights.

## Metrics

- cumulative return: product of `(1+r)` minus 1;
- annualized return: arithmetic daily mean x 365;
- annualized volatility: sample daily standard deviation x sqrt(365);
- Sharpe: annualized return / annualized volatility;
- max drawdown and longest consecutive drawdown duration;
- win rate: positive returns among non-zero return days;
- BTC benchmark: full-panel forward-filled BTC simple returns aligned to OOS;
- information ratio: regress strategy return on BTC with intercept, then compute
  `mean(strategy - beta*BTC) / std(strategy - beta*BTC) * sqrt(365)`.

## Match rule

The primary 004A verdict is `MATCH` only if our independent implementation reproduces every
published holdout display metric at the precision printed by the source notebook. Average turnover
is also compared diagnostically with absolute tolerance `1e-12` but does not override a complete
published-display match if only last-bit floating arithmetic differs.
