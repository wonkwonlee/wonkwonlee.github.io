---
layout: page
title: Epistemic Parity: Reproducibility as an Evaluation Metric for Differential Privacy
description: A benchmark and evaluation for reproducibility in differential privacy with state-of-the-art DP synthesizers.
img: assets/img/synrd/synrd-figure1.pdf
importance: 1
category: research
related_publications: true
---

## Introduction

This project proposes an evaluation methodology called **epistemic parity**, which assesses the reproducibility of empirical conclusions in peer-reviewed papers using differentially private (DP) synthetic data. We reproduced findings from a selection of peer-reviewed papers using public datasets and compared these results to those generated using DP synthetic data. The goal is to determine whether conclusions hold when DP mechanisms are applied, thereby evaluating the utility of synthetic data. 

This methodology aims to shift the focus of DP mechanisms toward preserving utility in real-world applications by measuring how likely the conclusions of papers remain unchanged when using DP synthetic data.

## Methodology

### 1. Benchmark Creation & Dataset Selection

We created a benchmark using a diverse selection of peer-reviewed papers from public repositories like **ICPSR**. These papers span various domains, including sociology and other social sciences, where privacy concerns are paramount. Each paper was chosen based on the availability of the dataset and the potential sensitivity of the information involved, making them ideal candidates for applying differential privacy mechanisms.

The datasets were processed using five state-of-the-art DP synthesizers: **MST**, **PrivBayes**, **PATECTGAN**, **AIM**, and **PrivMRF**. These synthesizers were applied with various privacy budgets (`ε`) to generate synthetic versions of the original data, preserving privacy while attempting to retain utility.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/synrd/synrd-figure2.png" title="Figure 2: Workflow" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### 2. Evaluation via Epistemic Parity

We introduce **epistemic parity** as a new metric to measure the reproducibility of findings when using differentially private synthetic data. This metric evaluates how well the results obtained from synthetic data match those from the original datasets. 

For each benchmark paper, we reran the original analyses using both the real and synthetic data. We then compared key metrics, such as model accuracy, effect sizes, or statistical significance, between the original and synthetic datasets. This comparison allows us to assess whether the empirical conclusions drawn from real data hold true when using synthetic data, providing a tangible measure of the utility of DP mechanisms.

### Results

The results demonstrate that state-of-the-art DP synthesizers are able to achieve high epistemic parity in many cases, though some papers presented challenges due to high-dimensional data and specific findings.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/synrd/synrd-figure2.png" title="Figure 1: A Visual Finding from Fairman et al. (2020)" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/synrd/synrd-figure3.png" title="Figure 3: Epistemic Parity for Competitive Mechanisms" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Findings:
- **MST** and **PrivBayes** performed best on low-dimensional tabular data.
- **PATECTGAN** showed promise for high-dimensional data but struggled with some findings.
- **PrivMRF** was computationally expensive, limiting its application in high-dimensional settings.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/synrd/synrd-figure4.png" title="Figure 4: Average Epistemic Parity Across Papers" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Future Work

Future directions include improving DP mechanisms to handle high-dimensional data more effectively, focusing on application-specific threat models and utility guarantees. We also advocate for continued evaluation of DP mechanisms across diverse datasets and domains.

For more details, visit the [GitHub Repository](https://github.com/DataResponsibly/SynRD).
