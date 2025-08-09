---
layout: page
title: "Project: Predicting Mitochondrial Genetic Disorders"
description: "Tackling extreme class imbalance with robust resampling and carefully tuned ML models—while avoiding data leakage."
category: ml
importance: 3
---

## Overview

This project builds supervised learning models to **predict mitochondrial genetic disorders** from a Kaggle dataset. The work emphasizes **rigorous evaluation under class imbalance**, **leakage-safe pipelines**, and a **comparative study** of modern resampling strategies (SMOTE, Tomek Links, etc.) paired with models like **SVM, Random Forest, Gradient Boosted Trees,** and a **Feedforward Neural Network (FNN)**.

---

## Key Features

- **Literature-grounded setup**: Surveyed three papers to align preprocessing, targets, and metrics with state-of-the-art practice.
- **Imbalance handling**: Systematic comparison of **Random over/undersampling**, **Tomek Links**, and **SMOTE** variants.
- **Leakage prevention**: End-to-end **pipelines** with **stratified splits**, resampling **inside CV folds**, and **feature scaling fit only on training**.
- **Model zoo + tuning**: SVM, RF, GBT, and FNN with **grid/random search** (and early stopping where applicable).
- **Clear evaluation**: Stratified K-fold CV with **AUROC**, **AUPRC**, **F1**, **balanced accuracy**, and **calibration** checks.

---

## Dataset

- **Source**: Kaggle (mitochondrial genetic disorder dataset).
- **Task**: Multiclass / multilabel (depending on your setup) prediction of mitochondrial disorders.
- **Challenge**: **Severe class imbalance** and potential **feature/target leakage** if resampling or scaling happens before splits.

---

## Approach

1. **Problem Framing**
   - Defined targets per the dataset documentation and literature.
   - Established leakage-safe protocol: **split → fit scaler on train → resample train only → train → eval on untouched val/test**.

2. **Preprocessing**
   - Missing values: imputed within the **training fold** only.
   - Scaling: standardization / min–max as model-appropriate (e.g., SVM/FNN benefit).

3. **Imbalance Strategies**
   - **Oversampling**: Random Oversampling; **SMOTE** (and variants if applicable).
   - **Undersampling**: Random Undersampling.
   - **Hybrid**: **Tomek Links** (borderline clean-up) + SMOTE.
   - All resampling performed **inside each CV fold** to avoid leakage.

4. **Models & Tuning**
   - **SVM**: Linear/RBF kernels; tuned C, gamma.
   - **Random Forest**: n_estimators, max_depth, class_weight.
   - **Gradient Boosted Trees** (e.g., XGBoost/LightGBM/Sklearn GBDT): learning_rate, n_estimators, max_depth, subsample.
   - **FNN**: Depth/width, activation, dropout, optimizer, batch size, epochs with **early stopping** and validation splits.

5. **Evaluation Protocol**
   - **Stratified K-fold CV** (outer) for performance estimation.
   - Optional **inner CV** for hyperparameter search (nested CV).
   - Metrics: **AUROC**, **AUPRC** (key under imbalance), **F1**, **balanced accuracy**, per-class **recall/precision**, and **confusion matrices**.
   - Calibration: reliability curves / Brier score (optional).

---

## Results & Highlights

- **Imbalance Handling**: **SMOTE (+ Tomek Links)** generally improved **minority-class recall** and **AUPRC** without sacrificing too much precision.
- **Best Traditional Model**: (Fill in with your winner — e.g., **Gradient Boosted Trees with SMOTE** yielded the highest **AUPRC** and competitive **F1**.)
- **Neural Baseline**: FNN matched or surpassed tree methods when tuned and regularized, especially with robust early stopping and class-balanced loss.
- **Leakage Controls Matter**: Running resampling outside CV inflated scores; placing it **inside folds** produced **more realistic** performance.

> Replace this bullet with your concrete numbers if you’d like (e.g., “Best AUPRC = 0.61 (GBT+SMOTE), Macro-F1 = 0.54, Minority-class Recall = 0.68”).

---

## Reproducibility

- **Environment**: Python (scikit-learn, imbalanced-learn, numpy, pandas; for FNN, PyTorch or Keras/TensorFlow).
- **Determinism**: Fixed `random_state` seeds; logged versions.
- **Pipelines**: `sklearn.pipeline.Pipeline` / `imblearn.pipeline.Pipeline` to ensure **train-fold-only** fitting.

## PDF
[Final Report PDF Link](https://drive.google.com/file/d/11QFVQNtvrztNUheN-J5GAso6vRMAKr8j/view?usp=sharing)

### Sample Commands

```bash
# Train + evaluate with stratified K-fold CV
python train.py \
  --model gbt \
  --cv 5 \
  --resampling smote_tomek \
  --scaler standard \
  --metrics auroc auprc f1 balacc \
  --seed 42

# Hyperparameter search (example)
python tune.py \
  --model svm \
  --search random \
  --n_iter 50 \
  --cv 5 \
  --resampling smote \
  --seed 42
