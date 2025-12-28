# Eigen-Applications: Web Navigation & Image Compression

## Introduction

This project explores the practical application of Linear Algebra in two real-world scenarios: modeling web navigation (the foundation of the PageRank algorithm) and performing dimensionality reduction on image data using Principal Component Analysis (PCA). By leveraging eigenvalues and eigenvectors, we can simplify complex dynamical systems and compress high-dimensional data without losing significant information.

## Key Objectives

* Implement Discrete Dynamical Systems to model webpage transitions.

* Calculate Steady-State Probabilities using the eigenvectors of Markov Matrices.

* Perform Image Compression by reducing 4096-pixel dimensions into a fraction of the space.

* Analyze the Explained Variance to determine optimal data reconstruction thresholds.

## 1. Webpage Navigation (The PageRank Model)

The first part of the project models a user browsing a set of 5 webpages. The system is represented as a Markov Matrix where each column sums to 1, representing probability distributions.

**Core Methodology**
* Transition Matrix ($P$): Represents the probability of moving from page $j$ to page $i$.
* State Vector ($X_t$): The probability distribution of the user's location at time $t$.
* Dynamics: The system evolves via $X_t = P X_{t-1}$.
* Stationary Distribution: Instead of iterating $P$ many times ($P^m$), we solve for the eigenvector associated with the eigenvalue $\lambda = 1$ to find the long-run probabilities.

**Key Result:** In our 5-page model, Page 1 was identified as the most likely to be visited (39.4% probability), while Page 4 was the least likely (8.5%).

## 2. Image Compression via PCA

The second part of the project applies PCA to a dataset of cat images ($64 \times 64$ pixels) to demonstrate dimensionality reduction.

**The PCA Pipeline**

* **Data Flattening:** Converting $64 \times 64$ matrices into row vectors of size 4096.
  
* **Mean Centering:** Shifting the data so the mean of each pixel variable is zero.
  
* **Covariance Matrix:** Computing $\Sigma = \frac{1}{n-1} X^T X$ to understand how pixels vary together.
  
* **Eigen-Decomposition:** Finding the principal components (eigenvectors) that capture the most variance.
  
* **Projection:** Transforming the original 4096 variables into $k$ principal components.

**Reconstruction & Variance Analysis**

We analyzed how many components are required to "reconstruct" a recognizable cat image:

* **1 Component:** Captures basic silhouettes and lighting.

* **20 Components:** Significant features (eyes, nose, ears) become clear.

* **35 Components:** Explains 95% of the total variance, providing a high-fidelity reconstruction while reducing data size by over 99%.
