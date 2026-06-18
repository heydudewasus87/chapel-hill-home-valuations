# Chapel Hill Housing Valuation

A Python project that estimates a fair value for homes in Chapel Hill, NC using real-estate
finance, then flags which homes look **under-** or **over-priced** versus their asking price —
and plots them on an interactive map (green = undervalued, red = overvalued).

Sites like Zillow and Redfin have their own black-box estimates. This project builds its
**own** valuation from first principles, so you can see exactly *why* a home is flagged.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/heydudewasus87/YOUR_REPO_NAME/blob/main/Chapel_Hill_Housing_Valuation.ipynb)

> Replace `YOUR_REPO_NAME` in the badge link with this repo's exact name.

---

## How to run it

1. Click the **Open in Colab** badge above.
2. In Colab, go to **Runtime → Run all**.
3. It runs end to end and ends with the map and ranked tables.

No setup or accounts needed — it runs on realistic synthetic Chapel Hill data by default.
To use **real live listings**, add a free RentCast key (see below).

---

## What it does

The notebook values each home four different ways, blends them, and compares the result to
the asking price.

| Step | In plain words |
|------|----------------|
| Get data | Pull live listings (RentCast) or generate realistic synthetic homes |
| Clean | Fill in missing fields so every home can be valued |
| Value 4 ways | Income, cost, affordability, and comparable-sales approaches |
| Blend | Combine into one fair value (mostly from the asking-price-independent methods) |
| Label | Under / fairly / over-priced based on asking vs fair |
| Sensitivity | Check whether the labels survive different interest-rate assumptions |
| Map | Plot every home, colored by verdict |

---

## The four valuation methods

The fair value is built mostly from methods that **don't look at asking prices at all** — so
the over/under signal reflects real economics, not just how one listing compares to another.

- **Income approach** *(independent)* — what the home is worth based on the rent it can earn
  and a market cap rate.
- **Cost approach** *(independent)* — land value plus what it would cost to rebuild, minus
  depreciation for age.
- **Affordability** *(independent)* — the price a typical local household can actually finance
  at current mortgage rates.
- **Comparable sales** *(relative)* — peer homes' price per square foot. Carries the least
  weight (25%) because active listings aren't closed sales.

Each home also gets a **conviction score (0–3)**: how many of the independent methods agree
with the verdict. High-conviction calls are the ones to trust.

---

## Understanding the terms

| Term | What it means |
|------|---------------|
| **Fair value** | The model's estimate of what a home is worth, blending the four methods. |
| **Valuation gap** | `asking ÷ fair − 1`. Positive = asking is above fair (overpriced); negative = below (underpriced). |
| **Cap rate** | The yield a cash investor expects on a rental. Higher cap rate → lower value for the same rent. |
| **Gross rental yield** | Annual rent ÷ price. Chapel Hill's is ~2%, which is low — homes cost a lot relative to the rent they earn. |
| **NOI** | Net operating income: rent left after vacancy, management, taxes, insurance, and upkeep. |
| **Method agreement** | How many independent methods (0–3) back the verdict. The conviction score. |
| **Label-stable** | Whether a home keeps its verdict when interest-rate assumptions change. |

---

## Using real data (optional)

Add free API keys in Colab's **Secrets** panel (key icon, left sidebar) to upgrade from
synthetic to live data. The notebook loads them automatically and they never touch the file.

| Secret name | Unlocks | Where to get it | Needed? |
|-------------|---------|-----------------|---------|
| `RENTCAST_API_KEY` | Real Chapel Hill listings | rentcast.io | Only key that matters |
| `CENSUS_API_KEY` | Real local median income | api.census.gov/data/key_signup.html | Optional |
| `FRED_API_KEY` | — (mortgage rate works without a key) | — | Not needed |

**RentCast note:** the free plan allows ~50 requests per period. The notebook has a hard cap
and caches responses for 24 hours, so it can't blow your quota — it uses just **one request**
per fresh pull.

---

## Honest limitations

This is a transparent valuation framework, not an appraisal. Key caveats:

- **No ground truth** — there's no way to prove a fair value is "right."
- **Comps use active listings, not closed sales.**
- **The cost approach can over-value homes on large lots**, which can falsely flag them as
  underpriced — those show up as low-conviction (agreement 1) calls. Trust high-conviction
  calls. (See [RESULTS.md](RESULTS.md) and the roadmap.)
- **In expensive markets, income and affordability read below asking** — a real signal that
  prices reflect more than rent and local incomes.

Full breakdown of the live-data results, including findings and known issues, is in
**[RESULTS.md](RESULTS.md)**.

---

## Built with

Python · NumPy · pandas · Matplotlib · folium · requests

---

## Disclaimer

Research and educational project only. Not investment advice, not a professional appraisal,
and not a recommendation to buy or sell any property. Synthetic mode uses invented homes;
only the methodology is real.
