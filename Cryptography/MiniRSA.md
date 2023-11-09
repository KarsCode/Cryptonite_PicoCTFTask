### Mini RSA

In RSA encryption, the relationship between the plaintext message (M), the encryption (c), and the public key modulus (n) is described by the equation \( M^e \mod n = c \). This equation signifies that the original plaintext message cubed (raised to the power of 3) modulo the public key modulus equals the encrypted message. {Given \( e = 3 \)}

So, mathematically, \( M^3 = xn + c \), indicating that the original message cubed is equal to a multiple of the public key modulus (\( tn \)) plus the encrypted message (\( c \)), for some integer value of \( x \). Therefore, the decryption can be performed by taking the cube root of \( (xn + c) \), as \( M = \sqrt[3]{xn + c} \).

Since the value of \( M^3 \) is only slightly larger than \( n \) due to the nature of RSA encryption, it suggests that the plaintext message has been encrypted in such a way that it's very close in value to \( n \). Therefore, by testing and finding the right value of \( x \), it is feasible to perform the cube root operation on \( (xn + c) \) to retrieve the original message.
