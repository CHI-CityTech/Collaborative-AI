# Diffusion & ControlNet Module Setup (Collaborative AI)

## Overview

This guide explains how to add Stable Diffusion and ControlNet functionality to your existing Collaborative AI development environment. It assumes you have already completed the base setup as described in the [Mac AI Development Environment Guide](https://github.com/CHI-CityTech/Collaborative-AI/blob/main/docs/setup/Mac_Intial_Configuration.md).

## 1. Install Diffusion and ControlNet Packages

Install the necessary Python packages for Stable Diffusion and ControlNet workflows.

* **[diffusers](https://huggingface.co/docs/diffusers/index)**: HuggingFace library for running Stable Diffusion models.
* **[transformers](https://huggingface.co/docs/transformers/index)**: Tokenizer models and LLM utilities.
* **[accelerate](https://huggingface.co/docs/accelerate/index)**: Hardware optimization.
* **[controlnet\_aux](https://github.com/lllyasviel/ControlNet)**: ControlNet-specific utilities.
* **[torch & torchvision](https://pytorch.org/)**: PyTorch core libraries.

```bash
pip install --upgrade pip
pip install diffusers[torch] transformers accelerate
pip install git+https://github.com/huggingface/controlnet_aux.git
```

For Apple Silicon:

```bash
pip install torch==2.2.0 torchvision --index-url https://download.pytorch.org/whl/cpu
```

(Or MPS builds if GPU acceleration is desired.)

## 2. Download Models

Download Stable Diffusion and ControlNet models to your local directory.

```bash
mkdir -p models/diffusion

# Stable Diffusion v1.5
huggingface-cli download runwayml/stable-diffusion-v1-5 --local-dir models/diffusion/stable-diffusion-v1-5

# ControlNet OpenPose Model
huggingface-cli download lllyasviel/ControlNet-v1-1 --local-dir models/diffusion/controlnet
```

# ControlNet OpenPose Model

huggingface-cli download lllyasviel/ControlNet-v1-1 --local-dir models/diffusion/controlnet

```

## 3. Folder Structure Expectation
```

Collaborative-AI/
├── models/
│   └── diffusion/
│       └── stable-diffusion-v1-5/
│       └── controlnet/
├── src/
│   └── models/
│       └── diffusion/
│           ├── diffusion\_pipeline.py
│           ├── controlnet\_adapter.py
│           └── utils.py

```
```

## 4. Run a Pose-Guided Generation Test

Test the setup by generating an image.

```bash
python src/models/diffusion/diffusion_pipeline.py --prompt "A vintage illustration of a red-haired princess" --pose_image path/to/pose_reference.png
```

## Result

You will be able to generate pose-guided images using Stable Diffusion and ControlNet conditioning within your Collaborative AI workflow.

## References

* [https://huggingface.co/docs/diffusers/index](https://huggingface.co/docs/diffusers/index)
* [https://huggingface.co/lllyasviel/ControlNet-v1-1](https://huggingface.co/lllyasviel/ControlNet-v1-1)
* [https://huggingface.co/docs/transformers/index](https://huggingface.co/docs/transformers/index)
* [https://huggingface.co/docs/accelerate/index](https://huggingface.co/docs/accelerate/index)
* [https://pytorch.org/](https://pytorch.org/)
