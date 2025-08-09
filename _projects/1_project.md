---
layout: page
title: Connect 4
description: A 2-player alignment game in Java
img: /assets/img/games/connect4.png  # Optional: placeholder or later screenshot
importance: 1
category: games
related_publications: false
---

> **Personal Project**  
> A 2-player Connect 4 game using 2D arrays in Java. The game simulates a grid-based playfield and checks for **horizontal**, **vertical**, or **diagonal alignments of length four** to declare a winner. A tie is declared when the board fills up without any winning alignment.

This project deepened my understanding of:
- Array-based data representation
- Input handling with `Scanner`
- Game loop mechanics and board visualization
- Edge case handling for full columns and ties

### 💻 Gameplay Overview

Players alternate turns, choosing a column to drop their token:
- Player 1 is `'O'`
- Player 2 is `'X'`
- The board updates automatically and checks for a winner

---

### 🔗 GitHub Repository

[View Full Code on GitHub]((https://github.com/pinakirm/Connect-Four)

---

### 🔍 Code Snippet

```java
public char checkAlignment(int row, int column) {
    for (int i = 0; i <= 2; i++) {
        for (int j = 0; j <= 3; j++) {
            if (board[i][j] != empty &&
                board[i][j] == board[i+1][j+1] &&
                board[i+1][j+1] == board[i+2][j+2] &&
                board[i+2][j+2] == board[i+3][j+3]) {
                return board[i][j];
            }
        }
    }
    // [similar checks for other directions...]
    return empty;
}
