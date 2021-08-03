### Discription:
```txt
The password for the next level is stored in the file "data.txt",
which is a hexdump of a file that has been repeatedly compressed.

For this level it may be useful to create a directory under /tmp in which you can work using mkdir.
For example: mkdir /tmp/myname123.
Then copy the datafile using cp, and rename it using mv (read the manpages!)
```

---

Just like the previous levels we ssh into the server using:
```zsh
$ ssh bandit.labs.overthewire.org -l bandit12 -p 2220
```

_You'll need to pass in the password from the previous level, i.e.: `5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu`_

<br>

As mentioned in the level discription, the password/data in `data.txt` has been repeatedly compressed and is a hexdump, so we can use the [`xdd`](https://linux.die.net/man/1/xxd) command to de-hex it.

But first, we'll use the [`mkdir`](https://linux.die.net/man/1/mkdir), [`cp`](https://linux.die.net/man/1/cp), and [`mv`](https://linux.die.net/man/1/mv) commands to create a directory under `/tmp` and copy the data from `data.txt` there.

```zsh
# Creating a directory named "decomp_hex".
bandit12@bandit:~$ mkdir /tmp/decomp_hex
bandit12@bandit:~$ cd /tmp/decomp_hex

# Copying the file to /tmp/decomp_hex
bandit12@bandit:/tmp/decomp_hex$ cp ~/data.txt .

# Renaming it to "data_copied.txt"
bandit12@bandit:/tmp/decomp_hex$ mv data.txt data_copied.txt
```

<br>
<br>


Now, we'll use [`xdd`](https://linux.die.net/man/1/xxd) to de-hex the hexdump.

```zsh
bandit12@bandit:/tmp/decomp_hex$ xxd -r data_copied.txt > data_dehex.txt
```

<br>


Next we can check what type of a file `data_dehex.txt` is by using the [`file`](https://linux.die.net/man/1/xxd) command:

```zsh
bandit12@bandit:/tmp/decomp_hex$ file data_dehex.txt
data_dehex.txt: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
```

Since it is a [gzip](https://en.wikipedia.org/wiki/Gzip) file, we can use the [`gzip`](https://linux.die.net/man/1/gzip) command to decompress it:

```zsh
# For some reason, gzip won't decompress the file with txt extension so we rename it:
bandit12@bandit:/tmp/decomp_hex$ mv data_dehex.txt data_dehex.gz

# Decompressing the gzip file:
bandit12@bandit:/tmp/decomp_hex$ gzip --decompress data_dehex.gz
bandit12@bandit:/tmp/decomp_hex$ ls
data_copied.txt  data_dehex
```

<br>

Let's once again check what type of file `data_dehex` is:
```zsh
bandit12@bandit:/tmp/decomp_hex$ file data_dehex
data_dehex: bzip2 compressed data, block size = 900k
```

We can see it's a file compressed using [bzip](http://www.bzip.org/), so we can use the [`bzip2`](https://linux.die.net/man/1/bzip2) command to decompress it:
```zsh
# Decompressing the bzip data
bandit12@bandit:/tmp/decomp_hex$ bzip2 --decompress data_dehex
bzip2: Can't guess original name for data_dehex -- using data_dehex.out

bandit12@bandit:/tmp/decomp_hex$ ls
data_copied.txt  data_dehex.out
```

<br>

Let's check what kind of a file `data_dehex.out` is:
```zsh
bandit12@bandit:/tmp/decomp_hex$ file data_dehex.out
data_dehex.out: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
```

We can see that it is a gzip compressed file, so we can use the [`gzip`](https://linux.die.net/man/1/gzip) tool once again to decompress it

```zsh
# Renaming the file so that gzip works:
bandit12@bandit:/tmp/decomp_hex$ mv data_dehex.out data_dehex.gz

# Decompressing the file:
bandit12@bandit:/tmp/decomp_hex$ gzip --decompress data_dehex.gz
```

<br>

Now, once again we'll check what type of a file this is:

```zsh
bandit12@bandit:/tmp/decomp_hex$ file data_dehex
data_dehex: POSIX tar archive (GNU)
```

Since it is a [tar](https://www.gnu.org/software/tar/manual/) archive, we can use the [`tar`](https://linux.die.net/man/1/tar) command/tool to decompress it.


```zsh
# Decompressing the tar archive
bandit12@bandit:/tmp/decomp_hex$ tar -xf data_dehex

bandit12@bandit:/tmp/decomp_hex$ ls
data5.bin  data_copied.txt  data_dehex
```

<br>

We've got a file: `data5.bin` as a result of the decompression, we can now check what type of a file it is:

```zsh
bandit12@bandit:/tmp/decomp_hex$ file data5.bin
data5.bin: POSIX tar archive (GNU)
```

We will once again use the [`tar`](https://linux.die.net/man/1/tar) command/tool to decompress `data5.bin`

```zsh
# Decompressing data5.bin:
bandit12@bandit:/tmp/decomp_hex$ tar -xf data5.bin

bandit12@bandit:/tmp/decomp_hex$ ls
data5.bin  data6.bin  data_copied.txt  data_dehex
```

<br>

Just like before, we check what type of a file `data6.bin` is:

```zsh
bandit12@bandit:/tmp/decomp_hex$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
```

We once again use the [`bzip2`](https://linux.die.net/man/1/bzip2) tool to decompress the file.

```zsh
# Decompressing data6.bin using bzip2:
bandit12@bandit:/tmp/decomp_hex$ bzip2 --decompress data6.bin
bzip2: Can't guess original name for data6.bin -- using data6.bin.out

bandit12@bandit:/tmp/decomp_hex$ ls
data5.bin  data6.bin.out  data_copied.txt  data_dehex
```

<br>


Now, we check the resultant file:

```zsh
bandit12@bandit:/tmp/decomp_hex$ file data6.bin.out
data6.bin.out: POSIX tar archive (GNU)

# Decompressing "data6.bin.out" using tar:
bandit12@bandit:/tmp/decomp_hex$ tar -xf data6.bin.out

bandit12@bandit:/tmp/decomp_hex$ ls
data5.bin  data6.bin.out  data8.bin  data_copied.txt  data_dehex
```

<br>

Checking `data8.bin`:

```zsh
bandit12@bandit:/tmp/decomp_hex$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
```

Using the [`gzip`](https://linux.die.net/man/1/bzip2) command/tool:

```zsh
# Renaming data8.bin to data8.gz
bandit12@bandit:/tmp/decomp_hex$ mv data8.bin data8.gz

# Decompressing data8.gz
bandit12@bandit:/tmp/decomp_hex$ gzip --decompress data8.gz

bandit12@bandit:/tmp/decomp_hex$ ls
data5.bin  data6.bin.out  data8  data_copied.txt  data_dehex
```

<br>

Now let's check the resultant file:

```zsh
bandit12@bandit:/tmp/decomp_hex$ file data8
data8: ASCII text
```

This is the final file containing the password :)

```zsh
bandit12@bandit:/tmp/decomp_hex$ cat data8
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

---

##### Password for next level:
    8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL

---

Link to the level: [Level 12 ➙ Level 13](https://overthewire.org/wargames/bandit/bandit13.html)
