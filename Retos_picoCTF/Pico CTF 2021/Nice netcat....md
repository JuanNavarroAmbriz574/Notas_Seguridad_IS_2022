## Objetivo
There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 7449`, but it doesn't speak English...

## Solución
Al correr el programa usando $ nc mercury.picoctf.net 7449 el programa imprime muchos números, estos números son la bandera solo que tenemos que transformarlos de números a letras del código ascii.

Para esto creamos un archivo numeros.txt donde estan todos los numeros que arroga el programa al correr $ nc mercury.picoctf.net 7449

Luego creamos un script en python para transformar los números a sus equivalentes en ascii

``` python
fichero = open("numeros.txt")
numeros = fichero.readlines()


flag = ""
for i in range(0,len(numeros)):
        numero = int(numeros[i])
        flag += chr(numero)

print(flag)
```

Al ejecutar el script anterior obtenemos
``` bash
juan574-picoctf@webshell:~$ python converit_numeros_a_ascii.py 
picoCTF{g00d_k1tty!_n1c3_k1tty!_f2d7cafa}
```
## Notas
1. Para ejecutar un script python en una terminal linux solo colocamos: `python nombre_del_script.py`