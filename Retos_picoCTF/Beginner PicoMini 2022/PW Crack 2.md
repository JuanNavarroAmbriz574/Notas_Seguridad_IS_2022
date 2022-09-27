## Objetivo
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/17/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/17/level2.flag.txt.enc) in the same directory too.

## Solución
Primero descargamos los archivos.
``` bash
juan574-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/17/level2.py https://artifacts.picoctf.net/c/17/level2.flag.txt.enc
--2022-09-26 18:31:26--  https://artifacts.picoctf.net/c/17/level2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 108.156.172.6, 108.156.172.42, 108.156.172.120, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|108.156.172.6|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 914 [application/octet-stream]
Saving to: 'level2.py'

level2.py           100%[==================>]     914  --.-KB/s    in 0s      

2022-09-26 18:31:27 (962 MB/s) - 'level2.py' saved [914/914]

--2022-09-26 18:31:27--  https://artifacts.picoctf.net/c/17/level2.flag.txt.enc
Reusing existing connection to artifacts.picoctf.net:443.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level2.flag.txt.enc'

level2.flag.txt.enc 100%[==================>]      31  --.-KB/s    in 0s      

2022-09-26 18:31:27 (14.2 MB/s) - 'level2.flag.txt.enc' saved [31/31]

FINISHED --2022-09-26 18:31:27--
Total wall clock time: 0.2s
Downloaded: 2 files, 945 in 0s (302 MB/s)
juan574-picoctf@webshell:~$ ls
README.txt  level2.flag.txt.enc  level2.py
```

Antes de ejecutar el archivo level2.py le hacemos un `cat` para ver que es lo qeu hace el script.
``` bash
juan574-picoctf@webshell:~$ cat level2.py
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

flag_enc = open('level2.flag.txt.enc', 'rb').read()



def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x34) + chr(0x65) + chr(0x63) + chr(0x39) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")
```

Vemos que como en el caso anterior el script preguntará por la contraseña para darnos la bandera y veoms que si la contraseña que proovemos es igaul a  `chr(0x34) + chr(0x65) + chr(0x63) + chr(0x39)` el script nos dara la bandera correcta, por lo tanto, creamos un script en python para convertimos  esos caracteres a cadena 
``` python
#Contenido del script de python
flag = '' + chr(0x34) + chr(0x65) + chr(0x63) + chr(0x39)
print(flag)
```

Ejecutamos el script de python esto nos dara la contraseña y luejo ejecutamos el script e introducimos la contraseña (4ec9) y esto nos dara la bandera.
``` bash
juan574-picoctf@webshell:~$ python flag.py 
4ec9
juan574-picoctf@webshell:~$ python level2.py 
Please enter correct password for flag: 4ec9
Welcome back... your flag, user:
picoCTF{tr45h_51ng1ng_9701e681}
```


## Notas