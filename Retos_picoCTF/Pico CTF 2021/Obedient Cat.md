## Objetivo
This file has a flag in plain sight (aka "in-the-clear").
[Download flag](https://mercury.picoctf.net/static/704f877da185904ec3992e7255a15c6c/flag).

## Solución
``` bash
juan574-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/704f877da185904ec3992e7255a15c6c/flag
--2022-09-22 21:44:42--  https://mercury.picoctf.net/static/704f877da185904ec3992e7255a15c6c/flag
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34 [application/octet-stream]
Saving to: 'flag'

flag                100%[==================>]      34  --.-KB/s    in 0s      

2022-09-22 21:44:42 (13.8 MB/s) - 'flag' saved [34/34]

juan574-picoctf@webshell:~$ ls
README.txt  file  flag
juan574-picoctf@webshell:~$ cat flag
picoCTF{s4n1ty_v3r1f13d_1a94e0f9}
```

## Notas
1. `wget` es un comnado que nos ayuda a descargar archivos de servidores. Este comando permite descargas a través de FTP, SFTP, HTTP y HTTPS y su sintaxis básica es wget URL_del_archivo_a_descargar.