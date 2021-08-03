### Discription:
```txt
The password for the next level is stored in the file "data.txt" next to the word "millionth"
```

---

Just like the previous levels we ssh into the server using:
```zsh
$ ssh bandit.labs.overthewire.org -l bandit7 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs`_

<br>

Keeping the level discription in mind, we can use the [`grep`](https://linux.die.net/man/1/grep) command to get the password for the next level:

```zsh
bandit7@bandit:~$ grep -H 'millionth' data.txt  2>&1
data.txt:millionth      cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

---

##### Password for next level:
    cvX2JJa4CFALtqS87jk27qwqGhBM9plV

---

Link to the level: [Level 7 ➙ Level 8](https://overthewire.org/wargames/bandit/bandit8.html)
