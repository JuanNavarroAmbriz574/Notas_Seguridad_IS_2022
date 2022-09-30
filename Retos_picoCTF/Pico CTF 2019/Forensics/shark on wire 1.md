## Objetivo
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.

## Solución
Primero descargamos el archivo.
``` bash
juan574-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap
--2022-09-29 13:24:23--  https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 239455 (234K) [application/octet-stream]
Saving to: 'capture.pcap'

capture.pcap        100%[==================>] 233.84K  --.-KB/s    in 0.1s    

2022-09-29 13:24:24 (1.97 MB/s) - 'capture.pcap' saved [239455/239455]

juan574-picoctf@webshell:~$ ls
README.txt  capture.pcap
```

## Notas
Modelo OSI