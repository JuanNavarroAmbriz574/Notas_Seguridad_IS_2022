## Objetivo
This [garden](https://jupiter.challenges.picoctf.org/static/43c4743b3946f427e883f6b286f47467/garden.jpg) contains more than it seems.

## Solución
1. Primero descargamos el archivo.
``` bash
juan574-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/43c4743b3946f427e883f6b286f47467/garden.jpg
--2022-09-29 13:16:46--  https://jupiter.challenges.picoctf.org/static/43c4743b3946f427e883f6b286f47467/garden.jpg
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2295192 (2.2M) [application/octet-stream]
Saving to: 'garden.jpg'

garden.jpg          100%[==================>]   2.19M  1.83MB/s    in 1.2s    

2022-09-29 13:16:47 (1.83 MB/s) - 'garden.jpg' saved [2295192/2295192]

juan574-picoctf@webshell:~$ ls
README.txt  garden.jpg
```

2. Hacemos un `strings` a la imagen descargada y obtenemos la bandera.
``` bash
juan574-picoctf@webshell:~$ strings garden.jpg | grep picoCTF
Here is a flag "picoCTF{more_than_m33ts_the_3y3657BaB2C}"
```
## Notas

