---
title: streamcipher
author: Quinten Cabo s1027427
date: \today
---

Stream ciphers is the general concept of what [lfsr](lfsr.md) s do. They take an initial state and generate an infinite key from that. This infinite key is called a Keystream (Z). Part of this keystream (truncated) can be used to encrypt a message (M) into a cipher text (C) and back.

lfsr do not work. What does work is some non linear behavior and then a diversifier. This works. But can we prove it is secure like with [otp encryption](otp.md)? No we can't. We can never know for sure wether a concrete cryptographic primative is secure. On the other hand, we can have confidence in the security of a concrete cryptographic primative. Such confidence is always based on the fact that the cryptographic primate was published and that many researches that are experts in cryptoanalysis have tried to break it but none succeded. This applies to all cyptographic primatives that is not otp. 
