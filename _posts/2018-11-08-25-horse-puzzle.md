---
layout: post
mathjax: true
comments: true
title:  "25 horse puzzle"
date:   2018-11-08
---

*Problem*: There are 25 horses, a 5 lane race track, no timer. The horses run consistently. How many races do you need to find the top 5 fastest horses?

*Solution*: This is a generalization of the well-known [25-horse problem to find the 3 fastest](https://www.geeksforgeeks.org/puzzle-9-find-the-fastest-3-horses/). In this case, you need 7 races. Suppose we divide the horses into 5 groups and race each group. Then we pick the fastest horse in each group and race them. Therefore, after these six races, we have the following situation,

A1 A2 A3 A4 A5

B1 B2 B3 B4 B5

C1 C2 C3 C4 C5

D1 D2 D3 D4 D5

E1 E2 E3 E4 E5

(A1>B1>C1>D1>E1)

A1 is the fastest horse. Then which of the remaining horses have probability of being in the top 5 fastest? They are:

A2 A3 A4 A5 B2 B3 B4 C2 C3 D2 + B1 C1 D1 E1

Obviously, we need careful design here. Suppose we race A2, B2, C2, D2, E1.

If E1 is the fastest, the top 5 fastest are A1 B1 C1 D1 E1. We need 7 races.

If D2 is the fastest, the top 5 fastest are A1 B1 C1 D1 D2. We need 7 races.

If C2 is the fastest, 
