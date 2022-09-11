
# Elliptic curve groups

If you have an [[eliptic curve]] than every point on the curve actually forms an elliptic curve group with it self. You get this group by adding a point on the curve to itself until you get to the point at infinity.

This looks like this:
$G \in \mathcal{E}$
- $i = 1 : G$
- $i = 2 : G + G$
- $i = 3 : G + G + G$
- $i = 4 : G + G + G + G$
- $i = 5 : G + G + G + G + G$
- $i = q : G + G + G + G~...~+ G = \mathcal{O}$

This is scalar multiplication. You call $[n]G$ the scalar multiplication of point $G$ by scalar $n$. So you add $G$ to itself $n$ times. So you write this like $[n]G$.

 At that point the cycle ends. So the order is $q > 0$ where $[q]G = \mathcal{O}$. 
 
The order of G ($\text{ord}(G)~\text{or}~\#G$)  is the smallest integer $q > 0$ such that  $[q]G = \mathcal{O}$ (the neutral element).

**The shared secret is the x-coordinate of the point on the elliptic curve**

**To get the shared secret you do scalar multiplication with your private key and the public key of the other party** 🪄

Basically if I send 2 and you send 4 we both land at 6. The magic is that the scalar multiplication does it.

The idea is that my private key is at index 2 and your private key is at index 4. If we then exchange our public keys mine also being at index 2 and yours also being at index 4. 

I do scalar multiplication [4]2 and you do [2]4 we both land at 6. I can not get your private key back though by knowing your public key.

## Discrete log elliptic curves

You take a $G \in \mathcal{E}$ and then:

> **Discrete log (DL) problem in $\mathcal{E}$**
> Let $G \in \mathcal{E}$ have order $q$. 
> Let $a \xleftarrow{\$} \mathbb{Z}/q\mathbb{Z}$
> Let $A \leftarrow [a]G$
> Now given $A$ determine $a$. 

For a good chosen elliptic curve this is hard.

![[Pasted image 20211218185057.png]]

So the private key is the index on the inner circle and the public key is the point on the elliptic curve.

# Domain parameters
We want a $\mathcal{E}$ with $\#\mathcal{E} = hq$ with q a large prime and $h \leq 10$. To find this is basically trail and error with educated guesses (Schoofs algoritm). 

These curves should have a point on them that generates a very large eliptic curve group.  

To ensure backdoor absence, choice of p, a, b in for the curve should be explainable and how you got them should be documented.

Then experts find a curve. If a good curve is found you get this:

> **ECC domain parameters**
> - The prime p 
> Generally, a prime power $p^n$ including p = 2
> - The curve parameter a and b
> - The generator G 
> The point on the curve that generates the cycle
> The order q of the generator. q is hard to calculate.
> The co-factor: h = $\#\mathcal{E}/q$

# Fast version of scalar multiply (double and add) 
Naively you might think that doing scalar multiplication takes n-1 elliptic curve point additions. So [n]G takes n -1 point additions. If this was the case it couldn't be used for crypto because the increase operation should be easy no matter the number of them. The algorithm is called **add and multiply**. You can go even faster by using homogeneous coordinates I think. 

The idea is the same as square and multiply where you reuse previous results. 

This is an example from the slides that calculates $[43]G$ with $G = (5,1) \in \mathcal{E}(\mathbb{F}_{23}) : y^2 = x^3 - x -4$

![[Pasted image 20211218230821.png]]

Here is speudocode for the algoritm:
![[Pasted image 20211218234137.png]]


# Applications
- Elgamal. Actually encrypt a point on the curve. Plaintext and ciphertext are points on the elliptic curve
- Schnorr signature. 
- ..
Its all the same really as before just the operation and what is the outer circle is different now. 