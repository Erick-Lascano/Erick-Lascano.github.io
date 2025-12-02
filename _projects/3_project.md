---
layout: page
title: Stochastic Optimization for Reforestation
description: Metaheuristic allocation of plant species to minimize ecosystem competition.
img: assets/img/reforest_cover.jpg
importance: 3
category: Applied Mathematics
related_publications: false
---

This research project addresses the critical challenge of **Reforestation Optimization** in Mexico. Using **Stochastic Optimization** and **Metaheuristic Algorithms**, we designed a mathematical model to distribute 10 different plant species across a 1-hectare grid ($14 \times 47$ layout), maximizing survival rates by minimizing inter-species competition.

### 🎯 Mathematical Formulation

The problem was modeled as a **Combinatorial Optimization Problem** on a grid $G = \{(i, j) | 1 \le i \le 14, 1 \le j \le 47\}$. The goal is to assign a species $k$ to each cell to minimize the global competition index $Z$, subject to nutrient availability and adjacency constraints (modeled using the "Tres Bolillo" planting system).

The objective function is defined as:

$$\min Z = \sum_{(i,j) \in G} \sum_{(u,v) \in N(i,j)} C(s_{i,j}, s_{u,v})$$

#### Competition Matrix Calculation
The core of the model is the **Competition Coefficient** ($C_{s_i s_j}$) between two species $s_i$ and $s_j$. This was calculated using a weighted dominance factor to penalize monocultures and favor biodiversity:

$$C_{s_i s_j} = \text{Base} + \text{Dominance Factor}$$

Where:
* **Base Competence:**
    * $$5$$ if $s_i$ and $s_j$ belong to the **same genus** (high competition).
    * $$2$$ if $s_i$ and $s_j$ belong to **different genera** (low competition).
* **Dominance Factor:** A penalty proportional to the abundance of the species to prevent overcrowding.
    $$\text{Dominance Factor} = \frac{\text{Total Count of Species } i}{50}$$

<div class="row justify-content-sm-center">
    <div class="col-sm-8">
        <div class="table-responsive">
            <table class="table table-sm table-hover border-bottom">
                <thead>
                    <tr>
                        <th scope="col">ID</th>
                        <th scope="col">Specie Name</th>
                        <th scope="col" class="text-right">Quantity</th>
                    </tr>
                </thead>
                <tbody>
                    <tr><th scope="row">1</th><td>Agave lechuguilla</td><td class="text-right">42</td></tr>
                    <tr><th scope="row">2</th><td>Agave salmiana</td><td class="text-right">196</td></tr>
                    <tr><th scope="row">3</th><td>Agave scabra</td><td class="text-right">42</td></tr>
                    <tr><th scope="row">4</th><td>Agave striata</td><td class="text-right">42</td></tr>
                    <tr><th scope="row">5</th><td>Opuntia cantabrigiensis</td><td class="text-right">49</td></tr>
                    <tr><th scope="row">6</th><td>Opuntia engelmannii</td><td class="text-right">38</td></tr>
                    <tr><th scope="row">7</th><td>Opuntia robusta</td><td class="text-right">73</td></tr>
                    <tr><th scope="row">8</th><td>Opuntia streptacantha</td><td class="text-right">64</td></tr>
                    <tr><th scope="row">9</th><td>Prosopis laevigata</td><td class="text-right">86</td></tr>
                    <tr><th scope="row">10</th><td>Yucca filifera</td><td class="text-right">26</td></tr>
                    <tr class="table-active">
                        <th scope="row">Total</th>
                        <td><strong>Specimens per Hectare</strong></td>
                        <td class="text-right"><strong>658</strong></td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="caption">
            Table 1: Distribution of the 10 plant species allocated in the 1-hectare grid simulation.
        </div>
    </div>
</div>

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

We evaluated the performance of each algorithm based on the final **Competition Score** ($Z$) and convergence stability. Lower scores indicate better ecological distribution.

| Metric | **Simulated Annealing (SA)** | **Sine Cosine (SCA)** | **PSO** |
| :--- | :---: | :---: | :---: |
| **Stability** | ⭐⭐⭐ (High) | ⭐ (Low) | ⭐⭐ (Medium) |
| **Min. Competition** | **Lowest (Best)** | High | Medium |
| **Convergence** | Slow but Steady | Fast but Unstable | Local Minima Prone |

* **Optimal Solution:** The **Simulated Annealing** algorithm consistently outperformed PSO and SCA, finding configurations with significantly lower competition indices (e.g., scores of ~40 vs ~76 in comparative runs).
* **Impact:** The model successfully adhered to the constraints of fixed specimen counts while ensuring spatial diversity, providing a coordinate map that forestry engineers can use to maximize long-term ecosystem stability.

### 📚 Technologies Used

* **Python:** Main simulation language.
* **NumPy:** For matrix manipulations and grid operations.
* **Matplotlib:** For visualizing the planting distribution maps.
