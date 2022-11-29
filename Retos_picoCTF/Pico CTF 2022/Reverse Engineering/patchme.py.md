## Objetivo
Can you get the flag?Run this [Python program](https://artifacts.picoctf.net/c/387/patchme.flag.py) in the same directory as this [encrypted flag](https://artifacts.picoctf.net/c/387/flag.txt.enc).

## Solución
1. Descargamos el programa enppython y el archivo encriptado.
2. Revisamos el código del programa en python.
``` python
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################


flag_enc = open('flag.txt.enc', 'rb').read()



def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "ak98" + \
                   "-=90" + \
                   "adfjhgj321" + \
                   "sleuth9000"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), "utilitarian")
        print(decryption)
        return
    print("That password is incorrect")



level_1_pw_check()

```
Nos damos cuenta que si la contraseña que le pasamos al programa user_pw == "ak98" + \"-=90" + \"adfjhgj321" + \"sleuth9000") el programa nos dará la bandera por lo que cambiamos esta condición por  ` != ` quedando el programa de la siguiente forma.

``` python
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################


flag_enc = open('flag.txt.enc', 'rb').read()



def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw != "ak98" + \
                   "-=90" + \
                   "adfjhgj321" + \
                   "sleuth9000"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), "utilitarian")
        print(decryption)
        return
    print("That password is incorrect")



level_1_pw_check()

```

3. Ejecutamos el programa, pasamos cualquier cadena y obtenemos la bandera.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ python patchme.flag.py
Please enter correct password for flag: hola
Welcome back... your flag, user:
picoCTF{p47ch1ng_l1f3_h4ck_f01eabfa}

```
## Notas