# Bandit Level

## Objetivo
he password for the next level is stored in **/etc/bandit_pass/bandit14 and can only be read by user bandit14**. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. **Note:** **localhost** is a hostname that refers to the machine you are working on.

## Cosas utilies
user: bandit13
password: wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

## Solucion
``` bash
bandit13@bandit:~$ ls
sshkey.private
bandit13@bandit:~$ ssh -i sshkey.private bandit14@localhost -p 2220
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

```

## Notas
Una llave SSH es un tipo de llave que sirve para iniciar sesción en un servidor remote sin necesidad de ingeresar la contraseña.