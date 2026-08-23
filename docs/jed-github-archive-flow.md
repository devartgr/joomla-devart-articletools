# GitHub / JED archive flow (Article Tools 2.0)

## After VPS QA of `pkg_devartarticletools_v2.1.0.zip`

1. Publish release ZIP + SHA-256 on GitHub `joomla-devart-articletools` as tag `v2.1.0`.
2. Confirm root `update.xml` and `changelog.xml` resolve on the `main` branch raw URLs used by the package.
3. Update JED listing for DevArt Article Tools to 2.1.0 suite description.
4. For Article Photo and Social Cards:
   - Ship final standalone releases **only** after P1 blockers from `docs/audit-triage.md` are fixed.
   - Add post-install migration message pointing to Article Tools 2.0.
   - Mark JED listings DEPRECATED.
   - Archive GitHub repos (do not delete); banner: merged into DevArt Article Tools.
5. Do **not** remap Photo/Social update servers to the Article Tools package element.
6. Backend Tools remains unpublished as a standalone product (frozen).

Operator confirmation of VPS QA is required before `PROJECT_STATUS.md` is updated to 2.1.0 verified.
