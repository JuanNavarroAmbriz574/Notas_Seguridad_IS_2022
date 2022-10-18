## Objetivo
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key). Recover the flag.

## Solución
1. Descargamos la caputra de paquetes. y la llave
``` bash

┌──(kali㉿kali)-[~/pico]
└─$ wget https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key
--2022-10-18 00:09:21--  https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13163 (13K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap                                    100%[======================================================================================================>]  12.85K  --.-KB/s    in 0.001s  

2022-10-18 00:09:21 (16.8 MB/s) - ‘capture.pcap’ saved [13163/13163]

--2022-10-18 00:09:21--  https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key
Reusing existing connection to jupiter.challenges.picoctf.org:443.
HTTP request sent, awaiting response... 200 OK
Length: 1704 (1.7K) [application/octet-stream]
Saving to: ‘picopico.key’

picopico.key                                    100%[======================================================================================================>]   1.66K  --.-KB/s    in 0s      

2022-10-18 00:09:21 (23.0 MB/s) - ‘picopico.key’ saved [1704/1704]

FINISHED --2022-10-18 00:09:21--
Total wall clock time: 0.6s
Downloaded: 2 files, 15K in 0.001s (17.4 MB/s)
                                                                                                                                                                                               
┌──(kali㉿kali)-[~/pico]
└─$ ls
capture.pcap  picopico.key
                                                                                                                                                                                               
┌──(kali㉿kali)-[~/pico]

```

2. La captura de paquetes esta encriptada usando TLS, así que si trataramos de leerlos directamente no podriamos, lo bueno es que tenemos la llave y podemos desncriptar los mensajes usando el siguiente comando.
``` bash
ssldump -r capture.pcap -k picopico.key
```

Este comando desencriptara la captura de paquete y ahora solo queda buscar la bandera entre estos paquetes usando el comando grep. Al final el comando que nos da la bandera es:
``` bash
└─$ ssldump -r capture.pcap -k picopico.key -d | grep pico -A 2
    61 67 3a 20 70 69 63 6f 43 54 46 7b 6e 6f 6e 67    ag: picoCTF{nong
    73 68 69 6d 2e 73 68 72 69 6d 70 2e 63 72 61 63    shim.shrimp.crac
    6b 65 72 73 7d 0d 0a 43 6f 6e 74 65 6e 74 2d 4c    kers}..Content-L
--
    67 3a 20 70 69 63 6f 43 54 46 7b 6e 6f 6e 67 73    g: picoCTF{nongs
    68 69 6d 2e 73 68 72 69 6d 70 2e 63 72 61 63 6b    him.shrimp.crack
    65 72 73 7d 0d 0a 43 6f 6e 74 65 6e 74 2d 4c 65    ers}..Content-Le
```

La bandera es:  picoCTF{nongshim.shrimp.crackers}

## Notas
**Seguridad de la capa de transporte** (en inglés: **Transport Layer Security** o **TLS**) y su antecesor **Secure Sockets Layer** (**SSL**; en español **capa de puertos seguros**) son protocolos criptográficos, que proporcionan comunicaciones seguras por una red comúnmente internet.