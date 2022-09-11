# Protective plains 
$y^2 = x^3 + ax + b$ is actually the equation in affine coordinates. Which I think is like the "normal" coordinate system. You can also have a "homogeneous" system where points are made out of 3 scalars. Finite curves are actually defined in this coordinate system but we can represent them in the affine system.

The actual Weierstrass equation is 

$$Y^2Z = X^3 + aXZ^2+bZ^3$$

They are capitals because coordinates on the homogeneous system are weird. Basically you take a 2d plain you write these like $\mathbb{P}^2$. Its $^2$ because you also have homogeneous lines. Then the middle of the plain is (0,0,0). This is actually not a point on the plain. Then you can fill in the values for (X,Y,Z). 

First take this step. 

The idea is that X and Y say which direction you want to go in from the center and Z says how far you want to go in that direction. 
So if I understand correctly if you have A = (3,3,3) and B = (3,3,4) then B is a point in the same direction from (0,0,0) as A but A little bit further along. So A is in a sense a bit behind B. Because the smaller Z the further away you are from the center.

Now for real the previous part is not how it works.

Now try to imagine that $(0,0,0)$ is actually at the center of a ball. Now the $Z$ is now needed to give a point in the ball. If you have $D = (4,4,2)$ and $E = (6,6,6)$  then $D$ is actually further away from you (standing at the center) than $E$ because the smaller Z the further away you are.. now if you have $A = (3,3,3)$ and $B = (4,4,4)$ then $B$ is further away from the center. But $A$ is also actually behind $B$ in the ball if you would look from the center (because the smaller the Z the further away from the center you are). In this case if you would look from the center you could only see $B$ because $A$ would be exactly behind it. So $B$ is blocking $A$ from view because it is in front of it. 

Now you can actually have all the points that are on the same line. So you can say that $(4,4,4)$ and $(1,1,1)$ are on the same line because $(1,1,1)$ would block $(4,4,4)$ if you would look at it from the center. So we can formalize that with $\lambda$.  We can say two points are on the same line if you can get from one point to the other point by multiplying all numbers of the point by the same scalar. This is that formally:

$$(X_1, Y_1, Z_1) \sim (X_2,Y_2,Z_2)\iff \exists \lambda \in K : (X_1, Y_1, Z_1) = (\lambda*X_2, \lambda*Y_2, \lambda*Z_2)$$ 
Where $K$ is some $\mathbb{P}^2$ without $(0,0,0)$.

$\sim$ is the symbol for the same line relation. 
$\iff$ is if and only if. 
$\exists$ is Exists.
$\in$ is in.

So now we can actually address all the points one one line. We are going to say that if $(X_1, Y_1, Z_1) \sim (X_2,Y_2,Z_2)$ then they are equivalent. It is a different point but they are also equivalent. So $(2,2,2) \sim (6,6,6) =$ True because you can multiply each number in the first point with 3 to get the second point. So in this case $\lambda = 3$.

The next syntax we introduce is for addressing all the points that are in a certain line with each other. We write this as $(X:Y:Z)$ so $(2,2,2)$ and $(6,6,6)$ are in the same $(X:Y:Z)$. I think that this is sort of why we call the equivalent because $(2,2,2)$ is in $(6:6:6)$ and $(6,6,6)$ is in $(2:2:2)$.  

We call all the points in a $(X:Y:Z)$ a class.

If $Z \neq 0$ we can write a point in the homogeneous system as a point in the alpine system by doing $(x,y) = (X \times Z^{-1}, Y \times Z^{-1})$. Neat.

So now we can say that the classes that have $Z = 0$ are at infinity. So everything in classes with $(X:Y:0)$ are at infinity. 

Now lets consider these relationship classes points. So we move from $(X,Y,Z)$ to $(X:Y:Z)$ as the points in the class are sort of similar and we only consider the classes. We can now say that all the points with $Z=0$ are at infinity. This creates a line at infinity. These points we can't transfer to the alpine plain.

So now we know that we can substitute any $(x,y)$ with $(X/Z,Y/Z)$ 

So we want to fill in a Z in $y^2 = x^3 + ax + b$ we can't do Z = 0 because we can't fill in a point at infinity. So instead we do $Z^3$.

So if you fill that in you apparently get (we already remove a Z I think): 

$$Y^2Z = X^3 + aXZ^2+ bZ^3$$

In this equation all terms have the same degree (3) that is why we these (X:Y:Z) are called homogeneous.

No the intersection of curve with line at infinity Z=0 is (0:1:0)

So (0:1:0) is the point at infinity that is on the elliptic curve. (no matter a and b).

So one advantage is that the inverse of these projected points is $-(X:Y:Z) =(X:-Y:Z)$ so computing with these you can avoid finding multiplicative inverses.

It works like this: $(X/R:0:Z) = (X:0:Z\times R)$. I don't think however that they teach how to use this.

This is just one type of projective coordinates.

[More representations](https://www.hyperelliptic.org)

You actually always send affine around because its the most compact. (just 2 numbers) but computation is much more efficient because you only need to find one inverse which is the inverse of Z to convert back to affine. 
11
$\mathcal{E}(F_61)$ 