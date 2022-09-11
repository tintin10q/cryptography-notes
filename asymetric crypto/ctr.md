Chineese remainder theorem. 


The chineese remainder theorem or ctr is a way to solve sets of equations that involve modulo. 

So lets say we have 

x ≡ 9 (mod 19);
x ≡ 12 (mod 23).

This means we want an x that when x mod 19 = 9 and x mod 23 = 12.

This is how you find it


x1 = 9
x2 = 12

p = 19

q = 23

  
n = p * q
n = 19 * 23 = 437


u1 = pow(q,-1,p) * q The inverse of q mod p times q
u2 = pow(p,-1,q) * p The inverse of p mod q times p
  
u1 is 115
u2 is 323

Then x = (x1* u1 + x2 * u2) mod n
x = (9* 115 + 12 * 323) mod 437
x = 104

And we can indeed see:
104 % 19 = 9
104 % 23 = 12 
