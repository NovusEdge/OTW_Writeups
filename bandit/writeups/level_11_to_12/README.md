### Discription:
```txt
The password for the next level is stored in the file "data.txt",
where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
```

---

Just like the previous levels we ssh into the server using:
```zsh
$ ssh bandit.labs.overthewire.org -l bandit11 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR`_

<br>

The data in the file `data.txt` is encoded using [`ROT13`](https://en.wikipedia.org/wiki/ROT13), which can be decoded using the [`tr`](https://linux.die.net/man/1/tr) and the [`cat`](https://linux.die.net/man/1/cat) commands.

```zsh
bandit11@bandit:~$ cat data.txt | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

---

##### Password for next level:
    5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

---

Link to the level: [Level 11 ➙ Level 12](https://overthewire.org/wargames/bandit/bandit12.html)
