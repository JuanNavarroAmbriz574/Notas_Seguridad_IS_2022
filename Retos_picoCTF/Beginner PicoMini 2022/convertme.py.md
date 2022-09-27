## Objetivo
Run the Python script and convert the given number from decimal to binary to get the flag.
[Download Python script](https://artifacts.picoctf.net/c/30/convertme.py)

## Solución
El primer paso para resolver el reto es descargar el script en python
``` bash
juan574-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/30/convertme.py
--2022-09-26 17:02:19--  https://artifacts.picoctf.net/c/30/convertme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 108.156.172.42, 108.156.172.120, 108.156.172.74, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|108.156.172.42|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1189 (1.2K) [application/octet-stream]
Saving to: 'convertme.py'

convertme.py        100%[==================>]   1.16K  --.-KB/s    in 0s      

2022-09-26 17:02:19 (52.3 MB/s) - 'convertme.py' saved [1189/1189]
```

Luego ejecutamos el script
``` bash
juan574-picoctf@webshell:~$ python convertme.py 
If 24 is in decimal base, what is it in binary base?
```
Nos pide convertir un número decimal a binario, podemos convertir el número usando un conversor en linea.
``` bash
If 24 is in decimal base, what is it in binary base?
Answer: 11000
That is correct! Here's your flag: picoCTF{4ll_y0ur_b4535_762f748e}
```


## Notas