---
title: Pseudorandom permutation security
author: Quinten Cabo s1027427
date: vr 29 okt 2021
---

# Pseudorandom Permutation Security
Let B be a block cipher with key size k. Let K be randomly drawn from the set of all keys. The advantage of an adversary $A$ in distinguishing $B_K$ from a random permutation $P$ is defined as $Adv^{prp}_B(A) = ∆A (B_K ; P)$ .

Alternatively, one may consider $P$ to be uniformly randomly drawn from the set of all
b-bit permutations.

# Strong Pseudorandom Permutation Security

Strong pseudorandom permutation security is when you protect against keep in mind the advantage of an adversary $A$ in distinguishing $B^{-1}_K$ from a $P^{-1}$. The advantage with strong pseudorandom permutation security is defined as:

$Adv^{sprp}_B (A) = ∆_A(B_K, B^{-1}_K, (A) = ∆_A (B_K , B_K; P, P^{-1})$

We often measure the the complexity of an adversary in the number of input blocks to the oracle. Rather then the number of bits.


PRP security is when you play the distinguising game with a random permutaion and a block cipher and you can only make querries against the **encryption version** of the block cipher.
It is prp secure if you can not find an advantage (less than key recovery)

SPRP security is when you play the distinguising game with a random permutation and you can make queries to the **encryption AND decryption**. It is sprp secure if you can not find an advantage less then key recovery 