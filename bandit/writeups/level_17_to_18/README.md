### Description:
```txt
There are 2 files in the home-directory: passwords.old and passwords.new. The
password for the next level is in passwords.new and is the only line that has been
changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into
bandit18, this is related to the next level, bandit19
```

---

Just like the previous levels we ssh into the server using:
```console
$ sudo ssh -i sshkey.private bandit17@bandit.labs.overthewire.org -p 2220
```

_You'll need to use the Private RSA key from the previous level, I've put it in the `sshkey.private` file_

<br>

We can use the [`diff`](https://linux.die.net/man/1/diff) tool to get the only line that is different in the 2 files: `password.new` and `password.old`

```console
$ diff passwords.old passwords.new
42c42
< w0Yfolrc5bwjS4qw5mq1nnQi6mF03bii
---
> kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
```

And there we have the password :)
---



##### Password for next level:
    kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd

---

Link to the level: [Level 17 ➙ Level 18](https://overthewire.org/wargames/bandit/bandit18.html)
