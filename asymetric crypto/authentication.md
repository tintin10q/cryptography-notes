How do you know Alice is the one that sends a public key. 

![[Pasted image 20211123144113.png]]

This is one way but this is bad because you have to send a. Directly.

> Completeness 
> If the prover knows the secret and prover and verifier run the protocaol as specified the protocol succeeds.

> Soundess
> If the prover does not the secret the protocol will only succeed with negiable.

This one is better

![[Pasted image 20211123144817.png]]

But the problem is Eve can first calculate s and then a V that will work. 

So you ask for 2 things. This is Caum Evertse van de graaf ceg protocol. A so called zero knoledge proof of knowledge. A zero knowledge proof is when you want to prove something to someone but you leak no other information then that the statement is indeed true. Alice proves that she knows a to Bob who has A.

![[Pasted image 20211123145314.png]]

So you first commit to a value and then you have to do something based on that commitment. But we don't want you to leak the private key.

The problem is that Eve can just guess if the challenge will be 0 or 1. It turns out that if Eve guesses right that she can win. There are only two challenges so ..... just make 3 guesses. So this is complete but not really sound because eve success is 0.5 .

So lets just repeat this a lot of times then success probability is $n^{-1}$ . You can do this in parallel but still. Only if everything is correct you know its right. 

This is the metaphor.

![[Pasted image 20211123150040.png]]

If she doesn't know how to open the door she is very lucky if she comes out the right way every time. 

However, this takes a lot effort. So simple solution just take a c from the group instead of just 1 or 0. 

![[Pasted image 20211123150751.png]]

v has to be random every time. 

This is sound and complete.

![[Pasted image 20211123151047.png]]

## Zero knowledge.
This means that Bob or Eve learns nothing from the protocol except that what is proven. This is formalized by the notions of transcript and simulator. 

Transcript is 

The point is that 
