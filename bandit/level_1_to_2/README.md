### Discription:
```txt
The password for the next level is stored in a file called - located in the home directory
```
---

According to the level discription, the password to the next level is in a file called: `-`, with path: `~/-`. i.e. located in the home directory.

<br>
<br>

First we need to log into the ssh server using the [`ssh`](https://linux.die.net/man/1/ssh) command like so:

```zsh
$ ssh bandit.labs.overthewire.org -l bandit1 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `boJ9jbbUNNfktd78OOpsqOltutMc3MY1`_

<br>

We're greeted with the following prompt:

```zsh
bandit1@bandit:~$
```

<br>
<br>

First, let we see what files are under the home directory:

###### Command:
```zsh
bandit1@bandit:~$ ls -l
```

###### Output:
```
total 4
-rw-r----- 1 bandit2 bandit1 33 May  7  2020 -
```


<br>
<br>


Now, following the level discription, we can use the following to get the password from the `-` file.

```zsh
bandit1@bandit:~$ cat ~/-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```

We can now proceed to the next level. :D

---

##### Password for next level:
    CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

---

Link to the level: [Level 1 ➙ Level 2](https://overthewire.org/wargames/bandit/bandit2.html)
