# Challenge 1 : Translating Characters

One of the purposes of piping data is to modify it. Many Linux commands will help you modify data in really cool ways. One of these is tr, which translates characters it receives over standard input and prints them to standard output.

In its most basic usage, tr translates the character provided in its first argument to the character provided in its second argument:
```sh
hacker@dojo:~$ echo OWN | tr O P
PWN
hacker@dojo:~$
```
It can also handle multiple characters, with the characters in different positions of the first argument replaced with associated characters in the second argument.
```sh
hacker@dojo:~$ echo PWM.COLLAGE | tr MA NE
PWN.COLLEGE
hacker@dojo:~$
```
Now, you try it! In this level, /challenge/run will print the flag but will swap the casing of all characters (e.g., A will become a and vice-versa). Can you undo it with tr and get the flag?

## Solution : 
- Step 1 : Open terminal
- Step 2 : Run the tr(trace) command properly as directed
- Step 3 : Copy and paste the flag
```sh
hacker@data~translating-characters:~$ /challenge/run
Your case-swapped flag:
PWN.COLLEGE{4GJkJU3eTUQO0koSm3h6lqhvI_a.01mXeZnXWsn4aZnZeZw}

hacker@data~translating-characters:~$ echo PWN.COLLEGE{4GJkJU3eTUQO0koSm3h6lqhvI_a.01mXeZnXWsn4aZnZeZw} | tr PWNCOLLEGEGJkJUeTUQOkoSmhlqhvIamXeZnX
WsnaZnZeZw pwncollegegjKjuEtuqoKOsMHLQHViAMxEzNxwSNAzNzEzW
pwn.college{4gjKju3Etuqo0KOsM3H6LQHVi_A.01MxEzNxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{4gjKju3Etuqo0KOsM3H6LQHVi_A.01MxEzNxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt about the translating command to modify data


# Challenge 2 : Deleting Characters

tr can also translate characters to nothing (i.e., delete them). This is done via a -d flag and an argument of what characters to delete:
```sh
hacker@dojo:~$ echo PAWN | tr -d A
PWN
hacker@dojo:~$
```
Pretty simple! Now you give it a try. I'll intersperse some decoy characters (specifically: ^ and %) among the flag characters. Use tr -d to remove them!

## Solution : 
- Step 1 : Open terminal
- Step 2 : Run the tr command with the proper arguments
- Step 3 : Copy and paste the flag
```sh
hacker@data~deleting-characters:~$ /challenge/run 
Your character-stuffed flag:
p%w^%n^.c^%o%l%l^%e^%g^%e^{g%R%w^%6^p^%6^%J^%1^R%p^F%q%p%O3F^%u^x^T%N^c%F^J^U^%f^%3^7^%.^%0%F^%N^%x^%E^%z%N^x^%wS^N%4%A%z%N^z%E%z%W^%}^%^%
hacker@data~deleting-characters:~$ echo p%w^n^.c^o^l^%l%e^%g^e{^%g^%R^%w^%6p^6^%J^1^R%p^F^%q%p^O3F^%ux^T%N^%c^%F%J^%U^f^3^%7^%.^%0F%N%x^%E^%z%N%x^w^%S%N4^%Az^N%zEz%W%}% | tr -d ^%
pwn.college{gRw6p6J1RpFqpO3FuxTNcFJUf37.0FNxEzNxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{gRw6p6J1RpFqpO3FuxTNcFJUf37.0FNxEzNxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt how to delete characters


# Challenge 3 : Deleting Newlines
A common class of characters to remove is a line separator. This happens when you have a stream of data that you want to turn into a single line for further processing. You can specify newlines almost like any other character, by escaping them:
```sh
hacker@dojo:~$ echo "hello_world!" | tr _ "\n"
hello
world!
hacker@dojo:~$
```
Here, the backslash (\) signifies that the character that follows it is a standin for a character that's hard to input into the shell normally. The newline, of course, is hard to input because when you typically hit Enter, you'll run the command itself. \n is a standin for this newline, and it must be in quotes to prevent the shell interpreter itself from trying to interpret it and pass it to tr instead.

Now, let's combine this with deletion. In this challenge, we'll inject a bunch of newlines into the flag. Delete them with tr's -d flag and the escaped newline specification!

Fun fact! Want to actually replace a backslash (\) character? Because \ is the escape character, you gotta escape it! \\ will be treated as a backslash by tr. This isn't relevant to this challenge, but is a fun fact nonetheless!

## Solution : 
- Step 1 : Open terminal
- Step 2 : Run the command to get the flag in an altered manner
- Step 3 : Delete the newlines using the proper commands to get the proper flag
- Step 4 : Copy and paste the flag
```sh
hacker@data~deleting-newlines:~$ /challenge/run 
Your line-split flag: 
p
wn
.
col
le
g
e{
Q
e
bh1
IQ3t
VXqXI
s
yh
hWu_
1
dqhV
P
.
0
V
NxEzN
xwS
N4
Az
Nz
EzW}
hacker@data~deleting-newlines:~$ echo "p
wn
.
col
le
g
e{
Q
e
bh1
IQ3t
VXqXI
s
yh
hWu_
1
dqhV
P
.
0
V
NxEzN
xwS
N4
Az
Nz
EzW}" | tr -d "\n"
pwn.college{Qebh1IQ3tVXqXIsyhhWu_1dqhVP.0VNxEzNxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{Qebh1IQ3tVXqXIsyhhWu_1dqhVP.0VNxEzNxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt about newlines and how to delete/modify them


# Challenge 4 : Extracting the first lines with head

In your Linux journey, you'll experience situations where you need to grab just the early output of very verbose programs. For this, you'll reach for head! The head command is used to display the first few lines of its input:
```sh
hacker@dojo:~$ cat /something/very/long | head
this
is
just
the
first
ten
lines
of
the
file
hacker@dojo:~$
```
By default, it shows the first 10 lines, but you can control this with the -n option:
```sh
hacker@dojo:~$ cat /something/very/long | head -n 2
this
is
hacker@dojo:~$
```
This challenge's /challenge/pwn outputs a bunch of data, and you'll need to pipe it through head to grab just the first 7 lines and then pipe them onwards to /challenge/college, which will give you the flag if you do this right! Your solution will be a long composite command with two pipes connecting three commands. Good luck!

## Solution : 
- Step 1 : Open terminal
- Step 2 : Run the command with the proper arguments and piping
- Step 3 : Copy and paste the flag
```sh
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college 
Congratulations, you piped the right codes!
pwn.college{UpTTs2PAJ20Rf1CYV-9n3_Y2htr.0lNxEzNxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{UpTTs2PAJ20Rf1CYV-9n3_Y2htr.0lNxEzNxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt about the head command and how to use it


# Challenge 5 : Extracting specific sections of text

Sometimes, you want to grab specific columns of data, such as the first column, the third column, or the 42nd column. For this, there's the cut command.

For example, imagine that you have the following data file:
```sh
hacker@dojo:~$ cat scores.txt
hacker 78 99 67
root 92 43 89
hacker@dojo:~$
```
You could use cut to extract specific columns:
```sh
hacker@dojo:~$ cut -d " " -f 1 scores.txt
hacker
root
hacker@dojo:~$ cut -d " " -f 2 scores.txt
78
92
hacker@dojo:~$ cut -d " " -f 3 scores.txt
99
43
hacker@dojo:~$
```
The -d argument specifies the column delimiter (how columns are separated). In this case, it's a space character. Of course, it has to be in quotes here so that the shell knows that the space is an argument rather than a space separating other arguments! The -f argument specifies the field number (which column to extract).

In this challenge, the /challenge/run program will give you a bunch of lines with random numbers and single characters (characters of the flag) as columns. Use cut to extract the flag characters, then pipe them to tr -d "\n" (like the previous level!) to join them together into a single line. Your solution will look something like /challenge/run | cut ??? | tr ???, with the ??? filled out.

## Solution : 
- Step 1 : Open terminal
- Step 2 : Run the command with the proper arguments and piping
- Step 3 : Copy and paste the flag
```sh
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{gBN_sRVsEuyPatcOrx1yzC_QgGk.01NxEzNxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{gBN_sRVsEuyPatcOrx1yzC_QgGk.01NxEzNxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt how to extract certain portions of text documents (the important ones)


# Challenge 6 : Sorting Data

Files (or output lines of commands) aren't always in the order you need them! The sort command helps you organize data. It reads lines from input (or files) and outputs them in sorted order:
```sh
hacker@dojo:~$ cat names.txt
  hack
  the
  planet
  with
  pwn
  college
hacker@dojo:~$ sort names.txt
  college
  hack
  planet
  pwn
  the
  with
hacker@dojo:~$
```
By default, sort orders lines alphabetically. Arguments can change this:

-r: reverse order (Z to A)
-n: numeric sort (for numbers)
-u: unique lines only (remove duplicates)
-R: random order!
In this challenge, there's a file at /challenge/flags.txt containing 100 fake flags, with the real flag mixed among them. When sorted alphabetically, the real flag will be at the end (we made sure of this when generating fake flags). Go get it!

## Solution : 
- Step 1 : Open terminal
- Step 2 : Run the sort command correctly with the proper arguments to get the flag
- Step 3 : Copy and paste the flag
```sh
hacker@data~sorting-data:~$ sort -r /challenge/flags.txt 
pwn.college{Q4QCSZbyOYCjDTnNbDK5CGAndDd.0FM0MDOxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{Q4QCSZbyOYCjDTnNbDK5CGAndDd.0FM0MDOxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt about how to sort data in the files in different manners
