# Bandit Level 7 - 8

## Objetivo
The password for the next level is stored in the file **data.txt** next to the word **millionth**.

## Cosas utilies
user: bandit7
password: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

## Solucion
``` bash
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ grep millionth data.txt
millionth       cvX2JJa4CFALtqS87jk27qwqGhBM9plV


```

## Notas
El comando grep sirve para buscar una palabra dentro de uno o varios archivos.
Syntaxis básica grep palabra_a_buscar archivo1 archivo2 ... archivoN