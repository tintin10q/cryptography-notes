---
title: Authenticated encryption schemes  
author: Quinten Cabo s1027427
date: vr 29 okt 2021
---
# AE function 

Cryptographic schemes that both encrypt data and authenticate it, are called authenticated en- cryption functions, AE functions for short. Just like an encryption scheme, it gets as input a message and often also a nonce, and it encrypts the plaintext to a ciphertext. It also computes a tag for authentication at the same time. Authenticated encryption schemes often also support the possibility to additionally process data that only needs to be authenticated. This data is called associated data.

# Scenario
[Alice](people.md) wants to send a message M and some associated data A to [Bob](people.md). The message may not be read by [Eve](people.md), so Alice wants to send this piece of information confidentially. Both the message and the associated data must not be tampered with, so Alice wants to send both pieces of information authentically. Alice and Bob have a shared K.    

# What can Alice do?
She can choose a proper nonce N, and compute [$(C, T) = AE_K(N, A, M)$](letters.md). The nonce N can be seen as a randomizer of the scheme. Bob, in turn, obtains $(N, A, C, T)$ . He needs to evaluate the “inverse” of $AE_K$ , namely a function that 

1. Verifies the tag
2. Outputs the message M **if and only if the tag is correct**. 

If the tag is not correct than we can't know if the message came from Alice and it probably didn't. 

This inverse function is often called an authenticated decryption function or decryption verification function. We call it authenticated decryption function. Mathematically, this function satisfies:  

![[AD.png]]

Both ae and de look like this as schemas:
 
![[aedeschema.png]]

The goal of this scheme are:
1. It should be infeasible to deduce information about M from (C,T) 
2. It should be infeasible to forge a ciphertext and tag (C,T) for a certain nonce, associated data, and message for an adversary that does not know the key K.

In the matching distinguisher game uses a [random oracle](randomoracle.md) for the nonce and encryption and a function ⊥ for the de that always returns NOK. 

Here, A is not allowed make any of the following two types of query:
- Query to its first oracle $(AE_K or RO)$ for a nonce N that was already used in an earlier query;
- Query to its second oracle $(AD_K or ⊥)$ on input of a tuple $(N, A, C, T )$ that was the result of an earlier query $(N, A, M ) \mapsto (C,T)$ to its first oracle $(AE_K or RO)$ .

indistinguishability is clear but unforgeability not so much but anyways one can prove that if AE K is hard to distinguish from random and if it is hard for an adversary to forge against AD K (in the sense of Definition 6.2.1), the authenticated encryption function achieves good AE security.        

These things do by themselves not protect against replay attacks.