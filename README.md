make_password
=============

An AWK program to generate a specified number of passwords with from eight to sixteen characters each.

Usage: awk -f make_password.awk [-v num=n] [-v len=n] [-v debug=1]

Generates one password by default.
Use -v num=n on the command line to specify the number of passwords.
  (num must be >= 1; the default is 1)

Generates eight-character passwords by default.
Use -v len=n on the command line to specify the length of the passwords. 
  (len must be >= 8 and <= 16; the default is 8)

A function is provided here that gets a random character from a source 
string that is not already in a destination string.  It is used in both 
steps of the password generation.  

The first step is to randomly choose the unique characters that will be 
in the password.  It does it by choosing characters at random from 
candidate lowercase, uppercase, numeric, and special characters that have
not already been chosen. 

The second step is to scramble the characters that were chosen.  It does
that by choosing characters at random from the already-chosen password 
characters until all of them have been chosen. 

The result of the two steps is a scrambled string containing random, unique
password characters.

