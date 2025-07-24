---
layout: page
title: Sequence Alignment of DNA Proteins with BLOSUM62
description: Python program for global and local sequence alignment between DNA and protein using BLOSUM62 and gap penalties.
importance: 2
category: science
---

## Overview

This project implements sequence alignment between a DNA sequence (translated into protein) and a protein sequence, using both global and local alignment. The tool is flexible for both types of queries, and is controlled via command line arguments.

The algorithm leverages:
- **Needleman-Wunsch/Smith-Waterman** dynamic programming for alignment.
- Translation of DNA to protein using BioPython.
- Flexible use of the **BLOSUM62** substitution matrix for scoring.
- A user-specified, length-independent gap penalty.

## Features

- **Global and Local Alignment**  
  Easily switch between global and local (Smith-Waterman) alignment with a command-line flag.
- **Translation of DNA**  
  The DNA sequence is translated (forward frames) before alignment to allow meaningful comparison with the protein sequence.
- **Customizable Gap Penalty**  
  The user sets the gap penalty (can be negative, e.g. `-5`).
- **Flexible Scoring**  
  Accepts any substitution matrix in standard format (default: BLOSUM62).
- **Comprehensive Output**  
  Reports:
  - Length of translated DNA and given protein.
  - The full DP (dynamic programming) table (optional, for debugging/analysis).
  - The optimal alignment score.
  - The final aligned sequences (in standard block format).
    
## Motivation

Sequence alignment is a core tool in bioinformatics, enabling comparison of genetic/protein sequences, annotation, and evolutionary studies. This project supports direct DNA-to-protein comparisons with custom scoring and is adaptable for many use-cases.

## GitHub Repo

[Link](https://github.com/pinakirm/Sequence_Alignment)

## How To Run

```bash
python3 sequencealignment.py filed.fasta filep.fasta 1 -5 blosum62.txt

