---
layout: page
title: "Epistemic Parity: Reproducibility as an Evaluation Metric for Differential Privacy"
description: "A benchmark and evaluation for reproducibility in differential privacy with state-of-the-art DP synthesizers."
img: assets/img/epistemic-parity.jpg
importance: 1
category: research
related_publications: true
---
<!-- To-DO: add figures -->

## Introduction

This project proposes an evaluation methodology called **epistemic parity**, which assesses the reproducibility of empirical conclusions in peer-reviewed papers using differentially private (DP) synthetic data. We reproduced findings from a selection of peer-reviewed papers using public datasets and compared these results to those generated using DP synthetic data. The goal is to determine whether conclusions hold when DP mechanisms are applied, thereby evaluating the utility of synthetic data. 

This methodology aims to shift the focus of DP mechanisms toward preserving utility in real-world applications by measuring how likely the conclusions of papers remain unchanged when using DP synthetic data.

## Methodology

We selected a benchmark of peer-reviewed sociology papers from the ICPSR repository, reproducing empirical findings on public datasets. We then generated DP synthetic datasets using five state-of-the-art DP synthesizers (MST, PrivBayes, PATECTGAN, AIM, and PrivMRF), and re-ran the experiments to compare the results with the original findings.

The benchmark consists of papers that span a variety of data and methodologies, and the primary evaluation metric is **epistemic parity**, which measures the reproducibility of findings on synthetic data compared to original data.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="<Figure 1: A Visual Finding from Fairman et al. (2020)>" title="Figure 1: A Visual Finding from Fairman et al. (2020)" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Results

The results demonstrate that state-of-the-art DP synthesizers are able to achieve high epistemic parity in many cases, though some papers presented challenges due to high-dimensional data and specific findings.

### Table 1: Synthesizer Performance on Benchmark Papers

| **Synthesizer** | **Parity (ε = e²)** | **Computational Feasibility** |
|----------------|----------------------|------------------------------|
| MST            | High                 | Efficient                    |
| PrivBayes      | High                 | Moderate                     |
| AIM            | Moderate             | Efficient                    |
| PATECTGAN      | Moderate             | High (GPU needed)            |
| PrivMRF        | Low                  | Very High (GPU needed)       |

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="<Figure 3: Epistemic Parity for Competitive Mechanisms>" title="Figure 3: Epistemic Parity for Competitive Mechanisms" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

### Findings:
- **MST** and **PrivBayes** performed best on low-dimensional tabular data.
- **PATECTGAN** showed promise for high-dimensional data but struggled with some findings.
- **PrivMRF** was computationally expensive, limiting its application in high-dimensional settings.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="<Figure 4: Average Epistemic Parity Across Papers>" title="Figure 4: Average Epistemic Parity Across Papers" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Future Work

Future directions include improving DP mechanisms to handle high-dimensional data more effectively, focusing on application-specific threat models and utility guarantees. We also advocate for continued evaluation of DP mechanisms across diverse datasets and domains.

For more details, visit the [GitHub Repository](https://github.com/DataResponsibly/SynRD).
