# Bandit Level

## Objetivo
To gain access to the next level, you should use the setuid binary in the home directory. Execute it without arguments to find out how to use it. The password for this level can be found in the usual place (/etc/bandit pass), after you have used to setuid binary.

## Cosas utilies
user: bandit 19
passeord: awhqfNnAbc1naukrpqDYcF95h7HoMTrC

## Solucion
``` bash
bandit19@bandit:~$ ls
bandit20-do
bandit19@bandit:~$ ./bandit20-do
Run a command as another user.
  Example: ./bandit20-do id
bandit19@bandit:~$ ./bandit20-do cat /etc/bandit_pass/bandit20
VxCazJaVykI6W36BkBU0mJTCM8rR95XT


```

## Notas
Para ejecutar un archivo binario se coloca ./ seguido del nombre del binario ejecutable.

