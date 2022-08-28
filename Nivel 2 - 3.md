# Bandit Level 2 - 3

## Objetivo
The password for the next level is stored in a file called spaces in this filename located in the home directory.

## Cosas utilies
user: bandit2
password: CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

## Solucion
``` bash
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat "spaces in this filename"
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

```

## Notas
Cuando quieras leer el contenido de un archivo usando el comando cat y este archivo tenga espacios debes ponerlo entre comillas dobles, de lo contrario el comando cat reconocera cada palabra como un archivo independiente.