# Eulers totent $\varphi$ function
This function $\varphi(n)$ computes the order of a group that has a set of number coprime to n. 

So if we have 9:
- $\gcd(9,1) = 1$
- $\gcd(9,2) = 1$
- $\gcd(9,3) = 3$
- $\gcd(9,4) = 1$
- $\gcd(9,5) = 1$
- $\gcd(9,6) = 6$
- $\gcd(9,7) = 1$
- $\gcd(9,8) = 1$

So the numbers that are coprime are $\set{1,2,4,5,7,8}$. The order of this set is 6. This means $\varphi(9) = 6$. 

How can we generalize this?

There are 3 cases.
- $n$ is prime. Then $\varphi(n) = n-1$. 
	- All numbers lower are coprime. 
- $n = a * b$ where $a$ and $b$ are coprime. Then $\varphi(n) = \varphi(a) * \varphi(b)$
- $n$ is a prime power then $\varphi(n)$ can be written as $\varphi(p^k)$ with p prime. Then 
	- $\varphi(p^k) = \varphi(p)*p^{k-1} = (p -1)*p^{k-1}$

So lets try this for 9. We can see that 9 is a prime power $3^2$. So $\varphi(9) = \varphi(3^2) = (3-1)*3^{2-1} = 2*3^1 = 2*3 =6$

# RSA
We have the public key and the private key:
- Public key is (n,e)
	- n is p * q with p and q being large primes. 
	- e is coprime to n. So $e = \gcd(\varphi(n),e) = 1$. 
- Private key is (n,d)
	- n is p * q with p and q being large primes. 
	- d is $e*d \equiv 1 \mod \upvarphi(n)$ which means $d = e^{-1} \mod \varphi(n)$ 
p and q are secret. This makes it hard to calculate $\varphi(n)$.  d is also secret. 

Then you can do:

![[Pasted image 20220116150522.png]]

This is textbook rsa though so you have to do more. 

So if Bob wants to send a message to Alice. Bob only has to exponenciate with d to get the message back. So e and d exponenciation mod n are eachothers inverses. The message has to be an integer in the set of the numbers coprime to n. But it doesn't because even if it is not we get the m back.

So we have: 
Why is $y = x^e \mod n$ when $x = y^d \mod n$ ?
1. So we can substitute one. 
2. $y^d \mod n = (x^e)^d \mod n$ 
3. $(x^e)^d \mod n = x^{ed} \mod n$ 
4. $x^{ed} \mod n= x^{ed \mod \varphi(n)} \mod n$ because of Euler. 
5. $x^{ed \mod \varphi(d)} \mod n= x^1 \mod n$ by definition of d. 
6. $x^1 \mod n= x \mod n$ 



