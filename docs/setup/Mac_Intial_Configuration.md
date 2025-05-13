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

* **[diffusers](https://huggingface.co/docs/diffusers/index)**: HuggingFace library for running Stable Diffusion models.
* **[transformers](https://huggingface.co/docs/transformers/index)**: HuggingFace library for LLMs and tokenizers.
* **[accelerate](https://huggingface.co/docs/accelerate/index)**: Optimizes training and inference across hardware.
* **[controlnet\_aux](https://github.com/lllyasviel/ControlNet)**: Utilities for ControlNet conditioning (pose, depth, etc).
* **[torch & torchvision](https://pytorch.org/)**: Core PyTorch libraries for tensor computations.

```zsh
pip install --upgrade pip
pip install diffusers[torch] transformers accelerate
pip install git+https://github.com/huggingface/controlnet_aux.git
pip install torch==2.2.0 torchvision --index-url https://download.pytorch.org/whl/cpu
```

## 6. Install GitHub CLI

* **[GitHub CLI](https://cli.github.com/)**: Allows interaction with GitHub from the terminal (issues, PRs, authentication).

```zsh
brew install gh
```

Authenticate:

```zsh
gh auth login
```

## 7. Install Visual Studio Code Extensions

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

Test your pose-guided image generation pipeline.

```zsh
python src/models/diffusion/diffusion_pipeline.py --prompt "A vintage illustration of a red-haired princess" --pose_image path/to/pose_reference.png
```

## 11. Optional: GitHub Desktop

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
