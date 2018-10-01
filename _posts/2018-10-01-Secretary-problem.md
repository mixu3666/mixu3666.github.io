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
After interviewing a candidate, the secretary has to decide whether to make an offer. If an offer is made to 
the candidate, the interview process ends. Or else the candidate needs to seek opportunities elsewhere
and the secretary will interview the next candidate. What is the secretary's strategy in order to maximize the probability
of making the offer to the best candidate?

*Solution*:

Here, we present a formal solution in the framework of Markov decision process by using dynamic programming.
First, we identify the state variable as $s_t=\\{0,1\\}$ where $t=1,2,...,N$, 0 represents the $t$-th candidate is not the best one
so far, and 1 represents it is the best one so far. The evolution of the state variable $s_{t}\rightarrow s_{t+1}$ here can be 
represented as a transition matrix, i.e.

$$\begin{eqnarray*}
Prob(s_{t+1}=0|s_t=0)&=&\frac{t}{t+1}, Prob(s_{t+1}=1|s_t=0)&=&\frac{1}{t+1}\\
Prob(s_{t+1}=0|s_t=1)&=&\frac{t}{t+1}, Prob(s_{t+1}=1|s_t=1)&=&\frac{1}{t+1}\\
\end{eqnarray*}
$$

Note that the decision of the secretary has no influence on the evolution of the state $s_t$. 

The function the secretary wants to maximize is defined as 

$$
\mathcal{P}_1(s_1)=\sum_{t=1}^N p_t(s_t,a_t)
$$

where $a_t=\{0,1\}$ represents making the offer ($a_t=1$) or not making the offer ($a_t=0$). Obviously, we have

$$
\begin{eqnarray}
p_t(0,0)&=&0\\
p_t(1,1)&=&\frac{t}{N}
\end{eqnarray}
$$

Suppose the offer is made at time $t_s$, $p_{t}=0$ for all $t>t_s$.

The above is the mathematical formulation of the secretary problem as a Markov decision process. It is beyond our scope here to introduce the general theory, which involves [Bellman's principle of optimality](https://en.wikipedia.org/wiki/Bellman_equation#Bellman's_Principle_of_Optimality), to solve the problem. Our solution 
below is based on the method of dynamic programming, which underlies Bellman's theory.

First, consider that the secretary waits until the last candidates to make the decision. What is the probability of making the
offer to the best candidate? This situation is very simple,

$t=N$, 

$$
\begin{eqnarray}
\mathcal{P}_N(0)&=&0,\\
\mathcal{P}_N(1)&=&1
\end{eqnarray}
$$

How about $t=N-1$? 

$$
\begin{eqnarray}
\mathcal{P}_{N-1}(0)&=&\frac{N-1}{N}\mathcal{P}_N(0)+\frac{1}{N}\mathcal{P}_N(1),\\
\mathcal{P}_{N-1}(1)&=&\max\\{\frac{N-1}{N}, \frac{N-1}{N}\mathcal{P}_N(0)+\frac{1}{N}\mathcal{P}_N(1)\\}=\max\\{\frac{N-1}{N},\mathcal{P}_{N-1}(0)\\}
\end{eqnarray}
$$


