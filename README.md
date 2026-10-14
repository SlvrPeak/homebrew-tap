# SlvrPeak Homebrew tap

Homebrew casks for FastPaste beta and, later, stable releases.

The beta cask is being prepared. No installable cask is published yet.

| Channel | Planned cask | App | Command |
|---|---|---|---|
| Beta | `fastpaste-beta` | `FastPaste Beta.app` | `fp-beta` |
| Stable, later | `fastpaste` | `FastPaste.app` | `fp` |

The [beta template](templates/fastpaste-beta.rb.in) stays outside `Casks/` until a verified release
provides its real version, tag, DMG filename, SHA-256 and supported minimum macOS.
[Maintainer instructions](docs/maintaining-casks.md) list the publication checks.

Approved downloads will come from [FastPaste-releases](https://github.com/SlvrPeak/FastPaste-releases).
