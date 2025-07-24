---
layout: page
title: "Project: Dish Recommendation System with Collaborative Filtering and Clustering"
description: "A machine learning project exploring two models—collaborative filtering and ingredient-based clustering—for restaurant dish recommendations."
importance: 2
category: ml
---

## Overview

This project implements two distinct models for dish recommendation using real-world user rating datasets:

- **Model 1**: Memory-based collaborative filtering (user-user)
- **Model 2**: Hard clustering of dishes (ingredient-based, K-medoids)

Both models were evaluated on their ability to predict user ratings and generate ranked recommendations, using real datasets of user–dish ratings and dish ingredient features.

---

## Features

- **Handles sparse and noisy real-world data**  
- **Compares collaborative and content-based approaches**  
- **Evaluation on multiple ranking metrics**  
- **Command-line interface for reproducible experiments**

---

## Running the Code

### Model 1 (Collaborative Filtering)
python3 MODELPART1.py dishes.csv user_ratings_train.json user_ratings_test.json

- `dishes.csv`: Contains dish metadata (dish IDs, ingredients)
- `user_ratings_train.json`: User–dish ratings for training
- `user_ratings_test.json`: User–dish ratings for testing

### Model 2 (K-Medoids Clustering)

python3 MODELPART2.py dishes.csv user_ratings_test.json 5



- The final number is the number of clusters (e.g., 5).

---

## Methodology

### Model 1: Collaborative Filtering

- **Supervised learning** using train/test split
- Computes per-user average ratings
- Predicts ratings for test users based on similar users’ history (cosine similarity on rating vectors)
- If no overlapping ratings, defaults to the user’s average rating from training data
- Clamps predicted ratings to the valid interval [1, 5]
- **Metrics computed**: MAE, Precision@n, Recall@n

#### Observations

- **Works well with dense data**; struggles with sparse user–item overlap.
- Average MAE ≈ 0.6 for typical datasets.
- Performance (especially recall) improves as training data grows.
- Limited by lack of shared history between users.

### Model 2: Ingredient-based Clustering

- **Content-based**: Dishes are clustered by ingredient similarity (binary vectors, custom similarity metric).
- Uses K-Medoids (robust to outliers, binary-friendly) with customizable number of clusters.
- Clusters are evaluated for tightness and separation (WC_SSE, BC_SSE).
- User’s test ratings are predicted as the mean rating within the assigned cluster.
- Recommendations made by selecting highest-rated clusters for each user.
- **Metrics computed**: MAE, Precision@n, Recall@n

#### Observations

- MAE values improve substantially as K increases (more clusters = finer grouping).
- Model outperforms a mode-rating baseline for all datasets.
- Recommendations are better aligned with actual user taste trends.
- The mean as a cluster label provides best results.

---

## Results Summary

| Metric     | Model 1 (500) | Model 1 (2000) | Model 2, K=50 (500) | Model 2, K=50 (2000) |
|------------|---------------|---------------|---------------------|----------------------|
| MAE        | 0.63          | 0.58          | 0.34                | 0.34                 |
| Prec@10    | 0.89          | 0.91          | 0.95                | 0.95                 |
| Recall@10  | 0.43          | 0.44          | 0.46                | 0.46                 |

- **Model 2** consistently outperforms Model 1 on all metrics, especially with more clusters and data.

---

## Insights

- Collaborative filtering struggles with sparse user–dish overlap, especially in cold-start scenarios.
- Clustering by dish ingredients (content-based) captures meaningful food similarities, producing better predictions and recommendations.
- Higher cluster counts (K) generally improve model performance by capturing finer-grained food preferences.

---

## How to Use

- Plug in your own CSV/JSON files with dish and user-rating data.
- Choose the model appropriate for your data density (collaborative vs. content-based).
- Tune the number of clusters (`K`) for best results in Model 2.

---
## Code
[Link](https://github.com/pinakirm/W2E)
