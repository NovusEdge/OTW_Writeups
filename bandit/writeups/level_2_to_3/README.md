### Discription:
```txt
The password for the next level is stored in a file called "spaces in
this filename" located in the home directory
```

---

Just like the previous level, we'll log onto the ssh server using the [`ssh`](https://linux.die.net/man/1/ssh) commmand:

```zsh
$ ssh bandit.labs.overthewire.org -l bandit2 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9`_

<br>

As the level discription states, we know that the password for the next level is in the directory: `spaces in the filename`.

Sure enough, using the [`ls`](https://linux.die.net/man/1/ls) command, we can see that such a directory does exist, and we can use the [`cat`](https://linux.die.net/man/1/cat) command to display it's contents:

```zsh
bandit2@bandit:~$ ls -l
total 4
-rw-r----- 1 bandit3 bandit2 33 May  7  2020 spaces in this filename

bandit2@bandit:~$ cat spaces\ in\ this\ filename
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```

Alternativey, one may also use:
```zsh
bandit2@bandit:~$ cat "spaces in this filename"
```

We can now move to the next level. :)

---

##### Password for next level:
    UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

---

Link to the level: [Level 2 ➙ Level 3](https://overthewire.org/wargames/bandit/bandit3.html)
