### Description:
```txt
The password for the next level is stored in a file readme in the homedirectory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.
```

---

Since we cannot log into the server using ssh, we can just `cat` the contents of `readme`

```console
$ sudo ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme
```

_You'll need to use the password from the previous level: `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd`_

We get the password for the next level :)
---



##### Password for next level:
    IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x

---

Link to the level: [Level 18 ➙ Level 19](https://overthewire.org/wargames/bandit/bandit19.html)
