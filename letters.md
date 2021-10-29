---
title: letters
author: Quinten Cabo s1027427
date: \today
---

This file keeps track of all the letters and shorthands in Cryptography. Hopefully they are consistent we will see.


# Letters for Things
- M -> The message that is send
- P -> Something that is in Plaintext
- K -> The Key. The secret used to make other things secret or secure. 
- RK -> A round key derived from K in a key schedule. 
- C -> A Cipher text.
- D -> A Diversifier. An extra input to be able to generate multiple keys treams (Z) from the same key. Usually send with the message. Can't repeat.
- Z -> A key stream. Usually generated from a K and a D pair. 
- ' -> Represents an alternative version of a variable
- s -> The unit for security strength. You say s bits of security.
- b -> The length of a block cipher. 
- k -> The length of a key.
- $RO$ -> A [random oracle](randomoracle.md) is an ideal cryptographic primitive that generates a random response to each query (and the same response for queries with the same argument).
- $Q_d$ -> The [online query](adversary.md) history in an attack. 
- $|Q_d|$ is the number of online queries that have been done.
- $Q_c$ -> The [offline query](adversary.md) history in an attack. 
- $|Q_d|$ is the number of offline queries that have been done.
- $|Q_f|$ the number of forgery attempts 
- A -> An adversary.
- IV -> A (random) initial value. This is used for the first block in [CBC mode](blockmodes.md)
- h -> A hash function. 
- H -> A digest of a hash function. Like so: $H = h_m$ . 
- L -> A dummy key
- T -> Is a tag of a message. This is like the signature that was made with a MAC a key and a message M. 
- A -> Associated data. Extra data that is included in the send data that is used for authentication.



# Cryptographic primitives
- SC -> [Stream Cipher](stream.md)
- WB -> Wide Block Cipher
- B  -> [Block Cipher](block.md) 
- LFSR -> [Linear Feedback Shift Register](lfsr.md) a type of stream cipher that is linear.


# People
![[people]]