### Play Nice

Thanks to the hint, we understand that finding the required flag involves using the Playfair Cipher. The Playfair cipher is a polygraphic substitution cipher that deals with pairs of letters (digraphs) instead of single letters, making it more resistant to frequency analysis than simple substitution ciphers.

The below code helps decrypt the PlayFair cipher. [Playfair Cipher - Wikipedia](https://en.wikipedia.org/wiki/Playfair_cipher)

```python
#!/usr/bin/python3 -u
import signal

SQUARE_SIZE = 6


def generate_square(alphabet):
	assert len(alphabet) == pow(SQUARE_SIZE, 2)
	matrix = []
	for i, letter in enumerate(alphabet):
		if i % SQUARE_SIZE == 0:
			row = []
		row.append(letter)
		if i % SQUARE_SIZE == (SQUARE_SIZE - 1):
			matrix.append(row)
	return matrix

def get_index(letter, matrix):
	for row in range(SQUARE_SIZE):
		for col in range(SQUARE_SIZE):
			if matrix[row][col] == letter:
				return (row, col)
	print("letter not found in matrix.")
	exit()

def encrypt_pair(pair, matrix):
	p1 = get_index(pair[0], matrix)
	p2 = get_index(pair[1], matrix)

	if p1[0] == p2[0]:
		return matrix[p1[0]][(p1[1] + 1)  % SQUARE_SIZE] + matrix[p2[0]][(p2[1] + 1)  % SQUARE_SIZE]
	elif p1[1] == p2[1]:
		return matrix[(p1[0] + 1)  % SQUARE_SIZE][p1[1]] + matrix[(p2[0] + 1)  % SQUARE_SIZE][p2[1]]
	else:
		return matrix[p1[0]][p2[1]] + matrix[p2[0]][p1[1]]

def encrypt_string(s, matrix):
	result = ""
	if len(s) % 2 == 0:
		plain = s
	else:
		plain = s + "meiktp6yh4wxruavj9no13fb8d027c5glzsq"[0]
	for i in range(0, len(plain), 2):
		result += encrypt_pair(plain[i:i + 2], matrix)
	return result

def decrypt_pair(pair, matrix):
    p1 = get_index(pair[0], matrix)
    p2 = get_index(pair[1], matrix)

    if p1[0] == p2[0]:
        return matrix[p1[0]][(p1[1] - 1) % SQUARE_SIZE] + matrix[p2[0]][(p2[1] - 1) % SQUARE_SIZE]
    elif p1[1] == p2[1]:
        return matrix[(p1[0] - 1) % SQUARE_SIZE][p1[1]] + matrix[(p2[0] - 1) % SQUARE_SIZE][p2[1]]
    else:
        return matrix[p1[0]][p2[1]] + matrix[p2[0]][p1[1]]

def decrypt_string(s, matrix):
    result = ""
    for i in range(0, len(s), 2):
        result += decrypt_pair(s[i:i + 2], matrix)
    return result

# Use the same key (alphabet) and generated square (matrix) used for encryption
alphabet = "meiktp6yh4wxruavj9no13fb8d027c5glzsq"
enc_msg ="y7bcvefqecwfste224508y1ufb21ld"
matrix = generate_square(alphabet)
dec_msg = decrypt_string(enc_msg, matrix)
print("Decrypted message:", dec_msg)






```

**decrypt_pair Function:**

- **Input:** pair (a string of two characters) and matrix (the Playfair matrix).
- **Output:** Returns the decrypted pair based on the Playfair rules.
- The function performs the following steps:
  - Retrieves the positions of the two characters in the matrix using get_index.
  - Checks if the characters are in the same row or column.
  - If they are in the same row, it shifts them to the left by one (mod SQUARE_SIZE).
  - If they are in the same column, it shifts them upward by one (mod SQUARE_SIZE).
  - If they form a rectangle, it swaps the columns.

**decrypt_string Function:**

- **Input:** s (the encrypted message) and matrix (the Playfair matrix).
- **Output:** Returns the decrypted message.
- The function decrypts the entire string by:
  - Iterating through the input string in pairs (as required by the Playfair cipher).
  - Decrypting each pair using the decrypt_pair function and appending the result to the result variable.


![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/b603c95c-65f0-4c6d-871c-1658b940a4ad)

