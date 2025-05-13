---
layout: post
title: The Column-Row factorization $(A = CR)$
description: We describe how every matrix $A \in \R^{m \times n}$ with rank $c \geq 1$ can be factorized into $A = CR$ where $C \in \R^{m \times c}$ and $R \in \R^{c \times n}$.
date: 2025-04-17
last_modified_at: 2025-05-03
permalink: /blog/cr_factorization.html
tags: main linear_algebra matrix_factorization
---
In this post we will describe the interesting fact that _every_ matrix can be factorized in the following way:

**Statement 1.**  Every matrix $A \in \R^{m \times n}$ with column rank $c \geq 1$ can be factorized into $A = CR$ where $C \in \R^{m \times c}$ and $R \in \R^{c \times n}$.

We prove this statement by a simple construction. Let $A_1, \dots A_n$ be the columns of $A$, i.e

$$
A =
\begin{bmatrix}
\Big| & & \Big| \\
A_1 & \cdots & A_n \\
\Big| & & \Big|
\end{bmatrix}
$$

Assume without loss of generality that the first $c$ columns of $A$ are linearly independent.
Then we construct $C$ as an $m \times c$ matrix made up of these $c$ columns:

$$
C =
\begin{bmatrix}
\Big| & & \Big| \\
A_1 & \cdots & A_c \\
\Big| & & \Big|
\end{bmatrix}
$$

We then construct $R$ as a $c \times n$ matrix as

$$
R =
\begin{bmatrix}
1 & 0 & 0 & \cdots & 0 & \star & \cdots & \star  \\
0 & 1 & 0 & \cdots & 0 & \star & \cdots & \star  \\
0 & 0 & 1 & \ddots & \vdots & \star & \cdots & \star  \\
\vdots & \vdots & \ddots & \ddots & & \star & \cdots & \star  \\
0 & \cdots &  & 0  & 1 & \star & \cdots & \star  \\
\end{bmatrix}
$$

where the first $c$ columns are the standard basis vectors in $\R^c$ (i.e the $k$'th vector has a 1 as the $k$'th element and 0 otherwise). The trailing $n-c$ columns of $A$ are a linear combination of the first $c$ columns. The remaining $n-c$ columns of $R$ hold the coefficients of this linear combination.

This completes our construction of both the $C$ and $R$ matrices.

$$
\begin{align*}
\begin{bmatrix}
\Big| & & \Big| \\
A_1 & \cdots & A_n \\
\Big| & & \Big|
\end{bmatrix}
=
\begin{bmatrix}
\Big| & & \Big| \\
A_1 & \cdots & A_c \\
\Big| & & \Big|
\end{bmatrix}
\begin{bmatrix}
1 & 0 & 0 & \cdots & 0 & \star & \cdots & \star  \\
0 & 1 & 0 & \cdots & 0 & \star & \cdots & \star  \\
0 & 0 & 1 & \ddots & \vdots & \star & \cdots & \star  \\
\vdots & \vdots & \ddots & \ddots & & \star & \cdots & \star  \\
0 & \cdots &  & 0  & 1 & \star & \cdots & \star  \\
\end{bmatrix}
\end{align*}
$$

This factorization is sometimes also called ``rank factorization`` or the ``rank-revealing factorization``. [(Wikipedia)](https://en.wikipedia.org/wiki/Rank_factorization).

---

Given a matrix factorization, it is a natural question to ask if it is unique. We will now show that:

##### A column row factorization is not unique.

We will demonstrate this by simply showing two possible column-row factorizations for an example matrix.

First, let us re-state how we can interpret the $C$ and the $R$ matrices:

1. The $C$ matrix contains the basis vectors of the linear transformation induced by $A$.
2. The $k$'th column of $A$ is a linear combination of the columns of $C$. The $k$'th column of $R$ supplies these coefficients.

Consider any square matrix with linearly independent columns. It might be helpful to use the following arbitrary matrix as an example:

$$
A =
\begin{bmatrix}
1 & 1 & 8 \\
4 & 1 & 2 \\
8 & 2 & 1
\end{bmatrix}
$$

You could factorize $A$ by setting $C = A$ and $R$ to be the identity matrix. Convince yourself that this factorization satisfies the two statements above.

$$
\underset{\large{A}}{\begin{bmatrix}
1 & 1 & 8 \\
4 & 1 & 2 \\
8 & 2 & 1
\end{bmatrix}}
=
\underset{\large{C}}{
\begin{bmatrix}
1 & 1 & 8 \\
4 & 1 & 2 \\
8 & 2 & 1
\end{bmatrix}}
\underset{\large{R}}{\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}}
$$

You could also factorize $A$ by setting $C$ to be the identity matrix and $R = A$. Again, convince yourself that this factorization satisfies the two statements above.

$$
\underset{\large{A}}{\begin{bmatrix}
1 & 1 & 8 \\
4 & 1 & 2 \\
8 & 2 & 1
\end{bmatrix}}
=
\underset{\large{C}}{\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}}
\underset{\large{R}}{
\begin{bmatrix}
1 & 1 & 8 \\
4 & 1 & 2 \\
8 & 2 & 1
\end{bmatrix}}
$$

---
##### The row space of $A$ is in the span of the rows of $R$
Consider a matrix $A \in \R^{2 \times 2}$. We know that it has a $CR$ factorization, and let it be the following one:

$$
\underset{\large{C}}{
\begin{bmatrix}
a & b \\
c & d
\end{bmatrix}}
\underset{\large{R}}{
\begin{bmatrix}
e & f \\
g & h
\end{bmatrix}}
=
\underset{\large{A = CR}}{
\begin{bmatrix}
ae+bg & af+bh \\
ce +dg & cf + dh
\end{bmatrix}}
$$

We now make two observations:

1. The $k$'th column of $CR$ is the linear combination of the the columns of $C$, with the coefficients coming from the $k$'th column of $R$.

For example, look at column 1 of $CR$:

$$
\begin{bmatrix}
ae+bg  \\
ce +dg
\end{bmatrix}
=
e
\begin{bmatrix}
a \\
c
\end{bmatrix}
+
g
\begin{bmatrix}
b \\
d
\end{bmatrix}
$$

This is not surprising, as this statement is simply another way of stating that $C$ holds the basis vectors of $A$.


2. The $k$'th row of $CR$ is the linear combination of the rows of $R$, with the coefficients coming from the $k$'th row of $C$.

For example, look at row 1 of $CR$:

$$
\begin{bmatrix}
ae+bg  & af+bh
\end{bmatrix}
=
\begin{bmatrix}
ae & af
\end{bmatrix}
+
\begin{bmatrix}
bg & bh
\end{bmatrix}
=
a
\begin{bmatrix}
e & f
\end{bmatrix}
+
b
\begin{bmatrix}
g & h
\end{bmatrix}
$$



This implies that the row space of $A$ is in the span of the rows of $R$.


---
##### Some Remarks
One might ask, reasonably, why one would be interested in this specific matrix factorization. Here are some immediate reasons we can think of, but undoubtedly there are (many) more:

1. It demonstrates easily what the rank of the matrix is, and also indicate the linearly independent columns. The rank tells the dimension of the range of the linear transformation and the linearly independent columns are the basis vectors of the range, so this representation seems useful.
2. It seems to be used as tool to prove the important result that row rank = column rank (i.e that the number of linearly independent rows of a matrix is the same as the number its linearly independent columns! We do not prove this result in this post.)

We think the first of these points makes it particularly useful for pedagogy. [^1] It explicitly shows that any matrix can be distilled into its essential bones (the basis vectors) and the columns of the matrix are simply linear combinations of these basis vectors.

Since this matrix decomposition seems so fundamental, we think that it can be used to possibly interpret other matrix decompositions too. For example, the $QR$ decomposition is the special case of the $CR$ decomposition with the additional property that the basis vectors (i.e columns of $C$) are orthogonal. [^2]

---
##### Footnotes:

[^1]: Professor Strang [seems to agree.](https://www.norbertwiener.umd.edu/FFT/2020/Faraway%20Slides/Faraway%20Strang.pdf) He also has [a paper](https://math.mit.edu/~gs/everyone/lucrweb.pdf) that expands on this as well as shows an algorithm to do this decomposition using Gaussian Elimination.

[^2]: If one could compute either the $CR$ or the $QR$ decomposition, which one should they compute? It comes down to taste or the use case. Having the original columns as the basis might be better for interpretability, and they are also often sparse and non-negative. Having an orthogonal basis has the benefits of, well, orthogonality, as well as the QR algorithm being the one more easy to implement.
