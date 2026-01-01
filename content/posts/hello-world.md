+++
title = 'Hello World'
date = 2026-01-01T23:39:20+09:00
draft = true
+++

## 1. Introduction
Here is a simple C++ code snippet for NPU context setup.

```cpp
#include <iostream>

template <typename T>
void run_kernel(T* data, int size) {
    // Zero-copy optimization loop
    for(int i=0; i<size; ++i) {
        data[i] = data[i] * 2; 
    }
}
```

## 2. Math Formula

Standard deviation formula using LaTeX:

$$ \sigma = \sqrt{\frac{1}{N} \sum_{i=1}^N (x_i - \mu)^2} $$

## 3. Architecture

Simple diagram test.

```mermaid
```