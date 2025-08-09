---
layout: page
title: "Project: RePO and RePO+ Evaluation under Simulated Attacks"
description: "Reproducing and extending RePO and RePO+ evaluation in Mininet, introducing new metrics and performance analysis."
category: ml
importance: 3
---

## Overview

This project reproduces the results of **RePO** and **RePO+**—robust path selection algorithms—under simulated network attack scenarios using the **Mininet** environment. Beyond reproduction, it addresses model shortcomings by incorporating additional performance metrics and suggesting future improvements.

---

## Key Features

- **Reproduction of RePO and RePO+** experiments under controlled attack simulations.
- **Evaluation with extended metrics** like Channel State Information (CSI) and Matthews Correlation Coefficient (MCC) to gain deeper insights into model performance.
- Visual performance assessment through **scatterplots** and **ROC curves**.
- Formulation of potential future directions for enhanced robustness.

---

## Approach

1. **Experiment Setup**  
   - Implemented RePO and RePO+ in **Mininet** to simulate attack scenarios.
   - Controlled network topology to isolate the effect of attacks.

2. **Metric Extension**  
   - Added CSI and MCC to evaluate the classification and detection capabilities more comprehensively.
   - Compared results to original evaluation metrics.

3. **Visualization**  
   - Generated scatterplots for CSI and MCC distribution analysis.
   - Constructed ROC curves to visualize trade-offs between true and false positive rates.

---

## Results & Evaluation

- Successfully reproduced baseline results for RePO and RePO+.
- CSI and MCC revealed **performance nuances** missed by original metrics.
- ROC curves indicated **RePO+ consistently outperformed RePO** in most attack scenarios.
- Scatterplot patterns highlighted **areas of model instability** under high attack intensity.

---

## Future Directions

- Explore hybrid approaches combining **RePO+ with adaptive path re-selection** strategies.
- Investigate deep learning–based anomaly detection to complement path selection.
- Extend testing to **real-world network traces** for validation.

---

## Conclusion

- RePO+ offers measurable improvements over RePO in robustness against simulated attacks.
- Incorporating richer metrics like CSI and MCC allows for more **holistic evaluation**.
- Visual analysis tools enhance interpretability of network performance.

---

## Report

[Full Report PDF](https://drive.google.com/file/d/1B0ZJf7vaSkFs8A84vT6jMlaE7RuhS4GQ/view?usp=sharing)
