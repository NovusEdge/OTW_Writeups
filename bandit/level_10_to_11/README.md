### Discription:
```txt
The password for the next level is stored in the file "data.txt",
which contains base64 encoded data
```

---


Just like the previous levels we ssh into the server using:
```zsh
$ ssh bandit.labs.overthewire.org -l bandit10 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk`_

<br>


As stated in the level discription, we have been given a file with [base64](https://en.wikipedia.org/wiki/Base64) encoded data, i.e. the password.

Let's first have a look at the raw base64 encoded data:

```zsh
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIElGdWt3S0dzRlc4TU9xM0lSRnFyeEUxaHhUTkViVVBSCg==
```

<br>

To get the decoded password, we'll use the [`base64`](https://linux.die.net/man/1/base64) command/tool.

```zsh
bandit10@bandit:~$ base64 -d data.txt
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

---

##### Password for next level:
    IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

---

Link to the level: [Level 10 ➙ Level 11](https://overthewire.org/wargames/bandit/bandit11.html)
