---
title: Mac
author: Quinten Cabo s1027427
date: \today
---


Encryption does not offer [data integrity](goals.md) and it was never meant to. Change a bit blabla. If you want that then you have to compute a cryptographic checksum and send it with the message. Then when Bob decrypts the message he can verify that it is the message that Alice actually send if the checksum is correct. These cuecksums are called a **tag** or a **mac**. 

A [wide block cipher](block.md) would be able to deliver both integeraty and confidenciality. 
