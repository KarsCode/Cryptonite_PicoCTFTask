### basic-mod-1
To decrypt the given set of numbers we are also given the following procedure: 
Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore.
I wrote a simply python script to decrypt the same: 
```python 
# Define the character set
characters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_"

# Given numbers
numbers = [165, 248, 94, 346, 299, 73, 198, 221, 313, 137, 205, 87, 336, 110, 186, 69, 223, 213, 216, 216, 177, 138]

# Map each number mod 37 to the character set
result = [characters[num % 37] for num in numbers]

# Join the characters together to form a string
result_string = ''.join(result)

print("Resulting string:", result_string)
```



![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/1a4f3c4d-4a2a-4856-9cbb-f6766e269ab5)



