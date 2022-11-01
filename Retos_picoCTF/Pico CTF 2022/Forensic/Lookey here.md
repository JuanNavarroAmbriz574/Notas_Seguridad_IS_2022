## Objetivo
Attackers have hidden information in a very large mass of data in the past, maybe they are still doing it.Download the data [here](https://artifacts.picoctf.net/c/295/anthem.flag.txt).

## Solución
1. Descargamos el archivo de texto.
2. Buscamos en el archivo la palabra picoCTF y obtenemos la bandera.
``` bash
┌──(kali㉿kali)-[~/pico]
└─$ cat anthem.flag.txt | grep picoCTF
      we think that the men of picoCTF{gr3p_15_@w3s0m3_58f5c024}
```

## Notas

