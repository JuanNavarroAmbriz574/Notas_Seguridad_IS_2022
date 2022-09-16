# Bandit Level

## Objetivo
There is a setuid binary in the homedirectory that does the following: it makes a connection to localhost on the port you specify as a commandline argument. It then reads a line of text from the connection and compares it to the password in the previous level (bandit20). If the password is correct, it will transmit the password for the next level (bandit21). NOTE: To beat this level, you need to login twice: once to run the setuid command, and once to start a network daemon to which the setuid will connect. NOTE 2: Try connecting to your own network daemon to see if it works as you think.

## Cosas utilies
user: bandit20
passeord: VxCazJaVykI6W36BkBU0mJTCM8rR95XT

## Solucion
Terminal 1
``` bash
bandit20@bandit:~$ ls
suconnect
bandit20@bandit:~$ nc -l 30003
VxCazJaVykI6W36BkBU0mJTCM8rR95XT
NvEJF7oVjkddltPSrdKEFOllh9V1IBcq

```

Terminal 2
``` bash
bandit20@bandit:~$ ./suconnect 30003
Read: VxCazJaVykI6W36BkBU0mJTCM8rR95XT
Password matches, sending next password

```
## Notas
El comando nc -l [port] sirve para poner a la terminal a escuchar por el puerto especifico.