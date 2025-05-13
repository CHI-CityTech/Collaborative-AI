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


