## Objetivo
I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://jupiter.challenges.picoctf.org/static/74274b96fe966126a1953c80762af80d/whitepages.txt) is all blank!

## Solución
1. Primero descargamos el archivo.
``` bash
┌──(kali㉿kali)-[~/retosPIcoCTF/whitePages]
└─$ wget https://jupiter.challenges.picoctf.org/static/74274b96fe966126a1953c80762af80d/whitepages.txt
--2022-10-09 18:44:38--  https://jupiter.challenges.picoctf.org/static/74274b96fe966126a1953c80762af80d/whitepages.txt
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2964 (2.9K) [application/octet-stream]
Saving to: ‘whitepages.txt’

whitepages.txt                            100%[===================================================================================>]   2.89K  --.-KB/s    in 0s      

2022-10-09 18:44:38 (46.8 MB/s) - ‘whitepages.txt’ saved [2964/2964]

┌──(kali㉿kali)-[~/retosPIcoCTF/whitePages]
└─$ ls
whitepages.txt

```

2. Hacemos una vaciado hexadecimal al archivo whitepages.txt.
``` bash
┌──(kali㉿kali)-[~/retosPIcoCTF/whitePages]
└─$ xxd whitepages.txt | head
00000000: e280 83e2 8083 e280 83e2 8083 20e2 8083  ............ ...
00000010: 20e2 8083 e280 83e2 8083 e280 83e2 8083   ...............
00000020: 20e2 8083 e280 8320 e280 83e2 8083 e280   ...... ........
00000030: 83e2 8083 20e2 8083 e280 8320 e280 8320  .... ...... ... 
00000040: 2020 e280 83e2 8083 e280 83e2 8083 e280    ..............
00000050: 8320 20e2 8083 20e2 8083 e280 8320 e280  .  ... ...... ..
00000060: 8320 20e2 8083 e280 83e2 8083 2020 e280  .  .........  ..
00000070: 8320 20e2 8083 2020 2020 e280 8320 e280  .  ...    ... ..
00000080: 83e2 8083 e280 83e2 8083 2020 e280 8320  ..........  ... 
00000090: e280 8320 e280 8320 e280 83e2 8083 e280  ... ... ........
```
Si revisamos el vaciado nos damos cuenta que existen 2 tipos de caracteres el 20 que es el espacio normal de ASCII y el e28083 que es un tipo de espacio en unicode. 

3. Toma los espacios e28083 (espacio en unicode) como ceros y los espacios 20 (espacios normales) como 1 y arma una expresión binaria.
4. Creamos un script en python para automatizar el punto 3.
Para eso primero instalamos la libreria pwntools de python
``` bash
$ python3 -m pip install pwntools
```

Contenido del script de python
``` python
from pwn import *
file = open('whitepages.txt','rb')
data = bytearray(file.read())
data = data.replace(b'\xe2\x80\x83',b'0')
data = data.replace(b'\x20',b'1')
data = data.decode('ascii')
data = unbits(data)

print(data)

```

5. Corremos el script python y esto nos da la bandera.
``` bash
──(kali㉿kali)-[~/retosPIcoCTF/whitePages]
└─$ python script.py        
b'\n\t\tpicoCTF\n\n\t\tSEE PUBLIC RECORDS & BACKGROUND REPORT\n\t\t5000 Forbes Ave, Pittsburgh, PA 15213\n\t\tpicoCTF{not_all_spaces_are_created_equal_c54f27cd05c2189f8147cc6f5deb2e56}\n\t\t'
```
La bandera es: picoCTF{not_all_spaces_are_created_equal_c54f27cd05c2189f8147cc6f5deb2e56}
## Notas
1. Unicode es un estádar para poder representar más caracteres como por ejemplo caracteres de distintos alfabetos como chino, aleman, japones.
2. UTF-8 es un esquema de codificaión que ocupa de 1 a 4 bytes para representar un caracter.