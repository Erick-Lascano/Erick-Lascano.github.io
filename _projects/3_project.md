---
layout: page
title: Stochastic Optimization for Reforestation
description: Metaheuristic allocation of plant species to minimize ecosystem competition.
img: assets/img/cover.jpg
importance: 3
category: Applied Mathematics
related_publications: false
---

This research project addresses the critical challenge of **Reforestation Optimization** in Mexico. Using **Stochastic Optimization** and **Metaheuristic Algorithms**, we designed a mathematical model to distribute 10 different plant species across a 1-hectare grid ($14 \times 47$ layout), maximizing survival rates by minimizing inter-species competition.

### 🎯 Mathematical Formulation

The problem was modeled as a **Combinatorial Optimization Problem** on a grid $G = \{(i, j) | 1 \le i \le 14, 1 \le j \le 47\}$. The goal is to assign a species $k$ to each cell to minimize the global competition index $Z$, subject to nutrient availability and adjacency constraints (modeled using the "Tres Bolillo" planting system).

The objective function can be defined as:

$$\min Z = \sum_{(i,j) \in G} \sum_{(u,v) \in N(i,j)} C(s_{i,j}, s_{u,v})$$

Where:
* $N(i,j)$ is the set of neighboring cells (adjacency) for position $(i,j)$.
* $s_{i,j}$ is the species assigned to cell $(i,j)$.
* $C(a, b)$ is the **Competition Coefficient** between species $a$ and $b$ (derived from nutrient matrices).

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/reforest_grid.jpg" title="Planting Grid Layout" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/reforest_competence.jpg" title="Competition Matrix" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/reforest_results.jpg" title="Algorithm Comparison" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Methodology Visualization: (Left) The $14 \times 47$ simulation grid. (Middle) Heatmap representing the inter-species competition matrix. (Right) Convergence results comparing Simulated Annealing vs. PSO.
</div>

### 🛠️ Algorithms & Methodology

Given the combinatorial complexity (assigning 524 new plants from 10 species into empty slots), exact methods were computationally infeasible. We implemented and compared three **Metaheuristic Algorithms**:

1.  **Simulated Annealing (SA):** A probabilistic technique approximating the global optimum by mimicking the cooling of metals.
2.  **Particle Swarm Optimization (PSO):** A population-based algorithm inspired by bird flocking behavior.
3.  **Sine Cosine Algorithm (SCA):** A mathematical optimization method using trigonometric functions to explore the search space.

### 📊 Results & Impact

We evaluated the performance of each algorithm based on the final **Competition Score** and convergence time.

* **Optimal Solution:** The **Simulated Annealing** algorithm provided the most stable configuration with the lowest competition index.
* **Species Distribution:** The model successfully adhered to the constraints of fixed specimen counts (e.g., 196 *Agave salmiana*, 86 *Prosopis laevigata*) while ensuring spatial diversity.

The final output is a coordinate map that forestry engineers can use to plant specimens in a way that mathematically guarantees better resource usage and long-term ecosystem stability.

### 📚 Technologies Used

* **Python:** Main simulation language.
* **NumPy:** For matrix manipulations and grid operations.
* **Matplotlib:** For visualizing the planting distribution maps.
