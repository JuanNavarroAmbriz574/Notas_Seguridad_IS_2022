# Bandit Level

## Objetivo
The password for the next level is stored in a hidden file in the **inhere** directory.

## Cosas utilies
user: bandit3
password: aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

## Solucion
``` bash
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 May  7  2020 .
drwxr-xr-x 3 root    root    4096 May  7  2020 ..
-rw-r----- 1 bandit4 bandit3   33 May  7  2020 .hidden
bandit3@bandit:~/inhere$ cat .hidden
2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

```

## Notas
El comando ls por default solo lista los archivos visibles, pero no los archivos coculos para poder ver los archivos ocultos usamos la opciona -a y para ver una listado en formato largo usamos la opción de -l 