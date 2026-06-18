# Results

What the model found when run on **29 live Chapel Hill listings** from the RentCast API
(Jan 2025), valuing each home from real-estate finance first principles and comparing the
result to its asking price.

**The finding:** by fundamentals — what homes earn in rent and what local incomes
can finance — Chapel Hill homes broadly trade **above** fair value. This matches the documented state of the market. The map's real value is showing *relative* stretch: which homes are most over-priced
versus the few that look reasonable even on demanding fundamentals.

---

## The map

Green = underpriced, amber = fairly valued, red = overpriced. Bigger, more opaque markers are
higher-conviction calls (more independent methods agree). 

<img width="493" height="419" alt="image" src="https://github.com/user-attachments/assets/467ce1a6-e301-4314-9b3e-2b1e5abd65bc" />

---

## Headline numbers

| | Count | Share |
|---|------|-------|
| Potentially overpriced | 23 | 79% |
| Fairly valued | 4 | 14% |
| Potentially underpriced | 2 | 7% |

Median valuation gap: **+28.7%** — across the sample, asking prices sit ~29% above what the
blended fair value supports. **97% of homes keep their label** across nine cap-rate ×
mortgage-rate scenarios, so the call is robust to interest-rate assumptions.

<img width="692" height="243" alt="image" src="https://github.com/user-attachments/assets/b89ffda6-5d5e-4b10-893c-9e89b7ec76e0" />


---

## Why the model reads "expensive" — three independent angles agree

The over-valuation call isn't one method's opinion; three methods that never look at asking prices all point the same way:

- **Income approach:** gross rental yields are about **2%** across the sample. A home earning
  2% in rent is priced at roughly 50× its annual rent which is far above what a cash-flow investor
  would pay (the model assumes a 5.75% cap rate). On rent alone, almost everything looks rich.
- **Affordability:** most homes sit well above what a median local household can finance at
  current mortgage rates.
- **Cost approach (land-capped):** even after rebuilding cost and land, fair value lands below
  asking for most homes.

Only the comp method (which reflects what other sellers are asking) tracks the asking prices.
When three of four independent methods agree a market is expensive, it is a signal the market is overpriced.

<img width="694" height="242" alt="image" src="https://github.com/user-attachments/assets/68b637b7-5f5a-4fa2-9c7b-e69c50767c9d" />


---

## By property type

| Type | n | Median $/sqft | Median yield | Median price-to-rent | Median gap |
|------|---|---------------|--------------|----------------------|------------|
| Single family | 19 | $343 | 2.0% | 49.5 | +33.5% |
| Condo | 5 | $252 | 2.7% | 36.5 | +26.2% |
| Townhouse | 3 | $222 | 3.1% | 32.0 | +19.3% |
| Multi-family | 1 | $357 | 1.9% | 51.5 | +88.3% |
| Land | 1 | $55 | — | 7.9 | −78.8% |

The single-family core (n=19, the bulk of the data) shows the clearest signal: a +33.5%
median gap and a price-to-rent near 50. Townhouses are the least stretched of the real
property types. The multi-family and land rows are single listings and not representative;
the land row in particular is mislabeled data (a "land" record carrying bedrooms and
bathrooms) and should be ignored.

---

## The homes that look reasonable

In a market this stretched, the interesting output is the handful of homes that hold up *even
on demanding fundamentals*. The most credible:

- **39 Monteith Dr** (single family, +0.8% gap) — essentially fairly valued; the cleanest
  "priced about right" home in the set.
- **126 Black Bear Ct** (single family, +9.1% gap) — near the top of the fair band.

These are the relative best values. Note the two homes the model labels "underpriced" are
**not** reliable picks: 244 Brown Bear is the mislabeled land record, and 245 N Crest is a
low-conviction (agreement 1) call driven by a single method. The conviction score correctly
marks them as weak.


The highest-conviction over-priced calls (agreement 3) — 594 Cedar Lake (+88%) and 68 Willow
Way (+70%) — are where rent, affordability, and cost all agree the price runs well ahead of
fundamentals.

---

## Does the wider market agree?

Yes. The model's read lines up with independent market data:

- Chapel Hill's median home runs roughly **$495K–$600K** while median rent is about
  **$1,730/month**, a **price-to-rent ratio near 24–29** — solidly "expensive relative to
  rent" by standard measures. (The model's sample skews toward $1M+ single-family homes, so
  its ratios run higher than the citywide median.)
- With a typical household income near **$96,000**, a $500K+ median price is roughly 5–6×
  income, well above the ~3× affordability benchmark.
- The structural driver matches: limited land supply plus steady UNC-and-RTP-driven demand
  keeps prices rising and affordability strained — homes price in location, schools, and
  expected appreciation that rent and income don't capture.

So "Chapel Hill trades above fundamentals" is the consensus read, not just this model's.

*Sources: Redfin, RentCafe, Bankrate, and local market reports, Jan 2025–2026.*

---

## Limitations

- **"Above fundamentals" is not a crash prediction.** A high price-to-rent in a desirable,
  land-constrained college town is normal and can persist for years as buyers are paying for
  appreciation and amenities, not cash flow. The model measures value versus *fundamentals*,
  not where prices will go. 
- **No ground truth.** There's no realized outcome to score fair value against. This is a
  transparent framework, not a claim to know each home's true price.
- **Fundamentals-based valuation structurally reads desirable markets as overvalued.** That's
  a feature here, but it means the +29% median gap reflects the method's lens as much as the
  market.
- **The land-cap ratio (0.50) is a tunable lever.** It controls how much large lots add to the
  cost approach; changing it shifts the magnitude of the gaps (not the overall direction).
- **Comps use active listings, not closed sales**, so that pillar reflects asking-price
  positioning — which is why it carries only 25% weight.
- **Small per-type samples** (5 condos, 1 multi-family, 1 land) and **no condition,
  renovation, view, or school-zone data**, so individual calls can be wrong even when the
  method is sound.

---


*This is a research and educational project, not investment advice, an appraisal, or a
recommendation to buy or sell any property.*
