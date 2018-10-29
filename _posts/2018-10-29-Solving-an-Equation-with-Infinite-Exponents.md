---
layout: post
mathjax: true
comments: true
title:  "Solving an Equation with Infinite Exponents"
date:   2018-10-29
---

This is a tricky problem that often appears in technical interviews.

*Problem*: If x^x^x^x^x^x^x^x^x^x^x...... = 2, solve for x. (Please see [Tetration](https://en.wikipedia.org/wiki/Tetration#cite_note-8))

*Solution*:

This problem has an obvious recursive structure. We can rewrite the problem as

$$
x^2=2
$$

Then $x=\sqrt{2}$.

The interview will often go further. What if x^x^x^x^x^x^x^x^x^x^x...... = 4? Applying the same technique,

$$
x^4=4
$$

Again $x=\sqrt{2}$. How come it is the same as previous one? This kind of dilemma often arises from the existence of the limit.
Define $a(1)=x$, $a(2)=x^x$, $a(3)=x^{x^x}$ and so on. Then we have the recursion relation 

$$
a(n)=x^{a(n-1)},
$$

which is $\log a(n)=a(n-1)\times \log(x)$. Euler showed that, to ensure that a steady state exists, $e^{-e}\le x \le e^{1/e}$.
