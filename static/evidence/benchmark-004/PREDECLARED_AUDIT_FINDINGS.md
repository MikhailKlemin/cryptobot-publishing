# Predeclared audit findings and limitations

These issues were identified **before** running our independent Benchmark 004A reproducer. A perfect
numerical match will not erase them.

## A1 - Full-sample availability filter

The executable notebook selects symbols by requiring at least 90% non-null close coverage over the
**full panel through August 2025**, before the portfolio is evaluated from 2024 onward.

That allows future availability information to affect the 2024 universe. It is a survivorship /
look-ahead methodology concern. Benchmark 004A reproduces it exactly because the first question is
whether the published result is reproducible, not whether the methodology is ideal.

A later audit may test a prospective universe rule, but that would be a separately frozen experiment
and must not replace the published-result replication.

## A2 - Documentation and executable volatility scaling disagree

The explanatory prose says:

- 30-period rolling standard deviation;
- higher-volatility assets are scaled down;
- EWMA smoothing with alpha=1/3.

The executed holdout code instead:

- uses a 35-day rolling sample standard deviation;
- **multiplies** positions by `sqrt(std)` before normalization;
- does not apply the described EWMA smoothing in the final holdout path.

Benchmark 004A follows the executable code. A customer audit would flag this as a specification /
documentation discrepancy.

## A3 - Volume prose/comment mismatch

The executed parameter is `vol_pct=0.68`, i.e. the 68th percentile. An inline comment describes it
as the 70th percentile. The executable value 0.68 is authoritative for reproduction.

## A4 - Spot-price shorting is not an execution model

The data are Binance spot OHLCV while the strategy takes negative portfolio weights. The published
backtest does not model actual spot borrow availability/cost, perpetual funding, derivatives basis,
liquidation/margin constraints, or venue-specific short implementation.

Therefore even a perfect historical reproduction is **not yet an actionable-live qualification**.

## A5 - Cost interpretation

The README summarizes strategies as using 20 bps transaction costs "per trade". The executable code
charges `20 bps x daily portfolio turnover`. Benchmark 004A follows the executable turnover formula.

## A6 - Dynamic original universe construction

The data-collection notebook builds a universe from the then-current CoinGecko top-300 set, then-current
Binance USDT trading pairs, and additional symbols from an older hourly file. That dynamic discovery
cannot be reconstructed retrospectively without historical snapshots.

For independent-data Benchmark 004B, the 004A archived-source extraction freezes the exact resulting
66-symbol universe first. We do **not** query today's CoinGecko universe and pretend it is historical.

## A7 - Parameter-validation evidence is mixed

The notebook itself prints that all examined parameter sets had at least one validation window with a
negative Sharpe. The final choice is then selected using validation information-ratio comparisons before
being run on the held-out 2024-Aug-2025 execution test.

This does not invalidate the held-out result, but it matters when assessing model-selection uncertainty.

## A8 - Upstream redistribution

No LICENSE file was visible in the source repository during review. The commercial dry-run package does
not redistribute the author's notebooks or archived pickle. They are fetched by the operator directly
from the immutable source commit for private replication.
