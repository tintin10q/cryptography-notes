---
title: Older Hash Functions
author: Quinten Cabo s1027427
date: za 30 okt 2021
---

These are all implementation of [cryptographic hash functions](cryptographichash.md)

# MD5
Rivest designed MD5 (message digest 5)in 1991 based on an earlier design of his hand, MD4. It uses the Merkle-Damgård mode with the Davies-Meyer mode. The digest of this hash function is 128 bits.

## MD5 internals:
- 32 bit words;
- 4-word state;
- 16-word message blocks;
- 64 rounds, each taking one message word

![[md5.png]]

The window like squares denote integer addition, and the ≪ denotes a cyclic shift. Combining [bitwise addition (XOR)](xor.md), integer addition and rotation gave hope that this hash function was strong.

In 1993 already, it was shown that F was weak. At that time MD5 was not adopted that much. Ten years later, there was made great progress in breaking MD5. Even with all this progress towards breaking MD5, many companies were unwilling to let MD5 go in exchange for a better alternative. In 2005 Lenstra, Wang and De Weger use MD5 collisions to generate fake TLS certificates. Finally in 2016 MD5 was mostly replaced by a version of SHA-2.

# SHA-1
SHA-1 was then installed by NIST in 1995 drawing inspiration from MD5. The NSA designed SHA-1 that predictably uses the Merkle-Damgård mode with Davies-Meyer. It has a digest of 160 bits.

## Internals 
The internals of SHA-1 resemble those of MD5, except that it uses 80 rounds and 5-word states.
In SHA-1, a message extension takes place following the rule:

(![[sha1messageextension.png]]

## Round function
The round function can be observed in Figure 8.8. The similarity to MD5 is apparent.

![[roundsha1.png]]

Theoretical collision attacks with effort 2 61 were published in 2004-2007, while in 2017 collisions were published at shattered.io by Marc Stevens et al.

## SHA-2 
In 2001 and 2008 the NSA designed SHA-2 as reinforced versions of SHA-1. The SHA-2 consists of 6 hash functions with digests of 224, 256, 384 and 512 bits.

SHA-2 is a reinforced version of SHA-1 in the sense that we have 8-word states and a nonlinear message expansion. For SHA-256 and SHA-224 we have 32-bit words and 64 rounds. In the other versions (SHA-512, SHA-384, SHA-512/256, SHA-512/224) we have 64-bit words and 80 rounds. 

## SHA-2 Rounds
The round function can be observed in Figure 8.9.

![[sha2rounds.png]]

Since SHA-2 is built on Merkle-Damgård, length extension is a problem. However, at the moment there are no serious other threats.

## SHA-3
SHA-3 was made in a competition and based on the [sponge](sponge.md) technology. It comes after sha-2. 
