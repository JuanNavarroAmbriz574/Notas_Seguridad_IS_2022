## Objetivo
Fix the syntax error in this Python script to print the flag.[Download Python script](https://artifacts.picoctf.net/c/38/fixme1.py)

## Solución
Primero descargamos el script python
``` bash
juan574-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/38/fixme1.py
--2022-09-26 17:22:27--  https://artifacts.picoctf.net/c/38/fixme1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 108.156.172.6, 108.156.172.120, 108.156.172.74, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|108.156.172.6|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 837 [application/octet-stream]
Saving to: 'fixme1.py'

fixme1.py           100%[==================>]     837  --.-KB/s    in 0s      

2022-09-26 17:22:27 (274 MB/s) - 'fixme1.py' saved [837/837]

juan574-picoctf@webshell:~$ ls
README.txt  fixme1.py
```

Al ejecutar el archivo da un error
``` bash
juan574-picoctf@webshell:~$ python fixme1.py 
  File "/home/juan574-picoctf/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent
```

Por lo que modificamos el archivo usando `nano` y vemos que el error de que la linea `print('That is correct! Here\'s your flag: ' + flag)` está idenatada incorrectamente, por lo que la identamos correctamente quedando el archivo de la siguiente forma.
``` python
import random



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x5a) + chr(0x07) + chr(0x00) + chr(0x46) + chr(0x0b) + chr(0x1a) + chr(0x5a) + chr(0x1d) + chr(0x1d) + chr(0x2a) + chr(0x06) + chr(0x1c) + chr(0x5a) + chr(0x5c) + chr(0x55) + chr(0x40) + chr(0x3a) + chr(0x5e) + chr(0x52) + chr(0x0c) + chr(0x01) + chr(0x42) + chr(0x57) + chr(0x59) + chr(0x0a) + chr(0x14)

  
flag = str_xor(flag_enc, 'enkidu')
print('That is correct! Here\'s your flag: ' + flag)
```

Con el cambio hecho volvemos a ejecutar el archivo `fixme1.py` y esta vez obtenomos la bandera.
``` bash
juan574-picoctf@webshell:~$ python fixme1.py 
That is correct! Here's your flag: picoCTF{1nd3nt1ty_cr1515_09ee727a}
```

## Notas