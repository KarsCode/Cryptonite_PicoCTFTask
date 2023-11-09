### FileTypes

The given Flag.pdf is infact not a PDF file. On checking it with the file command we notice that it is infact a shell archive. Upon executing each file we realize that each archive leads to a nested archive. To obtain the flag we need to keep extracting and renaming files until we obtain the flag file of ASCII format. 




Using a simple Hexadecimal Decoder we can reveal the flag as follows: 

```python
from pwn import *

hexcode = "7069636f4354467b66316c656e406d335f6d406e3170756c407431306e5f6630725f3062326375723137795f33633739633562617d0a"
print(unhex(hexcode).decode())

