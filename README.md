# VVDF: Virtual Visual-Guided Domain-Shadow Fusion via Modal Exchanging

[![ACM MM 2024](https://img.shields.io/badge/ACM%20MM-2024-blue)](https://openreview.net/forum?id=dxbHuJtIpK)
[![Framework](https://img.shields.io/badge/Framework-fairseq-green)](https://github.com/facebookresearch/fairseq)
[![PyTorch](https://img.shields.io/badge/PyTorch-Implemented-red)](https://pytorch.org/)

This repository provides the implementation of our ACM MM 2024 paper:

> **Virtual Visual-Guided Domain-Shadow Fusion via Modal Exchanging**  
> Zhenyu Hou, Yuxiang Guo  
> ACM International Conference on Multimedia, 2024

VVDF is a multimodal machine translation framework designed to improve text generation by effectively exploiting visual information. The method introduces a virtual visual-guided domain-shadow fusion strategy and a modal exchanging mechanism to encourage stronger interaction between textual and visual representations.

---

## Overview

Multimodal machine translation aims to generate accurate target-language translations by jointly modeling source text and its associated visual context. However, visual features are often noisy, weakly aligned with text, or difficult to integrate effectively.

VVDF addresses this problem by:

- introducing visual-guided representation fusion for multimodal translation;
- exchanging informative textual and visual representations during encoding;
- using external visual features extracted from a pretrained ResNet-101 model;
- building on top of the `fairseq` sequence modeling framework.

The codebase is modified from `fairseq` and contains the core implementation of the proposed multimodal encoder, data loading logic, training scripts, checkpoint averaging, and generation scripts.

---

## Repository Structure

```text
VVDF/
├── fairseq/                  # Modified fairseq source code
│   ├── models/transformer.py # Main VVDF-related Transformer modifications
│   ├── tasks/translation.py  # Dataset loading and visual-feature loading logic
│   └── criterions/           # Training losses
├── scripts/
│   └── average_checkpoints.py
├── config/                   # Example configuration files
├── data-process.sh           # Data preprocessing example
├── data-train.sh             # General training example
├── data-train-small.sh       # Small-setting training example
├── data-train-large.sh       # Large-setting training example
├── data-checkpoint.sh        # Checkpoint averaging example
├── data-generate.sh          # Inference / generation example
├── train.py
├── generate.py
├── preprocess.py
└── README.md
