One problem used in public key crypto is modular aritmatic. Look at [math symbols first](mathsymbols.md)

![[mathsymbols]]

Z/nZ is a set  of positive integers smaller than n including 0.


# Modular addition

We can then do modular addition with numbers in this set and then the results will also be in the set. 

## Interesting properties 

![[Pasted image 20211109143955.png]]

# Modular multiplication

We can also do modular multiplication. The idea is that you multiply first by n and then subtract n again until you are lower then n. 

## Interesting properties 

![[Pasted image 20211109151937.png]]

# Writing it
You can write it in multiple ways:

- $a~mod~b$
- $a~\text{mod}~b$
- $a \mod b$
- $a \pmod b$
- $a \bmod b$
- $a ~\%~  b$

I feel like the \mod makes the most sense with the big space because it is sort of just looming there. You can really do it at any moment too. 

# Subtraction

With subtraction you have to imagine adding the modulo number again and again until you get between 0 and the modulo number. That is then the result. 

## Example
So $-20 \mod 11 = 2$
Because:
- -20 + 11 = -9 (not between 0 and 11 so add 11 again.)
- -9 + 11 = 2

Thats it.

# Division
Modular division is annoying but you need it for instance with calculating the slope when adding up two points on an [[eliptic curve]]. 

So modular division is impossible. But we can work around this by multiplying by the inverse of what you are trying to divide. 

So lets say you want to $\frac{34}{50}\mod61$.
To calculate this we do $34*50^{-1}\mod61$.

So how do we find $50^-1$? We have to do [[finding the modulo inverse]]. 

In this case the number that you use to mod is prime so we can easily find the inverse by using Fermat.  So $50^{-1} = 50^{61-2} = 50^{59}$. You can try to do this by doing square and multiply. See below.

So this is actually $50^{59}=17347234759768070944119244813919067382812500000000000000000000000000000000000000000000000000000000000$

Then we do this mod 61 its better to just do this right away. 

$50^{59}\mod 61 = 11$

So now we can do the division.

$\frac{34}{50}\mod61 = (34 * 11) \mod 61 = 8$

It seems like you do need the brackets around the multiplication. 

-----



| i   | e        | r                                      | a    |
| --- | -------- | -------------------------------------- | ---- |
| 1   | $50^1$   | 50                                     | 50   |
| 2   | $50^{2}$ | 50 $\times$ 50                         | 2500 |
| 4   | $50^{4}$ | 50 $\times$ 50 $\times$ 50 $\times$ 50 |      |

But this is actually just $2500*2500$ or $2500^2$

$50 * 50 = $

10 * 50 = 500
5 * 10 = 5
50 * 50 = 500
5 * 10 * 50 = 50*50
5*500 = 50*50

2*500 = 1000

3*500 + 1000 = 50*50
1*500 + 2000 = 50*50
50*50 = 2500

---

2500*2500 = 