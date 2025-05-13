# Stable Diffusion + ControlNet Setup Guide (Collaborative AI)

## Overview

This guide walks through installing and configuring the Stable Diffusion pipeline with ControlNet using HuggingFace's diffusers library. This setup is part of the Collaborative AI project to enable pose-guided image generation workflows.

## Prerequisites

* macOS (M1/M2/M3 recommended) or Linux
* Python 3.10+
* pip >= 22.x
* Git installed
* Access to HuggingFace model repositories

## 1. Clone the Collaborative AI Repository

```bash
cd ~/Projects
git clone https://github.com/your-org/Collaborative-AI.git  - Clone the repository
cd Collaborative-AI - Move into the repo directory
```


## 2. Setup Python Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
```

## 3. Install Required Python Packages

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

## 4. Install diffusers, transformers, accelerate, controlnet

```bash
pip install diffusers[torch] transformers accelerate
pip install git+https://github.com/huggingface/controlnet_aux.git
```

For Apple Silicon:

```bash
pip install torch==2.2.0 torchvision --index-url https://download.pytorch.org/whl/cpu
```

(Or MPS builds if GPU acceleration desired.)

## 5. Download Models

* Stable Diffusion v1.5
* ControlNet OpenPose conditioning model

```bash
mkdir -p models/diffusion
# Stable Diffusion v1.5
huggingface-cli download runwayml/stable-diffusion-v1-5 --local-dir models/diffusion

# ControlNet OpenPose
huggingface-cli download lllyasviel/ControlNet-v1-1 --local-dir models/diffusion/controlnet
```

## 6. Run Pose-Guided Generation Example

```bash
python src/models/diffusion/diffusion_pipeline.py --prompt "A vintage illustration of a red-haired princess" --pose_image path/to/pose_reference.png
```

## Folder Structure Expectation

```
Collaborative-AI/
├── models/
│   └── diffusion/
│       └── v1-5-princess/
│       └── controlnet/
├── src/
│   └── models/
│       └── diffusion/
│           ├── diffusion_pipeline.py
│           ├── controlnet_adapter.py
│           └── utils.py
```

## Result

* You will be able to generate pose-guided images in the style of your Collaborative AI workflows using Stable Diffusion + ControlNet.

## References

* [https://huggingface.co/docs/diffusers/index](https://huggingface.co/docs/diffusers/index)
* [https://huggingface.co/lllyasviel/ControlNet-v1-1](https://huggingface.co/lllyasviel/ControlNet-v1-1)
