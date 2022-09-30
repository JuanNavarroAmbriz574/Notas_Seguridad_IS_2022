## Objetivo
This is a really weird text file [TXT](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)? Can you find the flag?

## Solución
``` bash
juan574-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt
--2022-09-29 13:39:43--  https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9984 (9.8K) [application/octet-stream]
Saving to: 'flag.txt'

flag.txt            100%[==================>]   9.75K  --.-KB/s    in 0s      

2022-09-29 13:39:43 (324 MB/s) - 'flag.txt' saved [9984/9984]

juan574-picoctf@webshell:~$ ls
README.txt  flag.txt

juan574-picoctf@webshell:~$ mv flag.txt flag.png
juan574-picoctf@webshell:~$ ls
README.txt  flag.png
```

## Notas
Magic btytes es la forma del sistema operativo para saber que tipo de archivo.