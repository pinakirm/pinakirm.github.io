---
layout: page
title: Quicksort Analyzer
description: Java implementation to analyze the effect of pivot choice in Quicksort
importance: 3
category: theory
---

## Overview

This project implements the Quicksort algorithm in Java with **five different pivot selection strategies** and provides utilities to generate various input sequences for benchmarking. The goal is to compare how pivot choice and input order affect the number of comparisons and, ultimately, the runtime complexity.

## Features

- Five pivot selection methods:
  - Last element
  - First element
  - Middle element
  - Median of three (first, middle, last)
  - Median of five (10%, 30%, 50%, 70%, 90%)
- Custom input generators (sorted, reverse, patterned, random, etc.)
- Counts and prints number of comparisons for each run
- Easy to extend and experiment

[GitHub Repository](https://github.com/pinakirm/Quicksort-Analyzer)
