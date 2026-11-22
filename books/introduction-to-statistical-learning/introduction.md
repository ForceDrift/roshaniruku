---
layout: note
title: Introduction
date: 2025-02-09
author: Roshan Iruku
read_time: 12 min
permalink: /books/introduction-to-statistical-learning/introduction/
toc: true
math: true
---

Sample chapter notes for *An Introduction to Statistical Learning*.

## Mean squared error

For a fitted model $\hat{f}$, the expected test mean squared error decomposes into bias, variance, and irreducible error:

$$
\text{MSE}(x_0) = \operatorname{Var}(\hat{f}(x_0)) + \left[\operatorname{Bias}(\hat{f}(x_0))\right]^2 + \operatorname{Var}(\varepsilon)
$$

```python
import numpy as np

def mse(y_true, y_pred):
    y_true = np.asarray(y_true)
    y_pred = np.asarray(y_pred)
    return np.mean((y_true - y_pred) ** 2)

y = [3.0, 4.5, 2.1, 6.2]
y_hat = [2.8, 4.1, 2.6, 5.9]

print(mse(y, y_hat))
```

## Bias-variance tradeoff

A flexible model can fit the training data well while generalizing poorly. The goal is to find a model complex enough to capture the signal but simple enough to avoid fitting the noise.

## A quick example

Suppose we fit a polynomial regression curve. Increasing the degree lowers training error, but test error usually decreases and then increases.

### Where this shows up

This tradeoff appears in model selection, regularization, resampling, and almost every practical prediction problem.

[Back to chapter notes]({{ '/books/introduction-to-statistical-learning/' | relative_url }})
