# Bandit Level 8 - 9

## Objetivo
The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

## Cosas utilies
user: bandit8
password: cvX2JJa4CFALtqS87jk27qwqGhBM9plV

## Solucion
``` bash
bandit8@bandit:~$ cat data.txt | sort | uniq -c -u
      1 UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

```

## Notas
El comando uniq sirve para buscar ocurrencias de una cadena dentro de un archivo. El parámetro -c cuneta las ocurrencias de las cadenas en un archivo y el parámetro -u filtra los resultados mostrando unicamente los que aparecen 1 vez en el archivo.