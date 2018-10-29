---
layout: post
mathjax: true
comments: true
title:  "Probability of forming a triangle"
date:   2018-10-29
---

*Problem*: Given a wood stick of length $l$ and cut it twice into three pieces randomly. What is the probability for the three pieces to form a triangle?

*Solution*:

Suppose the length of the three pieces is $x_1$, $x_2$, and $x_3$ respectively. One condition is that $x_1<x_2+x_3$. Therefore, for the first cut, we should pick $x_1$ to be the smaller one, i.e. $0<x_1<l/2$, and the second cut should be on the $l-x_1$. Suppose the second cut produces stick of length $x_2$ and $x_3$. We must have $|x_2-x_3|<l-x_1$.
