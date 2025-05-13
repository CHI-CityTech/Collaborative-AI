# Mac AI Development Environment Setup Guide (Collaborative AI)

## Overview

This guide outlines how to configure a Mac (M1/M2/M3 preferred) for AI development, specifically for Collaborative AI projects involving Stable Diffusion, ControlNet, LLMs, and GitHub-based workflows. Each step includes an explanation of why the tool or package is needed and includes links for further reference.

## 1. Prerequisites

* macOS 12.3+ (Ventura/Sonoma recommended)
* Apple Silicon (M1/M2/M3) or Intel Mac (slower for AI workloads)

## 2. Install Homebrew (macOS Package Manager)

Homebrew is the standard package manager for macOS, simplifying the installation of development tools.

* **Homebrew website**: [https://brew.sh/](https://brew.sh/)

It allows you to install, update, and manage packages and applications via the command line.

```zsh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## 3. Install Core Development Tools

* **[git](https://git-scm.com/)**: Essential for version control and collaboration.
* **[python@3.10](https://www.python.org/)**: Required version for compatibility with AI libraries.
* **[wget](https://www.gnu.org/software/wget/)**: Useful for downloading models and assets.
* **[Visual Studio Code](https://code.visualstudio.com/)**: Recommended IDE for code editing.
* **[iTerm2](https://iterm2.com/)**: Enhanced terminal emulator for macOS.
* **[GitHub Desktop](https://desktop.github.com/)**: Visual interface for Git, useful for beginners.

```zsh
brew install git python@3.10 wget
brew install --cask visual-studio-code
brew install --cask iterm2
brew install --cask github
```

## 4. Configure Python Environment

Python 3.10.x is required for compatibility with Stable Diffusion and related libraries.

```zsh
brew install python@3.10
python3.10 --version
```

Virtual environments isolate dependencies, ensuring project-specific configurations.

```zsh
python3.10 -m venv .venv
source .venv/bin/activate
```

## 5. Install Essential Python Packages

(Section moved to diffusion\_controlnet\_setup.md)

This section has been moved to a project-specific guide for Stable Diffusion and ControlNet setup. Please refer to:

**[docs/setup/diffusion\_controlnet\_setup.md](docs/setup/diffusion_controlnet_setup.md)**

for instructions on installing diffusers, transformers, accelerate, controlnet\_aux, and related libraries.

## 6. Install GitHub CLI

* **[GitHub CLI](https://cli.github.com/)**: Allows interaction with GitHub from the terminal (issues, PRs, authentication).

```zsh
brew install gh
```

Authenticate:

```zsh
gh auth login
```

## 7. Install Visual Studio Code Extensions and GitHub Copilot

These extensions enhance development efficiency:

* **Python**: Syntax highlighting, linting, debugging.
* **[GitLens](https://gitlens.amod.io/)**: Visualizes Git history and blame.
* **Jupyter**: Run notebooks directly.
* **Markdown All in One**: Live preview and formatting.
* **Remote - SSH**: Optional for remote dev.

### Install GitHub Copilot

* **[GitHub Copilot](https://github.com/features/copilot)**: AI-powered code completion and suggestion tool integrated into VS Code.

To install:

1. Open Visual Studio Code.
2. Go to Extensions (Cmd+Shift+X).
3. Search for "GitHub Copilot" and click Install.

Authenticate using your GitHub account when prompted.

### Does GitHub Copilot Have an API?

GitHub Copilot is primarily designed as an in-editor coding assistant. While it integrates with VS Code and other IDEs, it does not currently offer a public API for external programmatic access like OpenAI's ChatGPT API. Interaction with Copilot happens within the editor environment.

However, integrating GitHub Copilot into your development environment ensures consistency in coding assistance across your Collaborative AI projects.
These enhance development efficiency:

* **Python**: Syntax highlighting, linting, debugging.
* **[GitLens](https://gitlens.amod.io/)**: Visualizes Git history and blame.
* **Jupyter**: Run notebooks directly.
* **Markdown All in One**: Live preview and formatting.
* **Remote - SSH**: Optional for remote dev.

## 8. Clone Collaborative AI Repository

This pulls down the project codebase for local development.

```zsh
cd ~/Projects
git clone https://github.com/your-org/Collaborative-AI.git
cd Collaborative-AI
```

## 9. Project Folder Structure

Organizes code, docs, collaborations, and tests for clarity and scalability.

```
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

## 10. Run a Test Inference (Diffusion)

(Section moved to diffusion\_controlnet\_setup.md)

Instructions for running a pose-guided image generation pipeline have been moved to the project-specific guide:

**[docs/setup/diffusion\_controlnet\_setup.md](docs/setup/diffusion_controlnet_setup.md)**

## 11. GitHub Desktop and Visual Studio Code Workflow

**GitHub Desktop** is a graphical interface that helps you manage your Git repositories. While it does not display individual files for editing, it allows you to:

* Clone repositories from GitHub.
* View and manage changes, branches, and commit history.
* Stage changes and sync with GitHub.

For actual file navigation and editing, you'll use **Visual Studio Code (VSC)**. VSC provides:

* File explorer to browse your project directory.
* Advanced code editing with syntax highlighting, linting, and debugging.
* Integrated terminal for running commands within the project directory.

### Typical Workflow:

1. Clone the repository using GitHub Desktop.
2. Use GitHub Desktop's **"Open in Visual Studio Code"** to launch the project.
3. Edit, navigate, and develop in VSC.
4. Switch back to GitHub Desktop to stage, commit, and push your changes.

This separation of tools keeps version control and code editing organized and efficient.

```zsh
brew install --cask github
```

For users preferring a visual Git interface.

```zsh
brew install --cask github
```

## 12. Version Control Workflow (CLI)

Basic Git commands for collaboration and version tracking.

```zsh
# Check status
git status

# Create feature branch
git checkout -b feature/diffusion-controlnet

# Stage, commit, push
git add .
git commit -m "Add diffusion pipeline adapter"
git push -u origin feature/diffusion-controlnet
```

## 13. Useful Tools

* **[Oh My Zsh](https://ohmyz.sh/)**: Enhanced terminal experience with git-aware prompts.
* **[Hugging Face CLI](https://huggingface.co/docs/huggingface_hub/quick-start)**: Model management and uploads.
* **[ControlNet Models](https://huggingface.co/lllyasviel/ControlNet-v1-1)**: Download pose/depth conditioning models.

## Result

You now have a fully configured macOS AI development environment ready for Collaborative AI workflows involving Stable Diffusion, ControlNet, and GitHub-based team collaboration.

## References

* [https://brew.sh/](https://brew.sh/)
* [https://huggingface.co/docs/diffusers/index](https://huggingface.co/docs/diffusers/index)
* [https://github.com/AUTOMATIC1111/stable-diffusion-webui](https://github.com/AUTOMATIC1111/stable-diffusion-webui)
* [https://ohmyz.sh/](https://ohmyz.sh/)
* [https://code.visualstudio.com/](https://code.visualstudio.com/)
* [https://cli.github.com/](https://cli.github.com/)
* [https://git-scm.com/](https://git-scm.com/)
* [https://huggingface.co/docs/transformers/index](https://huggingface.co/docs/transformers/index)
* [https://huggingface.co/docs/accelerate/index](https://huggingface.co/docs/accelerate/index)
* [https://pytorch.org/](https://pytorch.org/)
* [https://github.com/lllyasviel/ControlNet](https://github.com/lllyasviel/ControlNet)
