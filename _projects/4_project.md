---
layout: page
title: Heart Disease Diagnosis Pipeline
description: Comparative analysis of SVM, Neural Networks, and Probabilistic Clustering for clinical prediction.
img: assets/img/heart_cover.jpg
importance: 1
category: Machine Learning & Healthcare
related_publications: false
---

Submitted as the **"Choose Your Own" Capstone project for the HarvardX Data Science program** , this research develops a robust **Machine Learning Pipeline** to predict the presence of heart disease using the UCI Heart Disease dataset[cite: 5, 16]. Beyond standard linear regression, the analysis explores the effectiveness of non-linear classification algorithms and unsupervised probabilistic clustering to uncover hidden structures in clinical data.

### 🔍 Exploratory Data Analysis

Before modeling, the relationships between clinical features and heart disease were analyzed. The visualizations highlight key physiological markers: older age, asymptomatic chest pain, and lower maximum heart rates are strongly correlated with the presence of disease[cite: 139, 140, 141].

<div class="row justify-content-sm-center">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Distribution - Heart.png" title="Age Distribution" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Disease - Heart.png" title="Chest Pain Correlation" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Violin Distribution.png" title="Max Heart Rate Distribution" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Clinical Feature Analysis: (Left) Age distribution showing a higher prevalence of disease in older patients[cite: 139]. (Center) Proportion of disease by Chest Pain Type, highlighting Type 4 (Asymptomatic) as a critical indicator[cite: 140]. (Right) Maximum heart rate distribution, indicating lower rates in positive cases[cite: 141].
</div>

### 🎯 Mathematical Formulation & Unsupervised Analysis

To understand the intrinsic geometry of the data, the patient population was modeled using **Gaussian Mixture Models (GMM)**[cite: 7, 299]. Unlike K-Means, GMM assumes the data is generated from a mixture of a finite number of Gaussian distributions with unknown parameters[cite: 300].

The probability density function is defined as:

$$p(\mathbf{x}) = \sum_{k=1}^{K} \pi_k \mathcal{N}(\mathbf{x} | \boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)$$

Where:
* $\mathbf{x}$ represents the vector of 14 clinical attributes (e.g., age, cholesterol, thalach)[cite: 126].
* $\pi_k$ is the mixing coefficient for the $k$-th component (cluster).
* $\mathcal{N}(\mathbf{x} | \boldsymbol{\mu}_k, \boldsymbol{\Sigma}_k)$ is the multivariate Gaussian density.

The algorithm automatically selected $K=2$ components, aligning perfectly with the binary nature of the diagnosis (Healthy vs. Disease)[cite: 303].

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/GMM.png" title="GMM Clustering with PCA" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Decision Tree.png" title="Decision Tree Logic" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Model Visualization: (Left) PCA projection showing the confidence ellipses of the two clusters identified by GMM, which strongly correlate with actual diagnosis labels[cite: 311, 364]. (Right) The pruned Decision Tree showing key splitting rules like 'cp' (chest pain) and 'thal'[cite: 221, 232].
</div>

### 🛠️ Algorithms & Methodology

A rigorous **10-fold Cross-Validation** scheme was implemented to train and compare three distinct supervised learning paradigms to ensure robustness and prevent overfitting[cite: 10, 199]:

1.  **Support Vector Machine (SVM):** Utilized a **Radial Basis Function (RBF)** kernel to project data into higher-dimensional space, capturing non-linear relationships between physiological markers[cite: 202, 204].
2.  **Decision Tree (CART):** Optimized for interpretability, allowing for the derivation of explicit medical decision rules[cite: 201].
3.  **Neural Network:** A feed-forward single-hidden-layer architecture designed to model complex interactions between inputs[cite: 206].

### 📊 Results & Impact

The models were evaluated on a held-out validation set based on Accuracy, Sensitivity, and Specificity[cite: 268].

* **Optimal Solution:** The **SVM (Radial)** model achieved the highest performance with an **Accuracy of 78.3%**[cite: 290]. It provided the most balanced diagnostic capability, maximizing both Sensitivity (0.786) and Specificity (0.781)[cite: 291].
* **Interpretability vs. Performance:** While the Decision Tree offered clear clinical rules and high specificity (0.813), it yielded lower sensitivity (0.607), missing a significant portion of positive cases compared to the kernel-based method[cite: 296, 297].
* **Cluster Validation:** The unsupervised GMM analysis confirmed that clinical variables naturally separate into two distinct groups (Cluster 1 predominantly Disease, Cluster 2 predominantly Healthy), validating the feasibility of ML-based diagnosis[cite: 364].

The final pipeline demonstrates that non-linear kernel methods (SVM) significantly outperform traditional tree-based methods for this specific high-dimensional medical dataset[cite: 369].

### 📚 Technologies Used

* **R:** Primary language for statistical computing[cite: 24].
* **Caret:** Used for unifying the training workflow and hyperparameter tuning[cite: 51].
* **Mclust:** Employed for Gaussian Mixture Model-based clustering[cite: 62].
* **Kernlab:** Implementation of the SVM with RBF kernel[cite: 74].
* **Tidyverse:** For data preprocessing, cleaning, and high-quality visualization[cite: 27].
* **Caret:** Used for unifying the training workflow and hyperparameter tuning[cite: 51].
* **Mclust:** Employed for Gaussian Mixture Model-based clustering[cite: 62].
* **Kernlab:** Implementation of the SVM with RBF kernel[cite: 74].
* **Tidyverse:** For data preprocessing, cleaning, and high-quality visualization[cite: 27].
