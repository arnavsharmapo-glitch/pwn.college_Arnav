# Challenge 1 : Intro To Commands

In this challenge, you will invoke your first command! When you type a command and hit enter, the command will be invoked, as so:
```sh
hacker@dojo:~$ whoami
hacker
hacker@dojo:~$
```
Here, the user executed the whoami command, which simply prints the username (hacker) to the terminal. When the command terminates, the shell once again displays the prompt, ready for the next command.

In this level, invoke the hello command to get the flag! Keep in mind: commands in Linux are case sensitive: hello is different from HELLO.

## Solution
- Step 1 : Open the terminal
- Step 2 : Write the 'hello' command as instructed
- Step 3 : Copy and Paste the flag you got
```sh
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{IMbOZoo9GMbrntwP41Knn9fnZLJ.QX3YjM1wSN4AzNzEzW}
hacker@hello~intro-to-commands:~$
```

## Flag
```sh
pwn.college{IMbOZoo9GMbrntwP41Knn9fnZLJ.QX3YjM1wSN4AzNzEzW}
```

### Reference
None

### Notes
I learnt what a command is and how to execute it inside a terminal.


# Challenge 2 : Intro To Arguments
Let's try something more complicated: a command with arguments, which is what we call additional data passed to the command. When you type a line of text and hit enter, the shell actually parses your input into a command and its arguments. The first word is the command, and the subsequent words are arguments. Observe:
```sh
hacker@dojo:~$ echo Hello
Hello
hacker@dojo:~$
```
In this case, the command was echo, and the argument was Hello. echo is a simple command that "echoes" all of its arguments back out onto the terminal, like you see in the session above.

Let's look at echo with multiple arguments:
```sh
hacker@dojo:~$ echo Hello Hackers!
Hello Hackers!
hacker@dojo:~$
```
In this case, the command was echo, and Hello and Hackers! were the two arguments to echo. Simple!
In this challenge, to get the flag, you must run the hello command (NOT the echo command) with a single argument of hackers. Try it now!

## Solution : 
- Step 1 : Open Terminal
- Step 2 : Type the command 'Hello' and the argument 'Hackers'
- Step 3 : Copy and Paste the flag you got
```sh
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{8eTZfrdCO6yFyH79CvwYFna8ruO.QX4YjM1wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{8eTZfrdCO6yFyH79CvwYFna8ruO.QX4YjM1wSN4AzNzEzW}
```

### Reference
None

### Notes
Learnt what the difference between a command and an argument is.


# Challenge 3 : Command History

You're going to type a lot of commands, and typing everything from scratch can be annoying. Luckily, the shell saves a history of every command you invoke.

You can scroll through those saved commands with the up/down arrow keys, and we'll practice that in this challenge. This challenge will inject the flag into your history. Bring up a terminal, hit the up arrow, and grab it! In other challenges, the history will contain the log of the commands you've run, so if you need to run a similar command again, you can use the arrow keys to scroll through and find it!

## Solution :
- Step 1 : Open the Terminal
- Step 2 : Press the 'up arrow' to get you previously used command or to get your history
- Step 3 : Copy and Paste the flag you got
```sh
hacker@hello~command-history:~$ the flag is pwn.college{wUt661f71GfgBCdM2sOKIAP4j2M.0lNzEzNxwSN4AzNzEzW}^C
```

## Flag : 
```sh
pwn.college{wUt661f71GfgBCdM2sOKIAP4j2M.0lNzEzNxwSN4AzNzEzW}^C
```

### Reference :
None

### Notes
Learnt that we can easily get our previously written commands without even the hassle of going to the recipient location to copy and getting back to our location to paste it.
