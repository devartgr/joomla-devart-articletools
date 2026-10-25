# Listings cache groups

## Groups

| Group | Constant | Cleared on content save? | Contents |
|---|---|---|---|
| `com_devartarticletools_listings` | `ListingsCacheHelper::CACHE_GROUP` | Yes (content plugin) | View / ACL-sensitive listing callback data (`catids.*`, `blocked.*`, …) |
| `com_devartarticletools_listings_data` | `ListingsCacheHelper::DATA_CACHE_GROUP` | No (TTL only) | Strategy counts: tag map `COUNT(*)`, content-row estimates, category size estimates (`catsize.*`) |

## Why split

Every article/category/tag save cleared the single listings group. Strategy `COUNT(*)` for large tags
(cached ~30 minutes) was invalidated on every publish, causing repeated heavy queries on busy sites.

Strategy counts only choose query shape (map-driven vs content-driven / ordering fallback). Slight
staleness does not change who may see an article. ACL/visibility caches stay on the cleared group
(and `com_devartarticletools_visibility`).

## Operator note

`ListingsCacheHelper::clearData()` exists for rare manual/admin invalidation; the content plugin
does not call it on ordinary saves.
