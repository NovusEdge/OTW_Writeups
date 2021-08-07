### Discription:
```txt
Welcome to Krypton! The first level is easy. The following string encodes the
password using Base64:

S1JZUFRPTklTR1JFQVQ=

Use this password to log in to krypton.labs.overthewire.org with username
krypton1 using SSH on port 2231. You can find the files for other levels in /krypton/
```

---

We can simply decode the base64 string using [`base64`](https://linux.die.net/man/1/base64)

```zsh
$ echo "S1JZUFRPTklTR1JFQVQ=" | base64 --decode
KRYPTONISGREAT
```

---

##### Password for next level:
    KRYPTONISGREAT

---

Link to the level: [Level 0 ➙ Level 1](https://overthewire.org/wargames/krypton/krypton0.html)
