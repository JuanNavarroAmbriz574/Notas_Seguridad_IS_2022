## Objetivo
Download this image and find the flag.
-   [Download image](https://artifacts.picoctf.net/c/422/pico.flag.png)

## Solución
1. Descargamos la imagen.
2. Usamos Zsteg para obtener los datos ocultos de la imagen. Esta herramienta se puede instalar usando el siguiente comando `gem install zsteg`
3. utilizamos Zsteg para obtener la bandera.
``` bash
┌──(kali㉿kali)-[~/pico]
└─$ zsteg -a -v pico.flag.png | grep picoCTF
b1,rgb,lsb,xy       .. text: "picoCTF{7h3r3_15_n0_5p00n_a1062667}$t3g0"
    00000000: 70 69 63 6f 43 54 46 7b  37 68 33 72 33 5f 31 35  |picoCTF{7h3r3_15|
```
 Flag: picoCTF{7h3r3_15_n0_5p00n_a1062667}

## Notas
Zsteg es una herramienta para pder observar datos ocultos dentro de imagenes.