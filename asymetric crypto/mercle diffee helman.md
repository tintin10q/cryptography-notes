Mercle diffee helman is where you both have a private and public key with the cirlce. The private key is the inside of the circle and the public key is the outside of the circle. 

With deeffehellman discrete log has to be hard. Discrete log is when you have a (sub)group and you want to find the index. 

You have a group with has a max. This indicated by the number of the group. That number indicates where we cut of the numbers that are in the group otherwise the group would be infinite. So you write this like $((\mathbb{Z}/23\mathbb{Z},\text{x})\backslash\{0\})$ lets call it G. In this case the max is 23 this number is called **p**. To make sure all numbers stay inside this group we just modulo them. So if we have 24 then this is actually $24 \mod 23 = 1$ so we can kind of map all elements onto this group. p is pretty much always going to be prime. The number of elements in G is p-1 this is the order which we call q. 

Now we take one of the numbers in this group and because p is prime that number will also be a group with an operation! It is hard to predict which elements of G will be in this subgroup. The number we take is called the generator or more often **g**.  

Now we can generate the subgroup by for instance taking g = 3. We now generate the cycle by doing: 
3 = [3, 9, 4, 12, 13, 16, 2, 6, 18, 8, 1]

| i | calculation | 
|---|-------------|
| 0 | $3^0 \mod 23 =1$       |
| 1 | $3^1  \mod 23 = 3$     |
| 2 | $3^2  \mod 23 = 9$     |
| 3 | $3^3  \mod 23 = 4$     |
| 4 | $3^4  \mod 23 = 12$    |
| 5 | $3^5  \mod 23 = 13$    |
| 6 | $3^6 =  \mod 23 16$    |
| 7 | $3^7  \mod 23 = 2$     |
| 8 | $3^8  \mod 23 = 6$     |
| 9 | $3^9  \mod 23 = 18$    |
| 10 | $3^{10}  \mod 23 = 8$ |
| 11 | $3^{11}  \mod 23 = 1$ |

Now the multiplication is easy to do with square and multiply basically if you have $3^4 = 3 * 3 * 3 * 3 = 9 * 9 = 3^2 * 3^2$ So if you calculated a square you don't have to do it again. Discrete log is finding out what I a certain thing is so: $6 = 3^x \mod 23$ This is discrete log and there is no algoritm for it. But the otherway does work. 

So we have chosen p, g and q. Now Alice and Bob both pick an index or i on the inner cicle. Alice picks 8 Bob picks 9. We call these $a$ and $b$. These are their private keys. Now we calculate their public key by doing $g^a = 3^8 \mod 23 = 6$. Bob does the same $g^b = 3^9 \mod 23 =18$. The public keys we call $A$ and $B$. So now they have:

a = 8, A = 6 
b = 9, B = 18

They can share A and B all around. The trick is to arrive at a shared secret. They have to send their public keys to eachother or publish somewhere.

Then Bob does  : $A^b \mod p = 6^9 \mod 23 = 16$ 
Then Alice does: $B^a \mod p = 18^8 \mod 23 = 16$

The same number!!! But from the A or the B you can not find the a or the b. Its a miracle. Ok not really because the world of math knows no luck or coincidence. It actually makes a lot of sense if you look at the simple exponentation rule: $(A^b)^a = A^ba$. So we can do:

$$A^b = (g^a)^b = g^{ab} = g^{ba} = (g^b)^a=B^a$$
And thats the trick. 

Now who says that you can't find out the others private secret from this shared secret? This is not the same as the discrete log problem. This is called **(computational) Diffie-Hellman hardness  assumption (CDH)**.  

> CDH seems as hard as discrete log problem but no proof of this

So if discrete log is broken diffee helman is broken but if diffe helman is broken than that does not mean discrete log is broken. If CDH is broken then diffee helman is broken but maybe DL is not. Who knows. After you have the shared secret you need to turn it into bitstring which you hash or xof and then you have a shared secret.  With that you can do encryption. But still be carefull of the man in the middle its hard to avoid. 

> **Computational hardness assumption**
> Let s be the security strength
> A problem is computationally hard to solve with respect to s, if for all algorithms that solve it with computational complexity N and success probability p, it holds that $N/p \geq 2^s$






However you don't know for sure you are talking with Alice if you have her public key there can always be a man in the middle. You can even do auth do with public private keys with Snorr pretty cool.


Whats really going on? Whats really really going on? Whats really really really going on? Actually you are moving trough the layers of abstractions. Bottom up is always better because you know where you came from instead of heading from the light into the black void.
