### Play Nice

Thanks to the hint, we understand that finding the required flag involves using the Playfair Cipher. The Playfair cipher is a polygraphic substitution cipher that deals with pairs of letters (digraphs) instead of single letters, making it more resistant to frequency analysis than simple substitution ciphers.

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
