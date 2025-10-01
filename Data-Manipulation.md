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
Learnt

# Challenge 3 : 

## Solution : 
- Step 1 : Open terminal
- Step 2 :
- Step 3 : Copy and paste the flag
```sh
```

## Flag : 
```sh
```

### Reference : 
None

### Notes :
Learnt

# Challenge 4 : 

## Solution : 
- Step 1 : Open terminal
- Step 2 :
- Step 3 : Copy and paste the flag
```sh
```

## Flag : 
```sh
```

### Reference : 
None

### Notes :
Learnt

# Challenge 5 : 

## Solution : 
- Step 1 : Open terminal
- Step 2 :
- Step 3 : Copy and paste the flag
```sh
```

## Flag : 
```sh
```

### Reference : 
None

### Notes :
Learnt

# Challenge 6 : 

## Solution : 
- Step 1 : Open terminal
- Step 2 :
- Step 3 : Copy and paste the flag
```sh
```

## Flag : 
```sh
```

### Reference : 
None

### Notes :
Learnt

# Challenge 7 : 

## Solution : 
- Step 1 : Open terminal
- Step 2 :
- Step 3 : Copy and paste the flag
```sh
```

## Flag : 
```sh
```

### Reference : 
None

### Notes :
Learnt

# Challenge 8 : 

## Solution : 
- Step 1 : Open terminal
- Step 2 :
- Step 3 : Copy and paste the flag
```sh
```

## Flag : 
```sh
```

### Reference : 
None

### Notes :
Learnt
