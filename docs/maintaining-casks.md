# Maintaining FastPaste casks

Beta uses its own app, command and data identity. Stable is added separately after beta acceptance.
The template is preparation material; it is not an installable cask.

Before adding `Casks/fastpaste-beta.rb`, replace every template field with verified release metadata:

| Field | Required evidence |
|---|---|
| `@VERSION@` | App and bundled CLI report the approved product version |
| `@RELEASE_TAG@` | Exact public beta release tag, marked prerelease |
| `@DMG_FILENAME@` | Actual Apple Silicon asset filename on that release |
| `@DMG_SHA256@` | 64 hexadecimal characters; verify independently downloaded bytes |
| `@MINIMUM_MACOS@` | Supported release backed by native compatibility tests |

The DMG must contain `FastPaste Beta.app/Contents/MacOS/fp`. Confirm Developer ID signature,
notarization and stapling with quarantine intact. Confirm normal `fp-beta` invocation addresses
beta's data/socket, leaves stable's command and stores alone, and reports the expected version.

Validate the rendered cask with `ruby -c`, Homebrew style/audit, and real install/upgrade/uninstall
against its public URL. Normal uninstall retains user state. Add `zap` only with verified paths and
document it as explicit data removal.

The target is coexistence of Homebrew and in-app updates. Add `auto_updates true` only after the
updater works and tests cover concurrent replacement, permissions, bundle links, versions and
failed/interrupted updates. Until that gate passes, the cask is not offered for installation.

The eventual install command is `brew install --cask SlvrPeak/tap/fastpaste-beta`; it is unavailable
until an approved cask has landed. Updates must retain quarantine and signature acceptance.

Sources: [Homebrew cask cookbook](https://docs.brew.sh/Cask-Cookbook),
[HumanLayer beta cask](https://github.com/humanlayer/homebrew-humanlayer/blob/95f26c09f6d6cc786411ed58f99dfc9e8c3fd4d0/Casks/riptide-beta.rb),
[Tauri updater signing](https://v2.tauri.app/plugin/updater/#signing-updates).
