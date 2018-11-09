---
layout: post
mathjax: true
comments: true
title:  "Probability of Sitting in the Assigned Seat"
date:   2018-10-31
---

The problem has a surprising answer.

*Problem*: 100 passengers are boarding a plane. The first passenger lost his ticket and decide to take a random seat. All the other passengers have their ticket and will take their assigned seat if it is not occupied yet and will take a random seat if it is occupied. What is the probability of the last passenger taking his/her assigned seat?

*Solution*:

There is nothing special about 100. Let us consider the general case of $N$ passenger. Suppose the probability of the last passenger taking his/her assigned seat is $P(N)$. As we will see, this problem can be formulated as a dynamic programming problem.

If the first passenger took his assigned seat, it is sure that the last passenger will take the assigned seat. The probability of this situation is $1/N$.

If the first passenger took the second passenger's seat (the probability is $1/N$), how to relate this situation to a smaller poblem? The first passenger's seat is in the remaining $N-1$ seats. We relabel it as second passenger's seat. Under this manipulation, we construct a smaller problem of $N-1$ passenger. 

If the first passenger took the third passenger's seat (the probability is $1/N$), how to relate this situation to a smaller poblem? In this case, the second passenger takes his own seat. The first passenger's seat is in the remaining $N-2$ seats. We relabel it as third passenger's seat. Under this manipulation, we construct a smaller problem of $N-2$ passenger. 

...

If the first passenger took the $(N-1)$-th passenger's seat (the probability is $1/N$), how to relate this situation to a smaller poblem? In this case, the second to the $(N-2)$-th passenger take their own seat. The first passenger's seat is in the remaining 2 seats. We relabel it as $(N-1)$-th passenger's seat. Under this manipulation, we construct a smaller problem of 2 passenger. 

If the first passenger took the $N$-th passenger's seat (the probability is $1/N$), the last passenger can not take his own seat.

Based on the above analysis, 

$$
P(N)=\frac{1}{N}+\frac{1}{N}P(N-1)+...+\frac{1}{N}P(2)
$$

It is surprising that $P(N)=1/2$ in general.

The answer of $1/2$ reminds that there must be a simple argument behind the answer. 

**Lemma**: The last seat is either the first passenger's seat or the last passenger's seat.

*Proof*: If the last seat is $j$-th passenger's seat. The seat would have been taken by $j$-th passenger.

**Corollary**: If a passenger has to make a random choice of seats, he/she always has the first and last passenger's seat in his/her choices.

*Proof*: If the passenger has no first passenger's seat in his choices, he/she will has non-zero probability to choose the seat of last passenger. This contradicts with the above lemma.

The passenger has equal probability to choose the first and last passenger's seat. Therefore the probability of the last seat is last passenger's seat is 1/2.
