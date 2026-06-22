# 🔬 Model Selection for Clustering of Colorectal Tissue Images

## Overview

This project investigates the effectiveness of different feature representations, dimensionality reduction techniques, and clustering algorithms for unsupervised classification of colorectal tissue images.

Using a dataset of 5,000 histopathology image patches across nine tissue categories, we evaluate how various combinations of feature extraction models, projection methods, and clustering algorithms affect clustering quality. Since this is an unsupervised learning task, ground-truth labels are used only for evaluation purposes and not during model training.

The study compares four deep learning feature representations (PathologyGAN, ResNet50, InceptionV3, and VGG16), two dimensionality reduction methods (PCA and UMAP), and three clustering algorithms (K-Means, Gaussian Mixture Model, and Agglomerative Clustering).

---

## Objectives

* Compare multiple feature representations for tissue image clustering.
* Evaluate the effectiveness of PCA and UMAP for dimensionality reduction.
* Assess clustering performance using K-Means, GMM, and Agglomerative Clustering.
* Identify the optimal clustering pipeline for colorectal tissue classification.
* Visualize cluster structures using 2D and 3D embeddings.

---

## Dataset

### Colorectal Tissue Image Dataset

The dataset contains:

* 5,000 histopathology image patches
* 9 tissue classes
* Pre-extracted feature representations

### Feature Representations

* PathologyGAN
* ResNet50
* InceptionV3
* VGG16

---

## Methodology

### 1. Exploratory Data Analysis

Feature spaces were visualized using:

* Principal Component Analysis (PCA)
* Uniform Manifold Approximation and Projection (UMAP)

These visualizations provided insights into tissue separability before clustering.

### 2. Dimensionality Reduction

#### PCA

* Linear dimensionality reduction
* Preserves global variance structure

#### UMAP

* Non-linear dimensionality reduction
* Preserves local neighborhood structure
* Better suited for complex image feature spaces

### 3. Clustering Algorithms

#### K-Means

* Centroid-based clustering
* Assumes spherical clusters

#### Gaussian Mixture Model (GMM)

* Probabilistic clustering
* Supports flexible cluster shapes

#### Agglomerative Clustering

* Hierarchical clustering approach
* Builds clusters through iterative merging

Number of clusters:

```python
n_clusters = 9
```

---

## Evaluation Metrics

### V-Measure

Measures agreement between predicted clusters and true tissue labels.

Higher values indicate:

* Better homogeneity
* Better completeness

### Silhouette Score

Measures cluster compactness and separation.

Higher values indicate:

* Better-defined clusters
* Greater separation between groups

---

## Results

### Best Overall Configurations

| Feature Representation | Projection | Clustering    | V-Measure | Silhouette |
| ---------------------- | ---------- | ------------- | --------- | ---------- |
| ResNet50               | UMAP       | K-Means       | 0.7248    | 0.5742     |
| VGG16                  | UMAP       | Agglomerative | 0.7261    | 0.5580     |
| PathologyGAN           | UMAP       | Agglomerative | 0.6186    | 0.5470     |
| InceptionV3            | PCA        | GMM           | 0.6080    | 0.1099     |

---

## Key Findings

### UMAP Outperforms PCA

Across all feature representations, UMAP consistently produced:

* Higher V-measure scores
* Higher silhouette scores
* Better cluster separability

### Classification Features Outperform Generative Features

Feature representations extracted from classification networks:

* ResNet50
* VGG16
* InceptionV3

performed better than PathologyGAN features.

### ResNet50 and VGG16 Achieve the Best Results

The strongest clustering performance was obtained using:

* ResNet50 + UMAP + K-Means
* VGG16 + UMAP + Agglomerative Clustering

These combinations achieved the highest cluster quality and separability.

### GMM and Agglomerative Clustering Show Advantages

Compared with K-Means:

* Better handling of non-spherical clusters
* Improved V-measure scores in many settings
* More flexibility for complex tissue distributions

---

## Visualizations

The project includes:

* 2D PCA projections
* 2D UMAP projections
* 3D UMAP visualizations
* Cluster assignment plots
* Cluster-label heatmaps

These visualizations help interpret clustering behaviour and tissue group separability.

---

## Technologies Used

* Python
* NumPy
* Pandas
* Scikit-Learn
* UMAP
* PCA
* Matplotlib
* Seaborn

### Machine Learning Models

* K-Means Clustering
* Gaussian Mixture Model (GMM)
* Agglomerative Clustering

### Feature Extractors

* ResNet50
* VGG16
* InceptionV3
* PathologyGAN

---

## Conclusion

This study demonstrates that the choice of feature representation and dimensionality reduction technique significantly impacts clustering performance in histopathology image analysis.

The results show that UMAP consistently outperforms PCA for tissue clustering, while features extracted from classification networks provide stronger discriminative power than those from generative models. Among all evaluated pipelines, combinations involving ResNet50 or VGG16 with UMAP achieved the most accurate and well-separated clusters.

These findings highlight the importance of selecting appropriate feature representations and clustering strategies when performing unsupervised medical image analysis.

---


**Case Study 2 – Model Selection for Clustering**

