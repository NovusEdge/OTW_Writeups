### Discription:
```txt
The password for the next level is stored in a hidden file in the "inhere" directory.
```

---

Just like the previous levels we ssh into the server using:
```zsh
$ ssh bandit.labs.overthewire.org -l bandit3 -p 2220
```
_You'll need to pass in the password from the previous level, i.e.: `UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK`_

<br>

Now, as per the discription of the level, we navigate to the `inhere` directory using the [`cd`](https://linux.die.net/man/1/cd) command.

```zsh
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$
```

<br>

Since we've been given the hint that the file is "hidden", we can use the [`ls`](https://linux.die.net/man/1/ls) command with the `-a` flag to display all files within the directory.

```zsh
bandit3@bandit:~/inhere$ ls -a
.  ..  .hidden
```

There it is. The hidden file's named: `.hidden`

<br>

Once again using the [`cat`](https://linux.die.net/man/1/cat) command we can display the password for the next level:

```zsh
bandit3@bandit:~/inhere$ cat ./.hidden
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

---

##### Password for next level:
    pIwrPrtPN36QITSp3EQaw936yaFoFgAB

---

Link to the level: [Level 3 ➙ Level 4](https://overthewire.org/wargames/bandit/bandit4.html)
