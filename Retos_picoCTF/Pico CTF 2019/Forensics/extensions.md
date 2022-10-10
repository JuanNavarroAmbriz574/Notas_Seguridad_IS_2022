## Objetivo
This is a really weird text file [TXT](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)? Can you find the flag?

## Solución
1. Primero descargamos el archivo.
``` bash
juan574-picoctf@webshell:~$ wget https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt
--2022-09-29 13:39:43--  https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt
Resolving jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)... 3.131.60.8
Connecting to jupiter.challenges.picoctf.org (jupiter.challenges.picoctf.org)|3.131.60.8|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9984 (9.8K) [application/octet-stream]
Saving to: 'flag.txt'

flag.txt            100%[==================>]   9.75K  --.-KB/s    in 0s      

2022-09-29 13:39:43 (324 MB/s) - 'flag.txt' saved [9984/9984]

juan574-picoctf@webshell:~$ ls
README.txt  flag.txt

```

2. Si hacemo un vaciado hexadecimal al archivo nos damos cuenta que el archivo `flag.txt` realemente es una imagen con extensión .png.
``` bash
┌──(kali㉿kali)-[~/retosPIcoCTF]
└─$ xxd flag.txt | head                   
00000000: 8950 4e47 0d0a 1a0a 0000 000d 4948 4452  .PNG........IHDR
00000010: 0000 06a1 0000 0260 0802 0000 0085 ad5e  .......`.......^
00000020: 9a00 0000 0173 5247 4200 aece 1ce9 0000  .....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 0000 1625 0000 1625 0149  ..pHYs...%...%.I
00000050: 5224 f000 0026 9549 4441 5478 5eed dd6b  R$...&.IDATx^..k
00000060: 421b 39b7 05d0 3b2e 0694 f130 9a4c 2683  B.9...;....0.L&.
00000070: f9ae 5f80 4e3d 25bb 4cb3 f15a bfba a14a  .._.N=%.L..Z...J
00000080: 7574 2413 7927 c0ff fd0f 0000 0000 4826  ut$.y'........H&
00000090: e303 0000 0080 6c32 3e00 0000 00c8 26e3  ......l2>.....&.
```

3. Cambiamos la extensión del archivo `flag.txt`  de .txt a .png
``` bash
juan574-picoctf@webshell:~$ mv flag.txt flag.png
juan574-picoctf@webshell:~$ ls
README.txt  flag.png
```

4. Al abrir la imagen obtenemos la bandera.
![IMG25.png](../../imgRes/IMG25.png)
## Notas
Magic btytes es la forma del sistema operativo para saber que tipo de archivo.