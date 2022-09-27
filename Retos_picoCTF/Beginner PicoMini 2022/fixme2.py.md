## Objetivo
Fix the syntax error in the Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/67/fixme2.py)
## Solución
Primero descargamos el archivos
``` bash
juan574-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/67/fixme2.py
--2022-09-26 17:38:23--  https://artifacts.picoctf.net/c/67/fixme2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 108.156.172.120, 108.156.172.74, 108.156.172.6, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|108.156.172.120|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1029 (1.0K) [application/octet-stream]
Saving to: 'fixme2.py'

fixme2.py           100%[==================>]   1.00K  --.-KB/s    in 0s      

2022-09-26 17:38:23 (352 MB/s) - 'fixme2.py' saved [1029/1029]

juan574-picoctf@webshell:~$ ls
README.txt  fixme2.py
```

Ejecutamos el programa para ver cual es el error que arroja
``` bash
juan574-picoctf@webshell:~$ python fixme2.py 
  File "/home/juan574-picoctf/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
```

La condición `if flag = "":` está mal porque python lo interpreta como una asignación y no como una comparación por lo que la condición pasa a ser `if flag == "":` y ejecutamos el script una vez más oteniendo la bandera.
``` bash
juan574-picoctf@webshell:~$ python fixme2.py 
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_f6a5aefc}
```

## Notas