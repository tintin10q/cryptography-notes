Public key cryptography is a field inside the cryptography field that tries to deal with the problem of [establishing keys](keys establishment.md). 

What do we want from public key crypto:
- Set up a key remotely without the need for a secret channel.
- Authenticate an entity without having to share a secret key.
- Authenticate documents without the writers secret key. 
	- Cryptographic signatures (also called digital signature, electronic signature but we mean cryptographic signature.)

# Public Key Cryptography

In public key cryptography every entity has two keys. 

Prk = Private key
PK = Public key

Shemes:
![[Pasted image 20211109140646.png]]

The analogy:
![[anologypubliccrypto]]

There are loads of public crypto shemes but only a few are used. 

You can always get the private key from the public key but it is kind of hard. The creative challenge is coming up with public keys that are really hard to turn into private keys. 

Some ways to do are:

- [Modular aritmatic](modulararitmatic.md)


Public key cryptography is currently threatenet by [quantum computers](quantum computers.md)





