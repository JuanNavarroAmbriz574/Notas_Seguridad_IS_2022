## Objetivo
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/5bd86036f013ac3b9c958499adf3e2e2/strings) without running it?

## Solución
juan574-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/5bd86036f013ac3b9c958499adf3e2e2/strings
--2022-09-21 02:42:14--  https://jupiter.challenges.picoctf.org/static/5bd86036f013ac3b9c958499adf3e2e2/strings
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 776032 (758K) [application/octet-stream]
Saving to: 'strings'

strings                                         100%[======================================================================================================>] 757.84K  1.84MB/s    in 0.4s    

2022-09-21 02:42:14 (1.84 MB/s) - 'strings' saved [776032/776032]

juan574-picoctf@webshell:~$ ls
README.txt  hola.txtx  strings
juan574-picoctf@webshell:~$ cat strings | strings | grep picoCTF
picoCTF{5tRIng5_1T_827aee91}
## Notas
1. `wget` es un comnado que nos ayuda a descargar archivos de servidores. Este comando permite descargas a través de FTP, SFTP, HTTP y HTTPS y su sintaxis básica es wget URL_del_archivo_a_descargar.
2. `strings` es un comando que encuentra las cadenas que son entendibles o leibles por humanos en archivos binarios.