### credstuff
This challenge required us to find the password of the user ‘cultiris’ and then decrypt it. We know that each username in usernames.txt has it’s corresponding password lying on the same line in passwords.txt. 
Using grep I found the username and the line it was located on. 

Using sed I found it’s corresponding password and extracted the password on the 378th line using sed.
I then used ROT13 to decode the flag. 
