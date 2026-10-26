# Changelog

## Template 1.1.0 — 2026-08-04

- Restored generic documentation placeholders for new product bootstrap.
- Added Joomla production-series and workspace awareness to `scripts/validate.php`.
- Added PHP minimum, compatibility targets, and extension checks to validation.
- Added stronger package and extension naming validation.
- Made `scripts/build.php` validation-first with a source integrity guard.
- Preserved the original simple template architecture.

Product change history for bootstrapped repositories begins below this template
section.

## 1.0.6 — 2026-08-22

### Added

- French (fr-FR), German (de-DE), Spanish (es-ES), Italian (it-IT) and Portuguese (pt-PT) plugin language files
- Matching package language files for el-GR, fr-FR, de-DE, es-ES, it-IT and pt-PT

### Note

- Language expansion release
- Existing English (en-GB) and Greek (el-GR) plugin translations remain unchanged
- No runtime behaviour changes

## 1.0.5 — 2026-08-22

### Changed

- Migrated content plugin events to `SubscriberInterface` with `ContentPrepareEvent` and `AfterDisplayEvent`
- Removed legacy CMSPlugin listener registration to eliminate Joomla 6 deprecation notices

### Note

- Compatibility hardening release for Joomla 6 event architecture
- No intentional change to inside1, inside2 or intro styling behaviour

## 1.0.4 — 2026-08-22

### Fixed

- Intro styling fallback no longer applies font-size, font-weight and line-height to the entire article
- Intro matching now uses safe prefix detection instead of fragile `preg_replace`

### Changed

- Fallback intro wrapper uses CSS variables only so `:first-of-type` styles the first block
- Added `filter="cmd"` to the `module_style` plugin parameter

### Note

- Hardening release for intro styling and admin parameter safety
- No change to inside1 or inside2 module position behaviour

## 1.0.3 — 2026-05-14

### Changed

- Normalized repository to DevArt package architecture (plugin-only package)
- Migrated update ownership from standalone plugin to package-only
- Normalized manifest `creationDate` and `php_minimum` metadata

### Note

- Structural repository normalization release
- No plugin runtime behaviour changes

## Unreleased

Verification status belongs in `PROJECT_STATUS.md` and must record only
confirmed Joomla testing.

## 2.3.2 — 2026-10-26

### Added

- Native Category Blog/List → DevArt Fast Listing via `plg_system_devartarticletools_listings` (`onAfterRoute` swap; soft switch; namespaced menu params)
- Listings dashboard: native routing status, lost-flag diagnosis, operator setup steps, Cloudflare purge reminder
- Unit tests for `NativeRoutingResolver` and subcategory pagination route base

### Changed

- Public URLs / Itemid owned by native `com_content` menus; articles stay `ContentRouteHelper`
- Listings dashboard + menu-type copy (15 locales): native vs standalone DevArt menus
- Standalone Category / Multi-category / Tag / Multi-tag menus kept for special lists

### Fixed

- Subcategory under a flagged parent: pagination and canonical keep the child category path (not the parent list)

### Removed

- Interim 2.3.1 article SEF bridge (`ListingRouteHelper`, nested article forward, Schema build-rule rewrite)

### Note

- Soft-disable “Use DevArt on native menus” instead of disabling the listings system plugin when saving menus
- Plugin installs enabled; Tags list swap remains out of scope
- Artifact SHA-256: `1d9ed77175372f3f40c2ba2de6b5a9959479411767c5ff9ef743ca8cd3f2e0ec`

## 2.3.1 — 2026-10-26

### Note

- Interim Listings article SEF bridge only; superseded by 2.3.2 native renderer

## 2.3.0 — 2026-10-25

### Note

- Public suite release consolidating internal 2.2.6–2.2.41 (see package `changelog.xml`)

## 2.2.1 — 2026-09-24

### Added

- Social Share: Icons only display mode
- Social Share: Color theme (default network colours, or red/blue/green/orange/yellow/gray/black for all buttons)

### Changed

- Joomla 7 prep: Article Photo uses `getInput()`; Authors uses `UserFactoryInterface`
- Authors: list checkboxes for Edit/Delete; `delete()` return type aligned with AdminController
- Authors: missing `N_ITEMS_*` language strings for delete/publish messages
- Social Share hub: human-readable plugin status labels

### Note

- Requires Joomla 6+ and PHP 8.3+
- Install `pkg_devartarticletools_v2.2.1.zip` over 2.2.0
- See `changelog.xml` for the full JED-style release notes

## 2.1.0 — 2026-08-23

### Added

- First public **suite** release since the plugin-only line at **1.0.3**
- Package `pkg_devartarticletools` with shell component, five child components,
  four plugins, and administrator Recent Articles module
- Article Photo, Social Cards, Recent Articles, Social Share, Authors
- 15 packaged locales; hub summaries; production-readiness hardening (P1–P3)

### Changed

- Joomla native updates target the **package** at repository root `update.xml` /
  `changelog.xml` (Slider/Widgets/Exts pattern)
- Legacy plugin 1.0.3 sites install the package ZIP once; Positions/Intro params migrate
  to the suite component automatically

### Note

- Intermediate builds 1.0.4–1.0.6 and 2.0.x were not published to GitHub
- Administrator Recent Articles module is published on Control Panel on install/update by default
  (opt-out via Recent Articles → Options → Installer)
- Requires Joomla 6+ and PHP 8.3+
- See `changelog.xml` for the full JED-style release notes

