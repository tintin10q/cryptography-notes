---
title: Random Oracle
author: Quinten Cabo s1027427
date: do 28 okt 2021
---

I finally found the symbol its $\mathcal{O}$.

A random oracle is an ideal cryptographic primitive that generates a random response to each query (and the same response for queries with the same argument).  It accepts inputs of arbitrary size and generates infinite streams. We write the random oracle like  “RO” but then with fancy letters.   

## Fixed Length Random Oracle 
RO maintains an archive $AR$ that contains tuples $(M, Z)$ . We call an algorithm that keeps a state between queries stateful.  $M ∈ AR$ if there is a tuple $(M, Z)$ in $AR$ with as an $M$ as the first member of the tuple and $Z(M)$ the second  member of the tuple $(M, Z)$. $Z$ is the output given by $RO$ from the input $M$. 

Initially, the archive $AR$ is empty. If $RO$ is queried with an input $M$ it generates a $Z$ and then puts this as $(M, Z)$ in the archive AR and returns $Z(M)$ to the query.

> **When a query is made to the random oracle:**
> If $M \notin AR$, $RO$ generates a uniformly random string Z, and stores (M, Z) in AR.
> If $M \in AR$, $RO$ find the the previously generated Z in AR.
> 
> Return $Z$ .

We wish our RO oracle to be usable as a stream cipher. This implies it must be able to return an output Z of arbitrary length. Concretely, we adapt the query interface to $RO$ by also including the desired length of Z, denoted by $\ell$. The algorithm now becomes the following:

>RO is queried with $(M, \ell)$
>If $M \in AR$ and $Z(M)$ is shorter than $\ell$ bits. $RO$ updates $(M, Z)$ in $AR$ by appending enough uniform random bits so that the length of $Z$ becomes $\ell$ it integrates the query in the archive AR
>If $M \in AR$ and $Z(M)$ is shorter than $\ell$  bits, RO updates (M, Z) in the archive by appending enough uniform random bits to Z so that its length becomes $\ell$ .
> If $M \notin AR$, $RO$ generates a uniformly random string Z, and stores (M, Z) in AR.

