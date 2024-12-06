---
layout: page
title: "Nutritional Labels for Automated Decision Systems by Home Credit Default Risk"
description: A fairness and explainability analysis on loan repayment predictions using machine learning models.
img: assets/img/ads/pairwise.png
importance: 1
category: research
related_publications: false
---

## Introduction

This project analyzes the fairness and explainability of an Automated Decision System (ADS) designed to predict loan repayment using the Home Credit Default Risk dataset. We focused on applying Logistic Regression and Random Forest models, while ensuring fairness across subpopulations such as age, gender, and education.

## Data Preprocessing

We processed the Home Credit dataset to encode categorical variables, impute missing values, and scale features. We handled the imbalanced class distribution by applying evaluation metrics that account for it.

The dataset includes multiple files with loan applications, credit history, and client information. Key files:

- `application_train.csv` and `application_test.csv`: Loan application data with and without the target.
- `bureau.csv`: Data from the Credit Bureau on clients' past loans.

The target is imbalanced: far more loans are repaid than defaulted, introducing challenges to model accuracy.

## Model Selection

We evaluated two models: Logistic Regression as a baseline and Random Forest for final analysis. Random Forest was selected due to its higher accuracy and compatibility with fairness tools like AIF360 and explainability with LIME.

## Results

The Random Forest model achieved 67% accuracy and showed minimal bias when analyzing protected attributes such as age, gender, and education. However, the imbalanced class distribution affected model performance.

### Key Insights

- **Fairness**: Minimal bias was observed for age, gender, or education.
- **Imbalance**: Addressing the target imbalance is crucial for improving accuracy.

### Figures

<div class="row">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ads/ext.png" title="Figure 1: EXT_SOURCE Distributions" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ads/correlation.png" title="Figure 2: Correlation Analysis" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ads/correct1.png" title="Figure 3: LIME Explanation (Correct Classification)" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ads/class.png" title="Figure 4: Prediction Probabilities (Classified Example)" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ads/misclass.png" title="Figure 5: Prediction Probabilities (Misclassified Example)" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ads/pairwise.png" title="Figure 6: Mutual Information" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## Conclusion

The ADS demonstrated fairness, but future improvements should address the class imbalance and incorporate more external datasets to enhance prediction accuracy.

For more details, visit the [GitHub Repository](https://github.com/wonkwonlee/nutrition-labels-for-home-credit-default-risk).
