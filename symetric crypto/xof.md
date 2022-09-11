---
title: xof
author: Quinten Cabo s1027427
date: za 30 okt 2021
---

A XOF function is a function that allows generating an output Z (the term digest is no longer appropriate) of  arbitrary length. The function looks like this:

$XOF(M, \ell) = Z$

![[xof.png]]

Similarly to [hash](hash.md) functions, a XOF is considered secure if it offers the same resistance as a [random oracle](randomoracle.md) would. However, in concrete XOF functions, the achievable security strength is upper bound by a parameter, usually called the capacity.        

One single XOF can cover all use cases, since we can choose the output length. If we need multiple independent hash functions, we can just apply the XOF to the message like $M||0$ and $M||1$. This creates 2 new XOF functions  that are independent. This process is called domain separation and can be generalized to create $2^w$ functions, using any $D ∈ {0, 1}^w$ in: $XOF_D(M) = XOF(M||D)$    

## Turning Merkle Damgard into a XOF
A simple way to turn [Merkle-Damgard](merkledamgard.md) into a variable length output (XOF function) is to repeat the hash computation multiple times while including a counter. The counter is to avoid collisions. This is called MGF1 and looks like this:

![[mgf1.png]]

This can be computed in parallel. 