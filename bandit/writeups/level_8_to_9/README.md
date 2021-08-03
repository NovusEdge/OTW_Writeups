### Discription:
```txt
The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
```

---

Just like the previous levels we ssh into the server using:
```zsh
$ ssh bandit.labs.overthewire.org -l bandit8 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `cvX2JJa4CFALtqS87jk27qwqGhBM9plV`_

<br>


As mentioned in the level discription, we know that the password is the only unique text line that occurs in the file: `~/data.txt`

We can do this by using a mix of the [`uniq`](https://linux.die.net/man/1/uniq), [`sort`](https://linux.die.net/man/1/sort) and [`grep`](https://linux.die.net/man/1/grep) commands:


```zsh
bandit8@bandit:~$ sort data.txt | uniq -c | grep "1 "
      1 UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

---

##### Password for next level:
    UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

---

Link to the level: [Level 8 ➙ Level 9](https://overthewire.org/wargames/bandit/bandit9.html)
