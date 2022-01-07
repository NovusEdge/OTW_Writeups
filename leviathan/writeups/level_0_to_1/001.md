
## Leviathan 0

To solve the challenge, first we ssh into the given host:

```console
novusedge@system:~$ ssh -l leviathan0 -p 2223 leviathan.labs.overthewire.org
```


Upon inspecting the home directory, we find that a directory named: `.backup`, can be accessed. Within is `bookmarks.html`.

```console
leviathan0@leviathan:~$ ls -la
total 24
drwxr-xr-x  3 root       root       4096 Aug 26  2019 .
drwxr-xr-x 10 root       root       4096 Aug 26  2019 ..
drwxr-x---  2 leviathan1 leviathan0 4096 Aug 26  2019 .backup
-rw-r--r--  1 root       root        220 May 15  2017 .bash_logout
-rw-r--r--  1 root       root       3526 May 15  2017 .bashrc
-rw-r--r--  1 root       root        675 May 15  2017 .profile


leviathan0@leviathan:~$ cat ./.backup/bookmarks.html | grep "flag"
leviathan0@leviathan:~$ cat ./.backup/bookmarks.html | grep "pass"
<DT><A HREF="http://leviathan.labs.overthewire.org/passwordus.html | This will be fixed later, the password for leviathan1 is rioGegei8m" ADD_DATE="1155384634" LAST_CHARSET="ISO-8859-1" ID="rdf:#$2wIU71">password to leviathan1</A>
```


The challenge is thus solved and the password for next level is: `rioGegei8m`
