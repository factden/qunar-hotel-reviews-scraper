# Qunar Hotel Reviews Scraper

Documentation for the **[Qunar Hotel Reviews Scraper](https://apify.com/factden/qunar-hotel-reviews-scraper?fpr=factden)**
on the Apify Store. Scrape Qunar (去哪儿) hotel reviews, the China-market brand in the Trip.com Group, into
clean JSON or CSV: guest ratings, per-review sub-scores, review text, travel type, photos, owner replies and
reviewer data, with an LLM-ready markdown field. No login, no API key, no code.

- **Run it:** [apify.com/factden/qunar-hotel-reviews-scraper](https://apify.com/factden/qunar-hotel-reviews-scraper?fpr=factden)
- **Output fields:** see [FIELDS.md](./FIELDS.md)

## Input

Provide Qunar hotel URLs (e.g. `https://hotel.qunar.com/cn/nanjing/dt-17/`) and/or composite hotel IDs in
`{city}_{id}` form (e.g. `nanjing_17`). Filters: `maxReviewsPerHotel`, `fromDate`/`toDate`,
`minRating`/`maxRating` (Qunar's native 1 to 5 scale).

## Output

Two datasets: **Reviews** (one row per review, with `markdownContent`) and **Hotels** (one summary row per
hotel). Reviews are Chinese-language; the source provides no translation. The actor returns every review the
Qunar page shows, native and Ctrip-aggregated, each tagged with its origin (`reviewSource`).

## More FactDen review scrapers

- [Trip.com & Ctrip Reviews Scraper](https://apify.com/factden/ctrip-trip-reviews-scraper?fpr=factden)
- [Agoda Hotel Reviews Scraper](https://apify.com/factden/agoda-hotel-reviews-scraper?fpr=factden)
- [Google Hotels Scraper](https://apify.com/factden/google-hotels-scraper?fpr=factden)
- [Expedia Hotel Reviews Scraper](https://apify.com/factden/expedia-hotel-reviews-scraper?fpr=factden)
