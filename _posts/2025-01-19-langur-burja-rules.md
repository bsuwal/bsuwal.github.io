---
layout: post
title: The rules of Langur Burja
description: We state the rules of this popular Nepali betting game. We consider some alternate payoff schemes and argue against them.  
date: 2025-01-19
last_modified_at: 2025-01-26
permalink: /langur_burja_rules.html
tags: langur_burja nepal main
---
_We point the reader to [this notebook]({{ site.baseurl }}/notebooks/langur_burja.html) for other posts in this series. We also thank Suman Nepal for (re-)teaching us how to play Langur Burja in October 2024._

The following are the rules of the game, as played canonically.

* The game is played between the House and one or more Players. Each Player bets independently of the others.

* The game is played on a board of six distinct symbols, as shown below:

| ![center-img]({{ site.url }}/assets/img/langur_burja/board.png) |
|:--:|
| *Starting from the top left, the symbols are Jhandi/Langur ("झण्डी"/"लङ्गुर"), Burja ("बुर्जा"), Eet ("ईट"), Paan ("पान"), Surat ("सुरत") and Chidi ("चिडी").* |
| *<small>Img from https://www.pgyer.com/apk/zh/apk/com.samanrai.khorkhore</small>* |

* The player puts an original bet amount (colloquially called "बोट", and henceforth referred to as "bet amount") on one or more symbols.  

* Six fair six-sided dice with these symbols are rolled.

| ![center-img]({{ site.url }}/assets/img/langur_burja/dice.png) |
|:--:|
| *Langur Burja dice.* |

Suppose the Player bets Rs 1 on a symbol. Let $k \in \\{0, 1, 2, 3, 4, 5, 6\\}$  be the number of dice that show the Player's chosen symbol. *For the rest of the post, we will operate in this setting.*

The House distributes the payoff in the following manner:
1. If $k \in \\{0, 1\\}$, the Player loses their bet amount.
2. If $k > 1$, the Player's payoff is $k$ i.e the Player's payoff is the bet amount multiplied by the number of times the symbol appears. [^1]

```
Example 0:
The Player bets Rs 1 on the Paan symbol. The rolled dice shows 0 Paan in total.
The House pays nothing to the player. The Player's payoff is  -1.
```

```
Example 1:
The Player bets Rs 1 on the Paan symbol. The rolled dice shows 1 Paan in total.
The House pays nothing to the player. The Player's payoff is -1.
```

```
Example 2:
The Player bets Rs 1 on the Paan symbol. The rolled dice shows 3 Paan in total.
The House pays Rs 1 * 3 + Rs 1 = Rs 4 to the player. The Player's payoff is Rs 3.
```

The following map shows the payoff the Player gets when $k$ dice show the Player's chosen symbol:

$$
\begin{aligned}
\begin{array}{|c|c|}
\hline
\text {k} & \text { payoff } \\
\hline
0 & -1 \\
1 & -1 \\
2 & 2 \\
3 & 3 \\
4 & 4 \\
5 & 5 \\
6 & 6 \\
\hline
\end{array}
\end{aligned}
$$

Readers who wish to simply learn the rules of the game can stop reading here. The rules are simple enough (especially if you pay a few rounds). However, the reason we made this post was to consider some similar-sounding variants of the payoff rules that seemed reasonable at first glance, but do not make sense upon more thought.

**Somewhat surprisingly, the rules available online do not seem to agree across sources. For example, <a href="https://www.playonlinedicegames.com/jhandi-munda">this online game</a> uses the below mentioned Alternate payoff scheme 3, and other sites seem to have entirely different rules. For what it is worth, we ourselves initially thought Alternative payoff scheme 2 was the real payoff scheme.**

**Getting the rules correct is very  important because the House advantage may end up being negative (or atleast non-positive) with very simple-sounding modifications to the rules. In fact, we (empirically) observe that to be true for all the forthcoming payoff schemes in this post.**

<hr>
#### **Alternate payoff scheme 1:**
Under this scheme, which we call the Lenient बोट फिर्ता regime, the House distributes the payoff in the following manner. The way it departs from the payoff scheme above is highlighted in bold.

1. If $k = 0$, the Player loses their bet amount i.e payoff is -1.
2. **If $k = 1$, the House returns the Player's original bet amount (i.e बोट फिर्ता)**. The Player's payoff in this scenario is 0.
2. If $k > 1$, then the Player's payoff is $k$, the bet amount multiplied by the number of times the symbol appears.

The payoff the Player gets when $k$ dice show the Player's chosen symbol:

$$
\begin{aligned}
\begin{array}{|c|c|}
\hline
\text {k} & \text { payoff } \\
\hline
0 & -1 \\
1 & 0 \\
2 & 2 \\
3 & 3 \\
4 & 4 \\
5 & 5 \\
6 & 6 \\
\hline
\end{array}
\end{aligned}
$$

This payoff scheme is therefore more lenient than the one above, because the Player's payoff is 0 when one dice shows their chosen symbol, whereas the same would have resulted in a payoff of -1 earlier.

The reason why this payoff scheme does not make sense (for the House) is that the expected payoff for the Player is *positive*, meaning that the House has a negative house advantage.

While this is true for our game of 6 symbols and 6 fair dice, this also happens to be true whenever the number of symbols equals the number of fair dice (for eg, if we were to play with only 2 symbols and a fair coin instead). Interestingly, the house advantage in this setting stays around the 0.264 mark even with increasing $N$.

This is illustrated in the following figure. The $N=6$ case is our familiar case of playing with 6 dice.
![bot-firta]({{ site.url }}/assets/img/langur_burja/alternate-scheme-1.png)


#### **Alternate payoff scheme 2:**
Under this scheme, which we call the Strict बोट फिर्ता regime, the House distributes the payoff in the following manner. The way it departs from the regular payoff scheme above is again highlighted in bold.

1. If $k = 0$, the Player loses their bet amount.
2. **If $k = 1$, the House returns the Player's original bet amount (i.e बोट फिर्ता)**. The Player's payoff in this scenario is 0.
2. **If $k > 1$, then the Player's payoff is (k-1).**

The following map shows the Player's payoff under this scheme, where $k$ dice show the Player's chosen symbol:

$$
\begin{aligned}
\begin{array}{|c|c|}
\hline
\text {k} & \text { payoff } \\
\hline
0 & -1 \\
1 & 0 \\
2 & 1 \\
3 & 2 \\
4 & 3 \\
5 & 4 \\
6 & 5 \\
\hline
\end{array}
\end{aligned}
$$

The reason why this payoff scheme does not make sense (for the House) is because the expected payoff for the Player for any round in this case is 0. This means that the House advantage in any round is also 0, and therefore there is no reason for the House to play this game.

The following figure shows that this is true as long as the number of symbols equals the number of fair dice. The $N=6$ case is our canonical case of playing with 6 dice.
![bot-firta]({{ site.url }}/assets/img/langur_burja/alternate-scheme-2.png)

#### **Alternate payoff scheme 3:**
Under this scheme, the House distributes the payoff in the following manner. The way it departs from the regular payoff scheme is again highlighted in bold.
1. If $k = 0$, the Player loses their bet amount.
2. **If $k > 0$, then the Player's payoff is k.**

The following map shows the Player's payoff under this scheme, where $k$ dice show the Player's chosen symbol:

$$
\begin{aligned}
\begin{array}{|c|c|}
\hline
\text {k} & \text { payoff } \\
\hline
0 & -1 \\
1 & 1 \\
2 & 2 \\
3 & 3 \\
4 & 4 \\
5 & 5 \\
6 & 6 \\
\hline
\end{array}
\end{aligned}
$$

Again, this simple variation leads to the expected payoff of the Player to be positive, therefore we don't think it makes sense for the House to play this game. The $N=6$ case is our canonical case of playing with 6 dice.
![bot-firta]({{ site.url }}/assets/img/langur_burja/alternate-scheme-3.png)
---
**Footnotes:**

[^1]: Note that the House also returns the Player's original bet amount to the Player, but this amount is not counted as part of the payoff.
