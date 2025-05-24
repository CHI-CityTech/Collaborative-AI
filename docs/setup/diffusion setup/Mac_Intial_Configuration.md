# Mac AI Development Environment Setup Guide (Collaborative AI)

*Last updated: 2025-05-24*

## Overview

This guide outlines how to configure a Mac (M1/M2/M3/M4 preferred) for AI development, specifically for Collaborative AI projects involving Stable Diffusion, ControlNet, LLMs, and GitHub-based workflows. Each step includes an explanation of why the tool or package is needed and includes links for further reference.

## 1. Prerequisites

**Recommended macOS Versions:**

* ✅ **macOS Sequoia (15.x)** – Preferred for latest support and compatibility with modern AI libraries.
* ✅ **macOS Sonoma (14.x)** – Still fully supported.
* ⚠️ **macOS Ventura (13.x)** – Mostly compatible, but some tools may require workarounds.
* ❌ **macOS Monterey (12.x)** or earlier – Not recommended due to toolchain limitations.

**Apple Hardware Compatibility:**

* ✅ **Apple Silicon (M1/M2/M3/M4)** – Fully compatible. M4 introduces the Apple Neural Engine (ANE) with improved performance for on-device inference, but support in most open-source AI toolchains is still evolving. Expect broader benefits in Core ML-optimized pipelines or future Metal-accelerated workflows; for now, M1–M4 perform similarly under PyTorch + MPS unless explicitly optimized. M4 support is still stabilizing across libraries, but generally expected to perform well.
* ⚠️ **Intel Macs** – Functional but significantly slower for machine learning tasks and lacking GPU acceleration support (e.g., Metal/MPS).
*

## 2. Install Homebrew (macOS Package Manager)

[Homebrew](https://brew.sh/) simplifies installation of development tools on macOS.

> **Note:** Even if you already have some tools (like Git or Python) installed, running Homebrew commands will ensure you have the most up-to-date, stable, and properly linked versions. This helps avoid conflicts between pre-installed macOS versions and developer-ready environments managed through Homebrew.

```zsh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

---

## 3. Install Core System Tools

These are foundational packages for development:

```zsh
brew install git python@3.11 wget
brew install --cask visual-studio-code
brew install --cask iterm2
brew install --cask github
```

* **git**: Version control
* **python\@3.11**: Preferred version for performance and compatibility with modern AI libraries
* **wget**: Used to download models and datasets
* **Visual Studio Code**: IDE of choice
* **iTerm2**: Enhanced terminal
* **GitHub Desktop**: Optional GUI for Git

## 4. Python Environment Setup

> **Why Python 3.11?**
> 💡 *Note:* Python 3.12 is also supported by major AI libraries, and offers comparable or slightly better performance than 3.11. However, Python 3.11 remains the default recommendation due to broader ecosystem stability, community adoption, and toolchain compatibility. This guide will be updated once 3.12 becomes more widely standardized across all platforms.
> Python 3.10 was long the default for AI/ML workflows due to its broad compatibility. However, as of 2025, Python 3.11 (and 3.12) is fully supported by all major AI libraries—including PyTorch 2.x, TensorFlow 2.13+, and Hugging Face's `diffusers` and `transformers`. Python 3.11 introduces significant performance gains thanks to adaptive interpreter optimizations and improved memory efficiency. Unless you are working with legacy code or pinned environments, Python 3.11 is now the best default choice for most users. You can test compatibility in a virtual environment before migrating fully.

Check installation:

```zsh
python3.11 --version
```

Set up a virtual environment:

```zsh
python3.11 -m venv .venv
source .venv/bin/activate
```

---

## 5. Install GitHub CLI

Interact with GitHub from the terminal.

```zsh
brew install gh
```

Authenticate:

```zsh
gh auth login
```

This will prompt you to choose a login method (usually via browser), select your GitHub account, and grant permissions. Follow the on-screen instructions until authentication completes. Once authenticated, you'll be able to push, clone, and manage repositories from the command line using `gh` commands.

---

## 6. Install Visual Studio Code Extensions and GitHub Copilot

### Install GitHub Desktop (Optional)

[GitHub Desktop](https://desktop.github.com/) is a graphical interface for Git and GitHub workflows. It’s especially useful for users who prefer a visual approach to cloning, branching, and committing, rather than using Git in the terminal.

To install:

```zsh
brew install --cask github
```

Once installed:

1. Open the GitHub Desktop app.
2. Sign in to your GitHub account.
3. Clone repositories or manage branches and commits visually.

To install these extensions:

1. Open **Visual Studio Code**.
2. Press `Cmd+Shift+X` (or click the Extensions icon in the Activity Bar).
3. Search for each extension by name (e.g., "Python", "GitLens") and click **Install**.

Recommended extensions:

* **Python** – Adds syntax highlighting, debugging, linting, and IntelliSense for Python development.
* **[GitLens](https://gitlens.amod.io/)** – Enhances Git integration in VS Code by showing commit history, authorship, and inline blame annotations.
* **Jupyter** – Enables interactive notebooks (.ipynb) directly within VS Code, great for prototyping and data exploration.
* **Markdown All in One** – Provides Markdown live preview, formatting tools, and shortcuts for technical writing.
* **Remote - SSH (optional)** – Allows you to connect to and develop on remote servers or cloud instances directly through VS Code.

### GitHub Copilot

[GitHub Copilot](https://github.com/features/copilot) provides AI code completions directly in VS Code.

* Install via VS Code’s extension panel (Cmd+Shift+X)
* Authenticate with your GitHub account

**Note:** Copilot does not have a public API—it's integrated only through supported editors.

---

## 7. Clone Collaborative AI Repository

```zsh
cd ~/Projects
git clone https://github.com/your-org/Collaborative-AI.git
cd Collaborative-AI
```

## 8. Project Folder Structure

```plaintext
Collaborative-AI/
├── src/            # Source code (diffusion, llm, services)
├── docs/           # Setup guides, architecture docs
├── collaborations/ # AI dialogue records
├── resources/      # Research, references
├── tests/          # Unit & integration tests
├── .venv/          # Python virtual environment
├── README.md
└── requirements.txt
```

---

## 9. GitHub Desktop and VS Code Workflow

**GitHub Desktop**: Visual Git manager for clones, commits, and pushes.
**Visual Studio Code**: Primary editor with Git integration.

Typical workflow:

1. Clone repo with GitHub Desktop
2. Open project in VS Code
3. Edit & develop
4. Stage and commit in GitHub Desktop

---

## 10. Version Control Workflow (CLI)

Basic Git commands:

```zsh
git status
git checkout -b feature/branch-name
git add .
git commit -m "Add feature"
git push -u origin feature/branch-name
```

---

## 11. Useful Tools

* [Oh My Zsh](https://ohmyz.sh/): Better terminal experience
* [Hugging Face CLI](https://huggingface.co/docs/huggingface_hub/quick-start): For model download/upload
* [ControlNet Models](https://huggingface.co/lllyasviel/ControlNet-v1-1): Conditioning models for inference

---

## 12. Next Steps: Install Project-Specific Toolkits

To install Stable Diffusion and ControlNet support, see:
👉 [docs/setup/diffusion\_controlnet\_setup.md](docs/setup/diffusion_controlnet_setup.md)

Other modules (e.g. LLMs, Music, Pose Inference) will follow similar patterns and link to their own modular setup guides.

---

## References

* [Homebrew](https://brew.sh/)
* [Python](https://www.python.org/)
* [Git](https://git-scm.com/)
* [VS Code](https://code.visualstudio.com/)
* [GitHub CLI](https://cli.github.com/)
* [Hugging Face](https://huggingface.co/docs/diffusers/index)
* [PyTorch](https://pytorch.org/)
* [ControlNet GitHub](https://github.com/lllyasviel/ControlNet)
