# Maritime Vessel Segmentation Using Unsupervised Machine Learning

## Overview

This project applies unsupervised machine learning to analyze operational patterns in a maritime shipping company. The main objective is to evaluate whether the company’s vessels can be divided into two clearly defined operational groups, as initially suggested by the technical team.

Several clustering algorithms are implemented and compared in order to identify natural structures within the fleet and support data-driven operational decision-making.

## Business Problem

A maritime shipping company wants to understand whether there are meaningful operational differences among its vessels. The technical team proposes that the fleet can be divided into two main groups.

This project evaluates that hypothesis using clustering techniques based on vessel characteristics, route information, engine type, maintenance status, operational cost, revenue, efficiency and other operational variables.

## Objective

The objective of this project is to determine whether the operational data supports the existence of two clearly defined vessel groups.

Specifically, the project aims to:

- Explore the structure and quality of the dataset.
- Prepare numerical and categorical variables for clustering.
- Apply multiple unsupervised learning algorithms.
- Compare clustering results using the silhouette score.
- Interpret the results from a business and operational perspective.
- Provide a recommendation for fleet segmentation.

## Dataset

The dataset contains operational information about vessels in a maritime shipping company.

The variables include:

- Ship type
- Route type
- Engine type
- Maintenance status
- Speed over ground
- Engine power
- Distance traveled
- Draft
- Weather condition
- Cargo weight
- Operational cost
- Revenue per voyage
- Turnaround time
- Energy efficiency
- Seasonal impact
- Weekly voyage count
- Average load percentage

The original dataset contains 2736 records and 18 variables. After removing rows with missing values, the working dataset contains 2127 records.

## Methodology

The project follows an analytical workflow inspired by ASUM-DM:

1. Business understanding
2. Analytical approach
3. Data requirements
4. Data collection
5. Data understanding
6. Data preparation
7. Modeling
8. Model evaluation
9. Business interpretation

Since the problem does not contain predefined labels, the analysis uses unsupervised learning techniques.

## Models Implemented

The following clustering models were evaluated:

| Model | Description |
|---|---|
| K-Means | Partitions observations into a predefined number of clusters based on distance to centroids. |
| Hierarchical Clustering | Builds clusters using a tree-based structure and distance linkage criteria. |
| DBSCAN | Identifies dense regions and separates noise observations. |
| Gaussian Mixture Model | Models the data as a mixture of probabilistic Gaussian components. |

## Results

| Model | Number of groups identified | Silhouette score | Interpretation |
|---|---:|---:|---|
| K-Means | 9 | 0.13 | Provides a manageable segmentation, but with weak cluster separation. |
| Hierarchical Clustering | 3 | 0.05 | Suggests broad groups, but with very low separation. |
| DBSCAN | 333 clusters + 242 noise observations | 0.19 | Highest silhouette score, but produces excessive fragmentation. |
| Gaussian Mixture Model | 34 | 0.11 | Captures a more complex structure, but may over-segment the fleet. |

## Key Findings

The results do not support the hypothesis that the fleet can be divided into only two clearly defined operational groups.

Although DBSCAN obtained the highest silhouette score, its output is not operationally practical because it produces hundreds of small clusters and many noise observations.

K-Means with 9 clusters offers the most practical alternative for business segmentation, since it provides a more manageable number of groups while still capturing operational heterogeneity.

## Business Recommendation

The company should reject the initial two-group segmentation hypothesis.

Instead, a more granular segmentation should be considered. From a practical business perspective, K-Means with 9 clusters is the most useful starting point because it allows the company to analyze different vessel profiles without creating an excessive number of operational categories.

Future work should focus on profiling each cluster to understand the operational characteristics that define each group.

## Limitations

- The silhouette scores are low across all models, indicating weak separation between clusters.
- Removing all rows with missing values reduced the dataset size by approximately 22.3%.
- DBSCAN produced many small clusters and noise observations, limiting interpretability.
- The current analysis evaluates cluster structure, but does not yet profile each cluster in detail.
- The business hypothesis of exactly two groups should be tested explicitly as a baseline.

## Future Improvements

Future versions of this project could include:

- Testing K-Means explicitly with k = 2 to directly evaluate the business hypothesis.
- Using imputation strategies instead of dropping missing values.
- Applying PCA or UMAP for dimensionality reduction and visualization.
- Profiling each cluster using descriptive statistics.
- Creating business labels for each segment, such as high-efficiency vessels, high-cost vessels or long-haul heavy cargo vessels.
- Evaluating cluster stability across different random seeds.
- Building a dashboard to explore vessel segments interactively.

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Unsupervised learning
- Clustering
- Jupyter Notebook
