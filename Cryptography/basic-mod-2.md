### basic-mod-2
To decrypt the given set of numbers we are also given the following procedure:
Take each number mod 41 and find the modular inverse for the result. Then map to the following character set: 1-26 are the alphabet, 27-36 are the decimal digits, and 37 is an underscore.

Note on Modular Inverse: 
The modular inverse of an integer \(a\) is another integer \(x\) such that the product of \(a\) and \(x\) in a given modulus \(m\) equals 1. In other words, if \(a \times x\) is divided by the modulus \(m\), the remainder will be 1.

Mathematically, the modular inverse is denoted as \(a^{-1} \mod m\), where \(a\) is the integer, \(m\) is the modulus, and \(x\) is the modular inverse of \(a\) under \(m\).

Here is the python script that uses a tool for modular inverse to find the flag
```python
from sympy import mod_inverse

# Define the character set
characters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_"
print(len(characters))

# Given numbers
numbers = [268, 413, 438, 313, 426, 337, 272, 188, 392, 338, 77, 332, 139, 113, 92, 239, 247, 120, 419, 72, 295, 190, 131]

# Map each number mod 41 and find the modular inverse
mod_inv_result = [mod_inverse(num % 41, 41) for num in numbers]

# Map the modular inverse to the character set, ensuring it's within the valid range
result = [characters[num - 1] if num - 1 < len(characters) else characters[-1] for num in mod_inv_result]

# Join the characters together to form a string
result_string = ''.join(result)

print("Resulting string:", result_string)
```

![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/efd1b54f-894d-4292-9027-5bdedd7b33d3)


