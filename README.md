# Advanced Clustering Segmentation Analysis

## Project Overview
This project implements and evaluates multiple **unsupervised clustering algorithms** to discover hidden patterns and segment data into meaningful groups. The workflow follows a production-oriented data science pipeline, combining **feature scaling**, **model selection heuristics**, **quantitative evaluation**, and **visual validation**.

The goal is to compare clustering approaches and identify the most interpretable and stable segmentation strategy.

---

## Problem Statement
Given a multivariate dataset with no ground-truth labels, the objective is to:
- Identify natural groupings within the data
- Determine the optimal number of clusters
- Compare clustering techniques on structure, compactness, and separation
- Produce interpretable cluster assignments for downstream analysis

---

## Dataset Description
- Numerical, multi-feature dataset
- No missing values after preprocessing
- Features standardized to ensure distance-based algorithms perform correctly
- Dataset size: ~4,000+ observations (approx.)

> Feature scaling is mandatory due to the reliance on Euclidean distance across all clustering methods.

---

## Methodology & Pipeline

### 1. Data Preprocessing
- Standardization using `StandardScaler`
- Removal of scale bias across features
- Prepared data matrix for distance-based clustering

### 2. Exploratory Cluster Analysis
To estimate the optimal number of clusters:

**Elbow Method (WCSS)**
- Computes Within-Cluster Sum of Squares for k = 1 → 11
- Identifies diminishing returns in variance reduction

**Silhouette Score**
- Measures cohesion vs separation
- Used to validate cluster quality beyond visual heuristics

---

## Clustering Models Implemented

### K-Means Clustering
- Optimal clusters selected: **k = 5**
- Determined using Elbow Curve + Silhouette validation
- Cluster distribution shows both dominant and niche segments

**Key Characteristics**
- Fast and scalable
- Sensitive to initialization and scaling
- Assumes spherical cluster geometry

---

### Hierarchical Clustering (Agglomerative)
- Linkage: **Ward**
- Distance metric: **Euclidean**
- Cluster count aligned with K-Means (k = 5)

**Dendrogram Analysis**
- Used to visually confirm cluster separation
- Provides interpretability into merge hierarchy

---

### DBSCAN (Exploratory)
- Evaluated for density-based structure
- k-distance plot used to estimate epsilon
- Demonstrates limitations in high-dimensional standardized data

---

## Evaluation Metrics

| Metric | Purpose |
|------|--------|
| Silhouette Score | Measures inter-cluster separation |
| Davies–Bouldin Index | Penalizes overlapping clusters |
| WCSS | Measures cluster compactness |

> Metrics were used comparatively, not in isolation, to avoid misleading conclusions.

---

## Visualization Techniques
- PCA (2D) projection for cluster visualization
- Elbow & Silhouette plots
- Dendrogram for hierarchical interpretation

---

## Key Results & Insights
- **K-Means (k=5)** provided the most stable and interpretable segmentation
- Hierarchical clustering confirmed similar structure
- One small cluster suggests presence of niche or anomalous behavior
- DBSCAN was less effective due to uniform density assumptions breaking down

---

## Tech Stack
- Python
- NumPy, Pandas
- Scikit-learn
- Matplotlib, Seaborn
- SciPy

---

## Reproducibility
```bash
pip install numpy pandas scikit-learn matplotlib seaborn scipy

