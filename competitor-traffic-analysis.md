# Competitor Web Traffic Analysis — Excel & Python

## Objective

Analyze six months of web traffic data across five competing companies in a shared market, to identify meaningful growth signals and produce an actionable recommendation, in the context of a technical assessment for a data analytics role.

## Method

- **Scorecard design**: built two parallel scoring methodologies — an equal-weighted version and a **visit-weighted** version — to fairly compare companies of very different scale across multiple traffic channels (organic search, paid, direct, referral).
- **Why visit-weighted**: an equal-weighted approach would let a small channel with a few hundred visits swing the score as much as organic search with hundreds of thousands, distorting the picture. Visit-weighting ensures the channels that actually drive the business have proportional influence.
- **Data quality handling**: one company had a tracking outage for a full month in the dataset. Rather than silently deleting that period (which would distort the picture) or ignoring it, I flagged it explicitly with a validity flag and documented the limitation.
- **Verification**: recalculated all 145 formulas in the Excel workbook to confirm zero errors, then independently rebuilt the key numbers in Python as a second, separate calculation path — both matched to six decimal places.

## Key finding

One company's traffic grew approximately 47% in the second half of the period, outpacing every competitor in the set, driven mainly by **organic search rather than paid advertising** — a cheaper, more sustainable growth channel. In the same window, the market leader's traffic declined by over 30%.

## Business interpretation

This kind of signal has two distinct uses in practice:

- **Pre-investment screening**: a low-cost, early indicator before deeper financial due diligence — declining organic traffic alongside rising paid spend can flag weakening underlying demand.
- **Portfolio monitoring**: catching a competitor's growth or a decline early enough for an operating team to react, rather than waiting for it to show up in revenue figures months later.

## Tools used

Excel (advanced formulas, scorecard modeling), Python (independent validation).

---

[← Back to home](index.md)
