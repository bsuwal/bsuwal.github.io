---
layout: post
title: Notation for Markov Chains
description: A post containing the notation for all Markov Chain posts on this blog.
date: 2024-09-18
last_modified_at: 2024-09-18
permalink: /blog/mc_notation.html
tags: markovchains mixing randomwalks main
---

In this post I establish the notation used in posts on Markov Chains on this blog. Unless otherwise specified within the post, you should assume that this is the notation being used.

I will try our best to stick to this notation throughout, but sometimes error happen. In such a case, let me know!
This notation follows the notation established in {% cite LP17 %}.

---

- A Markov Chain is usually denoted as $(X_0, X_1. \cdots, X_n)$. We denote $P$ as the Markov Chain's transition matrix. $X_t$ takes values in the domain $\mathcal{X}$.

- $P(x, \cdot)$ is the $x$'th row of $P$.

- $\Pr_x$ and $\E_x$ denote the probabilities and expectations respectively of events when the Markov chains start at state $x$.

- Because of the way we have defined $P$, our distribution vectors (for example, $\pi$) are row vectors. This means that multiplying a distribution vector by $P$ from the right updates the distribution by one step.

- What if you multiply a column vector $f(x)$ by P on the left? Recall that $Pf = \E_x[f]$.

- $\Pr_x[X_t = y] = P^t(x, y)$.

- A Markov Chain is ***irreducible*** if every state can be reached by every other state. Conversely, a reducible Markov Chain is one where some states cannot be reached by other states. Formally, a chain $P$ is irreducible if for any two states $x, y \in \Omega$ there exists an integer $t$ s.t $P^t(x, y) > 0$.

- A Markov Chain is ***aperiodic*** if every state has a self-loop. By self-loop, we mean that there is a nonzero probability of remaining in that state. Similarly a state is aperiodic if it has a self loop.
  - We often see mention of "periodicity issues" in the literature. Consider a Markov Chain with period 2, i.e the minimum amount of time for a Markov Chain instance that starts at state $x$ to return to $x$ again is 2. (A simple random walk on a graph with two vertices and an edge is an example.) $P^{2t}(x, y)$ is distinct from $P^{2t+1}(x, y)$ - consider, for example in the Ehrenfest urn model that you are keeping track of the number of balls in urn 1 and $n=1$. In such a case $P^t(x, \cdot)$ will never converge as $t \rightarrow \infty$. This is an issue because we don't have a stationary distribution in this case!! This is why we often wish to study aperiodic chains, or "lazy" chains - chains that allow self-loops. For an arbitrary transition matrix $P$, $Q = \frac{I + P}{2}$ is the transition matrix for the lazy version of the Chain, where you remain in the same state w.p 1/2.

-  A state $x$ is called ***absorbing*** if there are no outgoing transitions from the state.

-  A state $x$ is said to be ***transient*** if, starting from $x$, there is a non-zero probability that the chain will never return to $x$. It is ***recurrent*** otherwise.

- We define the ***hitting time*** to state $x \in \mathcal{X}$ to be

$$
\t_x = \min\{t \geq 0: X_t = x\}
$$

- Notice that the above definition does not encapsulate the value of $X_0$, which is crucial in determining hitting times. If $X_0 = x$, then $\t_x = 0$. If we are interested only in hitting times that are positive, then we can define

$$
\t^{+}_x = \min\{t \geq 1: X_t = x\}
$$

When $X_0 = x$, we call $\t^+_x$ the ***first return time***.


---
- ***(Stationary Distribution)***
A probability distribution $\pi$ over $\mathcal{X}$ is called the stationary distribution if

$$
\pi = \pi P
$$

where $P$ is the transition matrix of $\mathcal{X}$.

We formulate $\pi$ as a row vector, and multiplying by $P$ from the right updates the distribution vector by one step. This definition is saying that $\pi$ is a vector such that taking an additional step does not change the distribution vector. This also means that once the stationary distribution has been reached by a Markov Chain, it remains there (since taking additional steps cannot bring the distribution "out" of it).

An element-wise formulation of the stationary distribution is:
\begin{equation} \label{pi_elementwise}
\pi(y) = \sum_{x \in \mathcal{X}} \pi(x) \cdot P(x, y)
\end{equation}
for all $x \in \mathcal{X}$. Intuitively I interpret this as - If you start from anywhere at the stationary distribution and take a step towards $x$, then the (weighted) average of your steps is the stationary distribution at $x$.

Since $P$ is stochastic i.e its entries are non-negative and sum to 1, you can also write $\pi$ as

$$
\pi(y) = \sum_{x \in \mathcal{X}} \pi(y) \cdot P(y, x)
$$

But this seems almost obvious to state in retrospect. It simply states that the weighted average of a number, when the weights sum to 1, is that number itself.

---
**Bibliography**
{% bibliography --cited %}
