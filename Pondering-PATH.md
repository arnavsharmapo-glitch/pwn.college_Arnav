# Challenge 1 : The PATH Variable

It turns out that the answer to "How does the shell find ls?" is fairly simple. There is a special shell variable, called PATH, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands. If you blank out the variable, things go badly:
```sh
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ PATH=""
hacker@dojo:~$ ls
bash: ls: No such file or directory
hacker@dojo:~$
```
Without a PATH, bash cannot find the ls command.

In this level, you will disrupt the operation of the /challenge/run program. This program will DELETE the flag file using the rm command. However, if it can't find the rm command, the flag will not be deleted, and the challenge will give it to you! Thus, you must make it so that /challenge/run also can't find the rm command!

Keep in mind: /challenge/run will be a child process of your shell, so you must apply the concepts you learned in Shell Variables to mess with its PATH variable! If you don't succeed, and the flag gets deleted, you will need to restart the challenge to try again!

## Solution : 
- Step 1 : Open ssh
- Step 2 : Set the PATH variable emoty using the proper commands and then run the correct command as instructed
- Step 3 : Copy and paste the flag
```sh
hacker@path~the-path-variable:~$ PATH=" "
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: command not found
The flag is still there! I might as well give it to you!
pwn.college{MTc9773Ci_-om702DZ0phptGm85.QX2cDM1wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{MTc9773Ci_-om702DZ0phptGm85.QX2cDM1wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt about the PATH variable


# Challenge 2 : Setting PATH

Okay, so things break when you blank out PATH. But what about doing something useful with PATH?

Let's explore how we would, for example, add a new directory of programs to our command repertoire. Recall that PATH stores a list of directories to find commands in and, for commands in nonstandard places, we must typically execute them via their path:
```sh
hacker@dojo:~$ ls /home/hacker/scripts
goodscript	badscript	okayscript
hacker@dojo:~$ goodscript
bash: goodscript: command not found
hacker@dojo:~$ /home/hacker/scripts/goodscript
YEAH! This is the best script!
hacker@dojo:~$
```
If you maintain useful scripts that you want to be able to launch by bare name, this is annoying. However, by adding directories to or replacing directories in this list, you can expose these programs to be launched using their bare name! For example:
```sh
hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!
hacker@dojo:~$
```
Let's practice. This level's /challenge/run will run the win command via its bare name, but this command exists in the /challenge/more_commands/ directory, which is not initially in the PATH. The win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory. Good luck!

## Solution : 
- Step 1 : Open ssh
- Step 2 : Set the PATH variable as directed and then run the correct command
- Step 3 : Copy and paste the flag
```sh
hacker@path~setting-path:~$ PATH=/challenge/more_commands
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{cYXFRNoN5J8EIkwKBdJ2CeAiIgm.QX1cjM1wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{cYXFRNoN5J8EIkwKBdJ2CeAiIgm.QX1cjM1wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to set the PATH variable


# Challenge 3 : Finding Commands

When you type the name of a command, something inside one of the many directories listed in your $PATH variable is what actually gets executed (of course, unless the command is a builtin!). But which file, precisely? You can find out with the aptly-named which command:
```sh
hacker@dojo:~$ which cat
/bin/cat
hacker@dojo:~$ /bin/cat /flag
YEAH
hacker@dojo:~$
```
Mirroring what the shell does when searching for commands, which looks at each directory in $PATH in order and prints the first file it finds whose name matches the argument you passed.

In this challenge, we added a win command somewhere in your $PATH, but it won't give you the flag. Instead, it's in the same directory as a flag file that we made readable by you! You must find win (with the which command), and cat the flag out of that directory!

## Solution : 
- Step 1 : Open ssh
- Step 2 : Find out the directory in which the flag is located and run the command 
- Step 3 : Copy and paste the flag
```sh
hacker@path~finding-commands:~$ which win
/challenge/paths/29534/win
hacker@path~finding-commands:~$ cat /challenge/paths/29534/flag
pwn.college{w4ui4SqB0sENs1wQ4pFIy6KgH3U.01NzEzNxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{w4ui4SqB0sENs1wQ4pFIy6KgH3U.01NzEzNxwSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to find commands in the system


# Challenge 4 : Adding Commands

Recall our example from the previous level:
```sh
hacker@dojo:~$ ls /home/hacker/scripts
goodscript	badscript	okayscript
hacker@dojo:~$ PATH=/home/hacker/scripts
hacker@dojo:~$ goodscript
YEAH! This is the best script!
hacker@dojo:~$
```
What we see here, of course, is the hacker making the shell more useful for themselves by bringing their own commands to the party. Over time, you might amass your own elegant tools. Let's start with win!

Previously, the win command that /challenge/run executed was stored in /challenge/more_commands. This time, win does not exist! Recall the final level of Chaining Commands, and make a shell script called win, add its location to the PATH, and enable /challenge/run to find it!

Hint: /challenge/run runs as root and will call win. Thus, win can simply cat the flag file. Again, the win command is the only thing that /challenge/run needs, so you can just overwrite PATH with that one directory. But remember, if you do that, your win command won't be able to find cat.

You have three options to avoid that:

- Figure out where the cat program is on the filesystem. It must be in a directory that lives in the PATH variable, so you can print the variable out (refer to Shell Variables to remember how!), and go through the directories in it (recall that the different entries are separated by :), find which one has cat in it, and invoke cat by its absolute path.
- Set a PATH that has the old directories plus a new entry for wherever you create win.
- Use read (again, refer to Shell Variables) to read /flag. Since read is a builtin functionality of bash, it is unaffected by PATH shenanigans.
Now, go and win!

## Solution : 
- Step 1 : Open ssh
- Step 2 : Add commandas in the file and then execute them properly
- Step 3 : Copy and paste the flag
In code :
```sh
#!/bin/bash
/run/dojo/bin/cat /flag
```

In terminal :
```sh
hacker@path~adding-commands:~$ chmod ugo+x win
hacker@path~adding-commands:~$ PATH=/home/hacker
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{MzuyHS6xRekUEiH0ahZP0n_tHEw.QX2cjM1wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{MzuyHS6xRekUEiH0ahZP0n_tHEw.QX2cjM1wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to add commands to run


# Challenge 5 : Hijacking Commands

Armed with your knowledge, you can now carry out some shenanigans. This challenge is almost the same as the first challenge in this module. Again, this challenge will delete the flag using the rm command. But unlike before, it will not print anything out for you.

How can you solve this? You know that rm is searched for in the directories listed in the PATH variable. You have experience creating the win command when the previous challenge needed it. What else can you create?

## Solution : 
- Step 1 : Open ssh
- Step 2 : Make a shebang named rm and then run the commands properly after making sure they are executable
- Step 3 : Copy and paste the flag
In code :
```sh
#!/bin/bash
/run/dojo/bin/cat /flag
```

In terminal :
```sh
hacker@path~hijacking-commands:~$ chmod ugo+x rm
hacker@path~hijacking-commands:~$ PATH="/home/hacker/"
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{klvQylVjymsWQSIHm_Oxgi3V7-N.QX3cjM1wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{klvQylVjymsWQSIHm_Oxgi3V7-N.QX3cjM1wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to hijack commands
