# Bandit Level 1 - 2

## Objetivo
The password for the next level is stored in a file called **-** located in the home directory.

## Cosas utilies
user: bandit1
password: boJ9jbbUNNfktd78OOpsqOltutMc3MY1

## Solucion
``` bash
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat ./-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
## Notas
1 - Para ver el contenido de un archivo que comienza con - utilizando el comando cat es necesario especificar la ruta del archivo.
2 - el ./ en linux es interpretado como directorio actual.
