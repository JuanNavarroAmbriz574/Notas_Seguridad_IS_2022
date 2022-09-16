# Bandit Level

## Objetivo
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new.

## Cosas utilies
user: bandit17
passeord: VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e o llave RSA generada del nivel 16

## Solucion
``` bash
bandit17@bandit:~$ ls
passwords.new  passwords.old
bandit17@bandit:~$ diff passwords.old passwords.new
42c42
< 09wUIyMU4YhOzl1Lzxoz0voIBzZ2TUAf
---
> hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg

```

## Notas
El comando diff compara 2 archivos linea por linea y muestra en cuales lineas los archivos difieren.