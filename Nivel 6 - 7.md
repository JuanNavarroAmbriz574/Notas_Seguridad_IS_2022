# Bandit Level 6 - 7

## Objetivo
The password for the next level is stored **somewhere on the server** and has all of the following properties:

-   owned by user bandit7
-   owned by group bandit6
-   33 bytes in size

## Cosas utilies
user: bandit6
password: DXjZPULLxYr17uwoI01bNLQbtFemEgo7

## Solucion
``` bash
bandit6@bandit:~$ find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
/var/lib/dpkg/info/bandit7.password
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

```


## Notas
El parámetro -user del comando find indica a que usuario le pertenece el archivo a buscar.
El parámetro -group del comando find indica a que grupo pertenece el archivo que se va a buscar.
El 2>/dev/null le indica al comando find que los resultados que tengan una salida de error cuando se ejecute la búsqueda no se muestren en el resultado final.