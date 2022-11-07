## Objetivo
We found a leak of a blackmarket website's login credentials. Can you find the password of the user `cultiris` and successfully decrypt it?Download the leak [here](https://artifacts.picoctf.net/c/534/leak.tar).The first user in `usernames.txt` corresponds to the first password in `passwords.txt`. The second user corresponds to the second password, and so on.

## Solución
1. Descargamos el leak.tar
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ wget https://artifacts.picoctf.net/c/534/leak.tar   
--2022-11-02 19:59:16--  https://artifacts.picoctf.net/c/534/leak.tar
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.249.74.22, 13.249.74.69, 13.249.74.56, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.249.74.22|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30720 (30K) [application/octet-stream]
Saving to: ‘leak.tar’

leak.tar                                  100%[===================================================================================>]  30.00K  --.-KB/s    in 0.02s   

2022-11-02 19:59:17 (1.26 MB/s) - ‘leak.tar’ saved [30720/30720]

┌──(kali㉿kali)-[~/pico]
└─$ ls
leak.tar  stegsolve.jar

```

2. Desconprimimos el .tar
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ tar xvf leak.tar
leak/
leak/passwords.txt
leak/usernames.txt

```
3. Debemos entrar al archivo y averiguar en que linea se encuentra el usuario cultiris dentro del archivo usernames.txt. Podemos hacer esto con un editor de texto buscando el texto `cultiris` y viendo en que linea se encuentra. Con esto nos damos cuenta que el uusername ``cultiris`` está en la línea 378.
4. Revisamos la linea 378 de nuestro archivo passwords.txt.
``` shell
┌──(kali㉿kali)-[~/pico/leak]
└─$ cat passwords.txt| head -n 378 | tail -n 1
cvpbPGS{P7e1S_54I35_71Z3}

```

5. Desencriptamos el resultado usando ROT13 y obtenemos la bandera.
FLAG: picoCTF{C7r1F_54V35_71M3}
## Notas