### Discription:
```txt
The password for the next level can be retrieved by submitting the password of
the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read
the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’
command also works in this version of that command…
```

---

Just like the previous levels we ssh into the server using:
```zsh
$ ssh bandit.labs.overthewire.org -l bandit15 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `BfMYroe26WYalil77FoDi9qh59eK5xNr`_

<br>


Since the password is SSL encrypted, we can use [`openssl`](https://linux.die.net/man/1/openssl) to retrieve the password:


```zsh
bandit15@bandit:~$ openssl s_client -ign_eof -connect localhost:30001 --quiet
depth=0 CN = localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = localhost
verify return:1
BfMYroe26WYalil77FoDi9qh59eK5xNr
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd
```

---

##### Password for next level:
    cluFn7wTiGryunymYOu4RcffSxQluehd

---

Link to the level: [Level 15 ➙ Level 16](https://overthewire.org/wargames/bandit/bandit16.html)
