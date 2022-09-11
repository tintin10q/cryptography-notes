---
title: Security Claim
author: Quinten Cabo s1027427
date: \today
---

# Primitive to Standard

People make cryptographic primitives. A cryptographic primitive is like a cryptographic algorithm that does something useful to increase security. It is like a contract. If you follow these steps then you get x amount of security. Other people try to break/attack it. When they do break it they publish their findings with perhaps some suggestions and the creators update etc repeat. 

If the primitive does not get broken for some time then it stabilizes. If a primitive has been public for a while and if it has attractive features such as high efficiency, and if there have been no attacks then we start getting confidence in it. If many experts have confidence then a primitive can become a standard which also adds to the trust.  

# Security Claims

What does it mean for a cryptographic primitive to be secure? This is defined clearly if the publication of the primitive is accompanied by a security claim. A security claim is an unambiguous statement that defines the minimum success probability an attack must have to be considered as breaking the primitive In the security claim breaking is usually well defined and usually means being able to distinguish the output of the primitive from a sequence of random bits (RO). The success probability is expressed in terms of computation -> offline complexity and online complexity.   

A security claim serves two purposes:
- For potential cryptanalists, it serves as a challenge. It is an invitation to come up with attacks that have a higher success probability as the one in the claim. If someone finds such an attack, the designer will have to admit his design is broken. He can then choose to strengthen his design or weaken the security claim.
- For potential users, it serves as a security specification. Assuming no attacks have been found that refute the claim, the user can assume there are no attacks with higher success probability than specified in the claim. Of course the confidence in the claim is based on the open cryptographic research activity: the older the claim and the more experts have tried to break the primitive, the higher the confidence.

If a cryptographic primitive is published without a security claim then the default is [exaustive key search](exaustive_key_search.md) as this should be the most efficient way to distinguish the primitives output from a sequence of uniformly random bits. It is the default security claim in absence of any better attacks. 

## Provable security  

We can also say things based on assumptions. Like if this and this then we CAN prove it is secure. You can't prove this and this (underlying primitive) but at least it allows you to focus on where things are not secure. Another version of this is were you say that a reduction of a security claim is equal to solving  or reducing a famous math problem like factoring or traveling salesman. 

# Expressing security strength.  
Often, a security claim, either challenged or assumed to be satisfied, is expressed as a number called the security strength.

If a claim for a cryptographic primitive implies that the expected effort to break it with success probability close to 1 is 2 s units, e.g., executions of the primitive, then we say the primitive has a claimed security strength of s bits. Clearly, due to the existence of exhaustive key search, the security strength of a cryptographic primitive taking a k-bit key is at most k bits.

----

# Claiming Security

A typical claim that the designers may have posed for a stream cipher is the following:

**Claim**: Let SC be a stream cipher with key size k. There exists no adversary $A$ with computational complexity $|Q_c|$ less than $2^{k−1}$ that succeeds in distinguishing $SC_K$ from a random oracle with advantage more than $1/2$ (naive guesser).

This claim captures the idea that there should be no attacks more efficient than exhaustive key search. However, it is rather vague about the advantage of adversaries with limited resources. The following claim is much more clear:

Claim 4.5.2. Let SC be a stream cipher with key size k. For any adversary A with computational complexity $|Q_c|$, the advantage is:

$Adv^{prf}_{SC} \leq \frac{|Q_c|}{2^k}$ 

## Breaking claims
Claims like these can't be proven but you can break them. This happens with attacks.  An attack is when someone finds a way to distinguish the stream cipher from a random oracle with a better claimed bound then was made in the claim. 

> **For example** a team of researchers find an attack on $SC$ . They show that $SC_K$ can be distinguished from a random oracle $RO$ with probability 1 using computational complexity $2^k/2$ . Formally, this means that this team of researchers have described an adversary $A'$ with computational complexity $|Q_c| = 2^{k/2}$ (so that is in half of the queries) such that $Adv^{prf}_SC(A') = 1$ . This is better than the claimed bound and thus considered to be a valid attack on the scheme. 