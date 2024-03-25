---
layout: post
title: Some convex loss functions
description: Basically taking some second derivatives for a sanity check.
date: 2023-10-25
permalink: /convex-loss-functions.html
tags: learning
---

Convex loss functions are of special interest because they have a global minimum. It is therefore convenient that the test for whether a function is convex is straightforward - the second derivative of the function should be positive.


Below we show the convexity of a commonly used convex loss function - the sum of squared errors.

Let $$(X, Y) \sim (\mathcal{X}, \mathcal{Y})$$ be a dataset with $$n$$ entries. For  $$f: \mathcal{X} \rightarrow \mathcal{Y}$$, the associated loss function is:

$$
L_f(X, Y) = \sum_{i=1}^{n} (y_i - f(x_i))^2
$$

The second derivative of this loss function w.r.t $$f(x)$$ is:

$$
\begin{align*}
\frac{\partial^2}{\partial f(x)^2} L_f(X, Y) &= \frac{\partial^2}{\partial f(x_i)^2} \sum_{i=1}^{n} (y_i - f(x_i))^2 \\
&= 2 \frac{\partial}{\partial f(x_i)}  \sum_{i=1}^{n} (y_i - f(x_i)) \cdot (-1) \\
&= 2 \frac{\partial}{\partial f(x_i)}  \sum_{i=1}^{n} (f(x_i) -y_i)\\
&= 2
\end{align*}
$$

I feel the above terms may not be correct, and therefore need to be reviewed.

### Todo:
* add other convex loss functions: hinge loss, logistic loss
* write this out in matrix notation - [this seems to be a good resource.](https://math.stackexchange.com/questions/483339/proof-of-convexity-of-linear-least-squares)
