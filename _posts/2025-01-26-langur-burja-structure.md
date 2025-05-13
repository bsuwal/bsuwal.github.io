---
layout: post
title: Why play Langur Burja with Six 6-sided dice
description: We consider how the game would vary if it was played with a different number of dice, or with a different number of symbols. We empirically observe that the number of faces in the dice should be greater than or equal to the number of dice for a House advantage.
date: 2025-01-26
last_modified_at: 2025-01-26
permalink: /blog/langur_burja_structure.html
tags: langur_burja nepal main
---
_This post is part of a series of posts about the popular Nepali betting game Langur Burja. We refer the reader to [this notebook]({{ site.baseurl }}/notebooks/langur_burja.html) for other posts in this series._

In [the last post]({{ site.baseurl }}/langur_burja_rules.html) we stated the payoff rules of Langur Burja and considered some alternate payoff schemes.

In a similar vein, we ask the following question in this post:

> Why is Langur Burja played with six dice with six faces each?

What happens, for example, if we play with five dice instead? What if we played with six dice, but each with seven faces instead?

---
***Recall that the House is only willing to play the game when it has an advantage, i.e when the Player's expected payoff is negative.***

---

##### Notation
Let $N$ be the number of dice, and $F$ be the number of faces of each dice. We assume that the number of symbols on the board is also $F$.

Suppose that the Player has bet Rs. 1 on one symbol.

---

##### Case: N=F
The following graph shows what the Player's payoff is when $N=F$ i.e the number of dice is the same as the number of faces on the dice. The $N=F=6$ is our canonical Langur Burja setting.
![img]({{ site.url }}/assets/img/langur_burja/N=F.png)

The plot shows that the Player's payoff remains negative, and therefore the House should be happy to play with this variant of the game.

---

##### Case: Varying N, F=6
We now hold the number of faces in the dice constant at $F=6$ (so, a regular dice) and change the number of dice $N$ that we play with.
![img]({{ site.url }}/assets/img/langur_burja/varying_N.png)

This plot is interesting because the Player's expected payoff is negative (and therefore the House's expected payoff is positive) right up till $N=6$. Playing with any additional dice gives the Player the advantage, therefore the House would not allow that.

This similar pattern persists even when we change $F$. For example, when $F=8$, the Player's expected payoff is negative right up to $N=8$. This suggests that

\begin{equation}\label{N_leq_F}
N \leq F
\end{equation}

is a necessary condition for the House to have an advantage in the game.

It should be remarked that a profit-maximizing House should in theory be happier to play with fewer than 6 dice. However, the best game for the House is one where the Player feels like they aren't losing (much) even when the odds are stacked against them, and it is possible that playing with fewer dice noticeably changes the Player's perception of their odds of winning. We will investigate related psychological aspects of this game in a future post.

##### Case: N=6, Varying F
We hold the number of dice constant at $N=6$ and change the number of faces $F$ on each dice. Recall that this also means that we change the number of symbols on the board, which is also $F$.

![img]({{ site.url }}/assets/img/langur_burja/varying_F.png)

Again, interestingly the Player's expected payoff is negative right at $F=6$ and onwards. This means that the House has an advantage at $F\geq 6$.

This pattern persists when we change $N$ too. For example, when $N=8$ , the Player's expected payoff is negative right at $F=8$ and onwards. Notice that this agrees with our hypothesis in Equation (\ref{N_leq_F}).

---
##### Conclusion
We empirically observe that as long as $F \geq N$, the House has an advantage and is therefore willing to play the game. The canonical $N=F=6$ satisfies this requirement.

##### Further directions
* We suspect that establishing (\ref{N_leq_F}) as a necessary (and probably sufficient?) condition this could be a rather straightforward proof to write.
