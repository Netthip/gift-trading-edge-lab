# Research Protocol

## 1. Purpose

This project is a prospective shadow-trading experiment. The objective is to compare entry methods using rules fixed before outcomes are known.

## 2. Unit of observation

One observation is one strategy-specific `ENTRY` signal. The same ticker on the same date may create more than one observation if more than one strategy independently triggers.

WATCH-only ideas are not observations and do not enter performance statistics.

## 3. Signal freeze

At signal time record:

- signal ID
- Bangkok scan timestamp
- U.S. market date
- ticker/company
- strategy ID/name/version
- setup score
- signal price and hypothetical entry
- stop, TP1, TP2
- reward/risk
- hypothetical THB position size and planned THB risk
- setup evidence and catalyst context
- trigger and invalidation
- source URLs
- market regime, sector, scan coverage, and data quality

After the signal is logged, entry/stop/targets must not be rewritten because of future price action. Genuine data corrections belong in notes with an audit explanation.

## 4. Sizing

Each strategy has an independent THB 10,000 counterfactual wallet.

Target planned loss per shadow trade: approximately THB 200.

Position sizing rule:

`position_thb = min(10000, 200 / stop_distance_pct)`

where `stop_distance_pct = abs(entry - stop) / entry`.

This shadow sizing is separate from any real-money Swing Wallet.

## 5. Outcome tracking

Use regular-session daily OHLC only. Track:

- close and return after 1, 3, 5, 10, and 20 trading days
- MFE (maximum favorable excursion)
- MAE (maximum adverse excursion)
- first stop/target hit and date
- final status
- realized R according to the frozen exit rules
- SPY 5-day and 10-day return from the same entry date
- excess return versus SPY

Percentage returns are stored as decimals: `0.025 = 2.5%`.

If stop and target are both touched inside one daily bar and reliable intraday ordering is unavailable, mark `AMBIGUOUS`. Do not assume the favorable path.

## 6. Comparison metrics

Per strategy compare:

- completed observations
- win rate
- average 5d and 10d return
- average R and median R
- profit factor
- expectancy in R
- average MFE and MAE
- stop-hit and target-hit rates
- average 5d/10d excess return versus SPY

## 7. Evidence thresholds

- `<30` completed entries: exploratory only.
- `>=30`: may be labelled `EDGE CANDIDATE` only when expectancy is positive and materially better than GR1 with comparable or lower downside.
- Prefer `50–100+` observations and more than one market regime before describing an apparent edge as robust.

No single win streak is evidence of an edge.

## 8. Anti-bias controls

- no look-ahead data
- no hindsight edits
- no cherry-picking only the winning strategy after the fact
- no duplicate signal IDs
- no counting WATCH ideas as if they were entries
- no changing definitions without incrementing strategy version
- incomplete market coverage must be declared in `scan_coverage`/`data_quality`

## 9. Benchmark

SPY is the default passive market benchmark for relative-return comparison. This does not imply SPY is the correct benchmark for every sector; it is used as a simple consistent baseline in the first research phase.

## 10. Public-repository boundary

This repository contains market research only. Never commit brokerage credentials, account numbers, API secrets, tax documents, personal identifiers, or other private financial information.
