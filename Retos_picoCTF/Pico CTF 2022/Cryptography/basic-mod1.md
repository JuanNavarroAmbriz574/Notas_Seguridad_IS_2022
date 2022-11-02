## Objetivo
We found this weird message being passed around on the servers, we think we have a working decryption scheme.Download the message [here](https://artifacts.picoctf.net/c/395/message.txt).Take each number mod 37 and map it to the following character set: 0-25 is the alphabet (uppercase), 26-35 are the decimal digits, and 36 is an underscore.Wrap your decrypted message in the picoCTF flag format (i.e. `picoCTF{decrypted_message}`)

## Solución
1. Descargamos el archivo  y vemos el contenido.
``` sehll
┌──(kali㉿kali)-[~/pico]
└─$ cat message.txt 
91 322 57 124 40 406 272 147 239 285 353 272 77 110 296 262 299 323 255 337 150 102 
```
El reto nos pide aplicar una serie de operafciones al conjunto de elementos del archivo. Para hacer esto vamos a crear un scrypt de python.

``` python
datos = open('message.txt').read().split()

flag = ''

for n in datos
	c = int(n) % 37
	if c>=0 and c<=25 :
		s = chr(c+65)
	elif c>=26 and c<=35:
		s = chr(c+22)
	else:
		s = '_'
	flag += s

print(f"picoCTF{{{flag}}}")
```

Ejecutamos el script anterior y obtenemos la bandera
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ python script.py
picoCTF{R0UND_N_R0UND_ADD17EC2}

```

## Notas