## Objetivo
Can you find the flag? [shark2.pcapng](https://mercury.picoctf.net/static/719e81d6fbb6b3157624268588fc0de8/shark2.pcapng).

## Solución
1. Descargamos la captura de paquetes.
``` bash
┌──(kali㉿kali)-[~/pico]
└─$ wget https://mercury.picoctf.net/static/719e81d6fbb6b3157624268588fc0de8/shark2.pcapng
--2022-10-25 11:41:05--  https://mercury.picoctf.net/static/719e81d6fbb6b3157624268588fc0de8/shark2.pcapng
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3520112 (3.4M) [application/octet-stream]
Saving to: ‘shark2.pcapng’

shark2.pcapng                             100%[===================================================================================>]   3.36M   919KB/s    in 4.4s    

2022-10-25 11:41:10 (785 KB/s) - ‘shark2.pcapng’ saved [3520112/3520112]

                                                                                                                                                                      
┌──(kali㉿kali)-[~/pico]
└─$ ls
shark2.pcapng
```

2. Abrimos neustra captura de paquetes usando whireshark
3. Filtramos los paquetes  y dejamos únicamente los paquetes DNS.
4. Volvemos a filtralo los paquetes pero esta vez filtramos por ip destino y solo tomaremos los paquetes que cuya  ip destino sea 18.217.1.57
5. Volvemos a filtrar los DNS, pero ahora los filtramos por nombre solo tomaremos los DNS cuyo nomnre sea local. la consulta final se veria algo como : ` dns && ip.dst == 18.217.1.57 && dns.qry.name contains local `
6. Guardamos los streams resultantes en un archivo CSV. (file -> export packet dissections -> as CSV en WhireShark) y eliminamos el primer renglón y el último.
7. En los paquetes hay partes de la bandera codificada en base 64 por lo que la decodificamos. con el siguiente comando y obtenemos la badnera. `cat data.csv | cut -d ' ' -f 5 | cut -d '.' -f1 | tr -d '\n' | base64 -d ` data es el nombre del archivo CSV del paso 6.
La bandera: picoCTF{dns_3xf1l_ftw_deadbeef}

## Notas