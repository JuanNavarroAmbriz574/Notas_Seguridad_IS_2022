# Bandit Level

## Objetivo
The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:
-   human-readable
-   1033 bytes in size
-   not executable

## Cosas utilies
user: bandit5
password: lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

## Solucion
``` bash
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere/
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere02  maybehere04  maybehere06  maybehere08  maybehere10  maybehere12  maybehere14  maybehere16  maybehere18
maybehere01  maybehere03  maybehere05  maybehere07  maybehere09  maybehere11  maybehere13  maybehere15  maybehere17  maybehere19
bandit5@bandit:~/inhere$ find -type f -size 1033c ! -executable
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```

## Notas
El comando find sirve para buscar un archivo en el disco duro de una computadora.
La opción type especifica el tipo de archivo. f significa un archivo regular.
La opción size es usada para especificar el tamaño del archivo a buscar. La c especifica que el peso del archivo está en bytes.