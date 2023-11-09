### Easy Peasy

The code provided doesn't seem to regenerate or refresh the key. In OTP (One-Time Pad), the key should be used only once, hence "one-time" pad. However, in this code, the key is reused, which weakens the security. The code exhibits a specific condition where the key cycling might cause a wrap-around behavior. This occurs when the key length exceeds a specific length (KEY_LEN = 50000) and wraps around to the beginning of the key when selecting the part for encryption.

Given that the provided flag is of length 32, submitting another 49968 characters as strings triggers the code to the wrap-around condition, resulting in the generation of the same key used to encrypt the flag. Once we obtain the same key used to encrypt the flag along with the corresponding two ciphertexts, it becomes possible to reveal the flag using the properties of XOR governing One Time Pads.


![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/23daed20-c3ef-46d0-a1b0-ca3222a95517)
![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/4f7a8e97-e2f4-48b2-b849-bc3059c7e411)





```python
enc_flag = "5b1e564b6e415c0e394e0401384b08553a4e5c597b6d4a5c5a684d50013d6e4b"
enc_a = "0346071d3d1904593d1903573d1950033d1958592a3d1905593d1900573f3d19"


plain_a = 'a' * 32  # The known plaintext for enc_a


enc_flag_bytes = bytes.fromhex(enc_flag)
enc_a_bytes = bytes.fromhex(enc_a)


key_part = bytes([a ^ ord('a') for a in enc_a_bytes])


flag_bytes = bytes([b ^ k for b, k in zip(enc_flag_bytes, key_part)])

# Convert the resulting bytes back to a string to reveal the flag
flag = flag_bytes.decode('utf-8')
print("The flag is:", flag)
```
![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/a97060f1-a760-4bdf-bb5c-c7577066a25c)

