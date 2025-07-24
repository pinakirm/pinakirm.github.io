---
layout: page
title: Length-Doubling Pseudorandom Generator from One-Way Permutation
description: Construction and empirical analysis of a cryptographic length-doubling PRG, built from a given OWP.
category: theory
importance: 3
---

## Overview

This project implements a length-doubling Pseudorandom Generator (PRG) based on a given One-Way Permutation (OWP).  
**Goal:** Given a 512-bit random seed, generate 1024 bits that are computationally indistinguishable from random, such that even a computationally unbounded adversary (without the seed or trapdoor) cannot feasibly guess any of the generated bits.

---

## Technical Details

- **Input:** 512-bit seed (64 bytes)  
- **Output:** 1024 bits (128 bytes)  
- **Primitive used:** A provided OWP function (from `64bytes` file)
- **PRG Construction:** Iterative use of the OWP, applying hardcore predicate techniques to expand the bit-length.  
- **Implementation:** Written in Python (`prog.py`).

### How It Works

1. **One-Way Permutation (OWP):**  
   A trapdoor function that is easy to compute but hard to invert. Provided as a black-box.

2. **PRG Construction:**  
   - Start from a 512-bit seed.
   - Repeatedly apply the OWP and extract "hardcore" bits at each step.
   - Concatenate the hardcore bits from all steps to produce a 1024-bit output.

3. **Security:**  
   - The security of the PRG is based on the assumed hardness of inverting the OWP.
   - No information about the output should be feasible to recover without the original seed.

---

## Files

- `prog.py` – Python implementation of the PRG.
- `64bytes` – Sample file of random 512 bits for input seed.
- `128bytes` – Example output file with 1024 pseudorandom bits produced by the PRG.

---

## Usage

1. Place `prog.py`, `64bytes`, and the OWP implementation in the same directory.
2. Run:
   ```bash
   python prog.py

---

## Code
[Link](https://github.com/pinakirm/Goldreich-Levine-Hardcore-Bit-Construction)
