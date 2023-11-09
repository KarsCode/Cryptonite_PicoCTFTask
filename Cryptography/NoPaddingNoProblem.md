### NoPaddingNoProblem

Understanding Unpadded RSA was the first step to solving this problem
 
We first take a known value, in this case 2 and then encrypt it by performing 2**e mod(n), after which c *x can be calculated. By the above discussed property we can come to the conclusion that 
c * x = encrypted(m) * encrypted(2) = encrypted(m*2)
After getting the value of m*2 we divide by 2 and format + decode to get the flag. 
 
