
## Leviathan 1

To solve the challenge, first we ssh into the given host:

```console
novusedge@system:~$ ssh -l leviathan1 -p 2223 leviathan.labs.overthewire.org
```


Upon logging in, and listing files in `~`, we notice that there's a file called, `check`.
`check` is an executable.

```console
leviathan1@leviathan:~$ ls -la
total 28
drwxr-xr-x  2 root       root       4096 Aug 26  2019 .
drwxr-xr-x 10 root       root       4096 Aug 26  2019 ..
-rw-r--r--  1 root       root        220 May 15  2017 .bash_logout
-rw-r--r--  1 root       root       3526 May 15  2017 .bashrc
-r-sr-x---  1 leviathan2 leviathan1 7452 Aug 26  2019 check
-rw-r--r--  1 root       root        675 May 15  2017 .profile
leviathan1@leviathan:~$ file check
check: setuid ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=c735f6f3a3a94adcad8407cc0fda40496fd765dd, not stripped
```


Sample run of check:


```console
leviathan1@leviathan:~$ ./check
password: password
Wrong password, Good Bye ...
```

Using `ltrace` to examine this executable...


```console
leviathan1@leviathan:~$ ltrace ./check
__libc_start_main(0x804853b, 1, 0xffffd694, 0x8048610 <unfinished ...>
printf("password: ")                                            = 10
getchar(1, 0, 0x65766f6c, 0x646f6700password: password
)                           = 112
getchar(1, 0, 0x65766f6c, 0x646f6700)                           = 97
getchar(1, 0, 0x65766f6c, 0x646f6700)                           = 115
strcmp("pas", "sex")                                            = -1
puts("Wrong password, Good Bye ..."Wrong password, Good Bye ...
)                            = 29
+++ exited (status 0) +++
```

The checking of the password string can be seen here:


```c
strcmp("pas", "sex")                                            = -1
```

So we now know that the password is: `sex` (haha)



```console
leviathan1@leviathan:~$ ./check
password: sex
$ whoami
leviathan2
```

Entering the correct password gives us access to a shell, which is as user: `leviathan2`.
Since we have the credentials to access the password in `/etc/leviathan_pass` for this level, we have our flag:


```console
$ cat /etc/leviathan_pass/leviathan2
ougahZi8Ta
```
