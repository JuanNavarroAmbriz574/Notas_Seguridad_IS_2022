## Objetivo
Can you get the flag?Reverse engineer this [Python program](https://artifacts.picoctf.net/c/465/unpackme.flag.py).

## Solución
1. Descargamos el programa de python.
2. Revisamos el código de programa.
``` python
import base64
from cryptography.fernet import Fernet



payload = b'gAAAAABiMD06eCisTWoohiYL5jHGdCte5LAviTFguZQSIyRLAWICJpmdrgxhdTB923h6eksddKpKH41I5-HGzI6xGF_7eb_1u0S2Phw2NvYGTF1KzE1-AU66FfIW6QXWnCpPHOS9CatNBuFXuyjEAx86Rld2E7GjvuKEOJJXx_GZE2JgAxnDmvcewoksfjVCCAwNqzixpUPKkIET2xmO4EsDqK4CUG8_JxP0HwSEzW4PH-hVpZrkyse4EodFPsjs7NVJF0hL1_8bP1TCiEEnFn7hCoTRRvlpYQ=='

key_str = 'correctstaplecorrectstaplecorrec'
key_base64 = base64.b64encode(key_str.encode())
f = Fernet(key_base64)
plain = f.decrypt(payload)
exec(plain.decode())

```
Si vemos bien en la linea
``` python
plain = f.decrypt(payload)
```
Se esta desencriptando la bandera por lo que solo necesitamos imprimir el valor de esa variable asi que modificamos el código de la siguiente forma
``` python
import base64
from cryptography.fernet import Fernet



payload = b'gAAAAABiMD06eCisTWoohiYL5jHGdCte5LAviTFguZQSIyRLAWICJpmdrgxhdTB923h6eksddKpKH41I5-HGzI6xGF_7eb_1u0S2Phw2NvYGTF1KzE1-AU66FfIW6QXWnCpPHOS9CatNBuFXuyjEAx86Rld2E7GjvuKEOJJXx_GZE2JgAxnDmvcewoksfjVCCAwNqzixpUPKkIET2xmO4EsDqK4CUG8_JxP0HwSEzW4PH-hVpZrkyse4EodFPsjs7NVJF0hL1_8bP1TCiEEnFn7hCoTRRvlpYQ=='

key_str = 'correctstaplecorrectstaplecorrec'
key_base64 = base64.b64encode(key_str.encode())
f = Fernet(key_base64)
plain = f.decrypt(payload)
print(plain.decode())
exec(plain.decode())

```

4. Volvemos a ejecutar el programa python y nos dara la bandera.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ python unpackme.flag.py

pw = input('What\'s the password? ')

if pw == 'batteryhorse':
  print('picoCTF{175_chr157m45_cd82f94c}')
else:
  print('That password is incorrect.')


What's the password? hola
That password is incorrect.

```
Bandera: picoCTF{175_chr157m45_cd82f94c}
## Notas