# eBay iPhone Resale — SQL Market Analysis

SQL market analysis on 2,172 eBay iPhone listings based on pricing, condition premiums, outlier detection, and a fair price estimator

## Why this project

Same dataset as the Python analysis, different lens. SQL lets you ask precise business questions instead of exploring visually. I wanted to practice thinking like a marketplace analyst: what drives price, where is the market noisy, and can you build something useful from raw listing data?

## What I found

**The market has three layers.** Normal second-hand listings, legitimate high-end (1TB, sealed, new), and a luxury/custom segment — gold plating, diamonds, Bentley editions. That last one is interesting but essentially unanalyzable: we don't know if those listings ever actually sell.

**The luxury/custom segment represents less than 0.6% of listings** (12 out of 2,172). Excluded from pricing analysis: low volume, unknown sell-through rate, and not comparable to the standard second-hand market.

**Condition keywords are pricing signals hidden in unstructured text.** "Excellent" and "Very Good" consistently pull higher averages. "Fair" drops price significantly. The challenge is that sellers write these inconsistently — extracting them required pattern matching on raw titles.

**The fair price estimator was the most satisfying part.** Given model + storage + condition, you get a reliable price benchmark. Simple idea, but it's the kind of output that's actually useful — a buyer could use it to spot underpriced listings in real time.

## Stack

SQL (SQLite) — CASE statements, aggregations, outlier filtering, pattern matching on unstructured text
