# Bandit Level

## Objetivo
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost

## Cosas utilies
user: 14
password: fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

## Solucion
``` bash
bandit14@bandit:~$ nc localhost 30000
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

```

## Notas
Netcat es un comando usado para leer o escribir entre 2 computadoras. La comunicación entre estas computadoras debe de ser en TCP o UDP.