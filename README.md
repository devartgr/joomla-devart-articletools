# DevArt Article Tools for Joomla

Joomla 6 article suite for module positions inside articles, intro styling, editorial utilities, and administrator workflows — without template overrides.

![Joomla](https://img.shields.io/badge/Joomla-6.x-blue)
![PHP](https://img.shields.io/badge/PHP-8.3%2B-green)
![Release](https://img.shields.io/badge/Version-2.2.0-orange)
![License](https://img.shields.io/badge/License-GPLv3-red)

---

## Overview

DevArt Article Tools is a production **package** for Joomla 6 editorial websites: news portals, magazines, publishers, and high-traffic content sites.

The suite ships one shell component, six child components, four plugins, and one administrator module. Positions and Intro still run through the familiar content plugin (`plg_content_devartarticletools`).

Designed for reliability, performance, Joomla-native architecture, and safe coexistence with legacy DevArt products.

---

## Version 2.2.0

DevArt Article Tools **2.2.0** is the current **public** release.

### Highlights in 2.2.0

**Schema**
- Dedicated Schema app (`com_devartarticletools_schema`) under Article Tools
- Default **Article** JSON-LD for all articles (enabled on install)
- New rules override specific articles or categories: Article / Service / Product / WebPage
- Product emits nested `brand` + `offers`; Service nests `provider`
- Suite-owned ItemSelect article picker (no DevArt Slider dependency)
- Competing Article JSON-LD from other extensions is stripped when a non-Article override is active

### From 2.1.1

**Social Cards**
- Templates: **Split**, **Strips**, **Arrow**, **Slant** (native PHP GD only)
- Overlay and Clean polish with Color Themes, Yes/No switchers, accent line, collision avoidance
- Title uppercase switcher (Greek tonos removed on capitals)

### From 2.1.0

**Core article tools**
- **Positions / Intro** — `inside1` and `inside2` module positions inside articles; optional intro typography
- **Article Photo** — server-side image generation and administrator workflow
- **Social Cards** — Open Graph image cards for articles
- **Recent Articles** — bounded fast administrator article list
- **Social Share** — frontend share buttons with Open Graph metadata
- **Authors** — groups, profiles, virtual authors, SEF pages, list/card layouts

**Administrator experience**
- Suite dashboard hub with Settings, Schema, and Legacy Migration
- Each child app has its own Options, ACL, and enable/disable state
- Recent Articles module placed on Control Panel on install (publish opt-in in **Recent Articles → Options → Installer**)

**Languages**
- Package language packs for en-GB, el-GR, fr-FR, de-DE, es-ES, it-IT, pt-PT, cs-CZ, nl-NL, pl-PL, ru-RU, uk-UA, ja-JP, tr-TR, and zh-CN

**Security and stability**
- Schema and Open Graph loaders respect published state, access levels, and publish windows
- Legacy DevArt Article Photo, Social Cards, and Backend Tools are detected but never silent-uninstalled

---

## Requirements

- Joomla **6.0+**
- PHP **8.3+**
- MariaDB / MySQL

---

## Package Contents

Package ID: `pkg_devartarticletools`

| Extension | Type | Purpose |
|-----------|------|---------|
| `com_devartarticletools` | Component | Suite shell: dashboard, settings, legacy migration |
| `com_devartarticletools_photo` | Component | Article Photo |
| `com_devartarticletools_socialcards` | Component | Social Cards |
| `com_devartarticletools_recent` | Component | Recent Articles |
| `com_devartarticletools_socialshare` | Component | Social Share and Open Graph options |
| `com_devartarticletools_authors` | Component | Authors |
| `com_devartarticletools_schema` | Component | Schema rules and defaults |
| `plg_content_devartarticletools` | Content plugin | Positions / Intro runtime |
| `plg_content_devartarticletools_socialshare` | Content plugin | Social Share buttons |
| `plg_system_devartarticletools` | System plugin | Article JSON-LD schema |
| `plg_system_devartarticletools_opengraph` | System plugin | Open Graph metadata |
| `mod_devartarticletools_recent` | Administrator module | Recent Articles Control Panel widget |

---

## Installation

Download the latest release:

[`pkg_devartarticletools_v2.2.0.zip`](https://github.com/devartgr/joomla-devart-articletools/releases/download/v2.2.0/pkg_devartarticletools_v2.2.0.zip)

Install via **System → Install → Extensions**.

Do **not** install the old standalone `plg_content_devartarticletools_v*.zip` on new sites.

### Upgrade from 2.1.1

Install **`pkg_devartarticletools_v2.2.0.zip`** over 2.1.1 (Extensions → Install, or Joomla Update).

### Upgrade from 2.1.0

Install **`pkg_devartarticletools_v2.2.0.zip`** over 2.1.0 (or update stepwise via Joomla Update).

### Upgrade from plugin 1.0.3

Install the suite package ZIP once (Extensions → Install, or Joomla Update if offered on the legacy plugin channel).

- Positions / Intro plugin parameters migrate automatically to the suite component
- After the first package install, future updates use Joomla native **package** updates (`pkg_devartarticletools`)
- No manual database fixes are required

If legacy DevArt Article Photo, Social Cards, or Backend Tools are still installed, open **Article Tools → Settings → Legacy Migration** for guidance. Migration is optional and never automatic.

---

## Updates

Updates are **package-only** after the first suite install. The package manifest owns the Joomla update server:

`https://raw.githubusercontent.com/devartgr/joomla-devart-articletools/main/update.xml`

Sites still on plugin-only **1.0.3** may discover the suite package through the legacy content-plugin update channel; the offered download is the same suite package ZIP.

All suite extensions update together as one package.

---

## Perfect For

- News websites and editorial portals
- Magazine and publishing platforms
- Content-heavy Joomla installations
- High-traffic and Cloudflare-powered sites
- Professional Joomla deployments without template overrides

---

## Performance

- Lightweight frontend rendering for Positions / Intro
- No external CSS dependency for core plugin output
- No jQuery or external frontend frameworks
- Joomla cache and CDN friendly

---

## Security

- Joomla ACL on all child components
- Published-state and access-level checks on schema and Open Graph loaders
- CSRF-protected administrator workflows
- GPL open source

---

## Repository Layout

- `source/` — development source (single source of truth)
- `scripts/validate.php` — repository validation
- `scripts/build.php` — validation-first packaging with SHA-256
- `builds/` — generated development packages
- `releases/` — verified release packages
- `update.xml` / `changelog.xml` — Joomla update server files (repo root)
- `docs/` — architecture and release documentation
- `qa/checklist.md` — Joomla QA checklist

---

## Validate and Build

```shell
php scripts/validate.php
php scripts/build.php
```

Repository validation does not replace Joomla runtime QA.

---

## Documentation

- `docs/architecture.md` — suite structure
- `docs/jed-github-archive-flow.md` — GitHub release checklist
- `qa/checklist.md` — installation and functional QA

---

## Integrity (2.2.0)

| | |
|---|---|
| **File** | `pkg_devartarticletools_v2.2.0.zip` |
| **SHA-256** | `3fbf7504e501599e848e3dc0ad479d81824c7e581c8e2a2d10cee2bd6e2658e3` |

---

## Developer

**Stathopoulos Kostas – DevArt**  
https://devart.gr

GitHub repository:

https://github.com/devartgr/joomla-devart-articletools

---

## License

GNU General Public License version 3 or later.

---

## Disclaimer

This software is provided "as is", without warranty of any kind.

DevArt shall not be held liable for any damages, data loss, downtime, security issues, or other problems resulting from the use or misuse of this software.

Users are responsible for testing in their own environment and maintaining proper backups before installation or upgrades.

Always test on a staging environment before using in production.
