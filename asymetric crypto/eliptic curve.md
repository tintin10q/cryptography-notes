# Elliptic curve 
Because the required numbers for modular exponentiation got too large they switched to additions of points on an elliptic curve.

An elliptic curve is is a set of points from a [[field]] that satisfy:

$y^2 = x^3 + ax + b$

If a point is is on the curve the above must hold.

a and b are domain parameters. 

You consider all points in existence but you limit it to the points in the [[field]] by doing modulo p. 

So it is more like:

$y^2~mod~p = x^3 + ax + b~mod~p$

All these operations are in the field! This means that all the operations are mod p. Also division is mod p. Division in a field is actually multiplying by multiplicative inverse, see [[finding the modulo inverse]]. 

This is called the (short) Weierstrass equation  
All elliptic curves over $\mathbb{F}_p$ can be represented this way.

There is one point that is always on the curve. This is $\mathcal{O}$. This is a point at infinity. It does not satisfy the Weierstrass equation. 

# How many points are on the curve?

## How many possible points are there?

If you take $\mathbb(F)_20$ then x and y can both take 20 different values. This means there are $20 * 20 = 400$ possible elements (points) on the elliptic curve. 

## So how many of those are actually on the curve?

There seems to be no quick way of calculating this. Basically you fill in the numbers in the formula and if its ok its ok if its not ok its not ok what do you expect. 

So remember the formula is: 

$y^2 \mod p = x^3 + ax + b\mod{p}$

Statistics actually tells us that you can expect $\frac{1}{p}$ points to be on the curve. So because the number of possibilities is $p*p$  you can expect there to be around $p$ points on the curve. Not exactly p though that is apparently important. 

So you expect about p. But there is bounds on this. The Hasse Theorem tells us that for an elliptic curve over $\mathbb{F}_p: \#\mathcal(E) = p + 1 + t$ with $-2\sqrt{p} \leq t \leq 2\sqrt{p}$. The plus one is there because the element at infinity and then the real number max  $2\sqrt{p}$ more or less. So relatively its a small difference from p but absolutely it can be big because the root of a large number is still a large number.

# Symmetry
Because the underlying theory of the elliptic curve is [[fields]] which underlying theory is [[rings]] which are mostly 2 [[groups]] together without an inverse. The point is the underlying theory of the elliptic curve is basically groups. 

This means there is some symmetry that is being modeled in the group and this is carried forth in the curve.  We can see this if we look at the elliptic curve that is actually infinite. 

![[Pasted image 20211218161747.png]]

This is: $y^2 = x^3 + ax + b$ without the mod. 

With mod it looks more like this: 

![[eliptic curve with mod.png]]

The above is a different curve however. These curves are also not from a prime field they are just feeding the continues x into the formula. Below there is a real example of a curve. This only has integers on it!

You can see that the curve is symmetrical over the x as. You can fold the top side of the x on the other side of the x and the line would lay on top of each other. This is the symmetry in the group.

The reason for this symmetry is that the equation that gives the curve has $y^2 =$ this means that if 12 is on the curve that -12 is also on the curve (because $(-12)^2 = 12^2$).  

# Elliptic curve group
We represent all the points on the elliptic curve as a $\mathcal{E}$.

## Point at infinity 
This set contains one point at infinity as well. The point is in the direction of the y-axis. It is called $\mathcal{O}$. This is the neutral element. It is not on the curve but we still include it. 

We need to have this point at infinity to be able to approach it I think. 

# Addition on an elliptic curve

Addition of points on an elliptic curve is not trivial. It can be understood why by remembering symmetry. Symmetry means that if you do an operation that the outcome of the operation must be in the same set or hold the same rules or look the same.

**So a if you add two points of an elliptic curve the outcome of the operation must also be on the elliptic curve!** This is why the addition is defined in such a way to make sure this happens. This is why the addition is not trivial because elliptic curves are not trivial but the result of the addition has to be on the curve and also in a symmetric way. 

# How do you add two points on an elliptic curve?
You pick two points on the curve you want to add. These points are P and Q. Then you [draw a line trough Q and P](computing slope of linear line.md). Because P and Q are on the elliptic curve it is guaranteed that one point on the line between P and Q crosses the elliptic curve again in another point R. Then you mirror this point R on the x-as. This point will also be on the elliptic curve. This point this is the answer to adding points on an elliptic curve. 

So this is the steps:
1. Pick the points you want to add. P and Q
2. Create a line through P and Q.
3. Find the third point where the line crosses the curve. This is -R.
4. Mirror this point over the x to get the result. This is R. 

![[Pasted image 20211217020359.png]]

In the above the blue line is step two and the red line is step 4. 

This is/gives us the group law. 
This addition works because the following holds:

## Group law
I think this is for info but 
The group law is defined because of the following property.

>**Definition of the group law**
> Let P, Q, R $\in \mathcal{E}$ : P+Q+R= $\mathcal{O}$ iif they are on a straight line.
>
> If they are on a straight line $\mathcal{O}$ is at infinity in the direction of the y-axis

The idea is that you take 3 points on the elliptic curve. Then saying P + Q + R is saying that they are on a straight line.

The idea is that we have this point at infinity which is the identity element of the elliptic curve. 

Here are some examples of this in action and special cases.

![[Pasted image 20211217024633.png]]

# Properties of $\mathcal{E}$
- Closure : A strait line intersecting the curve in 2 points on the curve will intersect in a 3rd point. 
- Associative holds but proof is not trivial
- Identity - the point at infinity $mathcal{O}$
- Inverse If P = (x,y) then -P = (x, -y) we saw this 
- Commutative: roles of P and Q in P + Q are symmetric. A line trough P and Q is also a line trough Q and P

An elliptic curve with this addition law is an abelian group. On any field. Also infinite ones.

# Algorithm to add points

Remember each operation you do is modulo $p$ from $\mathbb{F}_p$. Addition, subtraction and multiplication are all modulo p. Division requires  multiplication with the inverse. This requires [[finding the modulo inverse]].

## Long version
This is a longer version with a bit more explanation:

If $P = -Q$ So P is the inverse of Q then $Q+P = \mathcal{O}$ and your done.

Otherwise we need to get the slope ($\lambda$) to continue.

If $x_p \neq x_q$ then you can [[computing slope of linear line]] with $\lambda = \frac{y_p-y_q}{x_p-x_q}$. (difference of y / difference between x)

If $P = Q$ than we have one point need the slope of the tangent. You can calculate this with: $\lambda = \frac{3(x_p)^2+a}{2y_p}$.

Keep in mind that all this in $\mathbb{F}_p$. So you have to do everything modulo P. This means that you first calculate the top of the division than the bottom and then to do the division you  multiplying by the inverse of the bottom part. 

The inverse only exists if for the integer x there is another integer y such that x*y = the neutral element. 

Now we have the slope. We can make the line formula.
$y = y_p + \lambda(x-x_p)$

This is a $y$ we can put this in the Weierstrass equation. 

$(y)^2 = x^3 + ax + b$

Then you get:

$(y_p + \lambda(x-x_p))^2 = x^3 + ax + b$

So apparently now: $x^2 = -\lambda^2$ this means:

$x_p + x_q + x_r = \lambda^2$

So this means:
$x_r = \lambda^2 - x_p - x_q$  
$y_r = \lambda(x_p - x_r)- y_p$

## Short version
We start with 2 points:
- $P = (x_p, y_p)$
- $Q = (x_q, y_q)$
And the point we want to find:
- $R = (x_r, y_r)$

If $P = -Q$ So P is the inverse of Q then $Q+P = \mathcal{O}$ and your done. So $R = (\mathcal{O})$.

Otherwise we move on and we need to find the slope of the line through P and Q ($\lambda$) now:

If $x_p \neq x_q$ then $\lambda = (y_p-y_q)/(x_p-x_q)$ or $\frac{y_p-y_q}{x_p-x_q}$

If $P = Q$ then  $\lambda = (3*(x_p)^2+a)/2*y_p$ or $\frac{3*(x_p)^2+a}{2*y_p}$

Then we can calculate the points of r like this:

$x_r = \lambda^2 - x_p - x_q$  
$y_r = \lambda(x_p - x_r)- y_p$

## Shorter version
We start with 2 points:
- $P = (x_p, y_p)$
- $Q = (x_q, y_q)$

And the target:
- $R = (x_r, R_r)$

$P + Q = R$

If $P = -Q$ then $Q+P = \mathcal{O}$ Done!

Elif $x_p \neq x_q$ then $\lambda = (y_p-y_q)/(x_p-x_q)$

Elif $P = Q$ then  $\lambda = (3*(x_p)^2+a/2*y_p$

Then:

$x_r = \lambda^2 - x_p - x_q$  

You have to use $x_r$ for $y_r$.

$y_r = \lambda(x_p - x_r)- y_p$

The formulas for $x_r$ and $y_r$ and $\lambda$ are given on a formula sheet. 

# Example

Here we have a curve with $F_{23}$.

![[Pasted image 20211218181127.png]]

- (9,5) is in this curve. So $(9,5) \in \mathcal{E}$
- $#\mathcal{E} = 24$ 23 points (x,y) that satisfy the W equation plus $\mathcal{O}$. You can't visualize $\mathcal{O}$ 

# Visualizing curves.

You can actually show the curves with something like desmos.com. Really great. Input the formula just works. 

So if you do $y^{2}= x^{3}+ax+b$ you get:

![[Pasted image 20211217033239.png]]

And then if you add mod:  $\operatorname{mod}\left(y^{2},p\right)= \operatorname{mod}\left(x^{3}+ax+b,p\right)$ you get:

![[eliptic curve with mod.png]]

We can generalize this to the group law of elliptic curves. k

# Extra

$y^2 = x^3 + ax + b$ is actually the equation in affine coordinates. Which I think is like the "normal" coordinate system. You can also have a "homogeneous" system where points are made out of 3 scalars. Finite curves are actually defined in this coordinate system and they represent a donut in this system but we can represent them in the affine system. See [[Projective plains]] for more info. It will also show where 
