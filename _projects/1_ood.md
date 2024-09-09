---
layout: page
title: Out-of-distribution Robustness Evaluation of State-of-the-art Vision Models
description: Research project comparing the robustness of 58 computer vision models
img: assets/img/project-vision.jpg
importance: 1
category: work
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

### Top 15 Models - Performance on ImageNet, ImageNet-A, and ImageNet-O

| **Architecture**    | **ImageNet** | **ImageNet -A** | **ImageNet -O** |
|---------------------|--------------|-----------------|-----------------|
| ConvNext            | 87.8         | 35.79           | 2.18            |
| CaiT                | 86.5         | 34.4            | 2.2             |
| CrossViT            | 81.5         | 31.8            | 2.2             |
| DeiT3               | 83.1         | 40.12           | 2.22            |
| EfficientNetV2      | 87.3         | 22.31           | 2.21            |
| MViTv2              | 88.8         | 43.09           | 2.24            |
| Swin                | 87.3         | 39.41           | 2.19            |
| ResNeSt             | 83.9         | 5.47            | 2.2             |
| ViT                 | 85.17        | 11.25           | 2.61            |
| VOLO                | 87.1         | 41.03           | 2.23            |
| RegNet              | 80.25        | 26.48           | 2.17            |
| ResNet              | 79.29        | 1.88            | 2.23            |
| Xception            | 79.88        | 3.53            | 2.28            |
| MLPMixer            | 76.44        | 5.79            | 2.25            |
| Sequencer           | 84.6         | 35.36           | 2.18            |

### Performance on ImageNet-R, Stylized-ImageNet, and ImageNet-Sketch

| **Architecture**    | **ImageNet -R** | **Stylized-ImageNet** | **ImageNet -Sketch** |
|---------------------|-----------------|----------------------|----------------------|
| ConvNext            | 51.71           | 19.24                | 38.22                |
| CaiT                | 49.95           | 19.48                | 36.03                |
| CrossViT            | 47.1            | 18.51                | 33.49                |
| DeiT3               | 53.63           | 25.45                | 40.06                |
| EfficientNetV2      | 52.97           | 23.3                 | 40.33                |
| MViTv2              | 51.89           | 19.16                | 38.11                |
| Swin                | 48.64           | 18.36                | 34.37                |
| ResNeSt             | 37.77           | 7.39                 | 25.28                |
| ViT                 | 38.42           | 14.37                | 17.36                |
| VOLO                | 48.53           | 17.74                | 36.11                |
| RegNet              | 44.74           | 11.88                | 32.93                |
| ResNet              | 28.93           | 3.59                 | 16.84                |
| Xception            | 33.52           | 9.33                 | 18.26                |
| MLPMixer            | 32.75           | 10.04                | 19.32                |
| Sequencer           | 48.56           | 16.74                | 35.87                |

<!-- <div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/vision-1.jpg" title="Example Model Performance" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/vision-2.jpg" title="Benchmark Comparisons" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/vision-3.jpg" title="Visual Model Performance" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
    Performance comparison of various models on OOD datasets.
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/vision-summary.jpg" title="OOD Robustness Summary" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/vision-performance.jpg" title="Performance Metrics" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Summary of the overall robustness performance across different models.
</div> -->

To download the full report, you can access the attached [PDF](assets/reports/out-of-distribution-vision-models.pdf).