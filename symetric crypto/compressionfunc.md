---
title: compressionfunc
author: Quinten Cabo s1027427
date: za 30 okt 2021
---

The Davies-Meyer compression function uses a block cipher $B$ inside, and compresses a chaining value $CV_i$ and a message block $M_i$ as:

$CV_{i+1} = B_{M_i}(CV_i) ⊕ CV_i$ .

So the next chaining value is the output of the block cipher with part of the message as a key and then the current chaining value xor with the current chaining value.

We call the addition of CV_i at the end a feedforward. The feedforward is present to prevent collisions. Without the feed-forward, the compression operation is reversible; if you know the output of the compression function and the block of data being hashed, you could compute the input to the compression function.

Indeed, as we mentioned in Section 8.2.2, the Merkle-Damgård mode preserves collision resistance, but this is only meaningful if the underlying compression function is collision resistant. If the block cipher B is assumed to be an ideal cipher, one can prove that one requires at least 2 n/2 evaluations of Davies-Meyer to obtain a collision. An ideal cipher is one that is chosen uniformly from the set of all block ciphers with the given parameters.   
