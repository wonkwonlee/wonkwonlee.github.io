---
layout: page
title: Out-of-distribution Robustness Evaluation of State-of-the-art Vision Models
description: Research project comparing the robustness of 58 computer vision models
img: assets/img/ood/ood.png
related_publications: true
---

This project provides a thorough out-of-distribution (OOD) robustness comparison across 58 state-of-the-art computer vision models. These include models based on vision transformers, convolutional networks, hybrid mechanisms, and more.

The research investigates how different architectures perform under various distribution shifts, highlighting the strengths and weaknesses of each approach in terms of robustness.

The full paper can be accessed on [arXiv](https://doi.org/10.48550/arXiv.2301.10750) and the code is available on [GitHub](https://github.com/salman-lui/vision_course_project).

## Summary

This work offers a comparative study of out-of-distribution robustness across 58 models, such as vision transformers, CNNs, hybrid models, and others. The analysis was conducted using a unified training setup, covering diverse models like convolution-based, attention-based, sequence-based, and more. The findings reveal how robustness varies depending on model type and the OOD type being evaluated.

## Abstract

Vision transformers (ViT) have emerged as cutting-edge tools in visual recognition tasks, often surpassing CNNs in robustness due to their self-attention mechanisms. However, previous studies may have been biased by unfair experimental setups, only comparing a small number of models.

Our study explores 58 models, comparing attention, convolution, hybrid, and sequence-based architectures under fair and controlled conditions. Our findings demonstrate that robustness is not solely determined by architecture but also by training setup and OOD data type.

The research aims to assist the community in better understanding the robustness of vision models.

## Methods

We evaluated these models using benchmark OOD datasets, such as ImageNet-A, ImageNet-R, ImageNet-Sketch, and others. We trained and tested models using standardized setups to ensure fair comparisons.

- **Convolution-based models**: ResNet-50, DenseNet, and EfficientNet
- **Attention-based models**: ViT, DeiT, BEiT
- **Hybrid models**: ConViT, ConvNext
- **Other models**: MLP-Mixer, RegNet, Sequencer

### Top 5 Convolution-Based Models

| **Architecture** | **ImageNet** | **ImageNet -A** | **ImageNet -O** | **ImageNet -R** | **Stylized-ImageNet** | **ImageNet -Sketch** |
| ---------------- | ------------ | --------------- | --------------- | --------------- | --------------------- | -------------------- |
| ConvNext         | 87.8         | 35.79           | 2.18            | 51.71           | 19.24                 | 38.22                |
| EfficientNetV2   | 87.3         | 22.31           | 2.21            | 52.97           | 23.3                  | 40.33                |
| ResNeSt          | 83.9         | 5.47            | 2.2             | 37.77           | 7.39                  | 25.28                |
| ResNet           | 79.29        | 1.88            | 2.23            | 28.93           | 3.59                  | 16.84                |
| Xception         | 79.88        | 3.53            | 2.28            | 33.52           | 9.33                  | 18.26                |

#### Convolution-Based Models

Convolution-based models, such as ConvNets, process visual data through layers of convolutions, pooling, and non-linear activations. They excel at capturing local spatial hierarchies in images, making them highly effective for tasks like object recognition and classification. Over time, innovations like depthwise separable convolutions and residual connections have increased their efficiency and depth, leading to architectures like **ConvNext** and **EfficientNetV2**.

### Top 5 Attention-Based Models

| **Architecture** | **ImageNet** | **ImageNet -A** | **ImageNet -O** | **ImageNet -R** | **Stylized-ImageNet** | **ImageNet -Sketch** |
| ---------------- | ------------ | --------------- | --------------- | --------------- | --------------------- | -------------------- |
| CaiT             | 86.5         | 34.4            | 2.2             | 49.95           | 19.48                 | 36.03                |
| CrossViT         | 81.5         | 31.8            | 2.2             | 47.1            | 18.51                 | 33.49                |
| DeiT3            | 83.1         | 40.12           | 2.22            | 53.63           | 25.45                 | 40.06                |
| Swin             | 87.3         | 39.41           | 2.19            | 48.64           | 18.36                 | 34.37                |
| VOLO             | 87.1         | 41.03           | 2.23            | 48.53           | 17.74                 | 36.11                |

#### Attention-Based Models

Attention-based models, like Vision Transformers (ViT), capture long-range dependencies within images by applying self-attention mechanisms. Instead of relying on convolutional operations, these models divide images into patches and use multi-head attention to learn relationships between different parts of the image. Attention models excel at capturing global context, achieving state-of-the-art results in tasks requiring holistic image understanding, as seen in models like **Swin** and **DeiT3**.

### Top 5 Hybrid (Convolution + Attention) Models

| **Architecture** | **ImageNet** | **ImageNet -A** | **ImageNet -O** | **ImageNet -R** | **Stylized-ImageNet** | **ImageNet -Sketch** |
| ---------------- | ------------ | --------------- | --------------- | --------------- | --------------------- | -------------------- |
| ConViT           | 81.3         | 29.69           | 2.21            | 48.79           | 19.81                 | 35.53                |
| EdgeNeXt         | 71.2         | 21.83           | 2.23            | 51.04           | 16.26                 | 37.13                |
| LeViT            | 80.0         | 11.51           | 2.22            | 40.28           | 15.59                 | 26.39                |
| RegNet           | 80.25        | 26.48           | 2.17            | 44.74           | 11.88                 | 32.93                |
| Sequencer        | 84.6         | 35.36           | 2.18            | 48.56           | 16.74                 | 35.87                |

#### Hybrid Models (Convolution + Attention)

Hybrid models combine the strengths of both convolution and attention mechanisms. These architectures use convolution layers to extract low-level features and attention mechanisms to capture global dependencies. By fusing these two approaches, hybrid models like **ConViT** and **LeViT** balance local feature extraction with global context understanding, achieving both efficiency and accuracy in visual tasks.

### Other Architectures

| **Architecture** | **ImageNet** | **ImageNet -A** | **ImageNet -O** | **ImageNet -R** | **Stylized-ImageNet** | **ImageNet -Sketch** |
| ---------------- | ------------ | --------------- | --------------- | --------------- | --------------------- | -------------------- |
| MLPMixer         | 76.44        | 5.79            | 2.25            | 32.75           | 10.04                 | 19.32                |
| MobileNetV3      | 75.77        | 4.59            | 2.2             | 35.11           | 10.85                 | 22.95                |
| RegNet           | 80.25        | 26.48           | 2.17            | 44.74           | 11.88                 | 32.93                |
| Sequencer        | 84.6         | 35.36           | 2.18            | 48.56           | 16.74                 | 35.87                |

#### Explanation of the Top 5 Other Architectures

1. **MLPMixer**:

   - Uses MLPs instead of convolutions or self-attention for vision tasks by mixing spatial and channel information. Efficient for large datasets.

2. **MobileNetV3**:

   - Lightweight model designed for mobile devices, using depthwise separable convolutions and neural architecture search (NAS) to optimize performance with low computational cost.

3. **RegNet**:

   - Scalable model family balancing depth and width, designed for efficient computation across different resource constraints, performing well on large vision tasks.

4. **Sequencer**:
   - A vision model that adapts sequence modeling techniques from NLP, processing images as sequences to capture long-range dependencies.

 {% reference rahman2023out %}