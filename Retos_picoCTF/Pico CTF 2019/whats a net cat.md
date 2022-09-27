## Objetivo
Using netcat (nc) is going to be pretty important. Can you connect to `jupiter.challenges.picoctf.org` at port `64287` to get the flag?

## Solución

``` bash
nc jupiter.challenges.picoctf.org 64287
You're on your way to becoming the net cat master
picoCTF{nEtCat_Mast3ry_284be8f7}
```

## Notas
Netcat es un comando usado para leer o escribir entre 2 computadoras. La comunicación entre estas computadoras debe de ser en TCP o UDP.
La sintaxis básica de netcat es: nc host_nam
e port