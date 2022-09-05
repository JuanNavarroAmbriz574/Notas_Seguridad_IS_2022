# Bandit Level

## Objetivo
The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions.

## Cosas utilies
user: 11
password: 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM

## Solucion
``` bash
bandit11@bandit:~$ ls
data.txt
bandit11@bandit:~$ cat data.txt | tr [a-zA-Z] [n-za-mN-ZA-M]
The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv

```

## Notas
El comando tr sirve para manipular textos con este comando podemos hacer lo siguiente: 
- Cambiar caracteres, palabras y frases de mayúscula a minúscula o viceversa.
- Buscar palabras y reemplazarlas por otras.
- Borrar caracteres.
- Eliminar la totalidad de caracteres de puntuación de una frase.