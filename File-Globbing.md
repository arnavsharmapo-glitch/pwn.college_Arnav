# Challenge 1 : Matching with *
```sh
The first glob we'll learn is *. When it encounters a * character in any argument, the shell will treat it as a "wildcard" and try to replace that argument with any files that match the pattern. It's easier to show you than explain:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_*
Look: file_a file_b file_c
Of course, though in this case, the glob resulted in multiple arguments, it can just as simply match only one. For example:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: file_*
Look: file_a
When zero files are matched, by default, the shell leaves the glob unchanged:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ ls
file_a
hacker@dojo:~$ echo Look: nope_*
Look: nope_*
The * matches any part of the filename except for / or a leading . character. For example:

hacker@dojo:~$ echo ONE: /ho*/*ck*
ONE: /home/hacker
hacker@dojo:~$ echo TWO: /*/hacker
TWO: /home/hacker
hacker@dojo:~$ echo THREE: ../*
THREE: ../hacker
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use globbing to keep the argument you pass to cd to at most four characters! Once you're there, run /challenge/run for the flag!
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Change to the required directory using *
- Step 3 : Copy and paste the flag
```sh
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{42LcGOz4VCircIb02XRKQ1q8Mky.QXxIDO0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{42LcGOz4VCircIb02XRKQ1q8Mky.QXxIDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt about file globbing using *


# Challenge 2 : Matching with ?
```sh
Next, let's learn about ?. When it encounters a ? character in any argument, the shell will treat it as a single-character wildcard. This works like *, but only matches one character. For example:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_cc
hacker@dojo:~$ ls
file_a	file_b	file_cc
hacker@dojo:~$ echo Look: file_?
Look: file_a file_b
hacker@dojo:~$ echo Look: file_??
Look: file_cc
Now, practice this yourself! Starting from your home directory, change your directory to /challenge, but use the ? character instead of c and l in the argument to cd! Once you're there, run /challenge/run for the flag!
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Change to the required directory using ?
- Step 3 : Copy and paste the flag
```sh
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
This challenge resets your working directory to /home/hacker unless you change 
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{o9J_ZL4jFyaSCLBfJmDGayd5kgk.QXyIDO0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{o9J_ZL4jFyaSCLBfJmDGayd5kgk.QXyIDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt about file globbing using ?


# Challenge 3 : Matching with []
```sh
Next, we will cover []. The square brackets are, essentially, a limited form of ?, in that instead of matching any character, [] is a wildcard for some subset of potential characters, specified within the brackets. For example, [pwn] will match the character p, w, or n. For example:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
Try it here! We've placed a bunch of files in /challenge/files. Change your working directory to /challenge/files and run /challenge/run with a single argument that bracket-globs into file_b, file_a, file_s, and file_h!
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Change to the required directory using []
- Step 3 : Copy and paste the flag
```sh
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{Eq6fpwSzRhSzhxb6Zh3DZVYtqKZ.QXzIDO0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{Eq6fpwSzRhSzhxb6Zh3DZVYtqKZ.QXzIDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt about file globbing using []


# Challenge 4 : Matching paths with []
```sh
Globbing happens on a path basis, so you can expand entire paths with your globbed arguments. For example:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: /home/hacker/file_[ab]
Look: /home/hacker/file_a /home/hacker/file_b
Now it's your turn. Once more, we've placed a bunch of files in /challenge/files. Starting from your home directory, run /challenge/run with a single argument that bracket-globs into the absolute paths to the file_b, file_a, file_s, and file_h files!
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Change to the required directory using []
- Step 3 : Copy and paste the flag
```sh
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{YNfHASXe2LTNarcxC3ftiyo7WN7.QX0IDO0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{YNfHASXe2LTNarcxC3ftiyo7WN7.QX0IDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt about file globbing using [] and absolute paths


# Challenge 5 : Multiple Globs
```sh
So far, you've specified one glob at a time, but you can do more! Bash supports the expansion of multiple globs in a single word. For example:

hacker@dojo:~$ cat /*fl*
pwn.college{YEAH}
hacker@dojo:~$
What happens above is that the shell looks for all files in / that start with anything (including nothing), then have an f and an l, and end in anything (including ag, which makes flag).

Now you try it. We put a few happy, but diversely-named files in /challenge/files. Go cd there and run /challenge/run, providing a single argument: a short (3 characters or less) globbed word with two * globs in it that covers every word that contains the letter p.
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Change to the required directory using multiple globs
- Step 3 : Copy and paste the flag
```sh
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run p**
Your expansion did not expand to the requested files (happy optimistic pwning 
splendid uplifting).
Instead, it expanded to:
pwning
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run *p*
You got it! Here is your flag!
pwn.college{Y9cj0H1Yvv-pCSGYbAHb9SCkmhU.0lM3kjNxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{Y9cj0H1Yvv-pCSGYbAHb9SCkmhU.0lM3kjNxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt about multiple file globbing


# Challenge 6 : Mixing Globs
```sh
Now, let's put the previous levels together! We put a few happy, but diversely-named files in /challenge/files. Go cd there and, using the globbing you've learned, write a single, short (6 characters or less) glob that (when passed as an argument to /challenge/run) will match the files "challenging", "educational", and "pwning"!
```

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
Learnt about


# Challenge 7 : Exclusionary Globbing
```sh
Sometimes, you want to filter out files in a glob! Luckily, [] helps you do just this. If the first character in the brackets is a ! or (in newer versions of bash) a ^, the glob inverts, and that bracket instance matches characters that aren't listed. For example:

hacker@dojo:~$ touch file_a
hacker@dojo:~$ touch file_b
hacker@dojo:~$ touch file_c
hacker@dojo:~$ ls
file_a	file_b	file_c
hacker@dojo:~$ echo Look: file_[!ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[^ab]
Look: file_c
hacker@dojo:~$ echo Look: file_[ab]
Look: file_a file_b
Armed with this knowledge, go forth to /challenge/files and run /challenge/run with all files that don't start with p, w, or n!

NOTE: The ! character has a different special meaning in bash when it's not the first character of a [] glob, so keep that in mind if things stop making sense! ^ does not have this problem, but is also not compatible with older shells.
```

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
Learnt about


# Challenge 8 : Tab Completion
```sh
As tempting as it might be, using * to shorten what must be typed on the commandline can lead to mistakes. Your glob might expand to unintended files, and you might not spot it until the rm command is already running! No one is safe from this style of error.

A safer alternative when you are trying to specify a specific target is tab completion. If you hit tab in the shell, it'll try to figure out what you're going to type and automatically complete it. Auto-completion is super useful, and this challenge will explore its use in specifying files.

This challenge has copied the flag into /challenge/pwncollege, and you can freely cat that file. But you can't type the filename: we used some serious trickery to make sure that you must tab-complete it. Try it out!

hacker@dojo:~$ ls /challenge
DESCRIPTION.md  pwncollege
hacker@dojo:~$ cat /challenge/pwncollege
cat: /challenge/pwncollege: No such file or directory
hacker@dojo:~$ cat /challenge/pwn<TAB>
pwn.college{HECK YEAH}
hacker@dojo:~$
When you hit that tab key, the name will expand and you'll be able to read the file. Good luck!
```

## Solution :
- Step 1 : Open terminal
- Step 2 : Read the contents using tab completion
- Step 3 : Copy and paste the flag
```sh
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​ 
pwn.college{UftcMMsq7QaQfgkFXzKjtiLkNOD.0FN0EzNxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{UftcMMsq7QaQfgkFXzKjtiLkNOD.0FN0EzNxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt about using Tab completion for efficiency


# Challenge 9 : Multiple Options for Tab Completion
```sh
Consider the following situation:

hacker@dojo:~$ ls
flag  flamingo  flowers
hacker@dojo:~$ cat f<TAB>
There are multiple options! What happens?

What happens varies based on the specific shell and its options. By default bash will auto-expand until the first point when there are multiple options (in this case, fl). When you hit tab a second time, it'll print out those options. Other shells and configurations, instead, will cycle through the options.

This challenge has a /challenge/files directory with a bunch of files starting with pwncollege. Tab-complete from /challenge/files/p or so, and make your way to the flag!
```

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
Learnt about using


# Challenge 10 : Tab Completion on Commands
```sh
Tab completion is for more than files! You can also tab-complete commands. This level has a command that starts with pwncollege, and it'll give you the flag. Type pwncollege and hit the tab key to auto-complete it!

NOTE: You can auto-complete any command, but be careful: callous auto-completes without double-checking the result can wreak havoc in your shell if you accidentally run the wrong commands!
```

## Solution :
- Step 1 : Open terminal
- Step 2 : 
- Step 3 : Copy and paste the flag
```sh
hacker@globbing~tab-completion-on-commands:~$ pwncollege-27423 
Correct! Here is your flag:
pwn.college{sDcb-Cj6epSKFgSWDrQUiSBJb09.0VN0EzNxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{sDcb-Cj6epSKFgSWDrQUiSBJb09.0VN0EzNxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt about using tab completion on commands
