# Loan Portfolio Backtesting — Power BI

## Objective

Build a Power BI model to backtest a loan portfolio against a -5% breach threshold on a 21-business-day rolling change, across three years of daily portfolio index data.

## Method

- **Data modeling**: cleaned and transformed the raw CSV in Power Query, building a continuous sequential index (`SeqIndex`) to correctly handle year boundary resets in the dataset.
- **DAX measures built**:
  - `Rolling21Change` — percentage change over a 21-business-day rolling window
  - `BreachFlag` — flags any period where the rolling change drops below -5%
  - `DailyChange` and `Annualized Change` (average daily change × 252 trading days)
  - `Annualized Standard Deviation` — using **STDEV.P** (population), not STDEV.S (sample), since the full dataset was available, not a sample
  - `MA21` — 21-day moving average via `AVERAGEX` + `FILTER`
  - `BreachValue` — helper column to highlight breach points on the chart

## Key finding: a real data bug

While cross-validating every DAX result independently in Python, I discovered a **data localization issue**: decimal points in the source data were being misread due to locale settings, silently inflating certain values by roughly a factor of a million. Catching this before finalizing the analysis was only possible because I treated the Python cross-check as a real validation step, not a formality — I compared every key output line by line rather than trusting the DAX results at face value.

## Visualizations

- A historical trend line chart with breach points explicitly marked
- A small-multiples comparison of rolling change by year, with a manually forced uniform Y-axis across all three panels for accurate visual comparison

## Results & Recommendation

The portfolio grew steadily over the three-year period (index ~1.00 → ~1.47), with **three threshold breaches**, all concentrated in year three, where both the annualized change and annualized standard deviation were roughly double those of years one and two.

**Recommendation**: rather than widening the breach threshold (which would hide legitimate risk signals), the model should be periodically recalibrated to reflect the portfolio's evolving volatility profile.

## Tools used

Power BI (Power Query, DAX), Python (independent validation), Excel.

---

[← Back to home](index.md)
