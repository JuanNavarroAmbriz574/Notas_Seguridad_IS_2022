# Bandit Level

## Objetivo
Logging in to bandit26 from bandit25 should be fairly easy The shell for user bandit26 is not /bin/bash, but something else. Find out what it is, how it works and how to break out of it

## Cosas utilies
user: bandit25
password: p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d

## Solucion
``` bash
bandit25@bandit:~$ ls
bandit26.sshkey

bandit25@bandit:~$ cat /etc/passwd | grep bandit26
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext

bandit25@bandit:~$ cat /usr/bin/showtext
#!/bin/sh

export TERM=linux

exec more ~/text.txt

bandit25@bandit:~$ ssh -i bandit26.sshkey bandit26@localhost -p 2220

# haz pequeña la ventana de comandos
# se ejecuta el comando more
# Presiono v para entrar al editor de texto vi
# presiono ESC + : para entrar en el modo de comandos de vi
# Luego escribe :set shell sh=/bin/bash
# Luego escribe :shell


bandit26@bandit:~$ cat /etc/bandit_pass/bandit26
c7GvcKlw9mC7aUQaPx7nwFstuAIBw1o1


```

## Notas
1. Vi es otro editor de texto que es muy común y esta instalado en  la mayoria de las distribuciones de linux y unix.
2. El comando more muestra un archivo de texto, pero si este archivo de texto es muy grande lo muestra paginado y de una forma más agradable y controlable que con un cat.
3. En el directorio /etc/passwd podemos ver todos los usuarios que se han registrado en el sistema. Este directorio contiene la siguiente información: 
-   Nombre de usuario
-   Contrseña encriptada
-   ID de usuario (UID)
-   Número ID del grupo al que pertenece el ususario (GID)
-   Nombre completo del usuario (GECOS)
-   Home directory del usuario
-   Tipo de login shell que usa el susario
Este archivo solo puede ser editado por el usuario root o los usuarios restando usando sudo.
