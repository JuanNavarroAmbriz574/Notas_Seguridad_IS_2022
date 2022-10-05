## Objetivo
Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: [Addadshashanammu.zip](https://mercury.picoctf.net/static/72712e82413e78cc8aa8d553ffea42b0/Addadshashanammu.zip)

## Solución
El primer paso es descargar el archivo que nos presenta el problema.
``` bash
juan574-picoctf@webshell:~$ wget https://mercury.picoctf.net/static/72712e82413e78cc8aa8d553ffea42b0/Addadshashanammu.zip
--2022-09-22 23:16:50--  https://mercury.picoctf.net/static/72712e82413e78cc8aa8d553ffea42b0/Addadshashanammu.zip
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4520 (4.4K) [application/octet-stream]
Saving to: 'Addadshashanammu.zip'

Addadshashanammu.zi 100%[==================>]   4.41K  --.-KB/s    in 0s      

2022-09-22 23:16:50 (1.23 GB/s) - 'Addadshashanammu.zip' saved [4520/4520]

juan574-picoctf@webshell:~$ ls
Addadshashanammu.zip  README.txt
```

Descomprimimos el archivo .zip

``` bash
juan574-picoctf@webshell:~$ unzip Addadshashanammu.zip 
Archive:  Addadshashanammu.zip
   creating: Addadshashanammu/
   creating: Addadshashanammu/Almurbalarammi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/
   creating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/
  inflating: Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assurnabitashpi/Maelkashishi/Onnissiralis/Ularradallaku/fang-of-haynekhtnamet 

```
Por último, navegamos por las carpetas hasta encontrar el archivo ejecutable que contiene la contraseña del nivel.
```
juan574-picoctf@webshell:~$ ls
Addadshashanammu  Addadshashanammu.zip  README.txt
juan574-picoctf@webshell:~$ cd Addadshashanammu/
juan574-picoctf@webshell:~/Addadshashanammu$ cd Almurbalarammi/
juan574-picoctf@webshell:~/Addadshashanammu/Almurbalarammi$ cd Ashalmimilkala/
juan574-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala$ cd Assurnabitashpi/
juan574-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assur
nabitashpi$ cd Maelkashishi/
juan574-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assur
nabitashpi/Maelkashishi$ cd Onnissiralis/
juan574-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assur
nabitashpi/Maelkashishi/Onnissiralis$ cd Ularradallaku/
juan574-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assur
nabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$ ls 
fang-of-haynekhtnamet
juan574-picoctf@webshell:~/Addadshashanammu/Almurbalarammi/Ashalmimilkala/Assur
nabitashpi/Maelkashishi/Onnissiralis/Ularradallaku$ ./fang-of-haynekhtnamet 
*ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_6f332f10}
```
## Notas
1. El comando unzip nos permite descomprimir archivo .zip
2. El comando zip nos permite comprimir archivos en .zip