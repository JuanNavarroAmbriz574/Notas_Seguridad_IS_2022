# Bandit Level 4 - 5

## Objetivo
The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.

## Cosas utilies
user: bandit4
password: pIwrPrtPN36QITSp3EQaw936yaFoFgAB

## Solucion
``` bash
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ls
-file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
bandit4@bandit:~/inhere$ file ./-*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh

```

## Notas
El comando file nos indica el tipo  (texto ASCII, imagen, data, etc) que es un archivo cuando este comando nos arroga data significa que es un archivo que no puede ser comprendido por un humano debido a que es un archivo binario.