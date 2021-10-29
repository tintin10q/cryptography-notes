---
title: cryptographichash
author: Quinten Cabo s1027427
date: za 30 okt 2021
---

# What is a cryptographic Hash function?

 A hash function h is a primitive that takes as input an arbitrary-length string and returns an n-bit digest H (also known as the hash result or sometimes just even hash), with n some fixed length: $h(M) = H$ .       
 
 ![[hashf.png]]
 
In programming there are many use cases for hash functions. In most of these use cases, one hopes that the digest for different inputs look unrelated.

# Requirements 
These are the classic security requirements for hash functions.

## Collision Resistance
We want the results of a hash function to be unique. This way software can rely on the hash function to generate unique identifiers. This way you can also prove that one file is the same as another file because for each hash there should only be one file.  Thus it is important that no two different inputs map to the same digest.  

There are non cryptographic use cases for this and also cryptographic use cases. For instance you could sign a document by publishing the hash of your private key concat the document for a unique hash this could be a signature. 

In more detail, we call a hash function collision resistant if it is infeasible to find distinct messages $M_1 \neq M_2$ with the same digest $h_{M_1} = h_{M_2}$ .

Because the there is an infinite amount of inputs there also exists an infinite amount of collisions however it should be computationally hard to find a collision. 

For a random oracle, we can exactly quantify how hard it is by expressing the success probability of finding a collision as a function of the number of random oracle calls, that we will denote by $|Q_c|$ . As the output of a random oracle is unpredictable, the best an adversary can do is try different inputs until a collision is found. After computing the digest for $|Q_c|$ messages, we have obtained $\frac{|Q|}{2}$ pairs of messages. The collision probability is simply determined by the birthday bound in the digest length n. This probability becomes close to 1 if $|Q_c|$ gets close to $2^{n/2}$ . It follows that for a hash function the best possible collision resistance security strength that can be achieved is n/2.

## Second pre-image resistance
Second pre-image resistance is about finding a message that has the same hash as some other message. This is harder then just finding a collision. With a collision you just need to find messages that have the same hash. With second pre image resistance you already have a (M,H) pair and you have to find another M' that hashes to the same H.  

In more detail, we call a hash function second pre-image resistant if it is infeasible, given a message M, to find another message M' that has the same hash. Or $h(M') = h(M)$.

For a random oracle, the success probability of finding a second pre-image after $|Q_c|$ attempts is close to $|Q_c|/2^n$ . The expected cost of finding a second pre-image is hence about $2^n$ , so the second pre-image resistance security strength of any hash function is at most n. 

Second pre-image is just a special case of a collisions, but for a secure hash function it is much harder to achieve.

## Pre-image resistance
(first) pre-image resistance is the resistance of a function h against the ability to reverse a H. So you given some H you are able to find a M input that results in the H. This is harder than second pre-image.   

We call a hash function (first) pre-image resistant if it is infeasible, given a digest H, to find a message M that hashes to H, or $h(M ) = H$.

For a random oracle, the success probability of finding a pre-image after $|Q_c|$ attempts is close to $|Q_c|/2^n$ . The expected cost of finding a pre-image is hence also about $2^n$ , so the pre-image resistance security strength of any hash function is at most n.

## Keyed hashing
You can build [MAC](mac.md) and [Stream ciphers](stream.md) from hash functions. 