# DevArt Article Tools

Joomla 6 suite for editorial websites: article module positions, intro styling, and
extracted article utilities — without template overrides.

## Purpose

DevArt Article Tools helps Joomla sites place modules inside article content, style
intro text, and run article-related administrator workflows from one suite hub.

The product ships as a **package** (`pkg_devartarticletools`), not as a standalone
content-plugin ZIP. The original public release was the content plugin **1.0.3**;
**2.1.0** is the first public **suite** release.

## Suite inventory

```
pkg_devartarticletools
├── com_devartarticletools              (shell: dashboard, settings, legacy migration)
├── com_devartarticletools_photo        (Article Photo)
├── com_devartarticletools_socialcards  (Social Cards)
├── com_devartarticletools_recent       (Recent Articles)
├── com_devartarticletools_socialshare  (Social Share + Open Graph options)
├── com_devartarticletools_authors      (Authors)
├── plg_content_devartarticletools      (Positions / Intro runtime)
├── plg_content_devartarticletools_socialshare
├── plg_system_devartarticletools       (Schema JSON-LD, disabled by default)
├── plg_system_devartarticletools_opengraph
└── mod_devartarticletools_recent       (administrator module)
```

Each child app has its own `config.xml`, `access.xml`, Options and enable/disable
state. Child administrator menus are hidden; the shell submenu opens each app.

## Core features

- **Positions / Intro** — `inside1` and `inside2` module positions; optional intro
  typography (content plugin reads suite component options when enabled)
- **Article Photo** — server-side image generation and administrator workflow
- **Social Cards** — Open Graph image cards for articles
- **Recent Articles** — fast administrator article list and cpanel module
  (module is placed on Control Panel on install; publish is opt-in in
  Recent Articles → Options → Installer, same pattern as Backend Tools)
- **Social Share** — frontend share buttons and Open Graph metadata
- **Authors** — author groups, profiles, virtual authors, frontend listings
- **Schema** — optional Article JSON-LD (system plugin, off by default)
- **15 locales** — en-GB plus 14 translated languages (see `docs/i18n.md`)

## Requirements

- Joomla **6+**
- PHP **8.3+**

## Upgrade from plugin 1.0.3

Sites on the legacy **content plugin** (`plg_content_devartarticletools` 1.0.3):

1. Install **`pkg_devartarticletools_v2.1.0.zip`** once (Extensions → Install, or
   Joomla Update if the legacy plugin update channel offers 2.1.0).
2. Positions / Intro plugin parameters migrate automatically to the suite component.
3. Future updates use Joomla native **package** updates (`pkg_devartarticletools`).

Do not install the old standalone `plg_content_devartarticletools_v*.zip` on new sites.

Legacy standalone DevArt Article Photo / Social Cards / Backend Tools products may
still be present; the suite detects them and never silent-uninstalls them. See
**Article Tools → Settings → Legacy Migration**.

## Repository layout

- `source/package/` — package manifest, install script, package languages, update metadata
- `source/extensions/` — components, plugins, module
- `scripts/` — validation, build, smoke QA
- `builds/` — generated ZIP packages (disposable)
- `docs/` — architecture, i18n, API policy, JED/release notes

Develop only inside `source/`. Never develop from generated ZIP packages.

## Validate and build

```shell
php scripts/validate.php
php scripts/build.php
```

Validation must pass before building. Output:

- `builds/pkg_devartarticletools_v{version}.zip`
- matching SHA-256 sidecar

Local Herd smoke (optional):

```shell
php scripts/smoke-herd.php --zip=/absolute/path/to/pkg_devartarticletools_v2.1.0.zip
```

Override paths with `--joomla-cli=`, `--base-url=`, or env `DEVART_JOOMLA_CLI`.

## Update architecture

Update ownership is **package-only** (Slider / Widgets / Exts pattern):

| Item | Value |
|------|--------|
| Element | `pkg_devartarticletools` |
| Type | `package` |
| Update server | `https://raw.githubusercontent.com/devartgr/joomla-devart-articletools/main/update.xml` |
| Changelog | `https://raw.githubusercontent.com/devartgr/joomla-devart-articletools/main/changelog.xml` |
| Download | `pkg_devartarticletools_v{version}.zip` |

The root `update.xml` also publishes a **legacy plugin** update entry
(`devartarticletools` / `content`) so sites still on plugin 1.0.3 can discover the
suite package. Child extensions do not declare independent update servers.

## Documentation

- `docs/architecture.md` — suite structure
- `docs/i18n.md` — language pipeline
- `docs/api-policy.md` — Joomla 6 coding rules
- `docs/jed-github-archive-flow.md` — GitHub release checklist
- `qa/checklist.md` — Joomla QA

## Verification

Repository validation does not replace Joomla runtime QA. Record verified releases
only in `PROJECT_STATUS.md` after successful VPS testing.
