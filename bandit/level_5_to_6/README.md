### Discription:
```txt
The password for the next level is stored in a file somewhere under the "inhere" directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable
```

---

Just like the previous levels we ssh into the server using:
```zsh
$ ssh bandit.labs.overthewire.org -l bandit5 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `koReBOKuIDDepwhWk7jZC0RTdopnAYKh`_

<br>

Just as the level discription states, the password file is under the `inhere` directory, and has certain characterstics.

We'll test for each one-by-one:

```zsh
bandit5@bandit:~$ cd inhere/

# Listing all files undeer ~/inhere:
bandit5@bandit:~/inhere$ ls -la
total 88
drwxr-x--- 22 root bandit5 4096 May  7  2020 .
drwxr-xr-x  3 root root    4096 May  7  2020 ..
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere00
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere01
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere02
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere03
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere04
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere05
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere06
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere07
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere08

drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere09
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere10
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere11
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere12
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere13
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere14
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere15
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere16
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere17
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere18
drwxr-x---  2 root bandit5 4096 May  7  2020 maybehere19
```

<br>
<br>

Let's now check what type of stuff we have in `inhere` using the [`file`](file) command:

```zsh
bandit5@bandit:~/inhere$ file ./*
./maybehere00: directory
./maybehere01: directory
./maybehere02: directory
./maybehere03: directory
./maybehere04: directory
./maybehere05: directory
./maybehere06: directory
./maybehere07: directory
./maybehere08: directory
./maybehere09: directory
./maybehere10: directory
./maybehere11: directory
./maybehere12: directory
./maybehere13: directory
./maybehere14: directory
./maybehere15: directory
./maybehere16: directory
./maybehere17: directory
./maybehere18: directory
./maybehere19: directory
```

<br>
<br>

All of these directories are full of different files. We can now use the [`find`](https://linux.die.net/man/1/find) to find the desirable file.

```zsh
bandit5@bandit:~/inhere$ find . -type f -readable ! -executable -size 1033c
./maybehere07/.file2
```

<br>

We can now use the [`cat`](https://linux.die.net/man/1/cat) command to get the password for next level:

```zsh
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```

---

##### Password for next level:
    DXjZPULLxYr17uwoI01bNLQbtFemEgo7

---

Link to the level: [Level 5 ➙ Level 6](https://overthewire.org/wargames/bandit/bandit6.html)
