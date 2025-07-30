# MSCS 634 - Lab 5: Clustering Techniques Using DBSCAN and Hierarchical Clustering


Banoj Kumar Jena

## Course
MSCS 634 – Big Data Analytics

## Lab Title
Lab 5: Clustering Techniques Using DBSCAN and Hierarchical Clustering

---

## Objective
The purpose of this lab is to gain practical experience with two widely used clustering algorithms in unsupervised machine learning: **Hierarchical Clustering** and **Density-Based Spatial Clustering of Applications with Noise (DBSCAN)**. By applying both techniques to the Wine dataset, this lab aims to:
- Understand how clustering works without class labels.
- Explore differences in clustering behavior, performance, and visual interpretation.
- Develop skills in data preprocessing, parameter tuning, and evaluation using standard clustering metrics.

---

## Dataset Description

- **Source**: `sklearn.datasets.load_wine()`
- **Records**: 178 samples
- **Features**: 13 numerical attributes representing chemical properties of wine.
- **Target**: Wine cultivar (used for evaluation, not during clustering)

Features include:
- Alcohol
- Malic acid
- Ash
- Alcalinity of ash
- Magnesium
- Total phenols
- Flavanoids
- Nonflavanoid phenols
- Proanthocyanins
- Color intensity
- Hue
- OD280/OD315 of diluted wines
- Proline

---

## Lab Steps and Methodology

### 1. Data Preparation and Exploration
- Loaded the Wine dataset into a Pandas DataFrame.
- Explored data using `.head()`, `.info()`, `.describe()` to understand structure and distribution.
- Standardized features using `StandardScaler` to ensure uniform scale across all attributes.

### 2. Hierarchical Clustering
- Used `AgglomerativeClustering` with Euclidean distance and Ward linkage.
- Experimented with multiple values of `n_clusters` to assess impact on cluster formation.
- Visualized clusters using scatter plots (2D projections).
- Generated and interpreted a dendrogram using `scipy.cluster.hierarchy.dendrogram` to visualize how clusters merge.
- Key observation: Optimal number of clusters appeared to be 3, aligning loosely with the dataset’s actual class labels.

### 3. DBSCAN Clustering
- Applied the DBSCAN algorithm using `sklearn.cluster.DBSCAN`.
- Tested various combinations of `eps` (neighborhood size) and `min_samples` (minimum points to form a dense region).
- Identified optimal parameters: `eps = 2.4`, `min_samples = 3`
- Plotted resulting clusters and highlighted noise points (labeled as -1).
- Evaluated clustering using:
  - Silhouette Score
  - Homogeneity Score
  - Completeness Score

---

## DBSCAN Evaluation Metrics (Best Parameters)

| Metric              | Value     |
|---------------------|-----------|
| Silhouette Score    | 0.2144    |
| Homogeneity Score   | 0.4871    |
| Completeness Score  | 0.5491    |

---

## Comparative Analysis: DBSCAN vs Hierarchical Clustering

| Feature                      | DBSCAN                              | Hierarchical Clustering               |
|-----------------------------|--------------------------------------|----------------------------------------|
| Input Requirements           | No need to specify number of clusters | Must specify `n_clusters`              |
| Handles Noise/Outliers       | Yes                                 | No                                     |
| Cluster Shape                | Arbitrary shapes                     | Generally spherical/elliptical         |
| Interpretability             | Moderate (depends on parameters)     | High (dendrogram visual aid)           |
| Parameter Sensitivity        | High (especially `eps`)              | Moderate (linkage method, n_clusters)  |
| Best Use Case                | Complex, non-linear data             | When hierarchy or distance-based clustering is intuitive |

---

## Key Insights
- **Hierarchical Clustering** is easier to interpret and useful for understanding data structure, especially with dendrograms.
- **DBSCAN** is more flexible, automatically discovers the number of clusters, and handles noise effectively.
- For this dataset, DBSCAN slightly outperformed hierarchical clustering in terms of evaluation metrics but required fine-tuning of parameters.

---

## Challenges Faced
- Selecting optimal DBSCAN parameters (`eps` and `min_samples`) required trial and error.
- Silhouette Score was difficult to optimize due to overlapping class boundaries and moderate cluster separation.
- Visualizing high-dimensional data in 2D for analysis was challenging without applying PCA (considered for future work).

---

## Files Included

| File                     | Description                                              |
|--------------------------|----------------------------------------------------------|
| `Lab5_Clustering.ipynb`  | Main notebook with all code, outputs, and visualizations |
| `README.md`              | Overview of lab, findings, challenges, and insights      |

---

## How to Run

1. Clone this repository:
   ```bash
   git clone https://github.com/your-username/MSCS_634_Lab_5.git
