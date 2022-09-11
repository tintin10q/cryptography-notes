---
title: sponge
author: Quinten Cabo s1027427
date: za 30 okt 2021
---

# The Sponge Function

With lessons learned from the problems of the [Merkle Damgard](merkledamgard.md) designs in 2007 Bertoni et al. introduced “sponge functions”. The sponge construction uses a cryptographic permutation $f$ of $b = c + r$ bits. It operates on a state consisting of an inner part of c bits (the capacity) and an outer part of r bits (the rate). 

Message M is injectively padded into r-bit blocks, and each block is compressed by adding it to the outer part and transforming the state using the cryptographic permutation f . This is called the “absorbing” phase. At the end, once all message blocks are processed, the “squeezing” phase begins. In the squeezing phase, hash digest bits are taken from the outer part of the state r bits at a time, interleaved with evaluations of the cryptographic permutation f . This makes the sponge construction a XOF.

![[sponge.png]]

# Differences with Merkle Damgard 

The sponge construction does not have the collision preservation property. It turns out that this is not essential. You can have a collision secure hash function if if the underlying compression function is not. This happens for the sponge construction. You can see this by having a an F build like this:

$F(CV||M) = f(CV ⊕ (M||0^c))$

Here the function f is not collision resistant. You could make a M that will be the same as the CV. 

I don't know how how the hash function can be secure while there are collisions in the compression.  But if it is true it means you can remove the feed forward which saves on performance. 

Another difference is that the underlying function within the sponge is not a block cipher but rather a cryptographic permutation. This makes the mode conceptually simpler because block ciphers were not developed to be used in hashing. Block ciphers can also be reversed and this is not needed with hashing. You even don't want this. 

A third difference is that the sponge uses a b-bit state that and that digest extraction is from part of the state only. It leaves c bits of the state “untouched”, and there with eliminates the second preimage and length extension attack.

Apparently c determines the security strength of the sponge construction.

# Sponge Is Hard To Distinguish From Random
The sponge construction, unlike Merkle Damgard turns out to be indifferentiable. Bertoni et al. proved the following result.

> Theorem: Consider the sponge construction based on random permutation f . There exists a simulator S such that for any adversary A with data complexity $|Q_d|$ blocks:
> $Adv^{iff}_{sponge}(A) ≤ \frac{|Q_d|^2}{2^{c+1}}$

The sponge thus solves all problems that the Merkle-Damgård mode had! If we consider the
sponge with output truncated to n bits, above theorem also implies security against the following
attacks as indicated:

- Collision resistance: $min(c/2, n/2)$ ;
- Preimage resistance: $min(c/2, n)$ ;
- Second preimage resistance: $min(c/2, n)$ .

Unfortunately, this above theorem does not mean that a concrete hash function making use of the
sponge construction is a secure hash function. It only implies that the construction if instantiated
with a random permutation. Such a thing does not exist in reality; we are always stuck with an explicit permutation f.

Theorem should thus be interpreted as stating that the sponge construction resists generic
attacks. If $f$ has some exploitable weakness, this may give rise to a weakness in the hash function.

This is where cryptanalists come in. They try to find flaws in the permutation f that would be
exploitable when the permutation is used in the sponge function. This is not specific for sponge
but for ALL hashing modes.

# Message authentication from sponge
Can sponge be used to construct a [MAC](mac.md) function? Like so:

$MAC_K (M) = h(K||M)$ 

For the sponge, the construction works. In fact, one can use the sponge construction likewise
for the design of stream ciphers and key derivation functions. Figure below illustrates this.

![[spongemodes.png]]