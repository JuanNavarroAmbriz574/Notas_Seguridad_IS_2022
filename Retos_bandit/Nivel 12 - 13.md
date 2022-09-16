# Bandit Level

## Objetivo
The password for the next level is stored in the file **data.txt**, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!).

## Cosas utilies
user: bandit12
passeord: JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

## Solucion
``` bash
bandit12@bandit:~$ ls
data.txt
bandit12@bandit:~$ mkdir /tmp/juan54
bandit12@bandit:~$ cp ./data.txt /tmp/juan54/data.txt
bandit12@bandit:~$ cd /tmp/juan54

bandit12@bandit:/tmp/juan54$ ls
data.txt
bandit12@bandit:/tmp/juan54$ cat data.txt | xxd -r | file -
/dev/stdin: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/juan54$ cat data.txt | xxd -r | zcat | file -
/dev/stdin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/juan54$ cat data.txt | xxd -r | zcat | bzcat | file -
/dev/stdin: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/juan54$ cat data.txt | xxd -r | zcat | bzcat | zcat | file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/juan54$ cat data.txt | xxd -r | zcat | bzcat | zcat | tar  xO | file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/juan54$ cat data.txt | xxd -r | zcat | bzcat | zcat | tar  xO | tar xO | file -
/dev/stdin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/juan54$ cat data.txt | xxd -r | zcat | bzcat | zcat | tar  xO | tar xO | bzcat | file -
/dev/stdin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/juan54$ cat data.txt | xxd -r | zcat | bzcat | zcat | tar  xO | tar xO | bzcat | tar xO | file -
/dev/stdin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/juan54$ cat data.txt | xxd -r | zcat | bzcat | zcat | tar  xO | tar xO | bzcat | tar xO | zcat | file -
/dev/stdin: ASCII text
bandit12@bandit:/tmp/juan54$ cat data.txt | xxd -r | zcat | bzcat | zcat | tar  xO | tar xO | bzcat | tar xO | zcat | cat
The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw


```

## Notas
- Hexdump o vaciado exadecimal que hace referencia a la representación de un archivo ejecutable o entrada estándar de forma exadecimal.
- Con el comando xxd -r regresar un archivo que tiene un hexdump a su tipo original.
- Con el comando cp copias un archivo de una ubicación a otra.


