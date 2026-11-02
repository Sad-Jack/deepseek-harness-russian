# Plugin requirements review

[English](README.md) · [简体中文](README.zh.md) · [Русский](README.ru.md)

Reviewed on **November 3, 2026 (Europe/Moscow)** for package **1.0.2** and target **DeepSeek Harness 0.2.1-rc.5**. This records source-based checks and their limits; it is not approval by DeepSeek or the community catalog.

**Result:** the checked technical packaging and listing-format requirements are met. The community catalog's one-day repository-age condition is still pending at the time of review, and human review remains necessary. Other platforms and Harness versions are not claimed as manually verified.

## Sources and distinct distribution channels

1. **Harness package and index contracts:** [language-pack API](https://github.com/deepseek-ai/deepseek-harness/blob/dsh-v0.2.1-rc.5/packages/client/locale/README.md), [plugin-index guide](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/user/guide/plugin-market.md), and [reference index generator](https://github.com/deepseek-ai/deepseek-harness/blob/master/apps/plugin-market-generator/README.md).
2. **awesome-dsh-plugin**, the community list used by dsh-market: [contribution requirements](https://github.com/awesome-dsh-plugin/awesome-dsh-plugin/blob/main/contributing.md) and [our submission #11494](https://github.com/awesome-dsh-plugin/awesome-dsh-plugin/pull/11494).
3. **dsh-plugin.org / DSH Plugin Hub** is a separate community directory with its own [submission requirements](https://dsh-plugin.org/submit). Its embedded Plugin Hub requires an npm package; its website also indexes GitHub-only plugins. This package is not published to npm, so eligibility for that embedded hub is **not met**. That does not prevent GitHub, release-archive, author-index, or dsh-market installation.

Harness's built-in Discover reads index sources supplied by users. There is no default official public index in the checked contract. A public repository, a valid index, and a submitted catalog PR are three different states; none implies a catalog approval.

## Technical package and Harness index checks

| Requirement | Result | Evidence |
| --- | --- | --- |
| A real installable bundle, not only `dsh.client` | Pass | Root `package.json` declares `dsh.bundle.patch`; `cordis.patch.yml` inserts the package by its exact name. |
| Host and client entry points exist | Pass | `exports["."]` resolves to `index.js`, which exports `apply`; `exports["./client"]` resolves to `client.js`. |
| Browser module follows the Harness loader contract | Pass | Module id equals the package name; `dsh.client` declares Web platform, immediate activation, and the locale provider dependency. |
| Locale contributions use the supported API and release their resources | Pass | `ctx.locale.register` and `addLanguage` are owned by an effect; failure rollback, cleanup and re-enabling were checked on the installed locale runtime. |
| Existing Russian locale is not replaced | Pass | Registration is skipped if `ru` already exists; verified in the locale checks. |
| Public index-generator eligibility | Pass | `private: true` is absent; the package declares a bundle and valid SemVer. The old 1.0.0 tag still has its historical private flag; use 1.0.1 or newer for indexing. |
| Accurate compatibility, including prereleases | Pass | `engines.dsh` is exactly `0.2.1-rc.5`; this admits that prerelease and rejects `0.2.2-alpha.2`. No unverified broad range is advertised. |
| Display metadata and an accepted package icon | Pass | English, Chinese and Russian `meta.title` / `meta.description` resources are exported. The original SVG is inside the package and below the 256 KiB package-icon limit. |
| License and translation attribution | Pass | MIT license retains Copyright (c) 2026 DeepSeek; upstream commits and local adaptations are recorded. |
| Public homepage, repository and discovery terms | Pass | Manifest contains repository, homepage, author, issue tracker and relevant keywords; GitHub is public and has `dsh-plugin`. |
| Required files are actually distributed | Pass | The packed-file list includes runtime files, patch, metadata, icon, license, all three README files and this review. |
| Index format, source and compatibility | Pass | Public `plugin-index.json` parses with `@deepseek-ai/dsh-plugin-market-index`, names a 40-character Git commit and declares the same Harness range as the package. |
| Index is directly reachable | Pass | The public raw index responds with HTTP 200 without requiring a redirect; no login is needed. |
| Description matches the translation inventory | Pass | 64 namespaces / 2,909 keys; named placeholders match the extracted English inventory. Native menus and other exclusions are documented. |

`dsh.client.inject` is a Harness plugin dependency, not an npm dependency. This package imports no official runtime package into its host code, so it does not vendor duplicate `@deepseek-ai/*` runtimes. If such npm imports are added later, review the catalog's recommendation to declare official packages as peers.

## awesome-dsh-plugin submission checks

| Requirement | Result | Evidence |
| --- | --- | --- |
| One correctly named YAML entry under `data/plugins/` | Pass | `Sad-Jack__deepseek-harness-russian.yml`; the PR adds only this entry and does not alter generated READMEs or unrelated plugins. |
| Valid URL, name, category and descriptions | Pass | Catalog entry validator passes; URL is unique, category is `ui`, English and Chinese descriptions describe the actual scope. |
| Public, non-archived repository with working code | Pass | GitHub metadata and inspected runtime files; the package was enabled and checked in the application. |
| `dsh-plugin` topic | Pass | Present in the public repository topics. |
| Real behavior rather than dependency aggregation | Pass | The package contributes its own language definition and dictionaries; it is not a collection of other plugins. |
| Repository is at least one day old | **Pending** | Created **2026-11-02 21:41:27 UTC**. The condition is met at **2026-11-03 21:41:27 UTC**, or **November 4, 00:41:27 Moscow time**. The local submission gate reports this as its only failure. |
| Human assessment of scope, quality and overlap with existing entries | **Pending review** | Other Russian/localization packages are already listed. Our PR explains the focused, official-source backport for 0.2.1-rc.5. Acceptance is the maintainers' decision. |
| Community CI and merge | **Not claimed** | Check the current status in PR #11494. Local validation is not a substitute for upstream CI or review. |

## Recommendations and their status

- **Prebuilt release archive:** provided as a GitHub-hosted `.tgz`; the catalog entry pins both the release tag and its versioned asset name. Anonymous downloading was checked.
- **npm publication:** recommended by this catalog, not required when GitHub/release installation is available. Not published to npm.
- **Catalog storefront icon:** optional; the catalog accepts GitHub-hosted raster images, while our package icon is SVG. No raster tile is submitted, so the catalog may use the author's avatar. This does not invalidate the package SVG.
- **Screenshots:** optional; no public screenshot set is declared. Application checks are documented in [UI-VERIFICATION.md](UI-VERIFICATION.md).
- **Additional platforms:** unverified. The source runs in the Harness Web client, but that is not evidence of a Windows or Linux installation test.

## Verification limits

The runtime and translation text are unchanged from the app-verified release. For this documentation/packaging update, the README links, packed files, manifest, compatibility, catalog schema and published artifacts were checked. The earlier runtime checks remain recorded in [verification.json](verification.json).

No all-screen manual coverage, security certification, official endorsement, npm listing, or guaranteed community-catalog acceptance is asserted. Future releases must repeat the packaging/index checks and update the pinned index version and commit.
