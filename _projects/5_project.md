---
layout: page
title: Family Tree – Java
description: A program designed to answer genealogy queries using graph algorithms, including finding Least Common Ancestors and analyzing familial relationships.
category: theory
Github: [Link](https://github.com/pinakirm/Family-Tree)
importance: 3
---

## Overview

This Java project models a family tree as a graph (using adjacency lists), enabling advanced queries and relationship analysis between family members. It provides not just the basic genealogy structure, but also efficient algorithms to answer questions about ancestry and connections within the tree.

## Key Features

- **Graph-based Family Tree:**  
  The family tree is internally represented as a graph, enabling scalable and flexible relationship modeling.

- **Least Common Ancestor (LCA) Queries:**  
  Implements Dijkstra’s Algorithm to efficiently find the least common ancestor between any two family members—a crucial operation for analyzing family genealogy and resolving queries such as “Who is the closest shared ancestor of X and Y?”

- **Relationship Finder:**  
  Supports queries to determine the exact relationship between any two people in the family (e.g., parent, child, sibling, cousin).

- **Random Family & Name Generator:**  
  Includes utility classes to generate large, randomized family trees and names for comprehensive testing and experimentation.

- **Interactive Testing:**  
  The project comes with detailed test files and utilities for running and validating family relationship queries.

## Motivation

Modern genealogy often requires complex relationship queries (especially for large families or historical records). Representing a family tree as a graph allows leveraging powerful algorithms for fast, reliable answers—enabling researchers or hobbyists to analyze ancestry at scale.

## How It Works

1. **FamilyTree.java:**  
   - Builds the graph structure for the family tree.
   - Stores parent-child relationships using adjacency lists.
   - Provides methods for adding members, querying relationships, and finding ancestors.

2. **FamilyTreeTest.java:**  
   - Contains sample trees and automated tests.
   - Demonstrates querying for LCAs and relationship paths.

3. **RandomFamilyGenerator.java** & **RandomNameGenerator.java:**  
   - Generate random names and family structures for robust testing.

## Example Queries

- **Find Least Common Ancestor:**  
  > "Who is the nearest common ancestor of Alice and Bob?"

- **Relationship Path:**  
  > "What is the relationship between Mary and Tom?"

- **Tree Generation:**  
  > "Create a random family tree of 100 members for benchmarking."

## Sample Output
Nearest Common Ancestor of Alice and Bob: Grandparent
Relationship between Mary and Tom: Cousins


## Technologies Used

- **Java** (Core logic, algorithms)
- **Graph Theory** (Adjacency list, LCA, Dijkstra’s Algorithm)
- **Randomization** (For generating sample data)

## Getting Started

- Clone the repo and run `FamilyTreeTest.java` to see example queries and outputs.
- Use `RandomFamilyGenerator` to generate large trees for your own experiments.

## What I Learned

- How to model hierarchical relationships as graphs.
- Applying graph algorithms (Dijkstra) to real-world ancestry queries.
- Handling edge cases and complex queries in family relationships.

## Why This Project Matters

Analyzing family history and genealogy is both a common hobby and a crucial task for historians. By combining graph theory with genealogy, this project enables fast, scalable, and accurate analysis of complex family relationships.

---

_See source code for implementation details and testing._

