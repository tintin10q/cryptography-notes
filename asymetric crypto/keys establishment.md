Key establishment is the problem of how Alice and Bob can securely establish a shared secret key with each other.

How do Bob and Alice establish secret keys?

- You can physically meet and exchange the key. You can do unique key pairs. For example business cards and then you combine them or USB stick. The advantage of paper is that you don't have to [trust software](Trust in technology.md). But what if you can't meet physically?
- Alice and Bob can use a shared friend. [Trusted Third Party](trusted third party.md).  Alice and Bob both trust this TTP. However now the TTP has the key aswell and can you really trust the TTP.  
- You can use temper evident physically uncloneable messages. For example temper evident uncloneable envelopes You can not open the envelopes without leaving traces. The envelopes should also be uncloneable so you can't have other envelopes from an opened one. You could put a money bill on the envelope. The idea here is that you **know** if someone else knows the key. More general you know that someone read the message if no one did you can use the key.

How do we do this in practice:

Peer-to-peer networks with participants coming and going. (whatsapp and stuff) 
		- Every new contact requires a key. 
		- Can be done with ttp so each users shares a key with  tpp but in peer to peer we dont want tpp
	
We could have one master key but if that leaks all hell is on earth. Having each device its own key is really hard to do. 

Some examples of key establishment. 

![[Pasted image 20211109140301.png]]

However all these things suck or are non optimal for one way of another. This is where [public key cryptography](publickeycrypto.md) comes to the rescue. 