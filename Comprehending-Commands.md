# Challenge 1 : cat: not the pet, but the command
```sh
One of the most critical Linux commands is cat. cat is most often used for reading out files, like so:

hacker@dojo:~$ cat /challenge/DESCRIPTION.md
One of the most critical Linux commands is `cat`.
`cat` is most often used for reading out files, like so:
cat will concatenate (hence the name) multiple files if provided multiple arguments. For example:

hacker@dojo:~$ cat myfile
This is my file!
hacker@dojo:~$ cat yourfile
This is your file!
hacker@dojo:~$ cat myfile yourfile
This is my file!
This is your file!
hacker@dojo:~$ cat myfile yourfile myfile
This is my file!
This is your file!
This is my file!
Finally, if you give no arguments at all, cat will read from the terminal input and output it. We'll explore that in later challenges...

In this challenge, I will copy the flag to the flag file in your home directory (where your shell starts). Go read it with cat!
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Read the flag directory using the cat command
- Step 3 : Copy and paste the flag
```sh
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{wVJ0kczBQkOMgXn6EJbLR4O3mJZ.QXxcTN0wSN4AzNzEzW}
hacker@commands~cat-not-the-pet-but-the-command:~$ ^C
```

## Flag : 
```sh
pwn.college{wVJ0kczBQkOMgXn6EJbLR4O3mJZ.QXxcTN0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to read out files directly from terminal


# Challenge 2 : Catting Absolute Paths
```sh
In the last level, you did cat flag to read the flag out of your home directory! You can, of course, specify cat's arguments as absolute paths:

hacker@dojo:~$ cat /challenge/DESCRIPTION.md
In the last level, you did `cat flag` to read the flag out of your home directory!
You can, of course, specify `cat`'s arguments as absolute paths:
...
In this directory, I will not copy it to your home directory, but I will make it readable. You can read it with cat at its absolute path: /flag.

FUN FACT: /flag is where the flag always lives in pwn.college, but unlike in this challenge, you typically can't access that file directly.
```

## Solution :
- Step 1 : Open terminal
- Step 2 : Read the flag directory using the cat command and absolute path
- Step 3 : Copy and paste the flag
```sh
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{M4ltSyjG5xUAHGGTsvOhj8VJ5A6.QX5ETO0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{M4ltSyjG5xUAHGGTsvOhj8VJ5A6.QX5ETO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to read out files directly from terminal using absolute paths


# Challenge 3 : More Catting Practice
```sh
You can specify all sorts of paths as arguments to commands, and we'll practice some more with cat. In this level, I'll put the flag in some crazy directory, and I will not allow you to change directories with cd, so no cat flag for you. You must retrieve the flag by absolute path, wherever it is.
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Directly read the contents of the mentioned directory without switching over to it
- Step 3 : Copy and paste the flag
```sh
You cannot use the 'cd' command in this level, and must retrieve the flag by 
absolute path. Plus, I hid the flag in a different directory! You can find it 
in the file /usr/share/gedit/flag. Go cat it out **without** cding into that 
directory!
hacker@commands~more-catting-practice:~$ cat /usr/share/gedit/flag
pwn.college{gjDmeDk2v2A-kOc5hFO47VfLnfg.QXwITO0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{gjDmeDk2v2A-kOc5hFO47VfLnfg.QXwITO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to read out files directly without the need of switching over to its location directory


# Challenge 4 : Grepping for a needle in a Haystack
```sh
ometimes, the files that you might cat out are too big. Luckily, we have the grep command to search for the contents we need! We'll learn it in this challenge.

There are many ways to grep, and we'll learn one way here:

hacker@dojo:~$ grep SEARCH_STRING /path/to/file
Invoked like this, grep will search the file for lines of text containing SEARCH_STRING and print them to the console.

In this challenge, I've put a hundred thousand lines of text into the /challenge/data.txt file. grep it for the flag!

HINT: The flag always starts with the text pwn.college.
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Write the keywords along with the command to print out desired results from the directory
- Step 3 : Copy and paste the flag
```sh
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{ovwYe263OHYQcVVxLLVEFoTxVqp.QX3EDO0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{ovwYe263OHYQcVVxLLVEFoTxVqp.QX3EDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to search using keywords.


# Challenge 5 : Comparing Files
```sh
When looking for changes between similar files, eyeballing them might not be the most efficient approach! This is where the diff command becomes invaluable.

diff compares two files line by line and shows you exactly what's different between them. For example:

hacker@dojo:~$ cat file1
hello
world
hacker@dojo:~$ cat file2
hello
universe
hacker@dojo:~$ diff file1 file2
2c2
< world
---
> universe
The output tells us that line 2 changed (2c2), with world in the first file (<) being replaced by universe in the second file (>).

Sometimes, when new lines are added, you'll see something like:

hacker@dojo:~$ cat old
pwn
hacker@dojo:~$ cat new
pwn
college
hacker@dojo:~$ diff old new
1a2
> college
This tells us that after line 1 in the first file, the second file has an additional line (1a2 means "after line 1 of file1, add line 2 of file2").

Now for your challenge! There are two files in /challenge:

/challenge/decoys_only.txt contains 100 fake flags
/challenge/decoys_and_real.txt contains all 100 fake flags plus the one real flag
Use diff to find what's different between these files and get your flag!
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Using diff command, get the real flag
- Step 3 : Copy and paste the flag
```sh
hacker@commands~comparing-files:~$ diff /challenge/decoys_only.txt /challenge/decoys_and_real.txt
10a11
> pwn.college{weT0Qdn4L3cBTqF655d1MPNnqcQ.01MwMDOxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{weT0Qdn4L3cBTqF655d1MPNnqcQ.01MwMDOxwSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to find the difference between two files/ compare them


# Challenge 6 : Listing Files
```sh
So far, we've told you which files to interact with. But directories can have lots of files (and other directories) inside them, and we won't always be here to tell you their names. You'll need to learn to list their contents using the ls command!

ls will list files in all the directories provided to it as arguments, and in the current directory if no arguments are provided. Observe:

hacker@dojo:~$ ls /challenge
run
hacker@dojo:~$ ls
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$ ls /home/hacker
Desktop    Downloads  Pictures  Templates
Documents  Music      Public    Videos
hacker@dojo:~$
In this challenge, we've named /challenge/run with some random name! List the files in /challenge to find it.
```

## Solution :
- Step 1 : Open terminal
- Step 2 : List the files
- Step 3 : Run the command
- Step 4 : Copy and paste the flag
```sh
hacker@commands~listing-files:~$ ls /challenge
7017-renamed-run-10969  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/7017-renamed-run-10969
Yahaha, you found me! Here is your flag:
pwn.college{sUuSKtaBgofclCloXrknzIcgZ-e.QX4IDO0wSN4AzNzEzW}
hacker@commands~listing-files:~$ ^C
```

## Flag : 
```sh
pwn.college{sUuSKtaBgofclCloXrknzIcgZ-e.QX4IDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to list files


# Challenge 7 : Touching Files
```sh
Of course, you can also create files! There are several ways to do this, but we'll look at a simple command here. You can create a new, blank file by touching it with the touch command:

hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ touch pwnfile
hacker@dojo:/tmp$ ls
pwnfile
hacker@dojo:/tmp$
It's that simple! In this level, please create two files: /tmp/pwn and /tmp/college, and run /challenge/run to get your flag!
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Create the files
- Step 3 : Run the command
- Step 4 : Copy and paste the flag
```sh
hacker@commands~touching-files:~$ touch /tmp/pwn
hacker@commands~touching-files:~$ touch /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{UyVUANzYrpVzRAoBBId5pw1LYQ_.QXwMDO0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{UyVUANzYrpVzRAoBBId5pw1LYQ_.QXwMDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to create files


# Challenge 7 : Removing Files
```sh
Files are all around you. Like candy wrappers, there'll eventually be too many of them. In this level, we'll learn to clean up!

In Linux, you remove files with the rm command, as so:

hacker@dojo:~$ touch PWN
hacker@dojo:~$ touch COLLEGE
hacker@dojo:~$ ls
COLLEGE     PWN
hacker@dojo:~$ rm PWN
hacker@dojo:~$ ls
COLLEGE
hacker@dojo:~$
Let's practice. This challenge will create a delete_me file in your home directory! Delete it, then run /challenge/check, which will make sure you've deleted it and then give you the flag!
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Delete the required file
- Step 3 : Run the command
- Step 4 : Copy and paste the flag
```sh
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:
pwn.college{woCI0iPreHHJ2KugtvJQmL568x5.QX2kDM1wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{woCI0iPreHHJ2KugtvJQmL568x5.QX2kDM1wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to delete files


# Challenge 8 : Moving Files
```sh
You can also move files around with the mv command. The usage is simple:

hacker@dojo:~$ ls
my-file
hacker@dojo:~$ cat my-file
PWN!
hacker@dojo:~$ mv my-file your-file
hacker@dojo:~$ ls
your-file
hacker@dojo:~$ cat your-file
PWN!
hacker@dojo:~$
This challenge wants you to move the /flag file into /tmp/hack-the-planet (do it)! When you're done, run /challenge/check, which will check things out and give the flag to you.
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Move the mentioned file
- Step 3 : Run the command
- Step 4 : Copy and paste the flag
```sh
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{0PMFvuFhn621O1Vk1UytTixu09I.0VOxEzNxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{0PMFvuFhn621O1Vk1UytTixu09I.0VOxEzNxwSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to move files into another


# Challenge 9 : Hidden File
```sh
Interestingly, ls doesn't list all the files by default. Linux has a convention where files that start with a . don't show up by default in ls and in a few other contexts. To view them with ls, you need to invoke ls with the -a flag, as so:

hacker@dojo:~$ touch pwn
hacker@dojo:~$ touch .college
hacker@dojo:~$ ls
pwn
hacker@dojo:~$ ls -a
.college	pwn
hacker@dojo:~$
Now, it's your turn! Go find the flag, hidden as a dot-prepended file in /.
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : List all files
- Step 3 : Read the required file
- Step 4 : Copy and paste flag
```sh
hacker@commands~hidden-files:~$ ls /. -a
.   .dockerenv             bin   challenge  etc   lib    lib64   media  nix  proc  run   srv  tmp  var
..  .flag-101601727318242  boot  dev        home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~hidden-files:~$ cat /.flag-101601727318242
pwn.college{YG18rBcPS5WF81gAcqX9Qiut7hd.QXwUDO0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{YG18rBcPS5WF81gAcqX9Qiut7hd.QXwUDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to access files otherwise hidden


# Challenge 10 : An Epic Filesystem Quest
```sh
With your knowledge of cd, ls, and cat, we're ready to play a little game!

We'll start it out in /. Normally:

hacker@dojo:~$ cd /
hacker@dojo:/$ ls
bin   challenge  etc   home  lib32  libx32  mnt  proc  run   srv  tmp  var
boot  dev        flag  lib   lib64  media   opt  root  sbin  sys  usr
That's a lot of contents! One day, you will be quite familiar with them, but already, you might recognize the flag file and the challenge directory.

In this challenge, I have hidden the flag! Here, you will use ls and cat to follow my breadcrumbs and find it! Here's how it'll work:
Your first clue is in /. Head on over there.
Look around with ls. There'll be a file named HINT or CLUE or something along those lines!
cat that file to read the clue!
Depending on what the clue says, head on over to the next directory (or don't!).
Follow the clues to the flag!
Good luck!
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Keep using the ls -a, cat and cd command to get to the flag
- Step 3 : Copy and paste the flag
```sh
hacker@commands~an-epic-filesystem-quest:~$ ls /
INSIGHT  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin      challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:~$ cat /INSIGHT
Yahaha, you found me!
The next clue is in: /usr/local/lib/python3.8/dist-packages/sympy/simplify/tests/__pycache__

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ ^C
hacker@commands~an-epic-filesystem-quest:~$ ls /usr/local/lib/python3.8/dist-packages/sympy/simplify/tests/__pycache__ -a
.                             test_cse.cpython-38.pyc         test_hyperexpand.cpython-38.pyc  test_simplify.cpython-38.pyc
..                            test_epathtools.cpython-38.pyc  test_powsimp.cpython-38.pyc      test_sqrtdenest.cpython-38.pyc
.GIST                         test_fu.cpython-38.pyc          test_radsimp.cpython-38.pyc      test_trigsimp.cpython-38.pyc
__init__.cpython-38.pyc       test_function.cpython-38.pyc    test_ratsimp.cpython-38.pyc
test_combsimp.cpython-38.pyc  test_gammasimp.cpython-38.pyc   test_rewrite.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:~$ cat /.GIST
cat: /.GIST: No such file or directory
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/local/lib/python3.8/dist-packages/sympy/simplify/tests/__pycache__/.GIST
Yahaha, you found me!
The next clue is in: /opt/pwndbg/.venv/lib/python3.8/site-packages/pkg_resources/_vendor/platformdirs/__pycache__

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ ^C
hacker@commands~an-epic-filesystem-quest:~$ ls /opt/pwndbg/.venv/lib/python3.8/site-packages/pkg_resources/_vendor/platformdirs/__pycache__ -a
.   .README                  __main__.cpython-38.pyc  api.cpython-38.pyc    unix.cpython-38.pyc     windows.cpython-38.pyc
..  __init__.cpython-38.pyc  android.cpython-38.pyc   macos.cpython-38.pyc  version.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/pwndbg/.venv/lib/python3.8/site-packages/pkg_resources/_vendor/platformdirs/__pycache__/.README
Tubular find!
The next clue is in: /opt/linux/linux-5.4/arch/csky/abiv2
hacker@commands~an-epic-filesystem-quest:~$ ^C
hacker@commands~an-epic-filesystem-quest:~$ ls /opt/linux/linux-5.4/arch/csky/abiv2 -a
.   CLUE      cacheflush.c  inc       memcmp.S  memmove.S  strcmp.S  strksyms.c  sysdep.h
..  Makefile  fpu.c         mcount.S  memcpy.S  memset.S   strcpy.S  strlen.S
hacker@commands~an-epic-filesystem-quest:~$ cat /opt/linux/linux-5.4/arch/csky/abiv2/CLUE
Congratulations, you found the clue!
The next clue is in: /usr/share/icons/hicolor/128x128/stock/data
hacker@commands~an-epic-filesystem-quest:~$ ^C
hacker@commands~an-epic-filesystem-quest:~$ ls /usr/share/icons/hicolor/128x128/stock/data -a
.  ..  DOSSIER
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/share/icons/hicolor/128x128/stock/data/DOSSIER
Great sleuthing!
The next clue is in: /usr/lib/python3.8/lib2to3/pgen2/__pycache__

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:~$ ^C
hacker@commands~an-epic-filesystem-quest:~$ ls /usr/lib/python3.8/lib2to3/pgen2/__pycache__ -a
.   MEMO-TRAPPED             conv.cpython-38.pyc    grammar.cpython-38.pyc   parse.cpython-38.pyc  token.cpython-38.pyc
..  __init__.cpython-38.pyc  driver.cpython-38.pyc  literals.cpython-38.pyc  pgen.cpython-38.pyc   tokenize.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/lib/python3.8/lib2to3/pgen2/__pycache__/MEMO-TRAPPED
Great sleuthing!
The next clue is in: /usr/local/lib/python3.8/dist-packages/future/backports/html

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:~$ ^C
hacker@commands~an-epic-filesystem-quest:~$ ls /usr/local/lib/python3.8/dist-packages/future/backports/html -a
.  ..  .SNIPPET  __init__.py  __pycache__  entities.py  parser.py
hacker@commands~an-epic-filesystem-quest:~$ cat /usr/local/lib/python3.8/dist-packages/future/backports/html/.SNIPPET
Lucky listing!
The next clue is in: /usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/google

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:~$ ^C
hacker@commands~an-epic-filesystem-quest:~$ cd /usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/google
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/google$ ls /usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/google -a
.  ..  ALERT  __init__.pyi  protobuf
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/google$ cd /
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2and3/google/ALERT
Lucky listing!
The next clue is in: /usr/local/lib/python3.8/dist-packages/future/backports/email
hacker@commands~an-epic-filesystem-quest:/$ ^C
hacker@commands~an-epic-filesystem-quest:/$ ls /usr/local/lib/python3.8/dist-packages/future/backports/email -a
.       __init__.py        _header_value_parser.py  base64mime.py  errors.py      header.py          message.py  policy.py
..      __pycache__        _parseaddr.py            charset.py     feedparser.py  headerregistry.py  mime        quoprimime.py
NUGGET  _encoded_words.py  _policybase.py           encoders.py    generator.py   iterators.py       parser.py   utils.py
hacker@commands~an-epic-filesystem-quest:/$ cat /usr/local/lib/python3.8/dist-packages/future/backports/email/NUGGET
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{oJYmCK4_vvLkmbUxx94m771Ue8e.QX5IDO0wSN4AzNzEzW}
hacker@commands~an-epic-filesystem-quest:/$
```

### Reference : 
None

### Notes : 
Learnt how to persevere through challenges


# Challenge 11 : Making Directories
```sh
e can create files. How about directories? You make directories using the mkdir command. Then you can stick files in there!

Watch:

hacker@dojo:~$ cd /tmp
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ ls
hacker@dojo:/tmp$ mkdir my_directory
hacker@dojo:/tmp$ ls
my_directory
hacker@dojo:/tmp$ cd my_directory
hacker@dojo:/tmp/my_directory$ touch my_file
hacker@dojo:/tmp/my_directory$ ls
my_file
hacker@dojo:/tmp/my_directory$ ls /tmp/my_directory/my_file
/tmp/my_directory/my_file
hacker@dojo:/tmp/my_directory$
Now, go forth and create a /tmp/pwn directory and make a college file in it! Then run /challenge/run, which will check your solution and give you the flag!
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Create the directory
- Step 3 : Run the command
- Step 4 : Copy and paste the flag
```sh
hacker@commands~making-directories:~$ mkdir /tmp/pwn
hacker@commands~making-directories:~$ touch /tmp/pwn/college
hacker@commands~making-directories:~$ /challenge/run
Success! Here is your flag:
pwn.college{ofxNo6SCN9djC0laWnck6wQ1oLM.QXxMDO0wSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{ofxNo6SCN9djC0laWnck6wQ1oLM.QXxMDO0wSN4AzNzEzW}
```

### Reference : 
None

### Notes : 
Learnt how to make directories


# Challenge 12 : Finding Files
```sh
So now we know how to list, read, and create files. But how do we find them? We use the find command!

The find command takes optional arguments describing the search criteria and the search location. If you don't specify a search criteria, find matches every file. If you don't specify a search location, find uses the current working directory (.). For example:

hacker@dojo:~$ mkdir my_directory
hacker@dojo:~$ mkdir my_directory/my_subdirectory
hacker@dojo:~$ touch my_directory/my_file
hacker@dojo:~$ touch my_directory/my_subdirectory/my_subfile
hacker@dojo:~$ find
.
./my_directory
./my_directory/my_subdirectory
./my_directory/my_subdirectory/my_subfile
./my_directory/my_file
hacker@dojo:~$
And when specifying the search location:

hacker@dojo:~$ find my_directory/my_subdirectory
my_directory/my_subdirectory
my_directory/my_subdirectory/my_subfile
hacker@dojo:~$
And, of course, we can specify the criteria! For example, here, we filter by name:

hacker@dojo:~$ find -name my_subfile
./my_directory/my_subdirectory/my_subfile
hacker@dojo:~$ find -name my_subdirectory
./my_directory/my_subdirectory
hacker@dojo:~$
You can search the whole filesystem if you want!

hacker@dojo:~$ find / -name hacker
/home/hacker
hacker@dojo:~$
Now it's your turn. I've hidden the flag in a random directory on the filesystem. It's still called flag. Go find it!

Several notes. First, there are other files named flag on the filesystem. Don't panic if the first one you try doesn't have the actual flag in it. Second, there're plenty of places in the filesystem that are not accessible to a normal user. These will cause find to generate errors, but you can ignore those; we won't hide the flag there! Finally, find can take a while; be patient!
```

## Solution : 
- Step 1 : Open terminal
- Step 2 : Find your file
- Step 3 : Read the files to get the flag
- Step 4 : Copy and paste the flag
```sh
hacker@commands~finding-files:~$ find / -name flag
find: ‘/root’: Permission denied
find: ‘/etc/ssl/private’: Permission denied
find: ‘/tmp/tmp.TpSOPGOVKK’: Permission denied
/usr/local/lib/python3.8/dist-packages/pwnlib/flag
/usr/lib/jvm/java-17-openjdk-amd64/legal/jdk.internal.ed/flag
^C
hacker@commands~finding-files:~$ ^C
hacker@commands~finding-files:~$ cat /usr/local/lib/python3.8/dist-packages/pwnlib/flag
cat: /usr/local/lib/python3.8/dist-packages/pwnlib/flag: Is a directory
hacker@commands~finding-files:~$ ^C
hacker@commands~finding-files:~$ cat /usr/lib/jvm/java-17-openjdk-amd64/legal/jdk.internal.ed/flag
pwn.college{gdmyYms4rwQl9GI8CIS4GY9OFqs.QXyMDO0wSN4AzNzEzW}hacker@commands~finding-files:~$
```

## Flag : 
```sh
pwn.college{gdmyYms4rwQl9GI8CIS4GY9OFqs.QXyMDO0wSN4AzNzEzW}hacker@commands~finding-files:~$
```

### Reference : 
None

### Notes : 
Learnt how to use the find command


# Challenge 14 : Linking Files 
```sh
If you use Linux (or computers) for any reasonable length of time to do any real work, you will eventually run into some variant of the following situation: you want two programs to access the same data, but the programs expect that data to be in two different locations. Luckily, Linux provides a solution to this quandary: links.

Links come in two flavors: hard and soft (also known as symbolic) links. We'll differentiate the two with an analogy:

A hard link is when you address your apartment using multiple addresses that all lead directly to the same place (e.g., Apt 2 vs Unit 2).
A soft link is when you move apartments and have the postal service automatically forward your mail from your old place to your new place.
In a filesystem, a file is, conceptually, an address at which the contents of that file live. A hard link is an alternate address that indexes that data --- accesses to the hard link and accesses to the original file are completely identical, in that they immediately yield the necessary data. A soft/symbolic link, instead, contains the original file name. When you access the symbolic link, Linux will realize that it is a symbolic link, read the original file name, and then (typically) automatically access that file. In most cases, both situations result in accessing the original data, but the mechanisms are different.

Hard links sound simpler to most people (case in point, I explained it in one sentence above, versus two for soft links), but they have various downsides and implementation gotchas that make soft/symbolic links, by far, the more popular alternative.

In this challenge, we will learn about symbolic links (also known as symlinks). Symbolic links are created with the ln command with the -s argument, like so:

hacker@dojo:~$ cat /tmp/myfile
This is my file!
hacker@dojo:~$ ln -s /tmp/myfile /home/hacker/ourfile
hacker@dojo:~$ cat ~/ourfile
This is my file!
hacker@dojo:~$
You can see that accessing the symlink results in getting the original file contents! Also, you can see the usage of ln -s. Note that the original file path comes before the link path in the command!

A symlink can be identified as such with a few methods. For example, the file command, which takes a filename and tells you what type of file it is, will recognize symlinks:

hacker@dojo:~$ file /tmp/myfile
/tmp/myfile: ASCII text
hacker@dojo:~$ file ~/ourfile
/home/hacker/ourfile: symbolic link to /tmp/myfile
hacker@dojo:~$
Okay, now you try it! In this level the flag is, as always, in /flag, but /challenge/catflag will instead read out /home/hacker/not-the-flag. Use the symlink, and fool it into giving you the flag!
```

## Solution : 
- Step 1 : Open terminal
