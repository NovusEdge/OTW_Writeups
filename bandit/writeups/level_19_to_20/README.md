### Description:
```txt
To gain access to the next level, you should use the setuid binary in the home-directory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit_pass), after you have used the setuid binary.
```

---
```console
$ sudo ssh -p 2220 bandit19@bandit.labs.overthewire.org
```

_You'll need to use the password from the previous level: `IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x`_

As mentioned in the description, let's check the binary in the home directory:

```console
bandit19@bandit:~$ ls
bandit20-do

bandit19@bandit:~$ file bandit20-do
bandit20-do: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=8e941f24b8c5cd0af67b22b724c57e1ab92a92a1, not stripped

bandit19@bandit:~$ ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do id
```

Let's check just one more thing:
```console
bandit19@bandit:~$ ./bandit20-do id
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
```

_Bingo_

We can see that the binary sets our `euid` to that of `bandit20`, so we can use it to get the password for the next level like so:

```console
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```

---

##### Password for next level:
    GbKksEFF4yrVs6il55v6gwY5aVje5f0j

---

Link to the level: [Level 19 ➙ Level 20](https://overthewire.org/wargames/bandit/bandit20.html)
