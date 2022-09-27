## Objetivo
If I told you a word started with 0x70 in hexadecimal, what would it start with in ASCII?

## Solucion
``` bash
$ echo '0x70' | xxd -r -p
p

```

## Notas
1. El comando xxd sirve para hacer un vaciado decimal.
2. Con la opción  -r se convierten caracteres de hexadecimal a ascii.
3. Con la opción -p se le especifica que la salida será en texto plano.