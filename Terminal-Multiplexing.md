# Challenge 1 : Launching Screen

Let's dive right in!

screen is a program that creates virtual terminals inside your terminal. It's somewhat like having multiple browser tabs, but for your command line!

Starting screen is super simple:
```sh
hacker@dojo:~$ screen
```
That's it! You're now inside a screen session. It looks exactly like a terminal, but there are new capabilities there, waiting to be discovered.

For this challenge, we've hooked things up so that just launching screen will get you the flag. Easy!

NOTE: When you're done with your command line, type exit or press Ctrl-D to leave the screen session. Then screen will terminate and return you to your original shell.

## Solution :
- Step 1 : Open terminal
- Step 2 : Launch a screen to get the flag
- Step 3 : Copy and paste the flag

```sh
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{0xaA_85snWNxAKpCKMsHFjviY_c.0VN4IDOxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{0xaA_85snWNxAKpCKMsHFjviY_c.0VN4IDOxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt how to launch screens


# Challenge 2 : Detatching and Attatching

Now we'll start digging in with the magic of detaching!

Imagine you're working on something important over a remote connection, and your connection drops. With a normal terminal (outside of this awesome dojo environment), everything's gone. With screen, your work keeps running, and you can reattach later!

You can also detach on purpose, which we'll do in this challenge. You detach by pressing Ctrl-A, followed by d (for detach). This leaves your session running in the background while you return to your normal terminal.
```sh
hacker@dojo:~$ screen
[doing some work...]
[Press Ctrl-A, then d]
[detached from 12345.pts-0.hostname]
hacker@dojo:~$ 
```
To reattach, you can use the -r argument to screen:

hacker@dojo:~$ screen -r
For this challenge, you'll need to:

- 1. Launch screen
- 2. Detach from it.
- 3. Run /challenge/run (this will secretly send the flag to your detached session!)
- 4. Reattach to see your prize
FUN FACT: Ctrl-A is screen's activation key for all of its shortcuts in its default configuration. All screen functionality is activated by some command combination starting with Ctrl-A.

HINT: Remember: Hold Ctrl and press A, then release both and press d.

HINT: If you see [detached from...], you did it right!

## Solution :
- Step 1 : Open terminal
- Step 2 :
- Step 3 : Copy and paste the flag

```sh
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
[detached from 139.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 139.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{8E4XGriNe93x_T0RzA9TrGvWVLS.0lN4IDOxwSN4AzNzEzW}
Yes! Flag is: pwn.college{8E4XGriNe93x_T0RzA9TrGvWVLS.0lN4IDOxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{8E4XGriNe93x_T0RzA9TrGvWVLS.0lN4IDOxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt how to detatch and reattatch to the screen


# Challenge 3 : Findong Sessions

Time for some screen detective work!

If you become an avid screen user, you will inevitably end up with multiple sessions running. How do you find the right one to reattach to?

Well, we can list them:
```sh
hacker@dojo:~$ screen -ls
There are screens on:
        23847.mysession   (Detached)
        23851.goodwork    (Detached)
        23855.morework    (Detached)
3 Sockets in /run/screen/S-hacker.
```
The identifiers of the sessions are the PID of each respective screen process, a dot, and the name of the screen session. To attach to a specific one, you use its name or its PID by giving it as an argument to screen -r.
```sh
hacker@dojo:~$ screen -r goodwork
```
In this challenge, we've created three screen sessions for you. One of them contains the flag. The other two are decoys!

You'll need to check each one until you find it. Don't forget to detach (Ctrl-A d) before trying the next session!

## Solution :
- Step 1 : Open terminal
- Step 2 : Check all screens and then run the right one to get the flag
- Step 3 : Copy and paste the flag

```sh
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        151.pts-0.terminal-multiplexing~launching-screen        (Remote or dead)
        139.pts-0.terminal-multiplexing~detaching-and-attaching (Remote or dead)
        144.session_45ac95ef52c98a43    (Detached)
        147.session_43a422d443a69ba9    (Detached)
        150.session_b85cbaad969c62a8    (Detached)
5 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r 144.session_45ac95ef52c98a43
[detached from 144.session_45ac95ef52c98a43]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r  147.session_43a422d443a69ba9
[detached from 147.session_43a422d443a69ba9]
hacker@terminal-multiplexing~finding-sessions:~$ screen -r   150.session_b85cbaad969c62a8
hacker@terminal-multiplexing~finding-sessions:~$  echo 'Congratulations! You found the right session!'
Congratulations! You found the right session!
hacker@terminal-multiplexing~finding-sessions:~$  echo pwn.college{8cP0LnLtaTEkHObSLGUuqEHQn40.01N4IDOxwSN4AzNzEzW}
pwn.college{8cP0LnLtaTEkHObSLGUuqEHQn40.01N4IDOxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{8cP0LnLtaTEkHObSLGUuqEHQn40.01N4IDOxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt


# Challenge 4 : Switching Windows

Okay, so far, screen is just a weird sort of terminal-with-a-terminal. But it can be much more!

Inside a single screen session, you can have multiple windows, like your browser has multiple tabs. This can be super handy for organizing different tasks!

These windows are handled with different keyboard shortcuts, all starting with Ctrl-A:

- Ctrl-A c - Create a new window
- Ctrl-A n - Next window
- Ctrl-A p - Previous window
- Ctrl-A 0 through Ctrl-A 9 - Jump directly to window 0-9
- Ctrl-A " - bring up a selection menu of all of the windows
For this challenge, we've set up a screen session with two windows:

- Window 0 has... well, you'll have to switch there to find out!
- Window 1 has a welcome message
Attach to the session with screen -r, then use one of the key combinations above to switch to Window 1. Go get that flag!

## Solution :
- Step 1 : Open terminal
- Step 2 :
- Step 3 : Copy and paste the flag

```sh
hacker@terminal-multiplexing~switching-windows:~$ screen -r
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Welcome to the window switching challenge!
> You are currently in window 1.
> The flag is hidden in window 0.
> Use Ctrl-A 0 to switch to window 0!
> MSG
hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{QzcLYg21T_qPz6aFlPlQqZOJvYr.0FO4IDOxwSN4AzNzEzW}
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{QzcLYg21T_qPz6aFlPlQqZOJvYr.0FO4IDOxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{QzcLYg21T_qPz6aFlPlQqZOJvYr.0FO4IDOxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt how to switch windows in screen


# Challenge 5 : Detatching and Attatching (tmux)

Let's try the same thing with tmux!

tmux (terminal multiplexer) is screen's younger, more modern cousin. It does all the same things but with some different key bindings. The biggest difference? Instead of Ctrl-A, tmux uses Ctrl-B as its command prefix.

So to detach from tmux, you press Ctrl-B followed by d.
```sh
hacker@dojo:~$ tmux
[doing some work...]
[Press Ctrl-B, then d]
[detached (from session 0)]
hacker@dojo:~$ 
```
The commands also differ:

- tmux ls - List sessions
- tmux attach or tmux a - Reattach to session
For this challenge:

- Launch tmux
- Detach from it.
- Run /challenge/run (this will send the flag to your detached session!)
- Reattach to see your prize

## Solution :
- Step 1 : Open terminal
- Step 2 : Run the tmux, detach and run the correct commands to get your flag
- Step 3 : Copy and paste the flag

```sh
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{ggJbC3JZCszQ0Pz118rc9qNuy7w.0VO4IDOxwSN4AzNzEzW}
Congratulations, here is your flag: pwn.college{ggJbC3JZCszQ0Pz118rc9qNuy7w.0VO4IDOxwSN4AzNzEzW}
```

## Flag : 
```sh
pwn.college{ggJbC3JZCszQ0Pz118rc9qNuy7w.0VO4IDOxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt how to detach and reattatch from a tmux window


# Challenge 6 : Switching Windows (tmux)

Let's learn to navigate windows in tmux!

Just like screen, tmux has windows. The key combos are different, but the concept is the same:

- Ctrl-B c - Create a new window
- Ctrl-B n - Next window
- Ctrl-B p - Previous window
- Ctrl-B 0 through Ctrl-B 9 - Jump to window 0-9
- Ctrl-B w - See a nice window picker
Tmux shows your windows at the bottom in a status bar that looks like:
```sh
[0] 0:bash* 1:bash
```
The * shows your current window, and each entry also shows the process that the window was created to run.

We've created a tmux session with two windows:

- Window 0 has the flag!
- Window 1 has your warm welcome.
Go get that flag!

## Solution :
- Step 1 : Open terminal
- Step 2 : Launch the tmux, open the window picker and go to page 0 to get the flag 
- Step 3 : Copy and paste the flag

```sh
hacker@terminal-multiplexing~switching-windows-tmux:~$ tmux
> MSG
Excellent work! You found window 0!
Here is your flag: pwn.college{EV4UvN7h_SCOZeg-ySKEhWGaBdM.0FM5IDOxwSN4AzNzEzW}  
```

## Flag : 
```sh
pwn.college{EV4UvN7h_SCOZeg-ySKEhWGaBdM.0FM5IDOxwSN4AzNzEzW}
```

### Reference : 
None

### Notes :
Learnt how to switch windows in tmux using the window picker
