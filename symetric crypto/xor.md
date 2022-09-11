---
title: XOR
author: Quinten Cabo s1027427
date: vr 29 okt 2021
---

# XOR operation

The xor operation is when you have two bits and you follow this truth table:

| Bit 1 | Bit 2 | Result |
| ----- | ----- | ------ |
| 0     | 0     | 0      | 
| 1     | 1     | 0      |
| 0     | 1     | 1      |
| 1     | 0     | 1      |

In short if the two bits are the same then the result is 0 if the bits are not the same the result is 1. This corresponds to the + operation.

$0+0=$ /
$0+1=$ /
$1+0=$ /
$1+1=0$ /

Of course $1 + 1 = 2$ but binary only has 2 number 1 and 0. Here the difference comes in between bitwise xor and carry xor. With bitwise xor we say $1+1=0$ and just call it a day and with carry xor $1+1=0$ but we have a carry for the next bit if there is any. Just like $19 + 2 = 20$ 9 + 2 = 0 but we carry the one so the 10 becomes 20.

In cryptography we always use bitwise XOR. This is a very fundamental operation/building block. 

