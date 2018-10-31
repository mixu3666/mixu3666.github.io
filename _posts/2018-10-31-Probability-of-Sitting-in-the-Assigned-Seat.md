---
layout: post
mathjax: true
comments: true
title:  "Probability of Sitting in the Assigned Seat"
date:   2018-10-29
---

The problem has a surprising answer.

*Problem*: 100 passengers are boarding a plane. The first passenger lost his ticket and decide to take a random seat. All the other passengers have their ticket and will take their assigned seat if it is not occupied yet and will take a random seat if it is occupied. What is the probability of the last passenger taking his/her assigned seat?

*Solution*:

Suppose the general case of $N$ passenger. And the probability of the last passenger taking his/her assigned seat is $P(N)$.

If the first passenger took his assigned seat, it is sure that the last passenger will take the assigned seat. The probability of this situation is $1/N$.

If the first passenger took a wrong seat (the probability is $(N-1)/N$), there are $N-1$ seats remained. How to relate this situation to $P(N-1)$ to form a recursion relation?

