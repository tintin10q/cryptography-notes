With [[eliptic curve]] if you would want to do Elgamal encryption it would look like this.

![[Pasted image 20220116122917.png]]

This means that what you send is 4 numbers which make up 2 points on the elliptic curve. $(x_c,y_c)$ and $(x_c,y_c)$. All these numbers can be like 200 bits or more which is pretty big. We can compress the points because storing the y point only adds one bit of information as if you have the x there is only two possible y. So you can just store the x and then a one bit 
= y mod 2. Which indicates if the number is even or odd . If its one then you have to have the odd number if its 0 the odd number. 

So the compressed point representation of (2,5) on $y^2 = x^3 + -1x + -4 \in \mathbb{F}_{23}$ , $(2,5) = (2,5 \mod 2) = (2,1)$

Now if we want to reconstruct this we can do: 

- First calculate weirstrass
- Pray that the point is an easy sqrt it should be because not easy is out of scope.
- Do the sqrt which gives two results. 
- Pick the even or odd one

Example for (20,1) on $y^2 = x^3 + 11x + 18$ on $\mathbb{F}_{23}$

![[Pasted image 20220116131338.png]]

