### Discription:
ROT13 is a simple substitution cipher.

Substitution ciphers are a simple replacement algorithm. In this example of a
substitution cipher, we will explore a ‘monoalphebetic’ cipher. Monoalphebetic
means, literally, “one alphabet” and you will see why.

This level contains an old form of cipher called a ‘Caesar Cipher’. A Caesar
cipher shifts the alphabet by a set number. For example:

plain:  a b c d e f g h i j k ...
cipher: G H I J K L M N O P Q ...

In this example, the letter ‘a’ in plaintext is replaced by a ‘G’ in the
ciphertext so, for example, the plaintext ‘bad’ becomes ‘HGJ’ in ciphertext.

The password for level 3 is in the file krypton3. It is in 5 letter group
ciphertext. It is encrypted with a Caesar Cipher. Without any further
information, this cipher text may be difficult to break. You do not have
direct access to the key, however you do have access to a program that will
encrypt anything you wish to give it using the key. If you think logically,
this is completely easy.

One shot can solve it!

Have fun.

Additional Information:

The encrypt binary will look for the keyfile in your current working
directory. Therefore, it might be best to create a working direcory in /tmp
and in there a link to the keyfile. As the encrypt binary runs setuid
krypton3, you also need to give krypton3 access to your working directory.

Here is an example:

```zsh
krypton2@melinda:~$ mktemp -d
/tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:~$ cd /tmp/tmp.Wf2OnCpCDQ
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ln -s /krypton/krypton2/keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
keyfile.dat
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ chmod 777 .
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ /krypton/krypton2/encrypt /etc/issue
krypton2@melinda:/tmp/tmp.Wf2OnCpCDQ$ ls
ciphertext  keyfile.dat
```

---

We'll first log onto `krypton.labs.overthewire.org` for the current level using [`ssh`](https://linux.die.net/man/1/ssh):

```zsh
$ ssh krypton.labs.overthewire.org -l krypton2 -p 2231
```

_You'll need to pass in the password from the previous level, i.e.: `ROTTEN`_


<br>

As stated in the example in the ctf discription, we follow the steps to give us access to the `encrypt` binary

```zsh
krypton2@krypton:~$ mktemp -d
/tmp/tmp.fj9b2Mlrp8
krypton2@krypton:~$ cd /tmp/tmp.fj9b2Mlrp8
krypton2@krypton:/tmp/tmp.fj9b2Mlrp8$ ln -s /krypton/krypton2/keyfile.dat
krypton2@krypton:/tmp/tmp.fj9b2Mlrp8$ chmod 777 .
krypton2@krypton:/tmp/tmp.fj9b2Mlrp8$ /krypton/krypton2/encrypt /etc/issue


krypton2@krypton:/tmp/tmp.fj9b2Mlrp8$ ls -l
total 8
-rw-r--r-- 1 krypton3 krypton2   21 Aug  9 12:23 ciphertext
lrwxrwxrwx 1 krypton2 krypton2   25 Aug  9 12:18 encrypt -> /krypton/krypton2/encrypt
lrwxrwxrwx 1 krypton2 root       29 Aug  9 12:15 keyfile.dat -> /krypton/krypton2/keyfile.dat
```

We already have the ciphertext, we just need to decode it :)

```zsh
krypton2@krypton:/tmp/tmp.fj9b2Mlrp8$ cat ciphertext
PQHGMZSZGXUZGJMEOUUZX
```



---

##### Password for next level:


---

Link to the level: [Level 2 ➙ Level 3](https://overthewire.org/wargames/krypton/krypton2.html)
