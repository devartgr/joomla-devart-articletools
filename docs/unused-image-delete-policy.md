# Unused image delete policy

## Recent Articles (optional, default Off)

Component Options → **Delete unused article images** (`recentarticles_delete_unused_images`).

When **Yes**, permanently deleting articles from Trash also deletes intro/full article image
files listed in the article **images JSON** field under `images/`, but only if no remaining
article still references that path.

- Default is **No** (safe).
- Body HTML (`introtext` / `fulltext`) is **not** scanned for `<img>` paths (performance).
- Paths outside `images/` and paths still referenced by other articles are skipped.
- Cap: limited paths per request (`ArticleImageCleanupHelper::MAX_PATHS_PER_REQUEST`).

## Article Photo

Photo **creates** new JPG files under the configured folder (default under `images/YYYY/MM/`)
and can update the article images field. It does **not** automatically delete a previous
article image file when you generate a replacement. Operators who need cleanup should use
media manager or enable the Recent optional delete when permanently removing articles.

Temp upload slots are deleted after use (`PhotoTempStorage`); that is unrelated to published
article media.

## Social Cards

Social Cards generate downloadable JPEG cards in the browser/admin flow. They do **not**
write into article `images/` by default and do **not** delete article media. Card source
images from media remain untouched.

## Recommendation

Leave Recent unused-image delete **Off** unless you understand that only the images JSON
field is considered and that body-embedded images will not be cleaned automatically.
