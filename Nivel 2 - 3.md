# Bandit Level 2 - 3

## Objetivo
The password for the next level is stored in a file called spaces in this filename located in the home directory.

## Cosas utilies
user: bandit2
password: rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

## Solucion
``` bash
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat "spaces in this filename"
aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

```

## Notas
Cuando quieras leer el contenido de un archivo usando el comando cat y este archivo tenga espacios debes ponerlo entre comillas dobles, de lo contrario el comando cat reconocera cada palabra como un archivo independiente.