---
layout: post
mathjax: true
comments: true
title:  "Probability of forming a triangle"
date:   2018-10-29
---

*Problem*: Given a rod of length $l$ and cut it randomly into three smaller rods. What is the probability for the three rods to form a triangle?

*Solution*:

After the first cut, the rod is divided into $x_1$ and $l-x_1$. Because to form a triangle, no rods should be longer than $l/2$. If $x_1<l/2$ ($x_1>l/2$), the second cut should be on the second part of length $l-x_1$ ($x_1$). After the second cut, the length of second and third pieces are $x_2$ and $l-x_2-x_1$. We must have $\mid x_2-(l-x_2-x_1) \mid < x_1$ ($\mid x_2-(l-x_2-x_1)\mid < l-x_1$), i.e.
$l/2-x_1<x_2<l/2$ ($0<x_2<l-x_1$). As a result, the probability of forming a triangle is

$$
\int_0^{l/2} \frac{x_1}{l} \frac{dx_1}{l} + \int_{l/2}^l \frac{l-x_1}{l}\frac{dx_1}{l}=\frac{1}{4}
$$
