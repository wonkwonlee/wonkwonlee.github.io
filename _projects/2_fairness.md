---
layout: page
title: "Fairness-Enhancing Interventions in ML Pipelines"
description: Exploring fairness-enhancing methods in binary classification pipelines using AIF360 and Folktables datasets.
img: assets/img/fairness/aif360.svg
importance: 1
category: research
related_publications: false
---

## Introduction

This project investigates fairness-enhancing interventions in binary classification pipelines, focusing on their impact on fairness and accuracy metrics. The project utilizes the Folktables ACSIncome dataset, where sex is the sensitive attribute. The goal is to implement fairness-enhancing algorithms and evaluate their effects on multiple metrics, using the AIF360 library and Python.

### Key Objectives:
1. Train a baseline Random Forest model and evaluate its performance.
2. Tune hyperparameters for the baseline model to improve accuracy while analyzing the impact on fairness.
3. Incorporate fairness-enhancing algorithms:
   - **Pre-Processing**: Disparate Impact Remover (DI-Remover).
   - **In-Processing**: Prejudice Remover.
   - **Post-Processing**: Reject Option Classification.

### Evaluation Metrics:
1. Overall accuracy.
2. Accuracy for the privileged group.
3. Accuracy for the unprivileged group.
4. Disparate Impact.
5. False Positive Rate Difference.

---

## Methodology

### 1. Baseline Random Forest Model
- Train a Random Forest model on the ACSIncome dataset using a 70/10/20 train-validation-test split.
- Evaluate the following metrics on the test set:
  - Overall accuracy
  - Accuracy for privileged and unprivileged groups
  - Disparate Impact
  - False Positive Rate Difference

### 2. Hyperparameter Tuning
- Optimize hyperparameters for the Random Forest model using the validation set.
- Evaluate the tuned model on 10 different train-validation-test splits, comparing performance on fairness and accuracy metrics before and after tuning.

### 3. Fairness-Enhancing Algorithms

#### a. Disparate Impact Remover (DI-Remover)
- Apply DI-Remover to the dataset with varying repair levels.
- Train the Random Forest model on the transformed datasets and evaluate the impact on fairness and accuracy metrics.

#### b. Prejudice Remover
- Train a Prejudice Remover classifier with different values of the `eta` parameter ([0.01, 0.1, 1]).
- Analyze the trade-off between fairness and accuracy.

#### c. Reject Option Classification
- Use Reject Option Classification on predictions from the baseline Random Forest model.
- Evaluate its impact on fairness metrics across 10 train-validation-test splits.

## Results and Discussion

- **Baseline Model**: Evaluated fairness and accuracy metrics, providing a benchmark for comparison.
- **Hyperparameter Tuning**: Examined its effect on improving accuracy and its unintended impact on fairness.
- **DI-Remover**: Analyzed how increasing repair levels affect Disparate Impact and accuracy trade-offs.
- **Prejudice Remover**: Explored how fairness regularization (`eta`) modifies both fairness and accuracy.
- **Reject Option Classification**: Compared results to other fairness-enhancing methods, highlighting its effectiveness in mitigating bias.


## Figures and Visualizations

### Metric Comparison Before and After Tuning
<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/fairness/privileged.png" title="Privileged Group Accuracy" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/fairness/unprivileged.png" title="Unprivileged Group Accuracy" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/fairness/di.png" title="Disparate Impact" %}
    </div>
</div>

### Impact of DI-Remover Repair Level

<div class="row">
    <div class="col-sm-5 mt-2 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/fairness/di-remover.png" title="Disparate Impact" %}
    </div>
    <div class="col-sm-5 mt-2 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/fairness/fpr.png" title="False Positive Rate Difference" %}
    </div>
</div>

## Notebook and Code

The complete code and analysis are available in the [Fairness-Enhancing Interventions Repository](https://github.com/wonkwonlee/fairness-intervention).

## Future Work

Future directions include:
1. Extending fairness-enhancing algorithms to multi-class classification problems.
2. Exploring advanced datasets with richer sensitive attributes.
3. Investigating other fairness-enhancing methods, such as adversarial debiasing.