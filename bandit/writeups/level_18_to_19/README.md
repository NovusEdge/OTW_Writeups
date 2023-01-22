### Discription:
```txt
The password for the next level is stored in a file readme in the 
homedirectory. Unfortunately, someone has modified .bashrc to log you out 
when you log in with SSH.
```

---

Just like the previous levels we ssh into the server using:
```shell-session
$ sudo ssh bandit18@bandit.labs.overthewire.org -p 2220
```

_You'll need to use the password: `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd` from the previous level_

<br>

As mentioned by the challenge description, the `.bashrc` file has been modified so that it kicks us out whenever we try and login with SSH. To work around this, we can just supply a command to be run to `ssh` so that it bypasses this "modification":

```shell-session
$ sudo ssh bandit18@bandit.labs.overthewire.org -p 2220 -t "/bin/sh"
bandit18@bandit.labs.overthewire.org's password: <Enter the password here>

$ ls
readme

$ cat readme
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```

---

##### Password for next level:
    IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x

---

Link to the level: [Level 18 ➙ Level 19](https://overthewire.org/wargames/bandit/bandit19.html)
