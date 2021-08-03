### Discription:
```txt
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
```

---

Just like the previous levels we ssh into the server using:
```zsh
$ ssh bandit.labs.overthewire.org -l bandit14 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e`_

<br>

As mentioned in the level discription, we can get the password for the next level by submitting the current password on `localhost:30000`.

For this we can use the [`telnet`](https://linux.die.net/man/1/telnet) command:

```zsh
bandit14@bandit:~$ telnet localhost 30000
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr

Connection closed by foreign host.
```


---

##### Password for next level:
    BfMYroe26WYalil77FoDi9qh59eK5xNr

---

Link to the level: [Level 14 ➙ Level 15](https://overthewire.org/wargames/bandit/bandit15.html)
