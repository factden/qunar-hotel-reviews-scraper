# Output field reference

Qunar Hotel Reviews Scraper. Two datasets: **Reviews** (per review) and **Hotels** (per hotel).
Ratings are on Qunar's native **1 to 5** scale.

## Reviews dataset

| Field | Type | Notes |
|-------|------|-------|
| `reviewId` | string | Qunar review id (`feedOid`). |
| `hotelId` | integer | Numeric id (the number in `{city}_{id}`). |
| `hotelName` | string | Hotel display name (Chinese), returned inline with each review. |
| `hotelCity` | string | City slug from the hotel key, e.g. `nanjing` or `shanghai_city`. |
| `hotelUrl` | string | The URL or id you supplied for this hotel. |
| `url` | string \| null | Per-review permalink on Qunar. |
| `source` | string | Always `qunar`. |
| `reviewSource` | string | `qunar_iphone` / `qunar_androidphone` (native) or `ctrip_import` (aggregated from Ctrip). |
| `isCtripImport` | boolean | True when aggregated from Ctrip (no per-review sub-ratings). |
| `submittedAt` | string \| null | Qunar's China local time (UTC+8) as a naive ISO 8601 string, matching qunar.com. |
| `checkInMonth` | string \| null | Guest check-in month, `YYYY-MM`. |
| `reviewer` | object | `{ name, userId, avatar, isAnonymous, identityLevel }`. `name` null when anonymous. |
| `travelType` | string \| null | Travel type as Qunar publishes it (e.g. 家庭出行). Native reviews only. |
| `roomName` | string \| null | Room type booked. |
| `language` | string \| null | Review language (`zh`). |
| `overallRating` | number \| null | 1 to 5. |
| `ratingLabel` | string \| null | Qunar descriptor (e.g. 非常好). |
| `subRatings` | array | Labeled sub-scores, e.g. `["Service: 5", "Location: 5"]`. Native reviews only. |
| `reviewTitle` | string \| null | Short review headline. |
| `reviewText` | string \| null | Review body (Chinese). |
| `sentiment` | string \| null | Qunar's POSITIVE / NEGATIVE / NEUTRAL classification. |
| `imagesCount` | integer | Photo count. |
| `images` | array | Photo URLs. |
| `ownerResponse` | object \| null | `{ text, date }` when the hotel has replied. Native reviews only. |
| `markdownContent` | string \| null | Self-contained per-review markdown for LLM/RAG. |
| `extractedAt` | string | Scrape time, naive ISO 8601 (no timezone), matching `submittedAt`. |

## Hotels dataset

| Field | Type | Notes |
|-------|------|-------|
| `hotelId` | integer | Numeric id. |
| `hotelName` | string | Hotel display name. |
| `hotelCity` | string | City slug. |
| `source` | string | Always `qunar`. |
| `url` | string | The URL or id you supplied. |
| `overallRating` | number \| null | Aggregate score, 1 to 5. |
| `recommendRate` | number \| null | Percent of guests who rated positively. |
| `reviewsCount` | integer | Total reviews Qunar reports (capped at 10,000). |
| `subRatings` | array | Hotel-level sub-scores when exposed (often empty). |
| `reviewsExtracted` | integer | Reviews this run collected. |
| `completenessPct` | number | `reviewsExtracted / reviewsCount` as a percentage. |
| `extractedAt` | string | Scrape time, naive ISO 8601 (no timezone). |
