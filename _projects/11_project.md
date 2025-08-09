---
layout: page
title: "Project: Critical Factors Determining Movie Success"
description: "An OLS Regression analysis to identify and quantify the key factors influencing movie box office performance."
category: ml
importance: 3
---

## Overview

This project applies **Ordinary Least Squares (OLS) Regression** to predict movie view counts using a dataset of 232 films. By combining **data preprocessing**, **statistical transformations**, and **diagnostic testing**, the study identifies significant predictors of movie success and develops a parsimonious regression model.

---

## Key Features

- **Applied OLS Regression** on a curated dataset from UCI Machine Learning Repository.
- Incorporated **Box-Cox transformation** and **Stepwise Regression** for model refinement.
- Conducted comprehensive **diagnostic tests** for normality, constant variance, multicollinearity, and outlier detection.
- Compared multiple models using **ANOVA** and **Adjusted R-squared** to select the most efficient predictor set.

---

## Approach

1. **Data Preparation**  
   - Selected relevant variables: `Views`, `Likes`, `Dislikes`, `Comments`, `Budget`, `Screens`, `Sequels`, and `Aggregate Followers`.
   - Removed incomplete rows (NA entries) to ensure model reliability.
   - Chose **Views** as the primary response variable.

2. **Model Building**  
   - Fit initial OLS regression models to capture relationships.
   - Applied **Box-Cox transformation** to address non-normality in residuals.
   - Used **Stepwise Regression** for feature selection and model simplification.

3. **Model Diagnostics**
   - **Shapiro-Wilk Test**: Checked residual normality.
   - **Brown-Forsythe Test**: Verified homoscedasticity.
   - **Variance Inflation Factor (VIF)**: Assessed multicollinearity.
   - **Cook’s Distance**: Identified influential outliers.

4. **Model Comparison**
   - Performed **ANOVA tests** to evaluate model improvements.
   - Selected the final model based on **Adjusted R-squared** and predictor significance.

---

## Results & Evaluation

- **Significant predictors** of movie views included audience engagement metrics (likes, dislikes, comments) and distribution factors (screens, budget).
- The **Box-Cox transformation** improved residual normality and reduced model bias.
- Stepwise Regression removed redundant variables, enhancing model interpretability.
- The final model balanced **predictive accuracy** with **simplicity**, achieving a higher adjusted R-squared than the baseline.

---

## Interesting Discoveries

- Movies with larger distribution (more screens) and strong social media presence (high aggregate followers) consistently achieved higher views.
- Sequels tended to outperform standalone films when controlling for other variables.
- Budget had a positive effect, but with diminishing returns beyond a certain threshold.

---

## Report
[Full Report (PDF)](https://docs.google.com/document/d/1_kKrx92Xw5iN_20H9PXs__xOrjk0im4iLV2AvHLyGlA/edit?usp=sharing)

## Sample Commands / Snippets

```r
# Box–Cox (lambda via MLE)
library(MASS)
bc <- boxcox(lm(Views ~ Likes + Dislikes + Budget + Screens, data=movies), lambda=seq(-2,2,0.1))

# Stepwise selection (both directions)
library(MASS)
final <- stepAIC(lm(Views ~ Likes + Dislikes + Comments + Budget + Screens, data=movies), direction="both")

# Diagnostics
shapiro.test(residuals(final))
library(car)
vif(final)

# Influence
plot(cooks.distance(final), type="h")
