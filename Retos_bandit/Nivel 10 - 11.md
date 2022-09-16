# Bandit Level

## Objetivo
The password for the next level is stored in the file **data.txt**, which contains base64 encoded data.

## Cosas utilies
user: bandit 10
password: G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s

## Solucion
``` bash
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ base64 -d data.txt
The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

```

## Notas
El comando base64 sirve para convertir un texto o algun archivo binario en texto en base 64. Un archivo en bae 64 contiene los siguientes caracteres: letras minúsculas de la a-z y mayúsculas de la A-Z, números de 1 a 9, -, +, =.
El parámetro -d sirve para converitr un texto codificado en base 64 a su estado original.
