## Objetivo
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap). Recover the flag that was pilfered from the network.

## Solución
1. Descargamos el archivo.
``` bash
┌──(kali㉿kali)-[~/pico]
└─$ wget https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap
--2022-10-17 23:43:49--  https://jupiter.challenges.picoctf.org/static/b506393b6f9d53b94011df000c534759/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 112318 (110K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap                                    100%[======================================================================================================>] 109.69K  6.85KB/s    in 16s     

2022-10-17 23:44:38 (6.85 KB/s) - ‘capture.pcap’ saved [112318/112318]

```


2. Filtramos paquetes los cuales su puerto destino sea 22.  Esto nos dará una lista con 35 paquetes.
3. Si restamos 5000 al número de puerto origen de todos los 35 paquetes obtenidos después de la filtración nos quedara una secuencia de números que si pasamos de números a código ASCII pbtenemos la bandera.
4. Para automatizar el paso 3 podemos crear un script de python. Para realizar el script será necesario instalar la herramienta de scapy. Comando `python3 -m pip install scapy`
A continuación se muestra el contenido del script de python
``` python
from scapy.all import *

packets = rdpcap('capture.pcap')

flag = ''

for p in packets:
        if UDP in p and p[UDP].dport == 22:
                if p[UDP].sport > 5000:
                        flag += chr(p[UDP].sport - 5000)

print(flag)

```

Si ejecutamos el script en python obtenderemos la bandera.
``` bash
┌──(kali㉿kali)-[~/pico]
└─$ python script.py
picoCTF{p1LLf3r3d_data_v1a_st3g0}

```
## Notas