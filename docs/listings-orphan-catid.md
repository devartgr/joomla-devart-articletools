# Listings — orphan `catid` tradeoff (tag paths)

## Context

Tag / multi-tag listings apply category visibility via `CategoryModel::applyCategoryVisibilityFilter`
(and the shared shell `CategoryVisibilityHelper` path for ancestor ACL).

When the set of **blocked** (unpublished / inaccessible) categories is small (≤ 200), the filter uses
`catid NOT IN (blocked…)` for performance instead of `catid IN (allowed…)`.

## Tradeoff

Articles whose `catid` points at a **missing** category row (orphan `catid`) are **not** in the
blocked set. With `NOT IN (blocked)`, those rows can still appear on tag listings.

Joomla core normally refuses to delete a category that still has articles, so orphan `catid` values
usually come only from imports, direct SQL, or broken migrations — not from normal admin use.

When blocked categories exceed the threshold, the code switches to `IN (allowed)`, which excludes
orphans. That path is intentionally reserved for large blocked sets.

## Decision

**Documented, not changed.** Always forcing `IN (allowed)` would regress the hot path that the
`NOT IN` optimization targets. Restricted / unpublished categories remain correctly blocked via the
blocked-id set and ancestor visibility.

## Operator note

If orphan articles appear on a tag listing after a data import, repair `#__content.catid` (or restore
the missing category) rather than expecting Listings to hide every orphan via `NOT IN`.
