---
layout: page
title: "Project: Document Ranking using TF-IDF and Okapi BM25"
description: "A comparative analysis of TF-IDF and Okapi BM25 on real-world information retrieval tasks."
category: ml
importance: 3
---

## Overview

This project implements and analyzes two popular document ranking algorithms in Information Retrieval: **TF-IDF** and **Okapi BM25 (Galago)**. The main goal is to understand their differences in ranking, precision, recall, scalability, and performance on real datasets.

---

## Key Features

- **Custom Python implementation** of TF-IDF with stopword removal, stemming, and cosine similarity.
- Integration of **Galago’s Okapi BM25** model for large-scale probabilistic ranking.
- Comprehensive evaluation on both **small and full text corpora**.
- Automatic generation of retrieval outputs and formal evaluation with standard IR metrics (Precision, Recall, F1).

---

## Approach

1. **TF-IDF Implementation**  
   - Performs keyword matching using cosine similarity.
   - Applies stopword removal, stemming (Krovetz), and ignores punctuation.
   - Treats queries and documents alike in vector space.

2. **Okapi BM25 (Galago)**
   - Probabilistic ranking; considers term frequencies and document length.
   - Ranks documents based on the probability of term occurrence in relevant vs. non-relevant documents.
   - More efficient for large data due to multi-threading and top-k retrieval.

---

## Results & Evaluation

### Precision, Recall, and F1-score Comparison

- On a full corpus with all queries:
    - **TF-IDF:**  
      Precision = 0.010, Recall = 0.926, F1 = 0.019
    - **Okapi BM25:**  
      Precision = 0.013, Recall = 0.879, F1 = 0.025

- For a single random query (q1: _“what articles exist which deal with tss time sharing system an operating system for ibm computers”_):

    | Metric           | TF-IDF     | Okapi BM25 |
    |------------------|------------|------------|
    | Precision        | 0.003      | 0.005      |
    | Recall           | 1.0        | 1.0        |
    | F1-score         | 0.005      | 0.009      |

    Both models retrieved all relevant documents, but Okapi BM25 showed higher precision and F1-score.

### Ranking Analysis

- Okapi BM25 consistently ranks relevant documents higher than TF-IDF in almost every case.
- Example: Document 1410 ranked 4th in Okapi but 40th in TF-IDF.

### Scalability and Usability

- Okapi BM25 is notably **faster** and better suited for large corpora.
- TF-IDF can become **computationally expensive** as vocabulary or document count increases.
- BM25 accommodates larger vocabulary, handles document length, and does not penalize queries with more terms.

---

## Interesting Discoveries

- **Krovetz Stemmer** (dictionary-based) helps reduce vocabulary and improve matches.
- Stopword removal and stemming can dramatically cut computation time.
- Practical note: Galago BM25 model returns results much faster and is robust to the addition of new query terms.

---

## Sample Commands Used

- TF-IDF output evaluation:
    ```
    galago eval --judgments=... --baseline=tfidfoutput.txt
    ```
- Okapi BM25 output evaluation:
    ```
    galago batch-search --scorer=bm25 > outputokapi.txt
    galago eval --judgments=... --baseline=outputokapi.txt
    ```

---

## Conclusion

- **Okapi BM25 outperforms TF-IDF** for both ranking and efficiency on large corpora.
- TF-IDF still offers strong recall and can be effective for smaller or well-defined datasets.
- This analysis provides practical insights for choosing the right document ranking approach in real-world search engines.

---

## Code
[Link](https://github.com/pinakirm/TFIDF-Search_Engine/tree/main)
