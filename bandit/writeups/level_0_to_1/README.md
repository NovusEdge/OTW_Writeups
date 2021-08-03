### Discription:
```txt
The password for the next level is stored in a file called readme located in the
home directory.

Use this password to log into bandit1 using SSH.

Whenever you find a password for a level, use SSH (on port 2220) to log into
that level and continue the game.
```

---

Now as stated in the discription, and from the previous level, i.e. `level 0`, we have already logged onto the ssh server.

As the discription states, the password to next level is located in a file:`~/readme` on the ssh server. To display it's contents, we simply use:

```zsh
bandit0@bandit:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```

We can now use this password to log onto the next level's ssh server :)

PS: to exit the ssh server prompt, simply use the [`exit`](https://linux.die.net/man/2/exit) command.

---

##### Password Password for next level:
    boJ9jbbUNNfktd78OOpsqOltutMc3MY1

---

Link to the level: [Level 0 ➙ Level 1](https://overthewire.org/wargames/bandit/bandit1.html)
