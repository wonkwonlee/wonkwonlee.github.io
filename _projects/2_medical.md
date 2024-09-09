---
layout: page
title: Time-series Medical Image Classification
description: Image Classification Model for Temporal Disease Progression of Chest X-ray dataset
img: assets/img/medical-image-classification.jpg
importance: 1
category: work
related_publications: true
---

## Introduction

Disease progression modeling (DPM) uses mathematical and scientific principles to describe the quantitative progression of a disease over time. One such task is to predict the three states of disease progression (improving, stable, or worsening) based on current and past chest X-ray images. This project fine-tunes and evaluates the pre-trained Torch X-ray Vision model for this temporal image classification task. For more details, check the [GitHub Repository](https://github.com/vaibhavg152/TimeSeriesMedicalImageClassification).

## Experiments and Results

The following table summarizes the performance of different feature extraction methods and classification models:

| **Model/Feature Extractor** | **Edema** | **Consolidation** | **Pleural Effusion** | **Pneumothorax** | **Pneumonia** | **Average Accuracy** |
|----------------------------|-----------|-------------------|----------------------|------------------|--------------|---------------------|
| DenseNet-RSNA               | 45.28%    | 45.0%             | 60.98%               | 50.0%            | 61.70%       | 53.70%              |
| DenseNet-MIMIC-CH           | 45.28%    | 42.5%             | 57.31%               | 54.76%           | 63.83%       | 53.40%              |
| DenseNet-CheX               | 47.17%    | 50.0%             | 62.20%               | 54.76%           | 63.83%       | 56.40%              |
| Logistic Regression         | 44.08%    | 51.00%            | 39.02%               | 37.21%           | 56.13%       | 45.49%              |

The DenseNet-CheX extractor consistently performed best across multiple metrics, highlighting its robustness for chest X-ray classification.

## Future Work

To improve the model, future research can explore semi-supervised learning techniques to handle missing data more effectively and investigate the use of lateral chest X-rays for enhanced predictive capabilities. Hyperparameter tuning of the Vision Transformer model can also lead to performance gains.