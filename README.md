# Gift Trading Edge Lab

A forward-looking shadow-trading research log for comparing multiple U.S. swing-entry methods under fixed rules.

## Goal

Test whether any entry method shows a repeatable advantage over Gift Rebound Classic (GR1) and over a simple SPY benchmark, without using hindsight to rewrite entries, stops, or targets.

This repository is **research only**. A logged shadow trade is a counterfactual experiment and does **not** mean a real trade was placed.

## Current strategies

| ID | Strategy | Core idea |
|---|---|---|
| GR1 | Gift Rebound Classic | Reversal confirmation near meaningful support/base with volume confirmation |
| MR1 | Oversold Reclaim | Mean reversion after oversold stretch plus reclaim confirmation |
| TP1 | Trend Pullback | Buy a controlled pullback inside an established uptrend |
| BR1 | Breakout Retest | Breakout followed by a successful retest and confirmation |
| VR1 | Volume Washout Reversal | Capitulation-like selling followed by a reclaim/reversal |

## Research rules

- Forward-log only: no hindsight entry selection.
- A signal is frozen once logged.
- WATCH ideas are not counted as performance entries.
- Same ticker/date may have separate entries for different strategies.
- Independent THB 10,000 shadow wallet per strategy.
- Target planned risk is about THB 200 per shadow trade.
- Regular-session daily OHLC is used for outcome tracking.
- If stop and target are both touched in the same daily bar and order cannot be verified, outcome is `AMBIGUOUS`.
- Track 1/3/5/10/20 trading-day performance, MFE, MAE, realized R, and SPY-relative return.
- Fewer than 30 completed trades per strategy is exploratory only.
- 30+ may qualify as an `EDGE CANDIDATE` only if expectancy is positive and materially better than GR1 with comparable or lower downside.
- Prefer 50–100+ observations across different market regimes before treating an edge as robust.

## Data layout

- `data/signals.csv` — frozen shadow entries
- `data/outcomes.csv` — forward outcomes for each signal
- `data/summary.csv` — per-strategy comparison metrics
- `config/strategies.yaml` — versioned strategy definitions
- `docs/PROTOCOL.md` — detailed methodology and anti-bias rules

Operational working log is also maintained in Google Sheets: **Gift Trading Edge Lab — Shadow Trade Log**.

## Privacy

This repository stores market-research data only. Do not commit brokerage credentials, account identifiers, API keys, personal financial documents, or other private information.

## Status

Started: 2026-09-01 (Asia/Bangkok)

Current phase: **Shadow / exploratory research**
