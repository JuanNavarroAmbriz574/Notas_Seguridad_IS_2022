## Objetivo
Another program, but this time, it seems to want some input. What happens if you try to run it on the command line with input "Hello!"?Download the program [here](https://artifacts.picoctf.net/c/352/run).




## Solución
1. Descargamos el archivo proporcionado.
2. Damos al archivo permisos de ejecución.
``` sehll
┌──(kali㉿kali)-[~/pico]
└─$ chmod +x run 
```
3. Ejecutamos el archivo.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ ./run
Run this file with only one argument.

```
Al parecer tenemos que correr el programa pasando un argumento.

4. Corremos el programa pasando el arguemento Hello!
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ ./run Hello!
The flag is: picoCTF{F1r57_4rgum3n7_96f2195f}                                                                                                                                                                      

```



## Notas