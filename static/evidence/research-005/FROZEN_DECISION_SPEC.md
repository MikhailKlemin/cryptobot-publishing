# Research 005 frozen evaluation and terminal-decision specification

## Required sample

The protected evaluation slice is exactly 365 physical daily rows:

- Fold 1: 2025-09-01 through 2025-11-30
- Fold 2: 2025-12-01 through 2026-02-28
- Fold 3: 2026-03-01 through 2026-05-31
- Fold 4: 2026-06-01 through 2026-08-31

If the official capture cannot be completed or parsed under the frozen provider contract, the
terminal result is `INCONCLUSIVE`.

Legitimate absence of a venue bar is represented as missing data and processed under the frozen
strategy semantics; it is not itself a provider failure.

## Deterministic metrics

Let `r_t` be the 365 frozen net daily portfolio returns.

### Annualized net return

`mean(r_t) × 365`

### Annualized net volatility

sample standard deviation of `r_t` (`ddof=1`) × `sqrt(365)`

### Net Sharpe

annualized net return / annualized net volatility.

A non-finite or zero-volatility Sharpe fails the survival criterion.

### Maximum drawdown

Start wealth at 1.0 and compound `wealth_t = wealth_(t-1) × (1 + r_t)`.

Maximum drawdown is the minimum of `wealth_t / running_peak_t - 1`.

Any `r_t <= -1` fails survival.

### Four chronological fold means

For each frozen fold, compute the arithmetic mean of its net daily returns.

A fold is positive iff its mean is strictly greater than 0.

### Physical-time Bartlett HAC lower bound

Use all 365 physical daily net returns, including zero-return days.

Frozen lag: `L = 33` daily lags, anchored to the reproduced strategy's 33-day maximum time mask.

Let `mu` be the arithmetic mean.

For lag `l`:

`gamma_l = (1/N) × sum_{t=l+1..N} (r_t - mu)(r_(t-l) - mu)`

Bartlett weight:

`w_l = 1 - l/(L+1)`

Long-run variance:

`LRV = gamma_0 + 2 × sum_{l=1..L}(w_l × gamma_l)`

Variance of the sample mean:

`Var(mu) = LRV / N`

`SE_HAC = sqrt(max(Var(mu), 0))`

Frozen one-sided 95% lower bound:

`LB95 = mu - 1.6448536269514722 × SE_HAC`

No alternative lag selector or IID standard error may replace this criterion after evaluation.

## Survival criteria

`SURVIVED_RESEARCH` requires **all** of:

1. exactly 365 protected evaluation rows;
2. annualized net return > 0;
3. net Sharpe >= 0.50;
4. one-sided 95% Bartlett-HAC lower bound on mean daily net return > 0;
5. at least 3 of the 4 frozen fold mean net returns > 0;
6. maximum drawdown > -0.50;
7. all required deterministic metrics are finite.

If valid evidence exists but any survival criterion fails:

`FALSIFIED`

If valid evaluation cannot be made because the frozen official capture itself is incomplete or
invalid:

`INCONCLUSIVE`

## No rescue semantics

After the terminal result is known, Research 005 cannot:

- alter criteria;
- alter costs;
- alter parameters;
- alter universe;
- alter sample dates;
- drop a bad fold;
- use another provider;
- retry an alternative signal;
- reverse LONG/SHORT direction;
- continue discovery automatically.

The one-shot discovery reopening closes on every terminal outcome.
