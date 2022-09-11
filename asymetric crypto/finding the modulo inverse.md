A lot of operations need the modulo inverse. 

For instance multiplicative division see [[modulararitmatic]].

How do you get it?

# Fermat's little theorem
If your modulo is prime then you can use this shortcut!

So if you have $x \mod p$ and p is prime you can find the inverse of x by doing $x^{-1} = x^{p-2}$. 

Most modulo will be prime because I think cyclic groups need primes as their modulo and we only threat prime fields and not prime powers.

## Example
Find the multiplicative inverse of $4 \mod 11$. 11 is prime so we can use Fermat. 

In this case the multiplicative inverse is $4^{11-2} = 262144$. 

Now we have to mod this again I think to get it back in range.

So the final number is $262144 \mod 11 = 3$.

# Extended euclidean algoritm
The extended Euclidean algorithm returns a pair $x, y \in Z$ with $n \cdot x + m \cdot y = \text{gcd}(n, m)$

The [Euclidean algorithm](https://en.wikipedia.org/wiki/Euclidean_algorithm "Euclidean algorithm") determines the greatest common divisor (gcd) of two integers, say a and m. If a has a multiplicative inverse modulo m, this gcd must be 1. The last of several equations produced by the algorithm may be solved for this gcd. Then, using a method called "back substitution", an expression connecting the original parameters and this gcd can be obtained.

## Example

We want $6x + 23y = gcd(6,23)$

gcd($6$,$23$) is $1$ because $23$ is prime. This means we want $6x + 23y = 1$. 

Express biggest one in terms of smaller one like bigger_one = smaller_one * something + something.

$23 = 6 * 3 + 5$

Now express smaller_one in terms of what you plussed like smaller_one = plussed * something + something.

$6 = 5 * 1 + 1$

Now express what you plussed before in what you plussed now. 

$1 = 1*1 + 0$

So we have:

- $23 = 6 * 3 + 5$
- $6 = 5 * 1 + 1$
- $1 = 1*1 + 0$

Now switch = and + and then change + into - so this gives:

- $23 - 6 * 3 = 5$
- $6 - 5 * 1 = 1$
- $1 - 1*1 = 0$

Then take gcd and work towards ax + by = gcd(a,b) in this case 6x + 23y = 1

Take from the last list of things:

- $1 =$
- $6 - 5 * 1 =$
- $6 - 5 =$
- $6 - (23 - 6 * 3) =$
- $- (23 - 6 * 3) + 6 =$
- $(-1 * 23 -1*(- 6 * 3)) + 6 =$
- $(-23 -1*(- 6 * 3)) + 6 =$
- $(-23 + (-1 * - 6 * 3)) + 6 =$
- $(-23 + (6 * 3)) + 6 =$
- $(-23 + 6 * 3) + 6 =$
- $-23 + 6 * 3 + 6 =$
- $-23 + 6 * 4 =$
- $23*-1 + 6 * 4 = 1$

This leaves us with $23 * -1 + 6 * 4 = 1$

$x = -1, y = 4$

This means the inverse of $6 mod 23 = 4$