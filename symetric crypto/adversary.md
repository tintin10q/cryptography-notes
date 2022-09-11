---
title: Adversary
author: Quinten Cabo s1027427
date: \today
---

# Types of adversaries

When designing a [cryptographic primitives](claim.md) you have to consider against what you want to protect. There are different  adversaries with different power levels you can consider. 

The adversary might know nothing about the plain text or might know a lot about the plain text. The adversary often knows that the input was was “meaningful” text. Having such information is a necessary condition in order to mount an attack in the first place.

Another typical case is that [$SC_K$](letters.md) is used to encrypt a message M and [Eve](people.md) knows a small portion of the message M . For example, M is an official letter with some standard heading. In this case, we speak of a known plaintext adversary. A known plaintext adversary can automate exhaustive key search with a program that systematically runs over all key values and only return those that have the standard heading in the deciphered cipher text. A secure [stream cipher](stream.md) generates seemingly independent random key streams ([Z](letters.md)) for different keys. This means applying with a wrong key K will result in a seemingly random message. If the standard heading is longer then the state of the stream cipher you can try to look at the difference between the result of the output bits and the heading to work back find the key. The program will only return one key guess: the correct one. 

Eve’s knowledge about the message may be more subtle. She may only know that it is ASCII encoded English text, or just know it is the letter when she sees it. Here one typically speaks of a **ciphertext-only adversary**. In these cases finding the key K by exhaustive key search is still possible if the message is long enough, but is trickier to implement. 

Eve’s knowledge about the message may likewise be much more. Eve may be able to choose a message herself and receive the corresponding cipher text. Clearly, this will give her knowledge of a key stream Z corresponding to one diversifier, but we would like that it reveals nothing about key streams from different diversifiers. In general, when evaluating a cipher, one assumes the most powerful adversary model. If it is secure in that model, it is also secure in many weaker models. 

# When does Eve have success?

If Eve manages to recover the key (key recovery attack) then all is lost [because the strength of a cipher can only rely on the secrecy of the key](kerchhoff.md). With the key Eve can compute any key stream for any diversifier or decrypt any block cipher because Eve has the key. This is success/valid attack.

This is not the only way for Eve to have success. If Eve, after having learned many (D, Z) pairs, can predict (keystream prediction attack) part of a new key stream for a specific D' then Eve can recover the plaintext were Alice decides to use this specific D'. Alice would be vulnerable here as she might have not used this D' before and would not consider it insecure to use. This is also success but the key recovery is kind of more of a success/valid attack for Eve. 

A key recovery allows Eve to predict a keystream but the opposite is not true. This means that a key recovery attack is stronger than a keystream prediction attack.

What if you can do a statistical analysis of the cipher text and find that the number of 1s in the cipher text is much higher then 50. This does not give Eve access to the plaintext or the key. Is this still a success/valid attack? 

We want to $SC_K$ to look like a function that responds randomly for each input. One such function is the theoretical function the [random oracle](randomoracle.md).  

we consider adversary Eve to be successful if she finds an attack that has a success probability that is higher than the one in the security claim that comes with
the cryptographic primitive.

This can be modeled with the [advantage game](advantage.md) .

# Adversarial complexity

There are two types of information that [$A$](people.md) might learn about its oracle. 

## Online Queries 

Online queries are queries were $A$ queries its oracle. This is either a stream cipher or a random oracle. These types of queries are called online queries. 

This is called online because in the real world these queries correspond to conversations with the keyed instance of $SC_K$ which you do not have in your possession. Thus you have to talk online. This also brings limits to how often you can query online as there might be rate limits or max log in attempts and you also can't query really fast as the query usually to travel some distance back and forth. 

The queries are stored in a query history $Q_d$ . It is called the online or data complexity.

## Offline Queries

The second source of information of $A$ comes from evaluations of $SC$ for arbitrarily chosen keys. For this, $A$ need does not have to be connected with its oracle. Because of the [kerckhoff principle](kerckhoff.md) the specification of $SC$ is known. This means A can implement it and run it offline. For this reason, these evaluations are called offline evaluations. They are stored in a query history $Q_c$ . These types of queries are faster then online queries because you can run the cipher yourself. 

What matters for $Q_c$ is the number of keystream bits, and we define by $|Q_c|$ the number of keystream bits in $Q_c$ . It is called the offline or computational complexity.

In practice, measuring $|Q_c|$ is subtle. The reason for this is that it, intuitively, measures the maximum number of evaluations of $SC$ that adversary $A$ can compute offline in a certain amount of time. 
A typical normalization that is often considered, is that generating one keystream bit takes one unit of time, but it may be that the adversary can use its time more efficiently to compute more than $|Q_c|$ keystream bits in time $|Q_c|$ . 

On the other side, $|Q_c|$ not only covers function evaluations, but also other computations that are relevant to the scheme but cannot be expressed as a function of the number of evaluations of SC. For example, to distinguish you may need to do linear algebra computations to make up its decision based on the gathered data but this is not a query. 

These two inaccuracies in the time parameter are generally neglected. One typically assumes that time is scaled and normalized and that $|Q_c|$ time allows for the generation of $|Q_c|$ keystream bits of $SC$.