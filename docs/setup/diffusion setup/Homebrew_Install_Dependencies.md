# Homebrew Install Dependencies Explained (Collaborative AI)

This section explains why certain dependencies are installed when setting up core development tools like `git` and `wget` via Homebrew.

## git Installation Dependencies

### libunistring

* **Purpose**: Library for Unicode string manipulation.
* **Why git needs it**: Ensures robust handling of international characters in file names, commit messages, and branches.

### gettext

* **Purpose**: Provides tools for internationalization (i18n) and localization (l10n).
* **Why git needs it**: Enables git to support multilingual outputs and system messages.

### pcre2

* **Purpose**: Perl-Compatible Regular Expressions (version 2).
* **Why git needs it**: Powers features like `git grep`, ignore patterns, and advanced filtering.

## wget Installation Dependencies

### libidn2

* **Purpose**: Supports Internationalized Domain Names (IDN).
* **Why wget needs it**: Allows downloading from URLs containing non-ASCII characters.

## Additional Notes

### Pouring Bottles

* **What it means**: Homebrew term for installing pre-built binary packages quickly.

### Cleanup Behavior

* Homebrew automatically cleans up old downloads and cached files after installation.
* Can be disabled with the environment variable: `HOMEBREW_NO_INSTALL_CLEANUP`.

### Shell Completions

* Installing `git` via Homebrew also adds **zsh completions** for enhanced command-line usability.

## Summary Table

| Package          | Purpose              | Why Needed                          |
| ---------------- | -------------------- | ----------------------------------- |
| **git**          | Version control      | Clone repos, manage code versions   |
| **wget**         | File download tool   | Scripted downloads of models/files  |
| **libunistring** | Unicode handling     | For text encoding in git            |
| **gettext**      | Localization support | Multilingual git messages           |
| **pcre2**        | Regex library        | Enables git grep & pattern matching |
| **libidn2**      | IDN support          | Handles non-ASCII URLs for wget     |

### My Terminal calls when I downloaded python.

Note I already had python 3.10 (this is an earlier version than the 3.12, but have been informed that sopme of the diffusion models need an earlier version)  

```bash
davidsmith@MacBook-Pro-50 Projects % brew install git python@3.10 wget
==> Downloading https://formulae.brew.sh/api/formula.jws.json
==> Downloading https://formulae.brew.sh/api/cask.jws.json
Warning: python@3.10 3.10.17 is already installed and up-to-date.
To reinstall 3.10.17, run:
  brew reinstall python@3.10
==> Downloading https://ghcr.io/v2/homebrew/core/git/manifests/2.49.0
############################################################################################################# 100.0%
==> Fetching dependencies for git: libunistring, gettext and pcre2
==> Downloading https://ghcr.io/v2/homebrew/core/libunistring/manifests/1.3
############################################################################################################# 100.0%
==> Fetching libunistring
==> Downloading https://ghcr.io/v2/homebrew/core/libunistring/blobs/sha256:38e44e319bfe11ec892bc6451d86b687d990ea01b
############################################################################################################# 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/gettext/manifests/0.25
############################################################################################################# 100.0%
==> Fetching gettext
==> Downloading https://ghcr.io/v2/homebrew/core/gettext/blobs/sha256:19c917a48a53614a6f6a611c018cc2884466268638d0aa
############################################################################################################# 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/pcre2/manifests/10.45
############################################################################################################# 100.0%
==> Fetching pcre2
==> Downloading https://ghcr.io/v2/homebrew/core/pcre2/blobs/sha256:549a4a79676a6e2c58896cb46cf7d36a8c86f3696e61c43f
############################################################################################################# 100.0%
==> Fetching git
==> Downloading https://ghcr.io/v2/homebrew/core/git/blobs/sha256:eb79df674513c1e717ca017d7f0a17b133848e290506bf6fdd
############################################################################################################# 100.0%
==> Downloading https://ghcr.io/v2/homebrew/core/wget/manifests/1.25.0
############################################################################################################# 100.0%
==> Fetching dependencies for wget: libidn2
==> Downloading https://ghcr.io/v2/homebrew/core/libidn2/manifests/2.3.8
############################################################################################################# 100.0%
==> Fetching libidn2
==> Downloading https://ghcr.io/v2/homebrew/core/libidn2/blobs/sha256:6c578e128c82759e211298ae9b004c83844c2626c074f5
############################################################################################################# 100.0%
==> Fetching wget
==> Downloading https://ghcr.io/v2/homebrew/core/wget/blobs/sha256:4d180cd4ead91a34e2c2672189fc366b87ae86e6caa3acbf4
############################################################################################################# 100.0%
==> Installing dependencies for git: libunistring, gettext and pcre2
==> Installing git dependency: libunistring
==> Downloading https://ghcr.io/v2/homebrew/core/libunistring/manifests/1.3
Already downloaded: /Users/davidsmith/Library/Caches/Homebrew/downloads/a570da63bc1839c7e217f203abd54d4d873ebd6b99f6e88994d0e79e2ebe987c--libunistring-1.3.bottle_manifest.json
==> Pouring libunistring--1.3.arm64_sonoma.bottle.tar.gz
🍺  /opt/homebrew/Cellar/libunistring/1.3: 59 files, 5.4MB
==> Installing git dependency: gettext
==> Downloading https://ghcr.io/v2/homebrew/core/gettext/manifests/0.25
Already downloaded: /Users/davidsmith/Library/Caches/Homebrew/downloads/344607fc5b91bb0c1287d07bb445cc40cc465a163a52e12eed3cc5cd60498f78--gettext-0.25.bottle_manifest.json
==> Pouring gettext--0.25.arm64_sonoma.bottle.tar.gz
🍺  /opt/homebrew/Cellar/gettext/0.25: 2,418 files, 27.7MB
==> Installing git dependency: pcre2
==> Downloading https://ghcr.io/v2/homebrew/core/pcre2/manifests/10.45
Already downloaded: /Users/davidsmith/Library/Caches/Homebrew/downloads/bbac938545583185faba88567f1a952d7cc0b825820a2980533f7b3550dc31ad--pcre2-10.45.bottle_manifest.json
==> Pouring pcre2--10.45.arm64_sonoma.bottle.tar.gz
🍺  /opt/homebrew/Cellar/pcre2/10.45: 242 files, 6.7MB
==> Installing git
==> Pouring git--2.49.0.arm64_sonoma.bottle.tar.gz
==> Caveats
The Tcl/Tk GUIs (e.g. gitk, git-gui) are now in the `git-gui` formula.
Subversion interoperability (git-svn) is now in the `git-svn` formula.

zsh completions and functions have been installed to:
  /opt/homebrew/share/zsh/site-functions
==> Summary
🍺  /opt/homebrew/Cellar/git/2.49.0: 1,731 files, 55.1MB
==> Running `brew cleanup git`...
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
==> Installing dependencies for wget: libidn2
==> Installing wget dependency: libidn2
==> Downloading https://ghcr.io/v2/homebrew/core/libidn2/manifests/2.3.8
Already downloaded: /Users/davidsmith/Library/Caches/Homebrew/downloads/f30f50fbde4bff9a71de54d684e482d7da3432656d680b97441163c6e5665468--libidn2-2.3.8.bottle_manifest.json
==> Pouring libidn2--2.3.8.arm64_sonoma.bottle.tar.gz
🍺  /opt/homebrew/Cellar/libidn2/2.3.8: 80 files, 939.5KB
==> Installing wget
==> Pouring wget--1.25.0.arm64_sonoma.bottle.tar.gz
🍺  /opt/homebrew/Cellar/wget/1.25.0: 92 files, 4.5MB
==> Running `brew cleanup wget`...
==> Caveats
==> git
The Tcl/Tk GUIs (e.g. gitk, git-gui) are now in the `git-gui` formula.
Subversion interoperability (git-svn) is now in the `git-svn` formula.

zsh completions and functions have been installed to:
  /opt/homebrew/share/zsh/site-functions
davidsmith@MacBook-Pro-50 Projects %
```
