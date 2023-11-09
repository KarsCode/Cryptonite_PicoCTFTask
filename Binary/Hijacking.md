### Hijacking

After launching the instance and SSHing into the server, I used ls -la to display all the files in the directory. I also used sudo -l command. The sudo -l command is used to list the allowed (or sometimes, all) commands that the current user is permitted to run using sudo (which allows users to execute commands with the security privileges of another user, typically the superuser or root).


`(ALL) /usr/bin/vi`: This line allows the user "picoctf" to run the vi text editor using sudo. The (ALL) specifies that it can be run from any host, and /usr/bin/vi is the full path to the vi editor executable. With this privilege, the user can execute vi with elevated privileges.

`(root) NOPASSWD: /usr/bin/python3 /home/picoctf/.server.py`: This line grants the user "picoctf" the ability to execute the specified Python script /home/picoctf/.server.py using sudo without requiring a password. The (root) part signifies that the command is executed with the permissions of the root user. The NOPASSWD directive means that the user doesn't need to enter their password when running this specific command

Utilizing vi, we can make the following changes to .server.py to display the contents of the JSON file in the /challenge directory. 


On running the python file as the root user we can see the flag