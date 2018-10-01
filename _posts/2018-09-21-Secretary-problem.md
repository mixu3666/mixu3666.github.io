This is an pretty interesting desicion making problem. Mathematically, it is the simplest 
[Markov decision process](https://en.wikipedia.org/wiki/Markov_decision_process) in the world with the dimension of state space 
and action space both being 2 (can not be smaller to make the problem interesting). Let us first look at the description of the
problem.

A secretary has $N$ job candidates to interview. They have distinct abilities and come to interview one by one randomly.
After interviewing a candidate, the secretary has to decide whether to make an offer to him/her. If an offer is made to 
the candidate and is accepted, the interview process ends. Or else the candidate needs to seek opportunities elsewhere
and the secretary will interview the next candidate. What is the secretary's strategy in order to maximize the probability
of making the offer to the best candidate?
