---
title Subsitution-permutation networks
author: Quinten 
date: \today
---

The oldest block ciphers were Substitution-permutation networks. 

![Substitution permutation networks](spn.jpeg)

These are a type of [block cipher](block.md) that achieve the diffusion and confusion goal by alternating two types of transformations: Substitution and Transportation. [DES](des.md) is an example of a cipher designed in this way.

## Substitution Layer
Substitution breaks the bits into small groups of any fixed size. Then it applies substitution to all these groups. This means replacing the whole group with another value according to a carefully constructed lookup table. These lookup tables are called **S-boxes**. Sometimes different s-boxes are used for different group positions but modern block ciphers apply the same s-box to all positions. The S boxes must satisfy non-linearity and diffusion criteria. 

- Non linearity criteras deals with the complexity of algebraic description of the S-box and the difficulty to pedict the output of the S-box if only part of the input is known. This is like how we could use a matrix to defeat [LFSRs](lfsr.md). Those kind of things should not be possible if you have good non-linearity. S-Boxes are reversable. 
- Diffusion criteria deal with the dependence of output bits on the input bits. You want to have each output bit depend on many of the input bits. This is were the security comes from because we want the property were if you change a small bit of the input you get a very different output.

## Permutatation
The permutation layer moves bits from one byte to different bytes or from groups to different groups. This is a non reversable process and should not be confused with invertable transfromation so that is why they call it transposition. This is also called a **p-box**.

The idea  is that the bits are divided into group. You then substitude all the group for another group with a lookup table and then you move all the bits around for the next round of substitution. Repeat. 

The alternation of substitution and transposition should ensure that each bit of the output depends on a complicated way of all the input bits, if enough rounds are taken.

## The Key

How does the key play? You can either make the key influence the s-boxes. In modern block ciphers we have another layer besides the s box and p box which adds (bitwise) a round key to the current result. The round keys are derived from the cipher key by means of a so-called key schedule.  

