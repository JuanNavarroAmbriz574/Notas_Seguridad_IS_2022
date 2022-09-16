# Bandit Level 8 - 9

## Objetivo
The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once

## Cosas utilies
user: bandit8
password: TESKZC0XvTetK0S9xNwm25STk5iWrBvP

## Solucion
``` bash
bandit8@bandit:~$ cat data.txt | sort | uniq -c -u
      1 EN632PlfYiZbn3PhVK3XOGSlNInNE00t

```

## Notas
El comando uniq sirve para buscar ocurrencias de una cadena dentro de un archivo. El parámetro -c cuneta las ocurrencias de las cadenas en un archivo y el parámetro -u filtra los resultados mostrando unicamente los que aparecen 1 vez en el archivo.