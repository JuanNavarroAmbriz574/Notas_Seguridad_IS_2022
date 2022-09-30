## Objetivo
What is 0x3D (base 16) in decimal (base 10)?

## Solucion
``` bash
$ echo '0x3D' | xxd -r -p
=
```
Pero el '=' en ascii es igual al número 61, por lo tanto, 0x3D es igual a 61.

Otra posible solución es usando el  comando `printf`

``` bash
$ printf "%d" 0x3D
61
```
## Notas
El comando printf nos puede ayudar a imprimir un numero en base hexadecimal a base 10.
El %d significa imprimir en base decimal.
