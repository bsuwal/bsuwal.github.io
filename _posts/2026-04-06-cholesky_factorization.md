---
layout: post
title: Cholesky Factorization
description: A short proof of the Cholesky Factorization $B = R^{\ast}R$ of a positive definite matrix $B$.
date: 2026-04-06
last_modified_at: 2026-04-06
permalink: /blog/cholesky.html
tags: main linear_algebra matrix_factorization
---
This proof is short only because arguably the $QR$ decomposition is doing most of the heavy lifting. 

<div class="env" markdown="1">
<span class="env-title">Statement.</span> Suppose $B$ is a positive definite matrix. Then there exists a unique upper triangular
matrix $R$ with only positive numbers on its diagonal such that

$$
B = R^{\ast} R
$$

where $R^{\ast}$ is the adjoint of $R$.
</div>

**Proof**

(Note that because $B$ is positive definite, it implies that $B$ is invertible and also that $B$ is a square matrix.)

$$
\begin{aligned}
B
&= A^2 & \text{(Every positive definite matrix has a unique positive square root)} \\
&= A^{\ast}A & \text{(Every positive operator is self-adjoint)} \\
&= (QR)^{\ast}(QR) & \text{(Every full-rank square matrix can be QR decomposed)} \\
&= R^{\ast} Q^{\ast} QR \\
&= R^{\ast}R & \text{($Q^{\ast}Q = I$ because $Q$ is unitary)}
\end{aligned}
$$

Above we have used the fact that since $B$ is invertible, $A$ is also invertible and therefore full-rank.

The $R$ is unique as desired as the $QR$ decomposition is unique if $Q$ is unitary and $R$ is upper triangular with only positive entries in the diagonal.

---
The primary reference used in this post is {% cite ladr %}.

---
##### Bibliography
{% bibliography --cited %}
