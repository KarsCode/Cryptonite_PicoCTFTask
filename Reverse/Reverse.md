### Reverse


To solve this question I utilized GDB. GDB (GNU Debugger) is a powerful and widely-used command-line debugger for various programming languages, primarily used for C, C++, and other related languages. It allows developers to observe and control the execution of their programs for the purpose of debugging, analyzing, and diagnosing issues within the software.

![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/56cb25f3-fc54-4c29-9328-00a65c7aa5ae)

![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/3993391a-bf9b-47e7-bfad-9b8e8b94836b)



I observerd the strcmp function ( at +176), which is a standard C library function used to compare two strings. It's part of the C standard library in the string.h header file and is commonly used for string comparison. This function is probably the one used for password checking and comparison. 

![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/bcc4ad36-78ae-4548-aeed-8e5f0ae35396)


After obtaining the register location at which the password is stored I displayed it revealing the flag. The GDB command x/s $rdx is used for examining memory in GDB, specifically to display the contents of memory as a null-terminated string starting from the memory address stored in the register $rdx.

![image](https://github.com/KarsCode/Cryptonite_PicoCTFTask/assets/117924364/2f75dd2a-d1ec-43b8-ad65-f4b492e17b4b)

