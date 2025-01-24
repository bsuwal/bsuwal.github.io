---
layout: post
title: Lower Bounds on Markov Chains - The Counting Bound
description: We follow the exposition of Levin and Peres to describe the counting bound, which is a way to lower bound the mixing times of Markov Chains.
date: 2024-08-26
last_modified_at: 2024-08-26
permalink: /blog/counting_bound.html
tags: markovchains mixing randomwalks main
---

Let $\{X_t\} : t\geq 0$ be a discrete Markov Chain defined on the state space $\mathcal{X}$ that has a stationary distribution $\pi$. Define $\X^x_t$ to be the state of sets accessible from state $x$ at time step $t$.  Finally, define

$$
\Delta = \max_{x \in \X^x_t} \deg(x)
$$

to be the maximum degree of the nodes in $\X^x_t$.

First, notice that a trivial upper bound[^1] on the number of states in $\X^x_t$ is

\begin{equation}\label{degree_bound}
|\X^x_t| \leq \Delta^t
\end{equation}

We make the two following assumptions:
1. $\Delta^t$ is less than the size of $\X$, i.e
\begin{equation}\label{assumption: counting bound}
\Delta^t < (1 - \e) |\mathcal{X}|
\end{equation}
for $\e \in (0, 1)$.
2. The stationary distribution $\pi$ is uniform over $\X$, i.e
\begin{equation}\label{assumption: counting bound uniform pi}
\pi(x) = \frac{1}{|\X|}
\end{equation}

Then,

$$
\begin{aligned}
\lVert P^t(x, \cdot) - \pi \rVert_{TV}
&\geq P^t(x, \X^x_t) - \pi(\X^x_t) & \text{(from the definition of TVD)} \\
&= \sum_{y \in \X^x_t} \big( P^t(x, y) - \pi(y) \big) \\
&= \bigg( \sum_{y \in \X^x_t}  P^t(x, y) \bigg) - \frac{|\X^x_t|}{|\X|}  & (\text{from (\ref{assumption: counting bound uniform pi})})\\
&\geq \bigg( \sum_{y \in \X^x_t}  P^t(x, y) \bigg)  - \frac{\Delta^t}{|\X|} & (\text{from (\ref{degree_bound})}) \\
&= 1 - \frac{\Delta^t}{|\X|} & \big(\sum_{y \in \X^x_t}P^t(x, y) =1 \text{ because the $\Pr$ is distributed only over $\X^x_t$.}\big)\\
&> \e & (\text{from (\ref{assumption: counting bound})})
\end{aligned}
$$

The time taken to reduce the TVD to $\e$ is by definition $t_{mix}(\e)$. Taking $\log$ on both sides for \ref{assumption: counting bound} we get:

$$
t_{mix}(\e) \geq \frac{\log{(1-\e) |\X| }}{\log{\Delta}}
$$

Let us think about these assumptions and their effect on the bound.

Notice that the first assumption is very strong. $\Delta^t$ grows exponentially so we would either be asking for $\| \X\|$ to either be very large or hoping that $t_{mix}(\e)$ is very small. The only reason we make this assumption is because we hope to have knowledge of $\Delta$. If we did not know $\Delta$, or even if we did, we could choose to
ignore it and simply replace this assumption with $|\X^x_t| < (1 - \e) |\mathcal{X}|$ to instead get the bound

$$
t_{mix}(\e) \geq \frac{\log{(1-\e) |\X| }}{\log{|\X^x_t|}}
$$

which would be looser, but gets rid of this rather stringent bound.

The second assumption is also unfortunately very strong. However, having
additional information about a non-uniformly distributed $\pi$ could still be useful. For example, say we knew $\pi(x) \geq k$ for some constant $k \leq \frac{1}{|\X|}$. Then following the same steps we would still get a bound of the form

$$
t_{mix}(\e) \geq \frac{\log{(1-\e) |\X| }}{\log{(k \cdot |\X^x_t|)}}
$$

which could still be a useful albeit looser bound.

___
**Footnotes:**

[^1]: This upper bound is trivial because the maximum size of $\X^x_t$ at $t=1$ is $\Delta$, and at $t=2$ is $\Delta^2$, and so on.
