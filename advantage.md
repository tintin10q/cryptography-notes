---
title: advantage
author: Quinten Cabo s1027427
date: vr 29 okt 2021
---

# Distinguishing advantage

We consider adversary Eve to be successful if she finds an attack that has a success probability that is higher than the one in the security claim that comes with the cryptographic primitive. This section is about how we can express such a claim. 

**In a claim, one takes the strongest possible attacker model and if a cryptographic primitive is secure in that model, it is also secure in all weaker attacker models.** 

Random oracle distinguishability is modeled by the following thought experiment:

Behind the back of Eve, we secretly select either $SC_K$ or $RO$. Either function is chosen with 50% possibility: we generate a random bit $b ← − {0, 1}$ , and select SC K if $b = 1$ and $RO$ if $b = 0$. We do not reveal our choice to Eve. However, Eve would like to know this. To measure the success probability that Eve has in guessing b, we consider the experiment the figure. 

![Distinguishing experiment for stream ciphers](distinguis.png)

In this figure, the adversary, Eve, is in either of two worlds: the “real world” where she speaks with $SC_K$ and the “ideal world” where she speaks with $RO$ ([random oracle](randomoracle.md)). As Eve does not know whether she is in the real or ideal world, we call the entity that is either SC K or RO her “oracle”. Eve can “query” her oracle. In a query she gives as input a diversifier D and requested stream length and her oracle responds with a keystream Z of  bits. In the real world, this keystream satisfies $Z = SC_K(D)$ and in the ideal world it satisfies $Z = RO(D)$. 

Eve can send a number of queries to her oracle, and eventually, she must guess whether she is in the real or in the ideal world. She does so by returning a bit $b' ∈ {0, 1}$. Eve returns 0 if she thinks she is in the real world and 0 if she thinks she is in the ideal world. 

Eve succeeds if $b' = b$ , and we denote this by the event `success`. Clearly, a naive adversary has a success probability of $1/2$ : she may simply make no queries and toss a coin to determine b' . Therefore, her goal would be to succeed in guessing b with probability significantly larger than $1/2$ . In other words, any adversary that succeeds with probability significantly more than $1/2$ can distinguish. 

When considering adversary Eve in a formal way, she (or rather, “it”) is an algorithm. We denote such an adversary by A. We now define the (probability) distance between the real world and the ideal world with respect to an adversary 

$∆_A(SC_K ; RO) = Pr A^{SCk} = 1) − Pr(A^{RO} = 1)$

In words, this distance is the difference between the probability that the adversary A returns $b'= 1$ in the real world minus the probability that it returns $b' = 1$ in the ideal world. This distance is equal to two times the success probability of the adversary A minus 1:   

$∆_A(SC_K ; RO) = 2Pr (success) − 1$

We call $∆_A(SC_K ; RO)$ **the advantage of A in distinguishing $SC_k$ from $RO$ .** In literature, it is also known as the advantage of A in breaking the pseudorandom function (PRF) security of $SC_K$ .

# Understanding the distinguishing advantage

There is no way to prove an upper bound for $Adv^{prf}_SC(A)$ for any concrete [stream cipher](stream.md), but it makes sense to claim such a bound. Breaking the cipher then simply corresponds with coming up with an algorithm A' with $Adv^prf_SC(A)$ higher than the one [claimed](claim.md).