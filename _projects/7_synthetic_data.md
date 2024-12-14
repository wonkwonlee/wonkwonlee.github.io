---
layout: page
title: "Privacy-Preserving Synthetic Data"
description: Generating privacy-preserving synthetic datasets and evaluating their accuracy and fairness using Data Synthesizer and MST.
img: assets/img/synthetic/box-whisker-kl.png
importance: 1
category: research
related_publications: false
---

## Introduction

This project explores privacy-preserving synthetic data generation using the Data Synthesizer and MST methods. We evaluate the generated data's statistical properties and how well it preserves relationships from sensitive datasets.

### Objectives:
1. Generate synthetic datasets from sensitive data using various modes (Random, Independent Attribute, Correlated Attribute).
2. Evaluate the accuracy of statistical properties in the synthetic data compared to the real data.
3. Compare two privacy-preserving synthetic data generators: Data Synthesizer and MST.

## Methodology

### Synthetic Data Generation
Using **Data Synthesizer**, synthetic datasets were generated under the following configurations:
- **Mode A:** Random mode.
- **Mode B:** Independent attribute mode with ε = 0.1.
- **Mode C:** Correlated attribute mode with k = 1, ε = 0.1.
- **Mode D:** Correlated attribute mode with k = 2, ε = 0.1.

Each dataset contains 10,000 samples.

### Evaluation Metrics:
1. **Statistical Queries:** Compare metrics (Mean, Median, Min, Max) for age and score attributes.
2. **Distribution Analysis:** Visualize histograms of age and sex for synthetic and real datasets.
3. **Statistical Tests:** Use Kolmogorov-Smirnov and KL-divergence to measure data similarity.
4. **Mutual Information:** Analyze pairwise mutual information between attributes.

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/synthetic/heatmap.png" title="Figure 1: Mutual Information Heatmap of Synthetic Data" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


## Results

- **Synthetic Data Accuracy:** Random mode showed lower accuracy in statistical queries compared to correlated attribute modes.
- **Distribution Analysis:** Independent attribute mode (B) better preserved the original distribution than random mode (A).
- **Privacy Budget Impact:** Lower ε values increased privacy but reduced the fidelity of the synthetic data.

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/synthetic/box-whisker-kl.png" title="Figure 2: Box-and-Whiskers plot of KL-divergence" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/synthetic/pairwise.png" title="Figure 3: Box-and-Whiskers plot of aggregated difference in pairwise mutual information" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/synthetic/pairwise-mst.png" title="Figure 4: Box-and-Whiskers plot of aggregated difference in pairwise mutual information for MST" class="img-fluid rounded z-depth-1" %}
    </div>
</div>



## Code
The code can be found in GitHub [repository](https://github.com/wonkwonlee/data-synthesizer).

## Future Work

1. Extend to multi-class classification datasets.
2. Evaluate synthetic data generation on larger and more complex datasets.
3. Compare additional privacy-preserving methods like PrivBayes and PATECTGAN.