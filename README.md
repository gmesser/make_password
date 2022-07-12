# make_password

## An AWK program to generate passwords.

This project provides a shell script and an AWK program that generates the passwords.

The default is one password, eight characters long.  

## The Shell Script

**Usage:** `make_password [-v num=n] [-v len=n] [-v debug=1]`

## The AWK Program

**Usage:** `awk -f make_password.awk [-v num=n] [-v len=n] [-v debug=1]`

### Number of Passwords - `[-v num=n]`

* Use "-v num=***n***" on the command line to specify the number of passwords./>(***n*** must be **>= 1**; the default is **1**)

### Password Length - `[-v len=n]`

* Use "-v len=***n***" on the command line to specify the length of the passwords.<br />(***n*** must be **>= 8** and **<= 16**; the default is **8**)

### Debug Output - `[-v debug=1]`

* Use "-v debug=1" on the command line to enable debug messages.<br />The debug messages report the number of passwords, password length, and number of characters from each group of characters.

<hr />

## Password Candidate Characters

Not all characters are password character candidates.  The generated passwords are sometimes displayed or (horror!) emailed to the user.  Depending on the font used, some characters are indistinguishable from each other.  These characters can lead to user aggravation and completely unnecessary support calls.

In the case of special characters, many of them are problematic for various reasons, like inserting into a spreadsheet cell, and there are plenty of other ones available.

Here are the candidates and exclusions in each group of characters:

* Lowercase Candidates: `abcdefghijkmnpqrstuvwxyz`<br /> Excluded lowercase characters: `l` and `o`.
* Uppercase Candidates: `ABCDEFGHJKLMNPQRSTUVWXYZ`<br /> Excluded uppercase character: `I` and `O`  
* Numeric Candidates: `23456789`<br />  Excluded numeric characters: `1` and `0` 
* Special Character Candidates: `!@#$%^&*-_=+/`
  Notable excluded special chacaters: `~` `(` `)` `[` `]` `{` `}` `|` `\` `'`  `;` `:` `"` `,` `<` `.` `>` `?`

<hr />

## Methodology

The AWK program includes a function that copies a unique, random character from a source array to a destination array.  The program uses that function in each of the two password generation steps below.  

First it selects the password characters by choosing unique characters at random from the arrays of candidate lowercase, uppercase, numeric, and special characters.

Then it scrambles the password characters by choosing characters at random from the just-chosen array of password characters until all of them have been chosen. 

The result of the two steps is a scrambled string containing unique, random password characters.

**Note:** Everything depends on the random number generator in the AWK interpreter actually being random.  ***If the default random number seed is always the same, all the runs will generate the same sequence of passwords***.  

If your AWK does not generate random passwords, or you're just AWK-curious, try The One True AWK (https://github.com:onetrueawk/awk.git).  That one works perfectly.

