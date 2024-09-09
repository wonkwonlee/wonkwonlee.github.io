---
layout: page
title: Time-series Medical Image Classification
description: Image Classification Model for Temporal Disease Progression of Chest X-ray dataset
img: assets/img/timeseries_medical/medical-1.jpg
related_publications: true
---

## Introduction

Disease progression modeling (DPM) uses mathematical and scientific principles to describe the quantitative progression of a disease over time. One such task is to predict the three states of disease progression (improving, stable, or worsening) based on current and past chest X-ray images. This project fine-tunes and evaluates the pre-trained Torch X-ray Vision model for this temporal image classification task.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/timeseries_medical/medical-1.jpg" title="Figure 1: Architecture of Model" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/timeseries_medical/medical-2.jpg" title="Figure 2: Data Sparsity in Time-series" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/timeseries_medical/medical-3.jpg" title="Figure 2: Data Sparsity in Time-series" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Experiments and Results

The following tables summarize the performance of different feature extraction methods and classification models for the five diseases in the dataset:

### Table 1: Performance of Models on Disease Progression Task

| **Model/Feature Extractor** | **Edema** | **Consolidation** | **Pleural Effusion** | **Pneumothorax** | **Pneumonia** | **Average Accuracy** |
| --------------------------- | --------- | ----------------- | -------------------- | ---------------- | ------------- | -------------------- |
| DenseNet-RSNA               | 45.28%    | 45.0%             | 60.98%               | 50.0%            | 61.70%        | 53.70%               |
| DenseNet-MIMIC-CH           | 45.28%    | 42.5%             | 57.31%               | 54.76%           | 63.83%        | 53.40%               |
| DenseNet-CheX               | 47.17%    | 50.0%             | 62.20%               | 54.76%           | 63.83%        | 56.40%               |
| Logistic Regression         | 44.08%    | 51.00%            | 39.02%               | 37.21%           | 56.13%        | 45.49%               |

### Table 2: Prediction on Flipped Input (Logistic Regression Model)

| **Original Prediction** | **Stable** | **Improving** | **Worsening** | **Prediction on Flipped Input** |
| ----------------------- | ---------- | ------------- | ------------- | ------------------------------- |
| Stable                  | 54         | 45            | 0             | Stable                          |
| Improving               | 21         | 92            | 7             | Improving                       |
| Worsening               | 4          | 32            | 3             | Worsening                       |

### Table 3: Prediction on Flipped Input (Model 2)

| **Original Prediction** | **Stable** | **Improving** | **Worsening** | **Prediction on Flipped Input** |
| ----------------------- | ---------- | ------------- | ------------- | ------------------------------- |
| Stable                  | 96         | 33            | 1             | Stable                          |
| Improving               | 39         | 58            | 22            | Improving                       |
| Worsening               | 1          | 13            | 1             | Worsening                       |

### Table 4: Prediction on Flipped Input (Model 3)

| **Original Prediction** | **Stable** | **Improving** | **Worsening** | **Prediction on Flipped Input** |
| ----------------------- | ---------- | ------------- | ------------- | ------------------------------- |
| Stable                  | 48         | 18            | 10            | Stable                          |
| Improving               | 12         | 41            | 29            | Improving                       |
| Worsening               | 9          | 21            | 76            | Worsening                       |

## Future Work

To improve the model, future research can explore semi-supervised learning techniques to handle missing data more effectively and investigate the use of lateral chest X-rays for enhanced predictive capabilities. Hyperparameter tuning of the Vision Transformer model can also lead to performance gains.

For more details, check the [GitHub Repository](https://github.com/vaibhavg152/TimeSeriesMedicalImageClassification).
