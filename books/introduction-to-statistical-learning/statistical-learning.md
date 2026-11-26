---
layout: note
title: Statistical Learning
date: 2026-11-25
author: Roshan Iruku
read_time: 18 min
permalink: /books/introduction-to-statistical-learning/statistical-learning/
toc: true
math: true
---

## What is Statistical Learning

Statistical learning is more generally a case where we observe a response $Y$ to $p$ predictors given $\{X_1, X_2, X_3, \dots, X_p\}$. We assume there is a given relationship between our **response** and our **input variables**.

This can be expressed in the general form:

$$
Y = f(X) + \varepsilon
$$

$f$ is some function of a given input $\{X_1, X_2, X_3, \dots, X_p\}$, and $\varepsilon$ is a random error term which is independent of $X$ and has an average value of 0. Given a scatter plot of points between an independent variable and a dependent variable, one must estimate $f$.

## What exactly is $\varepsilon$

With prior knowledge from introductory statistics, one may assume that error terms and residuals are the same. **Error terms** and **residuals** are not the same.

Although both measure a difference from a reference value, **error terms** refer to the unobservable true population model, while **residuals** are the difference between the predicted values from a regression and the actual data points in the dataset.

Essentially, the error term is random, unmeasured real-world randomness or noise.

## Why do we estimate $f$

There are two main reasons.

**Prediction:** Suppose we are given $\{X_1, X_2, X_3, \dots, X_p\}$, characteristics about a patient's blood, and $Y$ is the patient's risk of reacting badly to a drug. Using $X$, we can predict $Y$.

We can make this prediction using:

$$
\hat{Y} = \hat{f}(X)
$$

Where $\hat{f}$ represents our estimate for $f$, because $f$ is a fixed but unknown function. In this case, $\hat{f}$ is a black box.

The accuracy of $\hat{Y}$ depends on two types of errors: **reducible** and **irreducible error**. Note that $\hat{f}$ is not a perfect estimate of $f$. This error is reducible because it is possible to improve the accuracy of $\hat{f}$.

However, as mentioned earlier, since $\varepsilon$ is also a component of $\hat{Y}$, we have **irreducible error**, where $\varepsilon$ is real-world noise we cannot reduce.

The book showcases how $\varepsilon$ is irreducible by taking the expected value of the squared difference between the actual and predicted value. The accuracy of $Y$'s upper bound is always provided by our irreducible error $\varepsilon$. **This bound is always unknown in practice**, because we do not have the all-defining equation for the universe, so we cannot model what is out of our reach.

**Inference**

In this situation, we want to estimate $f$, and our goal is to anticipate what would happen next. Now $\hat{f}$, our predicted function, is no longer a black box, as we need to find its form.

Questions to ask:

- What predictors are associated with the response?
- What is the relationship between each predictor and the response?
- Is the relationship between the predictor and the response linear?

**Big picture:** The difference is that inference draws conclusions from existing clues, and those clues can help us anticipate what would happen next.

## How Do We Estimate $f$

We will always assume that we have observed a set of $n$ different observations or data points. These observations are called **training data** because we can use this data to train our model on how to estimate $f$.

The goal is to apply statistical learning methods to the training data in order to estimate $f$. In other words, we want to find a predictive function $\hat{f}$ such that our true output $Y$ is approximate to our predicted function with our inputs as the function $\hat{f}(X)$.

Most statistical learning methods can be modelled using **parametric methods** or **non-parametric methods**.

First, we can make an assumption that the functional form of $f$ is linear, which can then be modelled as:

$$
f(X) = \beta_0X_0 + \beta_1X_1 + \beta_2X_2 + \dots + \beta_pX_p
$$

Estimating a $p$-dimensional function $f(X)$, here $\beta_i$ is the weight, contribution, or bias of each input $X_i$ to the function $f$.

The parameters here are the weights, slopes, and intercepts or bias. The model-based approach of parametric modelling reduces the problem of estimating $f$ down to just estimating a set of parameters. What that means is that to find $f$, we need to find the internal parameters $\{\beta_0X_0, \dots, \beta_pX_p\}$.

Assuming a parametric form for $f$ simplifies the problem of estimating $f$, because it is easier to find $\beta_0, \beta_1, \dots, \beta_p$ than to fit the entire function $f$.

The potential disadvantage of parametric modelling is that the model we choose will usually not match the true form of $f$. If the chosen model is too far off from $f$, then our estimate will be poor.

### Non-parametric methods

We do not make any initial assumptions about the functional form of $f$. Instead, we seek an estimate of $f$ that gets close to the data points without being too rough or wiggly, as the book likes to put it. By avoiding any initial assumptions, we can accurately fit a wider range of possible shapes for $f$.

The major **disadvantage** is that since non-parametric approaches do not reduce the problem of estimating $f$ to a small number of parameters, a very large number of observations are required to get an accurate estimation of $f$.

## Tradeoff between Prediction Accuracy and Interpretability

For instance, linear regression is an inflexible approach, as it can only generate linear functions such as lines or planes.

If we are mainly interested in inference, then restrictive models are more interpretable. For instance, we can easily see how the features $X_1, X_2, \dots, X_p$ affect $Y$.

The book then discusses other statistical methods to showcase the gradient of prediction accuracy versus interpretability.

## Supervised vs Unsupervised Learning

Statistical learning problems fall into either supervised learning or unsupervised learning problems.

*Supervised learning* means that for each observation of the predictor measurements $x_i$, there is an associated response measurement $y_i$. This means every input data point in your dataset is paired with a known correct answer or outcome.

**Unsupervised learning** describes the challenging situation where every observation gives us a vector of measurements $x_i$, but no associated response. For data where we do not have a response variable, we can use other methods such as clustering analysis.

## Assessing Model Accuracy

In order to evaluate the performance of a statistical learning method on a given dataset, we need to measure or quantify how well the predictions match the actual dataset. In linear regression, we can use:

$$
MSE = \frac{1}{n}\sum_{i=1}^{n}(y_i - \hat{f}(x_i))^2
$$

So what does this actually mean? We are taking the average of the sum of squared differences between the observed value and the predicted value.

The MSE computed using training data is called **training MSE**, but that method is irrelevant. We want to apply MSE to data that has been previously unseen by our model.

Mathematically speaking, we want to see if $\hat{f}(x_0) \approx y_0$ such that $(x_0, y_0)$ is an unseen data point.

We want to choose the method that gives us the lowest **test MSE**. How can we do this? If we have the test data, we can evaluate on the test observation and select the method where the MSE is the lowest.

However, if the test data is not readily available, we cannot just find the lowest training MSE, as there is no guarantee that the lowest training MSE will also have the lowest test MSE.

From later findings, the training MSE decreases monotonically as a function's flexibility increases. This means that as a function becomes more flexible, it fits the data much better.

If a model yields a low training MSE but a high test MSE, we are overfitting the model. This happens if a procedure or method is working too hard to find patterns in the training data, following random error rather than discovering the true properties of the unknown function $f$.

## Bias-Variance Tradeoff

What is bias and variance? Variance is how much $\hat{f}$ would change if we estimated it using a different set of training data. If a method has high variance, then changes in the training data can result in large changes in $\hat{f}$.

More flexible statistical methods have higher variance because changing the data points would change $\hat{f}$ considerably.

Bias refers to the error that is introduced by approximating a real-world problem.

General rule: as methods become more flexible, variance increases and bias decreases. The rate of change of these quantities determines whether MSE increases or decreases.

## Classification Setting

Many of the concepts previously mentioned, such as the bias-variance tradeoff, transfer well to classification problems too.

The difference is that in $\{(x_1,y_1), (x_2,y_2), \dots, (x_n,y_n)\}$, our $y_i$ is now **qualitative**.

To find the accuracy of our estimate $\hat{f}$, we can get the training error rate:

$$
\frac{1}{n}\sum_{i=1}^{n}I(y_i \neq \hat{y}_i)
$$

Here we check if our predicted value matches an observed value with an indicator variable such that if $y_i \neq \hat{y}_i$ (classified incorrectly), our indicator variable is 1, and if $y_i = \hat{y}_i$, it is 0 (classified correctly).

Using a Bayes classifier, it is possible to show that the test error rate is minimized.

## K-Nearest Neighbours

In theory, we want to predict qualitative responses using the Bayes classifier, but for real data, we do not know the conditional distribution, that is, how observations interact with each other conditionally, so we cannot compute the Bayes classifier. KNN can estimate the conditional distribution of $Y$ given $X$.

Given a positive integer $K$ and a test observation $x_0$, KNN identifies the $K$ points that are closest to $x_0$. It then estimates the conditional probability for class $j$ as the fraction of points in $\mathcal{N}_0$ whose response values are $j$. Then it assigns $x_0$ to the class with the largest probability:

$$
Pr(Y = j \mid X = x_0) = \frac{1}{K} \sum_{i \in \mathcal{N}_0} I(y_i = j)
$$

# Exercises

## Conceptual

a) The flexible method would perform better, as we can capture lots of data points without fitting noise. Flexible models reduce bias, achieving a closer approximation of the true function $f$.

b) Let us decipher: the number of predictors is $\{X_0, X_1, \dots, X_p\}$ such that $p \gg 30$, and the number of observations $\{(x_0,y_0), \dots, (x_n,y_n)\}$ is small. We should use an inflexible model because flexible models fit noise on smaller datasets with many predictors.

c) We should use a flexible model that fits curved, non-linear relationships without forcing a straight line in the data or a rigid function $f$.

d) If the variance of the error terms is very high, $\sigma^2 = Var(\varepsilon)$, then changes in the training data can result in large changes in $f$. We should use a rigid model to not overfit noise or variance.

## Classification or Regression

a) As profit scales and you have fewer employees to pay, you can regress these factors. The target variable is a continuous quantitative value, so this is a regression problem. The number of predictors is 3 and the sample size is 500.

b) Clustering. $n = 20$ and $p = 14$. Observations are assigned to a distinct category rather than predicting a continuous number.

## Real-life applications

a) One example of a categorical application is credit card fraud, with predictors being merchant category, location, time of day, and user spending history. The goal is to immediately flag and block suspicious transactions.

b) Real estate price estimation with predictors such as square footage, number of bedrooms, lot size, neighbourhood school rating, and property age. The goal is that buyers want an accurate prediction for a given house on the market.

## Important things to know

- The advantage of a very flexible approach for regression or classification is that we can model complex non-linear relationships and fit a wider range of functions $f$.
- The disadvantage is that very flexible models can overfit observations or fit irreducible error or noise rather than the true underlying pattern $f$. As a result, they often perform well on training data but fail badly on test data.
- Less flexible models are great for fitting data with many predictors and fewer observations, as the model does not overfit the training data or noise. Lowering flexibility typically raises bias but lowers variance.
- Parametric methods use a fixed number of parameters and assume a predefined functional form, which means they can learn with a smaller training sample. They are usually very interpretable, making the weights $\beta_i$ easy to explain.
- Non-parametric methods are good for estimating complex non-linear $f$ because they do not restrict the model to following a strict functional form. Instead of forcing data into a rigid line or polynomial, they adapt to irregular local patterns.

### Code

Implemented on GitHub on the previous page. Exercise code is linked on the book overview page.

[Back to chapter notes]({{ '/books/introduction-to-statistical-learning/' | relative_url }})
