# Bandit Level

## Objetivo
The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.

## Cosas utilies
user: bandit9
password: EN632PlfYiZbn3PhVK3XOGSlNInNE00t

## Solucion
``` bash
bandit9@bandit:~$ ls
data.txt
bandit9@bandit:~$ cat data.txt | strings | grep ==
========== the*2i"4
========== password
Z)========== is
&========== G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

```

## Notas
El comando ``` bash strings```  encuentra las cadenas que son entendibles o leibles por humanos en archivos binarios.
