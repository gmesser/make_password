make_password
=============

An AWK program to generate a number of passwords with eight to sixteen characters each.

Usage: awk -f make_password.awk [-v num=n] [-v len=n] [-v debug=1]

Generates one password by default.
Use -v num=n on the command line to specify the number of passwords.
  (num must be >= 1; the default is 1)

Generates eight-character passwords by default.
Use -v len=n on the command line to specify the length of the passwords. 
  (len must be >= 8 and <= 16; the default is 8)
