# Qunar Hotel Reviews Scraper

Documentation for the **[Qunar Hotel Reviews Scraper](https://apify.com/factden/qunar-hotel-reviews-scraper?fpr=factden)**
on the Apify Store. Scrape Qunar (去哪儿) hotel reviews, the China-market brand in the Trip.com Group, into
clean JSON, CSV or Excel: guest ratings, per-review sub-scores, review text, travel type, photos, owner replies
and reviewer data, with an LLM-ready markdown field. It is the only Qunar review scraper on Apify. No login, no
API key, no code.

- **Run it:** [apify.com/factden/qunar-hotel-reviews-scraper](https://apify.com/factden/qunar-hotel-reviews-scraper?fpr=factden)
- **Output fields:** see [FIELDS.md](./FIELDS.md)
- **Watch the demo:** [YouTube walkthrough](https://youtu.be/7rDM-AK6Xug)

<p align="center"><a href="https://youtu.be/7rDM-AK6Xug"><img src="https://i.ytimg.com/vi/7rDM-AK6Xug/hqdefault.jpg" width="600" alt="Watch the Qunar Hotel Reviews Scraper walkthrough on YouTube"></a></p>

<p align="center"><img src="https://raw.githubusercontent.com/factden/apify-actor-assets/main/qunar-hotel-reviews-scraper/02-reviews-overview.png" width="1100" alt="Qunar Hotel Reviews Scraper Reviews dataset Overview showing per-review rating, sub-ratings, title, text, sentiment, travel type and owner response for a Qunar hotel"></p>

## Input

Provide Qunar hotel URLs (e.g. `https://hotel.qunar.com/cn/nanjing/dt-17/` or
`https://hotel.qunar.com/cn/shanghai_city/dt-297/`) and/or composite hotel IDs in `{city}_{id}` form
(e.g. `nanjing_17`, `shanghai_city_297`). Up to 100 hotels per run.

Options: `maxReviews` per hotel (default 200) and `fromDate` (`YYYY-MM-DD`) for cheap incremental syncs.
Reviews are read newest-first, so `fromDate` stops the crawl at the date boundary instead of scanning the
whole history. Rating filtering is done downstream: every row carries `overallRating` (1-5) and `sentiment`.

## Output

Two datasets: **Reviews** (one row per review, with `markdownContent`) and **Hotels** (one summary row per
hotel). Reviews are Chinese-language; the source provides no translation. The actor returns every review the
Qunar page shows, native and Ctrip-aggregated, each tagged with its origin (`reviewSource`). Timestamps are in
Qunar's own China local time (UTC+8), matching qunar.com.

## More FactDen review scrapers

- [Fliggy Hotel Reviews Scraper](https://apify.com/factden/fliggy-hotel-reviews-scraper?fpr=factden)
- [Trip.com & Ctrip Reviews Scraper](https://apify.com/factden/ctrip-trip-reviews-scraper?fpr=factden)
- [Agoda Hotel Reviews Scraper](https://apify.com/factden/agoda-hotel-reviews-scraper?fpr=factden)
- [Google Hotels Scraper](https://apify.com/factden/google-hotels-scraper?fpr=factden)
- [Expedia Hotel Reviews Scraper](https://apify.com/factden/expedia-hotel-reviews-scraper?fpr=factden)
- [Hotels.com Reviews Scraper](https://apify.com/factden/hotels-com-reviews-scraper?fpr=factden)
- [MakeMyTrip Scraper](https://apify.com/factden/makemytrip-scraper?fpr=factden)
- [Airbnb Data Scraper](https://apify.com/factden/airbnb-data-scraper?fpr=factden)
