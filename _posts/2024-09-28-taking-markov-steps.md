---
layout: post
title:  Taking Markov Steps
description: We walk through a simple example of a random walk on a finite graph.
date: 2024-09-28
last_modified_at: 2024-09-28
permalink: /blog/taking_markov_steps.html
tags: markovchains mixing randomwalks main
---
_This is a post I had originally written in April 2019. I post it here now with some modifications for clarity._

This post will have us walk through a simple random walk on a finite graph. The purpose of this blog post is to illuminate what each step looks like (as a matrix multiplication) and to develop intuition.

We will take a random walk on the following graph. The little swirls around the nodes pointing to themselves denote that a random walker might stay at the same node when taking the next step.

![center-img]({{ site.url }}/assets/img/rw_graph.png)

The transition matrix for a random walk on the above simple graph is:

$$
\begin{equation*}
P =
\begin{bmatrix}
    \frac{1}{3} & \frac{1}{3} & \frac{1}{3} & 0 & 0 & 0 \\
    \frac{1}{3} & \frac{1}{3} & \frac{1}{3} & 0 & 0 & 0 \\
    \frac{1}{4} & \frac{1}{4} & \frac{1}{4} & \frac{1}{4} & 0 & 0 \\
    0 & 0 & \frac{1}{4} & \frac{1}{4} & \frac{1}{4} & \frac{1}{4} \\
    0 & 0 & 0 & \frac{1}{3} & \frac{1}{3} & \frac{1}{3} \\
    0 & 0 & 0 & \frac{1}{3} & \frac{1}{3} & \frac{1}{3} \\
\end{bmatrix}
\end{equation*}
$$

Say we start at node A. When we start, we know we are at node A with a probability of 1. Our position vector would be:

$$
\begin{equation*}
 X_{0} =
\begin{bmatrix}
    1 & 0 & 0 & 0 & 0 & 0
\end{bmatrix}
\end{equation*}
$$

### **A step at a time**
To take a Markov Step we simply multiply our position vector $X_0$ by the transition matrix from the right. The resulting vector $X_1$ gives us the probabilities of where the random walker will be at after taking 1 step:

$$
\begin{equation*}
X_{0} P =
\begin{bmatrix}
    1 & 0 & 0 & 0 & 0 & 0
\end{bmatrix}
\begin{bmatrix}
    \frac{1}{3} & \frac{1}{3} & \frac{1}{4} & 0 & 0 & 0 \\
    \frac{1}{3} & \frac{1}{3} & \frac{1}{4} & 0 & 0 & 0 \\
    \frac{1}{3} & \frac{1}{3} & \frac{1}{4} & \frac{1}{4} & 0 & 0 \\
    0 & 0 & \frac{1}{4} & \frac{1}{4} & \frac{1}{3} & \frac{1}{3} \\
    0 & 0 & 0 & \frac{1}{4} & \frac{1}{3} & \frac{1}{3} \\
    0 & 0 & 0 & \frac{1}{4} & \frac{1}{3} & \frac{1}{3}
\end{bmatrix}
=
\begin{bmatrix}
    \frac{1}{3} & \frac{1}{3} & \frac{1}{3} & 0 & 0 & 0
\end{bmatrix}
= X_{1}
\end{equation*}
$$

To know the probabilities of where the random walker is going to be at time $t=2$ we repeat the above procedure by multiplying $X_1$ by $P$ from the right:

$$
\begin{equation*}
X_{1} P =
\begin{bmatrix}
    \frac{1}{3} & \frac{1}{3} & \frac{1}{3} & 0 & 0 & 0
\end{bmatrix}
\begin{bmatrix}
    \frac{1}{3} & \frac{1}{3} & \frac{1}{4} & 0 & 0 & 0 \\
    \frac{1}{3} & \frac{1}{3} & \frac{1}{4} & 0 & 0 & 0 \\
    \frac{1}{3} & \frac{1}{3} & \frac{1}{4} & \frac{1}{4} & 0 & 0 \\
    0 & 0 & \frac{1}{4} & \frac{1}{4} & \frac{1}{3} & \frac{1}{3} \\
    0 & 0 & 0 & \frac{1}{4} & \frac{1}{3} & \frac{1}{3} \\
    0 & 0 & 0 & \frac{1}{4} & \frac{1}{3} & \frac{1}{3} \\
\end{bmatrix}
=
\begin{bmatrix}
    0.3056 & 0.3056 & 0.3056 & 0.0833 & 0 & 0
\end{bmatrix}
= X_{2}
\end{equation*}
$$

---

##### **Sanity Check**
This is a good time to pause and inspect that the numbers make sense. We have claimed that $X_t$ contains the vector of probabilities that the random walker is at a node. Representing each 'hop' or time-step as a $\rightarrow$, let's see all the different nodes we can arrive to in two time-steps if we start at node $A$.

$$
\begin{aligned}
\begin{array}{c|c|c|c|c|}
\hline
& \text {Ways we can arrive at A:} & \text { Ways we can arrive at B: } & \text {Ways we can arrive at C:} & \text {Ways we can arrive at D:}\\
\hline
& A \rightarrow A \rightarrow A \text{ w.p } \frac{1}{3} \times \frac{1}{3} & A \rightarrow A \rightarrow B \text{ w.p } \frac{1}{3} \times \frac{1}{3} & A \rightarrow A \rightarrow C \text{ w.p } \frac{1}{3} \times \frac{1}{3} & A \rightarrow C \rightarrow D \text{ w.p } \frac{1}{3} \times \frac{1}{4}\\

& A \rightarrow B \rightarrow A \text{ w.p } \frac{1}{3} \times \frac{1}{3}  & A \rightarrow B \rightarrow B \text{ w.p } \frac{1}{3} \times \frac{1}{3} & A \rightarrow B \rightarrow C \text{ w.p } \frac{1}{3} \times \frac{1}{3}\\

& A \rightarrow C \rightarrow A \text{ w.p } \frac{1}{3} \times \frac{1}{4} & A \rightarrow C \rightarrow B \text{ w.p } \frac{1}{3} \times \frac{1}{4} & A \rightarrow C \rightarrow C \text{ w.p } \frac{1}{3} \times \frac{1}{4} \\

\hline
\text{Total }\Pr: & 0.3056  &  0.3056 &  0.3056 & 0.0833 \\
\hline
\end{array}
\end{aligned}
$$

This also makes sense intuitively. A,B and C are more "densely" connected, so if I start in that cluster I should probably end up somewhere in the cluster.

---

Notice from the above steps that if we wished to know the probabilities of where the random walker is after an arbitrary $t$ steps, that can be simply be written as:

$$
X_t = X_{t-1} \cdot P = X_{t-2} \cdot P \cdot P = \cdots = X_0 P^t
$$


#### **The stationary distribution emerges**
The above equation leads us to now believe that the matrix $P^t$ is an object of interest. At this point we will compute it for our above transition matrix for $t=100$.

The following is a snippet of code written in Julia:

```
using LinearAlgebra

# Adjacency matrix
A = [1 1 1 0 0 0;
     1 1 1 0 0 0;
     1 1 1 1 0 0;
     0 0 1 1 1 1;
     0 0 0 1 1 1;
     0 0 0 1 1 1];

# Diagonal matrix
D = diagm(vec(sum(A, dims=2)))

# This is the transition matrix
P = inv(D) * A

# Take a 100 steps
t = 100;
P^t
```
and this gives us the following output:

$$
\begin{equation*}
P^{100} =
\begin{bmatrix}
    0.15 & 0.15 & 0.20 & 0.20 & 0.15 & 0.15 \\
    0.15 & 0.15 & 0.20 & 0.20 & 0.15 & 0.15 \\
    0.15 & 0.15 & 0.20 & 0.20 & 0.15 & 0.15 \\
    0.15 & 0.15 & 0.20 & 0.20 & 0.15 & 0.15 \\
    0.15 & 0.15 & 0.20 & 0.20 & 0.15 & 0.15 \\
    0.15 & 0.15 & 0.20 & 0.20 & 0.15 & 0.15 \\
\end{bmatrix}
\end{equation*}
$$

Each row of this matrix is the same, and it is the stationary distribution $\pi$. [We talk more about stationary distributions in this post.]({% link _posts/2024-09-18-stationary.md %})

It may sound obvious in retrospect but we think it is worth emphasizing that at no point in the above
computation (of $P^t$!) did we use $X_0$ or any other position vector. The above matrix also tells us that no matter where our random walker started her walk, we would have ended up with the same vector $X_t = \pi$ - this is because $X_0$ would have one 1 element somewhere and the rest would be zeros, and the $X_0 \cdot P^t$ multiplication would only pluck out a row from $P^t$, and all the rows are the same. What if $X_0$ was a probability vector without all the probability mass concentrated at one node? The magical thing (which the reader should check) is that $X_t$ would still be $\pi$.
