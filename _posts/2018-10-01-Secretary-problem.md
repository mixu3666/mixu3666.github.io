---
layout: post
mathjax: true
comments: true
title:  "Secretary problem"
date:   2018-10-01
---

This is an pretty interesting desicion making problem. Mathematically, it is the simplest 
[Markov decision process](https://en.wikipedia.org/wiki/Markov_decision_process) in the world with the dimension of state space 
and action space both being 2 (can not be smaller to make the problem interesting). Let us first look at the description of the
problem.

*Problem*: A secretary has $N$ job candidates to interview. They have distinct abilities and come to interview one by one randomly.
After interviewing a candidate, the secretary has to decide whether to make an offer to him/her. If an offer is made to 
the candidate, the interview process ends. Or else the candidate needs to seek opportunities elsewhere
and the secretary will interview the next candidate. What is the secretary's strategy in order to maximize the probability
of making the offer to the best candidate?

*Solution*:

Here, we present a formal solution in the framework of Markov decision process by using dynamic programming.
First, we identify the state variable as $s_t=\{0,1\}$ where $t=1,2,...,N$, 0 represents the $t$-th candidate is not the best one
so far, and 1 represents it is the best one so far. The evolution of the state variable $s_{t}\rightarrow s_{t+1}$ here can be 
represented as a transition matrix, i.e.
$$\begin{eqnarray}
Prob(s_{t+1}=0|s_t=0)&=&\frac{t}{t+1}\\
Prob(s_{t+1}=0|s_t=1)&=&\frac{t}{t+1}
\end{eqnarray}
$$
