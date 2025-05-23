# Diffusion & ControlNet Module Setup (Collaborative AI)

# Overview

This guide explains how to add Stable Diffusion and ControlNet functionality to your existing Collaborative AI development environment. It assumes you have already completed the base setup as described in the [Mac AI Development Environment Guide](https://github.com/CHI-CityTech/Collaborative-AI/blob/main/docs/setup/diffusion%20setup/Mac_Intial_Configuration.md).

## ![HuggingFace Logo](https://huggingface.co/front/assets/huggingface_logo-noborder.svg)About HuggingFace


[HuggingFace](https://huggingface.co/) is a central hub for open-source AI models and tooling. They provide accessible APIs, pre-trained models, and libraries like Diffusers and Transformers that have democratized access to powerful generative AI models such as Stable Diffusion. HuggingFace's contributions enable developers to integrate state-of-the-art AI capabilities with minimal setup, fostering innovation and collaboration across the AI community.

## 1. Install Diffusion and ControlNet Packages

Install the necessary Python packages for Stable Diffusion and ControlNet workflows.
![Stability AI Logo](https://www.bigdatawire.com/wp-content/uploads/2022/10/stability-ai.jpg)

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

### Important for Apple Silicon Users (M1/M2/M3)

After installing the packages above, Apple Silicon (M1, M2, M3) users must re-install **torch** and **torchvision** with the correct build to ensure compatibility with their architecture. This step replaces the default x86 PyTorch build with an Apple Silicon-optimized version.

```bash
pip install torch==2.2.0 torchvision --index-url https://download.pytorch.org/whl/cpu
```

(Or use MPS builds if GPU acceleration is desired.)

This command should be run **after** the initial package installation to ensure the correct version of PyTorch is used.

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

```bash
huggingface-cli download lllyasviel/ControlNet-v1-1 --local-dir models/diffusion/controlnet

```

## 3. Folder Structure Expectation

Use a fenced code block with triple backticks and specify `plaintext` to ensure proper display without markdown interpretation issues.

```plaintext
Collaborative-AI/
├── models/
│   └── diffusion/
│       └── stable-diffusion-v1-5/
│       └── controlnet/
├── src/
│   └── models/
│       └── diffusion/
│           ├── diffusion_pipeline.py
│           ├── controlnet_adapter.py
│           └── utils.py
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
