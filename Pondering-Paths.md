# Challenge 1 : The Root
```sh
Alright, so the filesystem starts at /. Under that, there are a whole mess of other directories, configuration files, programs, and, most importantly, flags. In this level, we've added a program right in /, called pwn, that will give you the flag. All you need to do for this level is to invoke this program!

You can invoke a program by providing its path on the command line. In this case, you'll be giving the exact path, starting from /, so the path would be /pwn. This style of path, one that starts with the root directory, is referred to as an "absolute path".

Start the challenge, launch a terminal, invoke the pwn program using its absolute path, and Capture that Flag! Good luck!
```

## Solution :
Step 1 : Open Terminal
Step 2 : Write the absolute path to get the flag
Step 3 : Copy and Paste the flag
```sh
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{ANZSXeUVUqZgtvKzq2o7JNR0eag.QX4cTO0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{ANZSXeUVUqZgtvKzq2o7JNR0eag.QX4cTO0wSN4AzNzEzW}
```

### Reference :
None

### Notes :
Understood what a root, directory, path and an absolute path is.


# Challenge 2 : Program and Absolute Paths
```sh
Let's explore a slightly more complicated path! Except for in the previous level, challenges in pwn.college are in the challenge directory and the challenge directory is, in turn, right in the root directory (/). The path to the challenge directory is, thus, /challenge. The name of the challenge program in this level is run, and it lives in the /challenge directory. Thus, the path to the run challenge program is /challenge/run.

This challenge again requires you to execute it by invoking its absolute path. You'll want to execute the run file that is in the challenge directory that is, in turn, in the / directory. If you invoke the challenge correctly, it will give you the flag. Good luck!
```

## Solution : 
Step 1 : Open Terminal
Step 2 : Write the absolute path to get the flag
Step 3 : Copy and Paste the flag
```sh
hacker@paths~program-and-absolute-paths:~$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{I607yTD_eiWK-buYmdjjvuxd2QH.QX1QTN0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{I607yTD_eiWK-buYmdjjvuxd2QH.QX1QTN0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt that an absolute path includes all the branches it needs to get to a particular file.


# Challenge 3 : Position Thy Self
```sh
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!
```

## Solution : 
Step 1 : Open Terminal
Step 2 : Run the command to check which directory you need to change to
Step 3 : Change to that directory and run the command again to get you flag
Step 4 : Copy and Paste the flag
```sh
hacker@paths~position-thy-self:/$ cd
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /usr/include directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /usr/include
hacker@paths~position-thy-self:/usr/include$ cd/challenge/run
bash: cd/challenge/run: No such file or directory
hacker@paths~position-thy-self:/usr/include$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{Abd9vstt_evbXprRKEj9WRisPl3.QX2QTN0wSN4AzNzEzW}
hacker@paths~position-thy-self:/usr/include$ ^C
```

## Flag : 
```sh
pwn.college{Abd9vstt_evbXprRKEj9WRisPl3.QX2QTN0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to change to a particular directory to run commands in that or to find information within.


# Challenge 4 : Position Elsewhere
```sh
The Linux filesystem has tons of directories with tons of files. You can navigate around directories by using the cd (change directory) command and passing a path to it as an argument, as so:

hacker@dojo:~$ cd /some/new/directory
hacker@dojo:/some/new/directory$
This affects the "current working directory" of your process (in this case, the bash shell). Each process has a directory in which it's currently hanging out. The reasons for this will become clear later in the module.

As an aside, now you can see what the ~ was in the prompt! It shows the current path that your shell is located at.

This challenge will require you to execute the /challenge/run program from a specific path (which it will tell you). You'll need to cd to that directory before rerunning the challenge program. Good luck!
```

## Solution : 
