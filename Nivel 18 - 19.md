# Bandit Level

## Objetivo
The password for the next level is stored in a file readme in the home directory. Unfortunately, someone has modified .bashrc to log you out when you log in with SSH.

## Cosas utilies
user: bandit18
passeword: hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg

## Solucion
``` bash
$ ssh -p 2220 bandit18@bandit.labs.overthewire.org ls -la
drwxr-xr-x  2 root     root     4096 Sep  1 06:30 .
drwxr-xr-x 49 root     root     4096 Sep  1 06:30 ..
-rw-r--r--  1 root     root      220 Jan  6  2022 .bash_logout
-rw-r-----  1 bandit19 bandit18 3794 Sep  1 06:30 .bashrc
-rw-r--r--  1 root     root      807 Jan  6  2022 .profile
-rw-r-----  1 bandit19 bandit18   33 Sep  1 06:30 readme
$ ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme
awhqfNnAbc1naukrpqDYcF95h7HoMTrC
```

## Notas
El archivo bashrc es un archivo de configuración de shell que esta guardado en **~/.bashrc** . Este archivo es ejecutado cada vez que una sesión de terminal es abierta si este archivo es editado la forma normal en la que la terminal inicia puede cambiar dependiendo de lo que se haya agregado.
Al conectarse a un servidor remoto a través de ssh se pueden ejecutar comandos.