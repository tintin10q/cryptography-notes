# Snorr autentication
Snorr autentication is complete no conditions.
Snorr autentication is sound if DL is hard (and you don't repeat v). 
Snorr autentication is (honest verifier) zero knolege if we can make a similator to make transcript that you can't distinguish then its zero knolege. The simulator just makes a c and r and only then a $V = g^r * A^c$. It is honest verifier zero knolege because an non honest verifier can pick a challenge in a non random way and then you can distingish it. If the verifier always picks 0 or 1 well.

![[Pasted image 20220115112414.png]]

Because this protocol is interactive you can not show the transcript to your friends and prove that Alice is who she says she is again. The point of the time involved is what makes it work here. 

## Interactive

But we would actually like this to be the case can we make the protocol non interactive? That we can show the transcript to anyone and it would always be proven while still having completeness soundness but not (honest verifier) zero knolege because the response will be the proof. This is a signature.

We want to take Bob out of the picture and do a $\Sigma$ transform. Alice just sends one thing that works. We wanted before zero knolege that the transcript gives no proof so after its done it doesn't prove anything because Bob could just have made it himself they would say. Now we want the transcript to be the proof of something.

So we can do this with the fiat shamir transform. 

The idea is that you hash the challenge. This way you either have to reverse the hash or solve the hard problem because you can guess one but then you have to fix the other and if you fix the other you have to solve the one.

![[Pasted image 20220115120048.png]]

# Snorr signatures
A Snorr signature can be used to do message origin [[authentication]]

Alice wants to send a message m to Bob in such a way bob has some proof it is really coming from Alice. With symmetric this is easy you just compute the mac. If the message and mac don't match then you know the message did not come from something with the symmetric key. 

We can do a commit, challenge, response protocol. We call this $\Sigma$. 

Here we want the transcript to be the proof. You do this with yourself. 

![[Pasted image 20211123151623.png]]