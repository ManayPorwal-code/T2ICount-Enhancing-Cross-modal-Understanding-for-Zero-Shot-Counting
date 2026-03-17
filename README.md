# T2ICount – Text-Guided Zero-Shot Object Counting using Diffusion Models

This repository implements **T2ICount**, a diffusion-based framework for **text-guided zero-shot object counting**. The model estimates the number of objects in an image based solely on a **text prompt describing the target category**, without requiring exemplar images or class-specific training.

Traditional zero-shot counting methods rely on vision-language models like CLIP, which often struggle with **text sensitivity and local object understanding**. T2ICount addresses this limitation by leveraging the **rich visual-text representations from pretrained text-to-image diffusion models (Stable Diffusion)** and introducing mechanisms that improve cross-modal alignment between image features and text prompts.

The architecture extracts **multi-scale visual features from a diffusion U-Net using a single denoising step** for computational efficiency. These features are refined through a **Hierarchical Semantic Correction Module (HSCM)** that progressively enhances text-image alignment using semantic enhancement and correction operations. To further improve learning, the framework introduces a **Representational Regional Coherence Loss (LRRC)**, which uses cross-attention maps from the diffusion model to generate reliable supervision signals for distinguishing object regions from background.

The refined features are then passed to a **density estimation network** that predicts object density maps, where integrating the density map yields the final object count.

## Key Features

* **Text-guided zero-shot object counting**
* **Diffusion-based visual backbone (Stable Diffusion U-Net)**
* **Hierarchical Semantic Correction Module (HSCM)** for progressive feature refinement
* **Representational Regional Coherence Loss (LRRC)** for improved cross-modal supervision
* Density-map based counting for accurate instance estimation
* Designed to handle **arbitrary object categories specified via text prompts**

## Pipeline Overview

Image → VAE Encoder → Diffusion U-Net → Multi-scale Feature Extraction → HSCM → Counter Network → Density Map → Object Count

## Applications

* Counting objects specified by natural language prompts
* Open-world object counting
* Crowd or agricultural counting tasks
* Remote sensing and surveillance applications

## Dataset

The model is trained and evaluated on:

* **FSC-147** (class-agnostic object counting dataset)
* **CARPK** (drone-based car counting dataset)

## Results

T2ICount demonstrates strong performance in **zero-shot counting scenarios**, outperforming previous CLIP-based methods by significantly improving text-guided object localization and counting accuracy.
