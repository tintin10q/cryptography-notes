---
title: Padding
author: Quinten Cabo
date: vr 29 okt 2021 13:44
---

# Padding
We resolve messages that are not a multiple of b by using padding. Padding is when you add extra redundant information to a plaintext so that the result is the desired length. With cryptography is is usually done to add increase the length of plaintext to be a multiple of *b* bits for a [block cipher mode](blockmodes.md)

When doing padding you write it like this: A padding rule is  $pad_b$ that takes an arbitrary length message and makes it a multiple of *b*-bits. 

## Invertible padding 

Padding has to be invertible because after decryption you have to be able to undo the padding. If you can't undo the padding than you can't know if the cipher text was successfully decrypted. In other words the padding has to be [injective](https://simple.wikipedia.org/wiki/Injective_function)	

## Examples of padding rules for Block Ciphers 

A padding rule that does not work (not injective) is:

$pad_b : P \mapsto P ||0^{-|P| mod b}$ .

This keep adding 0 until the length of the block is multiple of b (using $mod$). This does not  work because after decryption you would not know how many 0 to remove. The message might have have been: "Give me $100". Real messages are with only 1 and 0 but the same applies. 

A simple padding rule that does work is:

$pad_b : P \mapsto P ||1||0^{-|P|-1 mod b}$ .

This rule starts the padding by always adding one 1 and then keeps adding 0 until you reach the desired length (multiple of $b$ ). In the worst case scenario your message was just one bit shy of being a multiple of $b$ and now receives a whole block of 0 at the end. 
With the inverse of this rule you just remove all trailing zeros and a single 1 to find the message without padding. This is the padding method that is generally used for [block cipher](block.md) encryption but there are many padding rules for different needs. 

# Why we do padding
After we do the padding we can support encryption with [block ciphers](block.md) with messages that are not a multiple of a block size because we just turn the message into a multiple of a block size. Sadly this does not give the desired properties of a wide block cipher because the blocks are still mostly encrypted separately. 
