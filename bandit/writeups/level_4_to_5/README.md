### Discription:
```txt
The password for the next level is stored in the only human-readable file in the inhere directory.
Tip: if your terminal is messed up, try the “reset” command.
```

---

Just like the previous levels we ssh into the server using:
```zsh
$ ssh bandit.labs.overthewire.org -l bandit4 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `pIwrPrtPN36QITSp3EQaw936yaFoFgAB`_

<br>

Now, as per the discription of the level, we navigate to the `inhere` directory using the [`cd`](https://linux.die.net/man/1/cd) command:

```zsh
bandit4@bandit:~$ cd inhere/
```

Next, we need to find which of these files is human readable. We can use the [`file`](https://linux.die.net/man/1/file) command to see what type of file is the odd one out:

```zsh
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
```

`-file07` is the only file which consists of ASCII text, and hence contains the password in accordance with the level discription.

We can then use the [`cat`](https://linux.die.net/man/1/cat) command to display the contents of `-file07` to get the password for the next level:


```zsh
bandit4@bandit:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```

---

##### Password for next level:
    koReBOKuIDDepwhWk7jZC0RTdopnAYKh

---

Link to the level: [Level 4 ➙ Level 5](https://overthewire.org/wargames/bandit/bandit5.html)
