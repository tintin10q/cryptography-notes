---
title: OTP
author: Quinten Cabo s1027427
date: \today
---

Otp encryption is when you encrypt all the bits  of a message by having a key of a length that is equal to the lenght of the message and then just simply adding them together. 

The problem with this is that:

- You need a lot of keys, hard disk example.
- You need a lot of keys for different people

However it does give perfect secrecy. 

The reason for this is that the $C$ gives **no** information about $M$ . You could turn that $C$ into any $M$ and you would not know if it was the right one. Nice. 


These issues with the key can be attempted to be resolved by making a keystream from a smaller key using a [stream cipher](stream.md) however we can prove OTP gives perfect secrecy and we can not do this with stream ciphers.