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

There is nothing special about 100. Let us consider the general case of $N$ passenger. Suppose the probability of the last passenger taking his/her assigned seat is $P(N)$.

If the first passenger took his assigned seat, it is sure that the last passenger will take the assigned seat. The probability of this situation is $1/N$.

If the first passenger took a wrong seat (the probability is $(N-1)/N$), there are $N-1$ seats remained. How to relate this situation to $P(N-1)$ to form a recursion relation? This is the *crux* of the problem. Suppose the first passenger took the seat assigned to passenger $A$. The first passenger's seat is in the remaining $N-1$ seats. We label it as the passenger $A$'s seat. Under this manipulation, the probability of the last passenger taking the assigned seat is just $P(N-1)$. If the last passenger is not passenger $A$, it is fine. However, there is $1/(N-1)$ probability that the last passenger is $A$. In this case, $A$ actually takes the first passenger's seat. Therefore, if the first passenger took the wrong seat, the probability of the last passenger taking the assigned seat is 

$$
P(N-1)*\frac{N-2}{N-1}
$$

Based on the above analysis, 

$$
P(N)=\frac{1}{N}+\frac{N-1}{N}P(N-1)\frac{N-2}{N-1}
$$

It is obvious that $P(2)=1/2$. We find that $P(3)=1/2$ and so on. It is surprising that $P(N)=1/2$ in general.

The answer of $1/2$ reminds that there must be a simple argument behind the answer. 

**Lemma**: The last seat is either the first passenger's seat or the last passenger's seat.

*Proof*: If the last seat is $j$-th passenger's seat. The seat would have been taken by $j$-th passenger.

**Corollary**: If a passenger has to make a random choice of seats, he/she always has the first and last passenger's seat in his/her choices.
