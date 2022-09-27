## Objetivo
Our flag printing service has started glitching! `$ nc saturn.picoctf.net 53933`

## Solución
Ejecutamos el comando `nc saturn.picoctf.net 53933`  y obtenemos lo siguiente
``` bash
juan574-picoctf@webshell:~$ nc saturn.picoctf.net 53933 
'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'
```

sabemos que la funcion chr conveierte un numero a unicode, por lo que creamos un script en python con el siguinete contenido

``` python
s = 'picoCTF{gl17ch_m3_n07_' + chr(0x61) + chr(0x34) + chr(0x33) + chr(0x39) + chr(0x32) + chr(0x64) + chr(0x32) + chr(0x65) + '}'
print(s)
```
El cual al ejecutarlo nos da la bandera del reto
``` bash
juan574-picoctf@webshell:~$ python flag.py 
picoCTF{gl17ch_m3_n07_a4392d2e}
```
## Notas
El comando `chr(x)` retorna el caracter al que equivale `x` en unicode, `x` puede ser decimal o hexadecimal.