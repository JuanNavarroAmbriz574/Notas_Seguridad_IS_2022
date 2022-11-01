## Objetivo
I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://vivian-dai.github.io/PicoCTF2021-Writeup/Forensics/MacroHard%20WeakEdge/Forensics%20is%20fun.pptm)

## Solución
1. Descargamos el archivo.
``` bash
┌──(kali㉿kali)-[~/pico]
└─$ wget https://vivian-dai.github.io/PicoCTF2021-Writeup/Forensics/MacroHard%20WeakEdge/Forensics%20is%20fun.pptm
--2022-10-25 09:43:46--  https://vivian-dai.github.io/PicoCTF2021-Writeup/Forensics/MacroHard%20WeakEdge/Forensics%20is%20fun.pptm
Resolving vivian-dai.github.io (vivian-dai.github.io)... 185.199.111.153, 185.199.110.153, 185.199.109.153, ...
Connecting to vivian-dai.github.io (vivian-dai.github.io)|185.199.111.153|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 100093 (98K) [application/vnd.ms-powerpoint.presentation.macroenabled.12]
Saving to: ‘Forensics is fun.pptm’

Forensics is fun.pptm                     100%[===================================================================================>]  97.75K   493KB/s    in 0.2s    

2022-10-25 09:43:47 (493 KB/s) - ‘Forensics is fun.pptm’ saved [100093/100093]

																			
┌──(kali㉿kali)-[~/pico]
└─$ ls
'Forensics is fun.pptm'

```

2. Desempaquetamos el archivo .pptm usando `unzip`
``` bash
┌──(kali㉿kali)-[~/pico]
└─$ unzip Forensics\ is\ fun.pptm
 ... Extract thing
```

- Analizamos los archivos y podemos ver que hay un hidden, por lo cual vamos a verlo.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ cd ppt/slideMasters

┌──(kali㉿kali)-[~/pico]
└─$ ls
hidden  _rels  slideMaster1.xml

┌──(kali㉿kali)-[~/pico]
└─$ cat hidden
Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q

```

-  Desencriptamos el contenido de hidden en base 64 y obtenemos la bandera.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ cat hidden | tr -d ' ' | base6 
flag: picoCTF{D1d_u_kn0w_ppts_r_z1p5}base64: entrada inválida

```
## Notas
