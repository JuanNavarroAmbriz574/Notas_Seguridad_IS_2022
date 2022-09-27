## Objetivo
Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/static)? This [BASH script](https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/ltdis.sh) might help!

## Solución
El primer paso es descargar los 2 archivos que nos proporciona el problema.
``` bash
juan574-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/static
--2022-09-22 22:59:42--  https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/static
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8376 (8.2K) [application/octet-stream]
Saving to: 'static'

static              100%[==================>]   8.18K  --.-KB/s    in 0s      

2022-09-22 22:59:42 (362 MB/s) - 'static' saved [8376/8376]

juan574-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/ltdis.sh
--2022-09-22 23:00:25--  https://mercury.picoctf.net/static/66932732825076cad4ba43e463dae82f/ltdis.sh
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 785 [application/octet-stream]
Saving to: 'ltdis.sh'

ltdis.sh            100%[==================>]     785  --.-KB/s    in 0s      

2022-09-22 23:00:25 (244 MB/s) - 'ltdis.sh' saved [785/785]

juan574-picoctf@webshell:~$ ls -l
total 32
-rw-r--r-- 1 root            root            4448 Sep 22 22:43 README.txt
-rw-rw-r-- 1 juan574-picoctf juan574-picoctf  164 Sep 22 22:48 converit_numeros_a_ascii.py
-rw-rw-r-- 1 juan574-picoctf juan574-picoctf  785 Mar 16  2021 ltdis.sh
-rw-rw-r-- 1 juan574-picoctf juan574-picoctf  186 Sep 22 22:37 numeros.txt
-rw-rw-r-- 1 juan574-picoctf juan574-picoctf 8376 Mar 16  2021 static

```
Al examinar  el archivo statics nos damos cuneta que es un archivo ejecutable, por lo que usamos el comando strings para obtener la parte legible del archivo, luego filtramos los resultados usando grep y buscanod la bandera

```
juan574-picoctf@webshell:~$ file static    
static: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=277d07901cf99a335a8107fbdd6642d9c6140bb5, not stripped
juan574-picoctf@webshell:~$ strings static | grep picoCTF
picoCTF{d15a5m_t34s3r_f5aeda17}
```

## Notas
El comando ``` bash strings```  encuentra las cadenas que son entendibles o leibles por humanos en archivos binarios.
