# DeepSeek Harness Russian

**English** · [简体中文](README.zh.md) · [Русский](README.ru.md)

Russian interface language pack for **DeepSeek Harness 0.2.1-rc.5**, based on official DeepSeek translations.

**2,909 strings · 64 namespaces · no runtime dependencies · no application archive patching.**

This is an independent backport of official translations, **not an official DeepSeek plugin**. If your Harness version already includes Russian, you do not need this package.

## Why we created it

The installed desktop build **0.2.1-rc.5** offered English and Chinese only, while Russian translations were already available in the official **0.2.2-alpha.2** source release.

When checked on **November 3, 2026**, both the built-in updater and the official Mac download still provided **0.2.1-rc.5**. The checked **0.2.2-alpha.2** GitHub release did not include a ready-made Mac installer, so updating the desktop application did not provide Russian.

This package brings those translations to the installed version through the supported language-pack API, without building Harness or modifying `app.asar`. Newer desktop releases may change the need for this backport.

Sources: [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness), [0.2.2-alpha.2 release](https://github.com/deepseek-ai/deepseek-harness/releases/tag/dsh-v0.2.2-alpha.2), and [language-pack API](https://github.com/deepseek-ai/deepseek-harness/blob/dsh-v0.2.2-alpha.2/packages/client/locale/README.md).

## Compatibility

| Item | Supported or verified scope |
| --- | --- |
| Harness version | **0.2.1-rc.5**, declared explicitly in `engines.dsh` |
| Manually verified platform | **macOS, Apple silicon** |
| Other platforms and versions | Not manually verified; no broader compatibility is claimed |
| Existing Russian locale | Registration is skipped when `ru` already exists |

Disable this package before installing another Russian language pack. It does not override an existing locale or attempt to translate newer, unverified versions.

## Installation

### From GitHub in the application

1. Open **Plugins → Add plugin**.
2. Enter:

   ```text
   https://github.com/Sad-Jack/deepseek-harness-russian
   ```

3. Select **Install**, wait for completion, then select **Enable now**.
4. Open **Account menu → Settings → General → Language → Русский** and explicitly select Russian.

With Russian system preferences, the interface may switch as soon as the plugin is enabled. Explicitly selecting the language saves your preference. Restart Harness if it asks you to.

The repository is public. No access to the author's account, manual dependency installation, or local build is required. If GitHub installation fails, use the local-folder method below.

### From the command line

With the `dsh` CLI already installed:

```sh
dsh plugin --profile desktop add github:Sad-Jack/deepseek-harness-russian
```

Use `--profile web` for the Web profile. Enable the package in **Plugins** if needed, then select **Русский** in the language settings. Prebuilt archives are also available in [Releases](https://github.com/Sad-Jack/deepseek-harness-russian/releases). Publishing to npm is not required for installation from GitHub.

### Through the built-in Discover tab

1. In **Plugins → Experimental plugins → More**, enable **Custom plugin markets**. Newer Harness versions call this component **Custom plugin indexes**.
2. Open **Discover** and add this index source:

   ```text
   https://raw.githubusercontent.com/Sad-Jack/deepseek-harness-russian/main/plugin-index.json
   ```

3. Open the language-pack card, check its installation source, and select **Install**.
4. Enable the package and select **Русский** in General settings.

This is an author-maintained index, not an official DeepSeek catalog. It pins an immutable Git commit and declares only the verified Harness version. Community-catalog acceptance is separate: [submission #11494](https://github.com/awesome-dsh-plugin/awesome-dsh-plugin/pull/11494).

### From a local folder

Download and extract the [repository ZIP](https://github.com/Sad-Jack/deepseek-harness-russian/archive/refs/heads/main.zip), or clone it:

```sh
git clone https://github.com/Sad-Jack/deepseek-harness-russian.git
```

Choose a permanent directory containing `package.json`, `client.js`, and `cordis.patch.yml` at its root. Node.js, `npm install`, and a build step are not needed.

In **Plugins → Add plugin → Package name or address**, enter the folder's absolute path, for example:

```text
/Users/your-name/Projects/deepseek-harness-russian
```

Replace that example with your actual path. Install and enable **Russian · official translations**, then select **Русский** in **Settings → General → Language**. In Russian, the same route is **Меню аккаунта → Настройки → Общие → Язык → Русский**.

**Keep a locally installed folder in place.** Harness links to it directly. To move it, remove the package through Harness, move the folder, and install it again.

### If installation stays on Checking…

On the verified Mac, the first local-folder inspection stalled. Closing the install dialog, restarting Harness normally, and retrying resolved it. A stalled dialog does not prove installation: check the installed-package list and its enabled switch.

## Translation coverage and adaptations

The 64 dictionaries cover all **2,909 English keys extracted from the installed build**, rather than assuming its public source tag has an identical inventory. They cover client sections such as chat, settings, sidebars, models, permissions, plans, automation, tools, subagents, and plugin management.

Most text comes directly from the official `dsh-v0.2.2-alpha.2` translations. The documented delta contains:

- **16 compatibility adaptations:** preserving the `1017` model identifier, supplying older keys absent from the newer release, and matching feature descriptions to 0.2.1-rc.5 behavior.
- **15 terminology corrections:** two literal translations of Shell as “seashell,” and 13 execution-state labels translated as the noun “running/race.” Appropriate Russian command-shell and execution-state terms are used instead.

Named placeholders such as `{count}` and `{path}` are preserved. Missing keys use Harness's normal English fallback. Exact source commits are recorded in [provenance.json](provenance.json); every changed entry is listed in [translations/compatibility.json](translations/compatibility.json).

## What remains untranslated

- **Native macOS menus** and separate sign-in/update windows: this release's desktop shell owns their dictionaries.
- Some experimental-plugin names and descriptions loaded from the application's own metadata.
- Model responses, terminal output, code, filenames, and user-authored content.

The plugin does not change the application layout. Long Russian labels may be shortened by narrow controls. The package adds no agent tools, install scripts, runtime dependencies, or translation-service requests; it registers dictionaries through `ctx.locale`.

## Verification and requirements

All 2,909 keys were checked using the installed 0.2.1-rc.5 locale runtime: key coverage, placeholders and interpolation, English fallback, preference persistence, cleanup, re-enabling, rollback after registration failure, and preservation of an existing Russian locale.

The main screen, sidebar, General settings, automation page, plugin list, and package details were inspected in the application. Russian remained selected after a full restart. This does not mean every possible screen or error was manually exercised.

See [verification.json](verification.json), [UI-VERIFICATION.md](UI-VERIFICATION.md), and the dated [requirements review](REQUIREMENTS.md). Technical eligibility and a passing check do not guarantee a community-catalog review or merge.

## Package contents

| File | Purpose |
| --- | --- |
| `client.js` | Ready-to-install client module with the embedded dictionaries |
| `index.js` | Minimal host module; adds no tools or services |
| `cordis.patch.yml` | Registers the bundle in the Harness composition |
| `package.json` | Package manifest, exports, files and compatibility |
| [translations/ru.json](translations/ru.json) | Complete Russian dictionaries |
| [translations/target-en.json](translations/target-en.json) | English key inventory from the verified installed build |
| [translations/compatibility.json](translations/compatibility.json) | Documented changes from upstream translations |
| `locale/*.json`, `icon.svg` | The package's own localized metadata and original icon |
| [provenance.json](provenance.json) | Source versions, commits, and file paths |
| [CHANGELOG.md](CHANGELOG.md) | Package release history |

`client.js` is already built. Editing only `translations/ru.json` does **not** automatically update the dictionaries embedded in `client.js`.

## Feedback

[Open an issue](https://github.com/Sad-Jack/deepseek-harness-russian/issues) with your Harness version, operating system, affected screen, and expected translation. Remove personal information from screenshots before posting them.

## Disable or uninstall

Select a different language in **Settings → General → Language**, then disable or remove the package under **Plugins**. Disabling releases its dictionaries and language definition. Keep the local folder until the package is removed through the application.

When upgrading to a Harness version with built-in Russian, disable this package and use the built-in locale.

## License

Official translations: **MIT**, Copyright (c) 2026 DeepSeek. The original notice is retained in [LICENSE](LICENSE). The local packaging and original icon are also provided under MIT. This repository is not an official DeepSeek project.
