
## Objetivo
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/51/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/51/level1.flag.txt.enc) in the same directory too.

## Solución
Primero descargamos los archivos.
``` bahs
juan574-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/51/level1.py
--2022-09-26 18:19:24--  https://artifacts.picoctf.net/c/51/level1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 108.156.172.74, 108.156.172.120, 108.156.172.42, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|108.156.172.74|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 876 [application/octet-stream]
Saving to: 'level1.py'

level1.py           100%[==================>]     876  --.-KB/s    in 0s      

2022-09-26 18:19:24 (72.9 MB/s) - 'level1.py' saved [876/876]

juan574-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/51/level1.flag.txt.enc
--2022-09-26 18:19:45--  https://artifacts.picoctf.net/c/51/level1.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 108.156.172.42, 108.156.172.120, 108.156.172.6, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|108.156.172.42|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30 [application/octet-stream]
Saving to: 'level1.flag.txt.enc'

level1.flag.txt.enc 100%[==================>]      30  --.-KB/s    in 0s      

2022-09-26 18:19:45 (14.4 MB/s) - 'level1.flag.txt.enc' saved [30/30]

juan574-picoctf@webshell:~$ ls
README.txt  level1.flag.txt.enc  level1.py
```
Hacemos cat al archivo level1.py para ver que es lo que hace el script y obtenemos lo siguiente
``` bash
juan574-picoctf@webshell:~$ cat level1.py
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


flag_enc = open('level1.flag.txt.enc', 'rb').read()



def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "691d"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")
```

Analizando un poco el código nos damos cuenta que el script pregunta por la bandera o flag del reto y vemos que si nuestra respuesta es igual a '691d' nos dara la contraseña por lo que ejecuntamos el script level1.py e introducimos como contraseña 691d y obtenemos la bandera.

``` bash
juan574-picoctf@webshell:~$ python level1.py 
Please enter correct password for flag: 691d
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_56891419}
```
## Notas
