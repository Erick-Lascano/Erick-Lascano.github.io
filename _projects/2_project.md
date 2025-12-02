---
layout: page
title: MovieLens Recommendation System
description: Collaborative filtering model on 10M dataset (HarvardX Capstone).
img: assets/img/movielens_cover.jpg
importance: 2
category: Data Science
github: https://github.com/Erick-Lascano/Data-Science-Capstone-MovieLens-HarvardX
---

This project is the capstone for the **HarvardX Data Science Professional Certificate**. The objective was to build a recommendation system using the **MovieLens 10M dataset** capable of predicting user ratings with a Root Mean Square Error (RMSE) below **0.86490**.

The final solution implements a **Regularized Collaborative Filtering** model, inspired by the Netflix Prize-winning algorithms (*BellKor's Pragmatic Chaos*), achieving a final RMSE of **0.8641**.

### 🎯 Project Goal & Mathematical Foundation

The core metric for evaluation is the RMSE, defined as:

$$RMSE = \sqrt{\frac{1}{N}\sum_{u,i}(\hat{y}_{u,i} - y_{u,i})^2}$$

Where $$y_{u,i}$$is the rating by user$$u$$for movie$$i$$, and $$N$$ is the total number of ratings. The goal was to minimize this error by modeling the inherent biases of users and movies.

<div class="row justify-content-sm-center">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Distribution-plot.png" title="Ratings Distribution" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/Ratings-peruser.png" title="Ratings per User" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row justify-content-sm-center mt-3">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/ratins-genre.png" title="Ratings by Genre" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/topmovies.png" title="Top Movies" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    <strong>Exploratory Data Analysis:</strong> (Top-Left) Global distribution of ratings showing integer bias. (Top-Right) Long-tail distribution of ratings per user. (Bottom-Left) Average rating variability across genres. (Bottom-Right) Top movies with the highest number of ratings.
</div>

### 🛠️ Methodology: Regularized Effects

The model improves upon a simple average by adding **bias terms** ($b$) that account for the fact that some movies are generally rated higher ($b_i$) and some users are more critical ($b_u$). To prevent overfitting on movies with few ratings, we applied **Regularization**:

The regularized estimate for the movie effect $\hat{b}_i(\lambda)$ is calculated as:

$$\hat{b}_i(\lambda) = \frac{\sum_{u=1}^{n_i} (y_{u,i} - \hat{\mu})}{n_i + \lambda}$$

Where $\lambda$ is a tuning parameter that penalizes estimates from small sample sizes ($n_i$). The final model equation becomes:

$$\hat{y}_{u,i} = \hat{\mu} + \hat{b}_i(\lambda) + \hat{b}_u(\lambda)$$

### 📊 Results & Conclusion

The model was trained on the `edx` set (90% of data) and validated on a held-out set. The optimal regularization parameter was found to be $\lambda = 5$.

* **Target RMSE:** < 0.86490
* **Final RMSE:** **0.8641** (Success)

This result demonstrates that a linear model with careful regularization can capture significant variance in user preferences without the computational cost of matrix factorization.

### 📚 Technologies Used

* **R & RStudio:** Core statistical computing.
* **Tidyverse:** For efficient data manipulation (`dplyr`) and visualization (`ggplot2`).
* **Caret:** For machine learning workflows.

<br>
<div class="alert alert-light">
    <p><strong>References:</strong> Koren, Y. (2009). The BellKor solution to the Netflix Grand Prize.</p>
</div>
