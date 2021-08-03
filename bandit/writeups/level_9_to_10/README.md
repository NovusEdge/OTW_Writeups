### Discription:
```txt
The password for the next level is stored in the file "data.txt"
in one of the few human-readable strings, preceded by several ‘=’ characters.
```

---

Just like the previous levels we ssh into the server using:
```zsh
$ ssh bandit.labs.overthewire.org -l bandit9 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR`_

<br>


Following the level discription, we can use the [`strings`](https://linux.die.net/man/1/strings) and [`grep`](https://linux.die.net/man/1/grep) to extract the password from `data.txt`

```zsh
bandit9@bandit:~$ strings data.txt | grep "=="
========== the*2i"4
========== password
Z)========== is
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```



---

##### Password for next level:
    truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

---

Link to the level: [Level 9 ➙ Level 10](https://overthewire.org/wargames/bandit/bandit10.html)
