---
layout: page
title: "Explaining Predictions with SHAP"
description: Using SHAP to interpret predictions from a classifier trained on the 20 Newsgroups dataset.
img: assets/img/shap/shap_summary1.png
importance: 1
category: research
related_publications: false
---

## Introduction

This project demonstrates the use of **SHAP (SHapley Additive exPlanations)** to explain predictions made by a text classifier trained on a subset of the 20 Newsgroups dataset. By analyzing SHAP values, we uncover insights into the features (words) that contribute to the classifier’s predictions, including cases of correct classifications and misclassifications.


## Methodology

### Dataset and Preprocessing
- **Dataset**: The 20 Newsgroups dataset (Atheism vs. Christianity categories) was used.
- **Preprocessing**: 
  - Text was vectorized using **TF-IDF** to represent words numerically.
  - Features were limited to the top 1,000 terms for efficiency.
  
### Classification
- **Model**: A linear Support Vector Machine trained using **SGDClassifier**.
- **Metrics**: The classifier’s accuracy was evaluated using a **confusion matrix**.

### SHAP Explanations
1. Generated SHAP explanations for correctly and misclassified documents.
2. Identified key features contributing to classification and misclassification.
3. Visualized SHAP values for individual documents and summarized feature importance across the dataset.

<div class="row">
    <div class="col-sm-5 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/shap/shap.png" title="Figure 1: Example of SHAP Explanation" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


## Results


### SHAP Analysis
- Misclassified documents were analyzed using SHAP to identify features contributing to errors.
- SHAP summary plots revealed that domain-specific words like "faith" and "science" had significant impacts on misclassifications.

<div class="row">
    <div class="col-sm-5 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/shap/shap_summary1.png" title="Figure 2: SHAP Summary Plot 1" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-5 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/shap/shap_summary2.png" title="Figure 3: SHAP Summary Plot 2" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/shap/count_weight.png" title="Figure 4: Number of misclassified documents vs Sum of misclassfied weights" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


### Feature Selection with SHAP
- SHAP values were used to identify the most important features for the model.
- A new model trained on selected features achieved an improved accuracy of 96.93%.
- Example: A document misclassified before feature selection was correctly classified after retraining the model on the selected features.

## Notebook and Code

The full implementation is available in the Jupyter Notebook:

[SHAP Explanations Notebook](../assets/notebooks/generating_explanations_with_shap.ipynb)

## Future Work

1. Extend SHAP explanations to multi-class classification tasks.
2. Experiment with other datasets and classifiers to compare SHAP’s utility.
3. Explore advanced feature selection methods informed by SHAP values.
