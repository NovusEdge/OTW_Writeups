### Discription:
```txt
The password for level 2 is in the file ‘krypton2’. It is ‘encrypted’ using a
simple rotation. It is also in non-standard ciphertext format. When using
alpha characters for cipher text it is normal to group the letters into 5
letter clusters, regardless of word boundaries. This helps obfuscate any
patterns. This file has kept the plain text word boundaries and carried them
to the cipher text. Enjoy!
```

---

We'll first log onto `krypton.labs.overthewire.org` for the current level using [`ssh`](https://linux.die.net/man/1/ssh):

```zsh
$ ssh krypton.labs.overthewire.org -l krypton1 -p 2231
```

_You'll need to pass in the password from the previous level, i.e.: `KRYPTONISGREAT`_


Successful login will present with the following prompt:
```zsh
krypton1@krypton:~$
```

<br>
<br>

Most of the files for the passwords are stored in `/krypton/`, so we can check that out:

```zsh
krypton1@krypton:~$ cd /krypton/
krypton1@krypton:/krypton$ ls
krypton1  krypton2  krypton3  krypton4  krypton5  krypton6
```

Now, we'll check out the `krypton1` directory and try and find/decrypt the flag from the files within:

```zsh
krypton1@krypton:/krypton$ cd krypton1
krypton1@krypton:/krypton/krypton1$ ls -l
total 8
-rw-r----- 1 krypton1 krypton1  26 May 19  2020 krypton2
-rw-r----- 1 krypton1 krypton1 882 May 19  2020 README

# Inspecting the contents of "krypton2"
krypton1@krypton:/krypton/krypton1$ cat krypton2
YRIRY GJB CNFFJBEQ EBGGRA
```

We can try and use rot13 decryption on the text:
```zsh
krypton1@krypton:/krypton/krypton1$ cat krypton2 | tr '[A-Za-z]' '[N-ZA-Mn-za-m]'
LEVEL TWO PASSWORD ROTTEN
```

---

##### Password for next level:
    ROTTEN

---

Link to the level: [Level 1 ➙ Level 2](https://overthewire.org/wargames/krypton/krypton1.html)
