## Objetivo
Download the disk image and use `mmls` on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

-   [Download disk image](https://artifacts.picoctf.net/c/114/disk.img.gz)
-   Access checker program: `nc saturn.picoctf.net 52279`

## Solución
1. Descargamos la imagen de disco.
``` bash
juan574-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/114/disk.img.gz
--2022-10-25 18:10:19--  https://artifacts.picoctf.net/c/114/disk.img.gz
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 108.156.172.42, 108.156.172.6, 108.156.172.120, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|108.156.172.42|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 29714372 (28M) [application/octet-stream]
Saving to: 'disk.img.gz'

disk.img.gz         100%[==================>]  28.34M  1.79MB/s    in 16s     

2022-10-25 18:10:34 (1.81 MB/s) - 'disk.img.gz' saved [29714372/29714372]

juan574-picoctf@webshell:~$ ls
README.txt  disk.img.gz
```

2. Descomprimimos la imagen de disco.
``` bash
juan574-picoctf@webshell:~$ gzip -d disk.img.gz 
```

3. Utilizamos el comando `mmls` pare ver como estan configuradas las particiones del disco de imagen.
``` bash

```

4.  ejecutamos `c saturn.picoctf.net 52279`


## Notas
`mmls` sirve para poder observar como estan configuradas las particiones en el disco de imagen.
