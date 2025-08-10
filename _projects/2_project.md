---
layout: page
title: RPN Expression Evaluator
description: A Java program to parse and evaluate infix expressions using stacks
importance: 1
category: theory
related_publications: false
---

> **Personal Project**  
> This Java program parses and evaluates **infix expressions** by internally converting them to **Reverse Polish Notation (RPN)** using custom-built **stack-based logic**. It handles a wide range of operators and parentheses — including `+`, `-`, `*`, `/`, `^`, `sin`, `cos`, `log`, and complex nested expressions.

---

### 💡 Features

- ✅ Custom **generic Stack<T>** implementation from scratch (no `java.util.Stack`)
- ✅ Expression validation with error handling for:
  - Unmatched parentheses
  - Consecutive operators
  - Empty expressions
  - Division by zero (handled with `NaN`, `Infinity`, `-Infinity`)
- ✅ Supports **unary operators** like `sin`, `cos`, `log`
- ✅ File-based batch evaluation via `input.txt`
- ✅ Throws clear, customized error messages for malformed inputs


---

### 🔗 GitHub Repository

[View Full Code on GitHub](https://github.com/pinakirm/RPN-Calculator/tree/master)

---

### 🔧 Code Snippet: Stack Implementation

```java
public class Stack<T> {
    private int top = -1;
    private int capacity;
    private ArrayList<T> arrayList = new ArrayList<>();

    public Stack(int capacity) {
        this.capacity = capacity;
    }

    public boolean push(T val) {
        top++;
        arrayList.add(top, val);
        return true;
    }

    public T pop() throws IndexOutOfBoundsException {
        if (top < 0) throw new IndexOutOfBoundsException("Empty Stack");
        return arrayList.remove(top--);
    }

    public T peek() {
        if (top < 0) throw new IndexOutOfBoundsException("Empty Stack");
        return arrayList.get(top);
    }

    public boolean isEmpty() {
        return top < 0;
    }

    public int size() {
        return arrayList.size();
    }
}
