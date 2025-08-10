---
layout: page
title: "Project: Patient-Friendly Clinical Text Summarization"
description: "Exploring transformer-based summarization models to improve patient comprehension of complex clinical notes."
category: nlp
importance: 3
---

## Overview

This project investigates **transformer-based summarization** approaches—specifically **T5**, **BART**, and **PEGASUS**—to generate **patient-friendly clinical text** from complex medical notes. The focus is on serving **low-health-literacy populations**, ensuring that summaries retain both informativeness and readability.

---

## Key Features

- Evaluation of **state-of-the-art transformer summarization models** in the clinical domain.
- **Dual evaluation objective**:
  - **Automatic metrics**: ROUGE, BLEU.
  - **Readability metrics**: Flesch-Kincaid Grade Level, SMOG Index.
- Experiments conducted on **real-world** and **semi-synthetic clinical datasets**.
- Special emphasis on balancing **semantic fidelity** with **patient comprehension**.

---

## Approach

1. **Model Selection**
   - Fine-tuned **T5**, **BART**, and **PEGASUS** for abstractive summarization.
   - Leveraged domain-specific preprocessing to handle medical terminology.

2. **Dual Evaluation Objective**
   - Informativeness assessed using **ROUGE** and **BLEU** scores.
   - Readability assessed using **Flesch-Kincaid** and **SMOG** indexes.

3. **Datasets**
   - Real-world clinical notes.
   - Semi-synthetic patient education datasets.

4. **Analysis**
   - Compared readability and informativeness across models.
   - Identified trade-offs between lexical simplification and information preservation.

---

## Results & Evaluation

- **BART** achieved the best balance between informativeness and readability.
- **PEGASUS** produced highly faithful summaries but often retained technical jargon.
- **T5** excelled at simplifying text but occasionally omitted key clinical details.

| Model    | ROUGE-L | BLEU | Flesch-Kincaid ↓ | SMOG ↓ |
|----------|---------|------|-----------------|--------|
| T5       | 0.xx    | 0.xx | x.xx             | x.xx   |
| BART     | 0.xx    | 0.xx | x.xx             | x.xx   |
| PEGASUS  | 0.xx    | 0.xx | x.xx             | x.xx   |

*(Lower readability scores = simpler, more patient-friendly text)*

---

## Key Insights

- Readability scores often inversely correlated with informativeness metrics.
- Controlled generation and **lexical simplification** techniques are promising next steps.
- Balancing **semantic fidelity** with **ease of understanding** remains the main challenge.

---
## Codebase

[Github Code](https://github.com/pinakirm/CS577-Project/tree/main)

---

## Conclusion

This work highlights the potential of **transformer-based summarization** in improving patient comprehension of complex clinical documents. Future work will focus on **controlled text generation**, **vocabulary simplification**, and integrating **domain adaptation** for specialized medical contexts.

---

## Report
[Full Project Report (PDF)](https://github.com/pinakirm/CS577-Project/blob/main/CS577_FinalProject.pdf)


