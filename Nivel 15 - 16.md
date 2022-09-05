# Bandit Level

## Objetivo
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

## Cosas utilies
user: bandit15
passeword: jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt

## Solucion
``` bash
bandit15@bandit:~$ openssl s_client -connect  localhost:30001 -ign_eof
CONNECTED(00000003)

jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
Correct!
JQttfApK4SeyHwDlI9SXGR50qclOAil1
```

## Notas
Openssl es un software de criptografía que hace la comunicación entre computadoras más segura. Este software usa el protocolo SSL (Secure Socket Layer) o también usa el protocolo TLS (Transport Layer Security)