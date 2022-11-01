## Objetivo
Figure out how they moved the [flag](https://mercury.picoctf.net/static/e4836d9bcc740d457f4331d68129a0bc/tftp.pcapng)

## Solución
1. Descargar el archivo.
2. Extraemos todos los paquetes del protocolo TFTP en nustra maquina.
3. Hacemos un cat a las instrucciones y vemos que no son legibles, por lo que aplicamos ROT13 al archivo instrucciones.txt
``` shell

┌──(kali㉿kali)-[~/pico]
└─$ cat instructions.txt
GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA
```
Al aplicar rot13 obtnemos : TFTP DOESNT ENCRYPT OUR TRAFFIC SO WE MUST DISGUISE
OUR FLAG TRANSFER .FIGURE OUT A WAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN (Se hagregaron espacios para hacer la cadena más legible)

4. Vemos el contenido de el archivo plan
```

┌──(kali㉿kali)-[~/pico]
└─$ cat plan
VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF

```
 Desencriptamos el mesnaje usando ROT13  y obtenemos lo siguiente: I USED THE PROGRAM AND HID IT WITH-DUEDILIGENCE.CHECK OUT THE PHOTOS

4. Esto nos dice que la bandera esta en las fotos. usamos la herramienta de `steghide` para etraer contenido de las imagens y como contraseña usamos  DUEDILIGENCE y obtenemos la bandera que se contraba en la imagen picture3.bmp

```

┌──(kali㉿kali)-[~/pico]
└─$ ls
instructions.txt  picture3.bmp             program.deb  tftp.pcapng
picture1.bmp      plan                     
picture2.bmp      PoryectosLabsol2022.pdf  

┌──(kali㉿kali)-[~/pico]
└─$ steghide --extract -sf picture1.bmp -p DUEDILIGENCE
steghide:  no pude extraer ningun dato con ese salvoconducto!

┌──(kali㉿kali)-[~/pico]
└─$ steghide --extract -sf picture2.bmp -p DUEDILIGENCE
steghide:  no pude extraer ningun dato con ese salvoconducto!

┌──(kali㉿kali)-[~/pico]
└─$ steghide --extract -sf picture3.bmp -p DUEDILIGENCE
"flag.txt".

┌──(kali㉿kali)-[~/pico]
└─$ cat flag.txt
picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}

```


## Notas
