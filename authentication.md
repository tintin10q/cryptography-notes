---
title: authentication
author: Quinten Cabo s1027427
date: vr 29 okt 2021
---

# What is authentication?
When [Alice](people.md) sends a message to [Bob](people.md), it is not only important to her that no one else (in particular that nasty [Eve](people.md) can read the message, but also that Bob gets the message she sent, and not something else. Similarly, when Bob receives a message from “Alice”, he wants to be sure that the message is indeed from Alice. All this is gathered under the term authentication.  

Authentication answers the question: "Is someone who they say they are?"  

## Authentication Attacks . 
What can go wrong without authentication?
- Sending a fake message. How do you know if the message "Please transfer 100000 euro to Eves account" really came from Alice. Some sort of signature is needed. 
-  If Eve intercepts a message that does something she could send it again and make something happen again while this was not the intention of the sender. For instance she could make a money transfer happen 100 times. Another example of a replay attack is recording someones voice for a system that uses voice recordings. This is called a **Replay attack**.
- If Alice has some sort of key then there must be some sort of way to verify it is really Alice that uses this key. If the key gets stolen than how can we know it was Alice. 

We can do authentication with signatures. You can have signatures by verifying public keys and by having a shared private key. If you are talking about public key signatures you call it signatures and with a shared private key you use a [MAC](mac.md) function (message authentication code).  We didn't get to public keys yet so MACs for now. 

You can verify yourself if you have a shared key by sending the tag of your message with the message to the receiver that also has the key. The receiver can then compute the tag of the message as well as if it is the same then you know the message cam from the person who has the key. You can only compute the tag with key trough the MAC function. This does not help against replay attacks. You protect against replay attack by including a counter in the message. This counter is then also kept by Bob and incremented every time to the counter that Alice send (if it is higher than the previous counter) if the tag verifies correctly. You can verify with the VFY function. 

If the tag is correct and the counter is higher Bob can accept the message and increase the counter to the counter to the new number that Alice send. Otherwise Bob rejects the message. 

Keeping a counter means Bob becomes statefull because Bob has to keep track of the counter somehow. 

## Unforgeability game
The adversary can make a certain amount of MAC requests M i to receive tags T i . It can then make a certain amount of forgery attempts (M_i , T_i ) in such a way that a forgery attempt never repeats an older MAC request. The adversary “wins” if the verification oracle every returns OK. 

## Freshness 
If Bob wants freshness then Bob can send a challenge to Alice (with domain separation?) that Alice can only solve by sending  the mac of it back. No Alice sends back the message the mac of the message the mac of the challenge and a counter. If all these things are correct then we have authentication with freshness that is resistant against freshness attacks.  