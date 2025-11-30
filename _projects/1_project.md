---
layout: page
title: Spotify Data Analysis
description: Unsupervised learning & EDA on Top 2023 Songs (Stanford CS 65W).
img: assets/img/spotify_cover.jpg
importance: 1
category: Data Science
github: https://github.com/Erick-Lascano/Data-Analysis-with-Python-Stanford-Continuing-Studies-CS-65W
related_publications: false
---

This repository contains the final project for the **Stanford Continuing Studies** course on **Data Analysis with Python (CS 65W)**. The project focuses on Exploratory Data Analysis (EDA), Data Preprocessing, Data Visualization, and the implementation of unsupervised machine learning algorithms on a real-world dataset.

### 🎯 Project Goal

The goal was to apply data analysis techniques to uncover insights in the **Top Spotify Songs 2023** dataset. By leveraging libraries like Pandas for manipulation and Scikit-Learn for clustering, we identified distinct patterns in musical features (danceability, energy, bpm) that define popular music today. This project demonstrates the skills and concepts learned during the course with instructor Matt Harrison.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/spotify_corr.jpg" title="Correlation Matrix" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/spotify_elbow.jpg" title="Elbow Method" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/spotify_clusters.jpg" title="PCA Clusters" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Visualizations from the notebook: Feature Correlation Matrix (Left), Elbow Method for optimal K (Middle), and PCA projection of song clusters (Right).
</div>

### 🛠️ Key Technologies & Methods

The analysis was performed using the Python ecosystem, specifically:

* **Pandas:** For rigorous data cleaning (handling encoding errors in the 'streams' column and missing values).
* **Matplotlib & Seaborn:** For visualizing distributions of BPM, modes, and feature correlations.
* **Scikit-Learn:**
    * **PCA (Principal Component Analysis):** Dimensionality reduction to visualize high-dimensional data.
    * **K-Means Clustering:** Grouping songs into distinct clusters based on audio features.

### 📊 Results & Insights

All the analysis is documented within the `Spotify_Data_Analysis.ipynb` notebook. Key findings include the identification of distinct clusters of songs that share similar "energy" and "danceability" profiles, providing a data-driven approach to playlist generation.

The dataset used in this project is courtesy of Kaggle: [Top Spotify Songs 2023](https://www.kaggle.com/datasets/nelgiriyewithana/top-spotify-songs-2023/data).

### 📚 Additional Resources

This project applies concepts from the course and the instructor's book, *"Effective Pandas: Patterns for Data Manipulation"* by Matt Harrison.

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/spotify_dashboard.jpg" title="Data Overview" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        <p><strong>Future Work:</strong> I plan to extend this analysis by integrating the Spotify API to pull real-time audio features and predict the popularity of new releases based on the identified clusters.</p>
        <p><strong>Contributing:</strong> Contributions are welcome! Please create a pull request or open an issue to discuss improvements.</p>
        <p><strong>License:</strong> This project is licensed under the MIT License.</p>
    </div>
</div>
