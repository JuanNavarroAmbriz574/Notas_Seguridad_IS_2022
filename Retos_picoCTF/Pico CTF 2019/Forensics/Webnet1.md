
## Objetivo
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key). Recover the flag.

## Solución
1. Descargamos la captura de paquetes y la llave que nos da el reto.
``` bash
┌──(kali㉿kali)-[~/pico]
└─$ wget https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key
--2022-10-18 00:36:53--  https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/capture.pcap
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 92525 (90K) [application/octet-stream]
Saving to: ‘capture.pcap’

capture.pcap                                    100%[======================================================================================================>]  90.36K   185KB/s    in 0.5s    

2022-10-18 00:36:54 (185 KB/s) - ‘capture.pcap’ saved [92525/92525]

--2022-10-18 00:36:54--  https://jupiter.challenges.picoctf.org/static/fbf98e695555a2a48fe42c9a245de376/picopico.key
Reusing existing connection to jupiter.challenges.picoctf.org:443.
HTTP request sent, awaiting response... 200 OK
Length: 1704 (1.7K) [application/octet-stream]
Saving to: ‘picopico.key’

picopico.key                                    100%[======================================================================================================>]   1.66K  --.-KB/s    in 0s      

2022-10-18 00:36:54 (20.6 MB/s) - ‘picopico.key’ saved [1704/1704]

FINISHED --2022-10-18 00:36:54--
Total wall clock time: 1.3s
Downloaded: 2 files, 92K in 0.5s (188 KB/s)
                                                                                                                                                                                               
┌──(kali㉿kali)-[~/pico]
└─$ ls
capture.pcap  picopico.key

```

2. Desencriptamos los paquetes usando la llave que nos proporciona el reto y luego filtramos la llave usando un grep y obtenemos la bandera. El comando final sería :

``` bash
┌──(kali㉿kali)-[~/pico]
└─$ ssldump -r capture.pcap -k picopico.key -d | grep pico -A 2
    61 67 3a 20 70 69 63 6f 43 54 46 7b 74 68 69 73    ag: picoCTF{this
    2e 69 73 2e 6e 6f 74 2e 79 6f 75 72 2e 66 6c 61    .is.not.your.fla
    67 2e 61 6e 79 6d 6f 72 65 7d 0d 0a 43 6f 6e 74    g.anymore}..Cont
--
    67 3a 20 70 69 63 6f 43 54 46 7b 74 68 69 73 2e    g: picoCTF{this.
    69 73 2e 6e 6f 74 2e 79 6f 75 72 2e 66 6c 61 67    is.not.your.flag
    2e 61 6e 79 6d 6f 72 65 7d 0d 0a 43 6f 6e 74 65    .anymore}..Conte
--
    Pico-Flag: picoCTF{this.is.not.your.flag.anymore}
    Keep-Alive: timeout=5, max=99
    Connection: Keep-Alive
--
    00 00 00 01 00 00 00 01 70 69 63 6f 43 54 46 7b    ........picoCTF{
    68 6f 6e 65 79 2e 72 6f 61 73 74 65 64 2e 70 65    honey.roasted.pe
    61 6e 75 74 73 7d 00 00 ff e2 02 1c 49 43 43 5f    anuts}......ICC_



```

La bandera es:  picoCTF{honey.roasted.peanuts}

## Notas
