# DevArt Article Tools — Architecture

## Repository Layout

`source/` is the only development source:

- `source/package/` — outer Joomla package manifest, install script, package languages.
- `source/extensions/component/com_devartarticletools` — suite control centre (`Feature/*` modules).
- `source/extensions/modules/mod_devartarticletools_recent` — administrator Recent Articles widget.
- `source/extensions/plugins/plg_content_devartarticletools` — Positions / Intro runtime.
- `source/extensions/plugins/plg_system_devartarticletools` — feature-flagged social meta / schema.

Generated packages belong only under `builds/`.

Public update metadata (Phase 1F):

- Repository root `update.xml` (canonical; includes legacy plugin + package entries)
- Repository root `changelog.xml`
- `source/package/update.xml` and `source/package/changelog.xml` mirror the root files

Design documents:

- [suite-roadmap.md](suite-roadmap.md)
- [feature-architecture.md](feature-architecture.md)
- [api-policy.md](api-policy.md)
- [audit-triage.md](audit-triage.md)
- [jed-github-archive-flow.md](jed-github-archive-flow.md)

## Package Composition (2.0.0)

Package: `pkg_devartarticletools` / packagename `devartarticletools`

Declared extensions:

- `com_devartarticletools`
- `plg_content_devartarticletools` (group `content`, element `devartarticletools`)
- `plg_system_devartarticletools` (group `system`, element `devartarticletools`, disabled by default)
- `mod_devartarticletools_recent` (administrator)

Outer ZIP: `pkg_devartarticletools_v2.0.0.zip`

## Product Architecture

DevArt Article Tools is a Joomla 6 utility suite for article-related tools:

- Component: Dashboard, Settings, Recent Articles, Feature placeholders (Photo, Social Cards, Meta, Schema, Authors), Legacy Migration
- Content plugin: module positions (`inside1` / `inside2`) and intro styling; reads component params when the suite component is enabled
- System plugin: optional Open Graph / JSON-LD when feature flags are on
- Administrator module: Recent Articles cpanel widget

Namespace examples:

- `DevArt\Component\Devartarticletools`
- `Devart\Plugin\Content\Devartarticletools`
- `Devart\Plugin\System\Devartarticletools`
- `DevArt\Module\DevartarticletoolsRecent`
