# Open Graph behind Cloudflare Full Page Cache

## Guest-cacheable HTML

Social Share Open Graph (`plg_system_devartarticletools_opengraph`) emits `og:*` tags into the
article HTML response. Designs stay **CF-safe** for anonymous traffic:

- Tags are rendered on the origin response for public article pages.
- No origin-only session or ACL branching is required for the default guest path.
- Cloudflare Full Page Cache may serve that HTML to subsequent guests; OG tags travel with the page.

## Canonical / `og:url`

The plugin prefers a clean article canonical (scheme/host/path, no stray query noise) when building
`og:url`. Behind Cloudflare:

- Ensure the **public hostname** (and HTTPS) that CF terminates matches what Joomla `Uri::root()` /
  SEF produce, or social previews may show an unexpected host.
- Subdirectory installs: absolute URLs must not double-prefix the install path (same class of issue
  fixed for Listings SEO absolute URLs).

## Locale (`og:locale`)

`og:locale` comes from component/plugin params (default style `el_GR`), not from per-request
negotiation beyond what the cached page already encodes. Multilingual sites should set locale to
match the language of the cached HTML variant (or use separate CF cache keys / language paths).

## Operator checklist

1. Purge CF cache after changing OG defaults or Social Share options if guests still see old tags.
2. Validate with “view source” on the **public** URL (not only origin bypass).
3. Do not rely on logged-in admin HTML for OG QA — CF FPC is guest-oriented.
