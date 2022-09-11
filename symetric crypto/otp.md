---
title: OTP
author: Quinten Cabo s1027427
date: \today
---

Otp encryption is when you encrypt all the bits  of a message by having a key of a length that is equal to the length of the message and then just simply adding them together. 

The problem with this is that:

- You need a lot of keys, hard disk example.
- You need a lot of keys for different people

However it does give perfect secrecy. 

The reason for this is that the $C$ gives **no** information about $M$ . You could turn that $C$ into any $M$ and you would not know if it was the right one. Nice. 

You can not reuse keys though because then you can find the difference between the plain texts!

C = M $\oplus$ K 
C' = M' $\oplus$ K

Now you can do C - C' = (M $\oplus$ K) $\oplus$ (M' $\oplus$ K) = M $\oplus$ M' $\oplus$ K $\oplus$ K = Difference between the plaintext. 

These issues with the key can be attempted to be resolved by making a keystream from a smaller key using a [stream cipher](stream.md) however we can prove OTP gives perfect secrecy and we can not do this with stream ciphers.