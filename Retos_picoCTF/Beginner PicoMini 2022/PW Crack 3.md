## Objetivo
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/24/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/24/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/24/level3.hash.bin) in the same directory too.There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

## Solución
Primero descargamos los archivos
``` bash
juan574-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/24/level3.py https://artifacts.picoctf.net/c/24/level3.flag.txt.enc https://artifacts.picoctf.net/c/24/level3.hash.bin
--2022-09-27 01:25:44--  https://artifacts.picoctf.net/c/24/level3.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 108.156.172.6, 108.156.172.120, 108.156.172.74, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|108.156.172.6|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1337 (1.3K) [application/octet-stream]
Saving to: 'level3.py'

level3.py           100%[==================>]   1.31K  --.-KB/s    in 0s      

2022-09-27 01:25:45 (62.6 MB/s) - 'level3.py' saved [1337/1337]

--2022-09-27 01:25:45--  https://artifacts.picoctf.net/c/24/level3.flag.txt.enc
Reusing existing connection to artifacts.picoctf.net:443.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level3.flag.txt.enc'

level3.flag.txt.enc 100%[==================>]      31  --.-KB/s    in 0s      

2022-09-27 01:25:45 (79.6 KB/s) - 'level3.flag.txt.enc' saved [31/31]

--2022-09-27 01:25:45--  https://artifacts.picoctf.net/c/24/level3.hash.bin
Reusing existing connection to artifacts.picoctf.net:443.
HTTP request sent, awaiting response... 200 OK
Length: 16 [application/octet-stream]
Saving to: 'level3.hash.bin'

level3.hash.bin     100%[==================>]      16  --.-KB/s    in 0s      

2022-09-27 01:25:45 (413 KB/s) - 'level3.hash.bin' saved [16/16]

FINISHED --2022-09-27 01:25:45--
Total wall clock time: 0.2s
Downloaded: 3 files, 1.4K in 0s (3.01 MB/s)

juan574-picoctf@webshell:~$ ls
README.txt  level3.flag.txt.enc  level3.hash.bin  level3.py
```

Como el problema lo indica hay 7 posibles contraseñas y tenemos que ver cual es la correcta, por lo que probamos cada una de ellasy vemos cual es la correcta para hacer esto modificamos el script python quedando de la siguinete forma.

``` python
import hashlib

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

flag_enc = open('level3.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level3.hash.bin', 'rb').read()


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_3_pw_check(ans):
    #user_pw = input("Please enter correct password for flag: ")
    user_pw = ans
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")




# The strings below are 7 possibilities for the correct password. 
#   (Only 1 is correct)
pos_pw_list = ["f09e", "4dcf", "87ab", "dba8", "752e", "3961", "f159"]

for pos_ans in pos_pw_list:
    level_3_pw_check(pos_ans)
```
Con el for del final del código probamos todas las soluciones y vemos cual es la correcta. por lo que ejecutamos el script y vemos el resultado.

``` bash
juan574-picoctf@webshell:~$ python level3.py 
That password is incorrect
That password is incorrect
That password is incorrect
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_cd6ed2eb}
That password is incorrect
That password is incorrect
That password is incorrect
```

## Notas