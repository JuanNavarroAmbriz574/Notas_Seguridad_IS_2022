## Objetivo
In RSA, a small `e` value can be problematic, but what about `N`? Can you decrypt this? [values](https://mercury.picoctf.net/static/b9ddda080c56fb421bf30409bec3460d/values)


## Solución
1. Descargamos el archivo y revisamos su contenido.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ cat values    
Decrypt my super sick RSA:
c: 964354128913912393938480857590969826308054462950561875638492039363373779803642185
n: 1584586296183412107468474423529992275940096154074798537916936609523894209759157543
e: 65537 
```

Vemos que para desencriptar el mensaje (FORMULA: c^d mod n ) es necesario obtener d que a su vez para calcular d es necesario calcular los valores de p,q. Para hacer esto podemos aprovechar que N es un valor pequeño para factorizar n y obtener p y q.

2. Factorizamos n utilizando el siguiente sitio: http://www.factordb.com/ y obtenemos que:
- p = 2434792384523484381583634042478415057961
- q = 650809615742055581459820253356987396346063
Ya con estos valores ya podemos desencriptar el texto usando python.

``` shell
┌──(kali㉿kali)-[~/pico]
└─$ python
Python 3.10.5 (main, Jun  8 2022, 09:26:22) [GCC 11.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> from Crypto.Util.number import long_to_bytes
>>> from Crypto.Util.number import inverse
>>> 
>>> 
>>> c = 964354128913912393938480857590969826308054462950561875638492039363373779803642185
>>> n = 1584586296183412107468474423529992275940096154074798537916936609523894209759157543
>>> e = 65537
>>> p = 2434792384523484381583634042478415057961
>>> q = 650809615742055581459820253356987396346063
>>> tn = (p-1)*(q-1)
>>> d = inverse(e,tn)
>>> m = pow(c,d,n)
>>> long_to_bytes(m)
b'picoCTF{sma11_N_n0_g0od_73918962}'

```
## Notas