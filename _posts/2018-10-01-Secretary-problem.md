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
and the secretary will interview the next candidate. The secretary is unaware of the quality of yet unseen candidates. What is the secretary's strategy in order to maximize the probability
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
p_t(0,a_t)&=&0\\
p_t(1,1)&=&\frac{t}{N}
\end{eqnarray}
$$

Suppose the offer is made at time $t_s$, $p_{t}=0$ for all $t>t_s$.

The above is the mathematical formulation of the secretary problem as a Markov decision process. It is beyond our scope here to introduce the general theory, which involves [Bellman's principle of optimality](https://en.wikipedia.org/wiki/Bellman_equation#Bellman's_Principle_of_Optimality), to solve the problem. Our solution 
below is based on the method of dynamic programming, which underlies Bellman's theory.

First, consider that the secretary waits until the last candidates to make the decision. What is the probability of making the
offer to the best candidate? This situation is very simple,

$t=N$, (for convenience, assume $N\gg1$)

$$
\begin{eqnarray}
\mathcal{P}_N(0)&=&0,\\
\mathcal{P}_N(1)&=&1
\end{eqnarray}
$$

How about $t=N-1$? 

$$
\begin{eqnarray}
\mathcal{P}_{N-1}(0)&=&\frac{N-1}{N}\mathcal{P}_N(0)+\frac{1}{N}\mathcal{P}_N(1)=\frac{1}{N}, \quad(\text{Optimal choice: wait})\\
\mathcal{P}_{N-1}(1)&=&\max(\frac{N-1}{N}, \frac{N-1}{N}\mathcal{P}_N(0)+\frac{1}{N}\mathcal{P}_N(1))=\max(\frac{N-1}{N},\mathcal{P}_{N-1}(0))=\frac{N-1}{N}, \quad(\text{Optimal choice: make offer})
\end{eqnarray}
$$

and $t=N-2$?

$$
\begin{eqnarray}
\mathcal{P}_{N-2}(0)&=&\frac{N-2}{N-1}\mathcal{P}_{N-1}(0)+\frac{1}{N-1}\mathcal{P}_{N-1}(1)
=\frac{N-2}{N}(\frac{1}{N-1}+\frac{1}{N-2}),\quad(\text{Optimal choice: wait})\\
\mathcal{P}_{N-2}(1)&=&\max(\frac{N-2}{N},\mathcal{P}_{N-2}(0))=\frac{N-2}{N}\quad(\text{Optimal choice: make offer})
\end{eqnarray}
$$

Performing the above back induction, in general we have

$$
\begin{eqnarray}
\mathcal{P}_{t}(0)&=&\frac{t}{t+1}\mathcal{P}_{t+1}(0)+\frac{1}{t+1}\mathcal{P}_{t+1}(1)\quad(\text{Optimal choice: wait})\\
\mathcal{P}_{t}(1)&=&\max(\frac{t}{N},\mathcal{P}_{t}(0)) 
\end{eqnarray}
$$

Here, we are able to observe that 

$$
\mathcal{P}_{t}(1)\ge\mathcal{P}_{t}(0), 
$$

and that 

$$
\mathcal{P}_{t}(0)\ge\mathcal{P}_{t+1}(0).
$$


As a result, as $t$ gets smaller, $t/N$ gets smaller while $\mathcal{P}_{t}(0)$ gets bigger. 

Therefore, at $t_s$ and $t<t_s$ where

$$
\frac{t_s}{N} = \mathcal{P}_{t_s}(0)
$$

the secretary's optimal choice is to not make the offer and wait. It should not be difficult to get that 

$$
\mathcal{P}_{t_s}(0)=\frac{t_s}{N}(\frac{1}{N-1}+...+\frac{1}{t_s+1}+\frac{1}{t_s})
$$

In conclusion, to maximize the probability of making the offer to the best candidate, the secretary needs to interview $t_s$ candidates
and make the offer to the next candidate that is best so far. $t_s$ is determined by

$$
\frac{1}{N-1}+...+\frac{1}{t_s+1}+\frac{1}{t_s}=1
$$

The left hand side of the above equation is a [harmonic series](https://en.wikipedia.org/wiki/Harmonic_series_(mathematics)). 
A usual trick to approximate the series with integration gives

$$
\int_{t_s}^{N}\frac{dx}{x}<\frac{1}{N-1}+...+\frac{1}{t_s+1}+\frac{1}{t_s}<\int_{t_s-1}^{N-1}\frac{dx}{x}
$$

For sufficiently big $N$

$$
\log\frac{t_s}{N}\approx 1
$$

i.e. $t_s/N=1/e$, the strategy selects the best candidate about 37% (1/$e$) of the time.


*Alternative Solution*:

Is there a solution if we do not resort to dynamic programming?

The optimal policy for the problem is a stopping rule. The interviewer rejects the first $r$ applicants and select the first sebsequent
applicant who is the best so far. The probability of choosing the best applicant under this strategy is therefore (the probability of
$i$-th candidate is the best is $1/N$)

$$
\sum_{i=r+1}^N\frac{1}{N}\mathrm{Pr}(\text{best in }i-1\text{ is in first r})=\sum_{i=r+1}^N\frac{1}{N}\frac{r}{i-1}=\frac{r}{N}
(\frac{1}{r}+\frac{1}{r+1}+...+\frac{1}{N-1})
$$

*Further thought*
1. What if the secretary wants to maximize the probability of making the offer to the second best candidates? What should be the 
state variables and their time evolution?

