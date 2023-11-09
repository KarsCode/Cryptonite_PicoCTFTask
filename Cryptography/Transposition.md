We know that we can divide the given ciphertext into groups of 3 and analyze the performed transposition. We notice that the characters in each subgroup have been right shifted with the character at position 1 being replaced by character at position 3. 

I wrote the following python code to decrypt the given ciphertext and find the flag. 

```python
given_string = "heTfl g as iicpCTo{7F4NRP051N5_16_35P3X51N3_V6E5926A}4"

# Function to shift characters in each subgroup to the right by 1 position
def shift_subgroups(text):
    shifted_text = ""
    subgroup = ""
    for char in text:
        subgroup += char
        if len(subgroup) == 3:
            shifted_subgroup = subgroup[-1] + subgroup[:-1]  # Shifting one position to the right
            shifted_text += shifted_subgroup
            subgroup = ""  # Reset the subgroup
    
    return shifted_text

result = shift_subgroups(given_string)
print("Shifted Result:", result)
```

![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/a4f9dbb1-e0a1-4ee1-916c-53c085ef4002)
