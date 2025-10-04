# Challenge 1 : Listing Processes

First, we will learn to list running processes using the ps command. Depending on whom you ask, ps either stands for "process snapshot" or "process status", and it lists processes. By default, ps just lists the processes running in your terminal, which honestly isn't very useful:
```sh
hacker@dojo:~$ ps
    PID TTY          TIME CMD
    329 pts/0    00:00:00 bash
    349 pts/0    00:00:00 ps
hacker@dojo:~$
```
In the above example, we have the shell (bash) and the ps process itself, and that's all that's running on that specific terminal. We also see that each process has a numerical identifier (the Process ID, or PID), which is a number that uniquely identifies every running process in a Linux environment. We also see the terminal on which the commands are running (in this case, the designation pts/0), and the total amount of cpu time that the process has eaten up so far (since these processes are very undemanding, they have yet to eat up even 1 second!).

In the majority of cases, this is all that you'll see with a default ps. To make it useful, we need to pass a few arguments.

As ps is a very old utility, its usage is a bit of a mess. There are two ways to specify arguments.

"Standard" Syntax: in this syntax, you can use -e to list "every" process and -f for a "full format" output, including arguments. These can be combined into a single argument -ef.

"BSD" Syntax: in this syntax, you can use a to list processes for all users, x to list processes that aren't running in a terminal, and u for a "user-readable" output. These can be combined into a single argument aux.

These two methods, ps -ef and ps aux, result in slightly different, but cross-recognizable output.

Let's try it in the dojo:
```sh
hacker@dojo:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
hacker         1       0  0 05:34 ?        00:00:00 /sbin/docker-init -- /bin/sleep 6h
hacker         7       1  0 05:34 ?        00:00:00 /bin/sleep 6h
hacker       102       1  1 05:34 ?        00:00:00 /usr/lib/code-server/lib/node /usr/lib/code-server --auth=none -
hacker       138     102 11 05:34 ?        00:00:07 /usr/lib/code-server/lib/node /usr/lib/code-server/out/node/entr
hacker       287     138  0 05:34 ?        00:00:00 /usr/lib/code-server/lib/node /usr/lib/code-server/lib/vscode/ou
hacker       318     138  6 05:34 ?        00:00:03 /usr/lib/code-server/lib/node --dns-result-order=ipv4first /usr/
hacker       554     138  3 05:35 ?        00:00:00 /usr/lib/code-server/lib/node /usr/lib/code-server/lib/vscode/ou
hacker       571     554  0 05:35 pts/0    00:00:00 /usr/bin/bash --init-file /usr/lib/code-server/lib/vscode/out/vs
hacker       695     571  0 05:35 pts/0    00:00:00 ps -ef
hacker@dojo:~$
```
You can see here that there are processes running for the initialization of the challenge environment (docker-init), a timeout before the challenge is automatically terminated to preserve computing resources (sleep 6h to timeout after 6 hours), the VSCode environment (several code-server helper processes), the shell (bash), and my ps -ef command. It's basically the same thing with ps aux:
```sh
hacker@dojo:~$ ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
hacker         1  0.0  0.0   1128     4 ?        Ss   05:34   0:00 /sbin/docker-init -- /bin/sleep 6h
hacker         7  0.0  0.0   2736   580 ?        S    05:34   0:00 /bin/sleep 6h
hacker       102  0.4  0.0 723944 64660 ?        Sl   05:34   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       138  3.3  0.0 968792 106272 ?       Sl   05:34   0:07 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       287  0.0  0.0 717648 53136 ?        Sl   05:34   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       318  3.3  0.0 977472 98256 ?        Sl   05:34   0:06 /usr/lib/code-server/lib/node --dns-result-order=
hacker       554  0.4  0.0 650560 55360 ?        Rl   05:35   0:00 /usr/lib/code-server/lib/node /usr/lib/code-serve
hacker       571  0.0  0.0   4600  4032 pts/0    Ss   05:35   0:00 /usr/bin/bash --init-file /usr/lib/code-server/li
hacker      1172  0.0  0.0   5892  2924 pts/0    R+   05:38   0:00 ps aux
hacker@dojo:~$
```
There are many commonalities between ps -ef and ps aux: both display the user (USER column), the PID, the TTY, the start time of the process (STIME/START), the total utilized CPU time (TIME), and the command (CMD/COMMAND). ps -ef additionally outputs the Parent Process ID (PPID), which is the PID of the process that launched the one in question, while ps aux outputs the percentage of total system CPU and Memory that the process is utilizing. Plus, there's a bunch of other stuff we won't get into right now.

Anyways! Let's practice. In this level, I have once again renamed /challenge/run to a random filename, and this time made it so that you cannot ls the /challenge directory! But I also launched it, so you can find it in the running process list, figure out the filename, and relaunch it directly for the flag! Good luck!

NOTE: Both ps -ef and ps aux truncate the command listing to the width of your terminal (which is why the examples above line up so nicely on the right side of the screen. If you can't read the whole path to the process, you might need to enlarge your terminal (or redirect the output somewhere to avoid this truncating behavior)! Alternatively, you can pass the w option twice (e.g., ps -efww or ps auxww) to disable the truncation.

## Solution : 
- Step 1 : Open the terminal
- Step 2 : Check for the running processes with the proper commands
- Step 3 : Copy and paste the flag
```sh
hacker@processes~listing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 21:46 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 21:46 ?        00:00:00 /run/dojo/bin/sleep 6h
root         132       1  0 21:46 ?        00:00:00 /challenge/16712-run-32573
root         135     132  0 21:46 ?        00:00:00 sleep 6h
hacker       146       1  0 21:46 ?        00:00:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.
hacker       150     146  0 21:47 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       160     150  0 21:47 pts/0    00:00:00 ps -ef
hacker@processes~listing-processes:~$ /challenge/16712-run-32573
Yahaha, you found me! Here is your flag:
pwn.college{8OBFExVYj2fW6yZ4iUfyRxvjN_R.QX4MDO0wSN4AzNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').
```

## Flag :
```sh
pwn.college{8OBFExVYj2fW6yZ4iUfyRxvjN_R.QX4MDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt about how to see all your running functions with additional data using the correct arguments


# Challenge 2 : Killing Processes

You've launched processes, you've viewed processes, now you will learn to terminate processes! In Linux, this is done using the aggressively-named kill command. With default options (which is all we'll cover in this level), kill will terminate a process in a way that gives it a chance to get its affairs in order before ceasing to exist.

Let's say you had a pesky sleep process (sleep is a program that simply hangs out for the number of seconds specified on the commandline, in this case, 1337 seconds) that you launched in another terminal, like so:
```sh
hacker@dojo:~$ sleep 1337
```
How do we get rid of it? You use kill to terminate it by passing the process identifier (the PID from ps) as an argument, like so:
```sh
hacker@dojo:~$ ps -e | grep sleep
 342 pts/0    00:00:00 sleep
hacker@dojo:~$ kill 342
hacker@dojo:~$ ps -e | grep sleep
hacker@dojo:~$
```
Now, it's time to terminate your first process! In this challenge, /challenge/run will refuse to run while /challenge/dont_run is running! You must find the dont_run process and kill it. If you fail, pwn.college will disavow all knowledge of your mission. Good luck.

## Solution : 
- Step 1 : Open the terminal
- Step 2 : Check the PID of the running process to kill it
- Step 3 : Now run the proper commands
- Step 4 : Copy and paste the flag
```sh
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 21:50 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 21:50 ?        00:00:00 /run/dojo/bin/sleep 6h
root         135       1  0 21:50 ?        00:00:00 su -c /challenge/.launcher hacker
hacker       136     135  0 21:50 ?        00:00:00 /challenge/dont_run
hacker       137     136  0 21:50 ?        00:00:00 sleep 6h
hacker       148       1  0 21:50 ?        00:00:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.
hacker       152     148  0 21:50 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       162     152  0 21:50 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run 
Great job! Here is your payment:
pwn.college{kTyiQHp9gJL_6eBn9-V9ytpIFgz.QXyQDO0wSN4AzNzEzW}
```

## Flag :
```sh
pwn.college{kTyiQHp9gJL_6eBn9-V9ytpIFgz.QXyQDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt hot to kill processes


# Challenge 3 : Interrupting Processes

You've learned how to kill other processes with the kill command, but sometimes you just want to get rid of the process that's clogging up your terminal! Luckily, terminals have a hotkey for this: Ctrl-C (e.g., holding down the Ctrl key and pressing C) sends an "interrupt" to whatever application is waiting on input from the terminal and, typically, this causes the application to cleanly exit.

Try it here! /challenge/run will refuse to give you the flag until you interrupt it. Good luck!

For the very interested, check out this article about terminals and "control codes" (such as Ctrl-C).

## Solution : 
- Step 1 : Open the terminal
- Step 2 : Run the command and then interrupt it as instructed
- Step 3 : Copy and paste the flag
```sh
hacker@processes~interrupting-processes:~$ /challenge/run 
I could give you the flag... but I won't, until this process exits. Remember, 
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{A55g43oyJffkXxjg6EN9Wg-HJlX.QXzQDO0wSN4AzNzEzW}
```

## Flag :
```sh
pwn.college{A55g43oyJffkXxjg6EN9Wg-HJlX.QXzQDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt hot to interrupt processes


# Challenge 4 : Killing Misbehaving Processes

Sometimes, misbehaving processes can interfere with your work. These processes might need to be killed...

In this challenge, there's a decoy process that's hogging a critical resource - a named pipe (FIFO) at /tmp/flag_fifo into which (like in the Practicing Piping FIFO challenge) /challenge/run wants to write your flag. You need to kill this process.

Your general workflow should be:

- Check what processes are running.
- Find /challenge/decoy in the list and figure out its process ID.
kill it.
- Run /challenge/run to get the flag without being overwhelmed by decoys (you don't need to redirect its output; it'll write to the FIFO on its own).
- Good luck!

NOTE: You might see a few decoy flags show up even after killing the decoy process. This happens because Linux pipes are buffered: conceptually, they have a sort of length through which data flows, and you might kill the decoy process while data is in the pipe. That data, having already entered the pipe, will proceed to the other end (your cat). If you wait a second, you'll see the decoys stop, and then you can /challenge/run and win!

## Solution : 
- Step 1 : Open the terminal
- Step 2 : Check the running processes to kill the misbehaving process. then run the proper commands
- Step 3 : Copy and paste the flag
```sh
hacker@processes~killing-misbehaving-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 21:57 ?        00:00:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin/dojo-init /run/dojo/bin/sleep 6h
root           7       1  0 21:57 ?        00:00:00 /run/dojo/bin/sleep 6h
root         137       1  0 21:57 ?        00:00:00 /bin/bash /challenge/.init
root         138       1  0 21:57 ?        00:00:00 /bin/bash /challenge/.init
root         139       1  0 21:57 ?        00:00:00 su -c exec /challenge/decoy > /tmp/flag_fifo hacker
root         140     138  0 21:57 ?        00:00:00 sleep 6h
root         141     137  0 21:57 ?        00:00:00 sleep 6h
hacker       142     139  0 21:57 ?        00:00:00 /usr/bin/python /challenge/decoy
hacker       153       1  0 21:57 ?        00:00:00 /nix/store/g0q8n7xfjp7znj41hcgrq893a9m0i474-ttyd-1.7.7/bin/ttyd --port 7681 --interface 0.0.0.
hacker       157     153  0 21:57 pts/0    00:00:00 /run/dojo/bin/bash --login
hacker       167     157  0 21:57 pts/0    00:00:00 ps -ef
hacker@processes~killing-misbehaving-processes:~$ kill 142
hacker@processes~killing-misbehaving-processes:~$ /challenge/run 
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{s0nSK2OH4tRp0l7qqT2VHTnmGf3.0FNzMDOxwSN4AzNzEzW}
```

## Flag :
```sh
pwn.college{s0nSK2OH4tRp0l7qqT2VHTnmGf3.0FNzMDOxwSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to kill misbehaving processes


# Challenge 5 : Suspending Processes

You have learned to interrupt processes with Ctrl-C, but there are less drastic measures you can use to get your terminal back! You can suspend processes to the background with Ctrl-Z. In this level, we'll explore how this works and, in the next level, we'll figure out how to resume those suspended processes!

This level's run wants to see another copy of itself running and using the same terminal. How? Use the terminal to launch it, then suspend it, then launch another copy while the first is suspended!

## Solution : 
- Step 1 : Open the terminal
- Step 2 : Run the command, suspend it and then run the same command again as instructed
- Step 3 : Copy and paste the flag
```sh
hacker@processes~suspending-processes:~$ /challenge/run 
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 22:05 pts/0    00:00:00 bash /challenge/run
root         148     146  0 22:05 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can 
background me with Ctrl-Z or, if you're not ready to do that for whatever 
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run 
I'll only give you the flag if there's already another copy of me running in 
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         146     136  0 22:05 pts/0    00:00:00 bash /challenge/run
root         153     136  0 22:05 pts/0    00:00:00 bash /challenge/run
root         155     153  0 22:05 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{Y9QGahJFLPhRHWzgaRo7wzJX1Wu.QX1QDO0wSN4AzNzEzW}
```

## Flag :
```sh
pwn.college{Y9QGahJFLPhRHWzgaRo7wzJX1Wu.QX1QDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to suspend processes


# Challenge 6 : Resuming Processes

Usually, when you suspend processes, you'll want to resume them at some point. Otherwise, why not just terminate them? To resume processes, your shell provides the fg command, a builtin that takes the suspended process, resumes it, and puts it back in the foreground of your terminal.

Go try it out! This challenge's run needs you to suspend it, then resume it. Good luck!

## Solution : 
- Step 1 : Open the terminal
- Step 2 : Run the command, suspend it and then resume it
- Step 3 : Copy and paste the flag
```sh
hacker@processes~resuming-processes:~$ /challenge/run 
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with 
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{c97KAd0j3DovT3RBd1noC4LWc7C.QX2QDO0wSN4AzNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```

## Flag :
```sh
pwn.college{c97KAd0j3DovT3RBd1noC4LWc7C.QX2QDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to resume suspended processes


# Challenge 7 : Backgrounding Processes

You've resumed processes in the foreground with the fg command. You can also resume processes in the background with the bg command! This will allow the process to keep running, while giving you your shell back to invoke more commands in the meantime.

This level's run wants to see another copy of itself running, not suspended, and using the same terminal. How? Use the terminal to launch it, then suspend it, then background it with bg and launch another copy while the first is running in the background!

ARCANUM: If you're interested in some deeper details, check out how to view the differences between suspended and backgrounded properties! Allow me to demonstrate. First, let's suspend a sleep:

## Solution : 
- Step 1 : Open the terminal
- Step 2 :
- Step 3 : Copy and paste the flag
```sh
hacker@processes~backgrounding-processes:~$ /challenge/run 
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S+   bash /challenge/run
root         148 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the 
background, and then launch a new version of me! You can background me with 
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to 
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run 
I'll only give you the flag if there's already another copy of me running *and 
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         146 S    bash /challenge/run
root         156 S    sleep 6h
root         157 S+   bash /challenge/run
root         159 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{Y1oakXW1CZa_MnmNotxnpSrm6a5.QX3QDO0wSN4AzNzEzW}
```

## Flag :
```sh
pwn.college{Y1oakXW1CZa_MnmNotxnpSrm6a5.QX3QDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt about backgrounding processes


# Challenge 8 : Foregrounding Processes

Imagine that you have a backgrounded process, and you want to mess with it some more. What do you do? Well, you can foreground a backgrounded process with fg just like you foreground a suspended process! This level will walk you through that!

## Solution : 
- Step 1 : Open the terminal
- Step 2 : Run the command, suspend it, backgrounf it and then foreground it as directed 
- Step 3 : Copy and paste the flag
```sh
hacker@processes~foregrounding-processes:~$ /challenge/run 
To pass this level, you need to suspend me, resume the suspended process in the 
background, and *then* foreground it without re-suspending it! You can 
background me with Ctrl-Z (and resume me in the background with 'bg') or, if 
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$ 


Yay, I'm now running the background! Because of that, this text will probably 
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times 
to scroll this text out. After that, resume me into the foreground with 'fg'; 
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{AqmR8nJqL-JV87PBLuu_jcFayxY.QX4QDO0wSN4AzNzEzW}
```

## Flag :
```sh
pwn.college{AqmR8nJqL-JV87PBLuu_jcFayxY.QX4QDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt about foregrounding already backgrounded processes


# Challenge 9 : Starting Backgrounded Processes

Of course, you don't have to suspend processes to background them: you can start them backgrounded right off the bat! It's easy; all you have to do is append a & to the command, like so:
```sh
hacker@dojo:~$ sleep 1337 &
[1] 1771
hacker@dojo:~$ ps -o user,pid,stat,cmd
USER         PID STAT CMD
hacker      1709 Ss   bash
hacker      1771 S    sleep 1337
hacker      1782 R+   ps -o user,pid,stat,cmd
hacker@dojo:~$ 
```
Here, sleep is actively running in the background, not suspended. Now it's your turn to practice! Launch /challenge/run backgrounded for the flag!

## Solution : 
- Step 1 : Open the terminal
- Step 2 : Run the command with the proper argunent to start it in the background
- Step 3 : Copy and paste the flag
```sh
hacker@processes~starting-backgrounded-processes:~$ /challenge/run  &
[1] 146
hacker@processes~starting-backgrounded-processes:~$ 


Yay, you started me in the background! Because of that, this text will probably 
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{cNLZlZysfJ0glgjUPds0rbUyCpO.QX5QDO0wSN4AzNzEzW}

[1]+  Done                    /challenge/run
```

## Flag :
```sh
pwn.college{cNLZlZysfJ0glgjUPds0rbUyCpO.QX5QDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to run a command which is already backgrounded from the start


# Challenge 10 : Process Exit Codes

Every shell command, including every program and every builtin, exits with an exit code when it finishes running and terminates. This can be used by the shell, or the user of the shell (that's you!) to check if the process succeeded in its functionality (this determination, of course, depends on what the process is supposed to do in the first place).

You can access the exit code of the most recently-terminated command using the special ? variable (don't forget to prepend it with $ to read its value!):
```sh
hacker@dojo:~$ touch test-file
hacker@dojo:~$ echo $?
0
hacker@dojo:~$ touch /test-file
touch: cannot touch '/test-file': Permission denied
hacker@dojo:~$ echo $?
1
hacker@dojo:~$
```
As you can see, commands that succeed typically return 0 and commands that fail typically return a non-zero value, most commonly 1 but sometimes an error code that identifies a specific failure mode.

In this challenge, you must retrieve the exit code returned by /challenge/get-code and then run /challenge/submit-code with that error code as an argument. Good luck!

## Solution : 
- Step 1 : Open the terminal
- Step 2 : Run the commands properly to first get the exit code for the command and then to input it as an argument for the next command
- Step 3 : Copy and paste the flag
```sh
hacker@processes~process-exit-codes:~$ echo /challenge/get-code $?
/challenge/get-code 120
hacker@processes~process-exit-codes:~$ /challenge/submit-code 120
CORRECT! Here is your flag:
pwn.college{I0_2Dq-IFOwWxdbzwryo97VvsL6.QX5YDO1wSN4AzNzEzW}
```

## Flag :
```sh
pwn.college{I0_2Dq-IFOwWxdbzwryo97VvsL6.QX5YDO1wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to access the exit codes of commands run
