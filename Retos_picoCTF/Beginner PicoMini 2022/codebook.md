## Objetivo
Run the Python script `code.py` in the same directory as `codebook.txt`.

-   [Download code.py](https://artifacts.picoctf.net/c/101/code.py)
-   [Download codebook.txt](https://artifacts.picoctf.net/c/101/codebook.txt)

## Solución
El primer paso es descargar ambos archivos
``` bahs
juan574-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/101/code.py https://artifacts.picoctf.net/c/101/codebook.txt
--2022-09-26 17:16:12--  https://artifacts.picoctf.net/c/101/code.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 108.156.172.6, 108.156.172.42, 108.156.172.120, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|108.156.172.6|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1278 (1.2K) [application/octet-stream]
Saving to: 'code.py'

code.py             100%[==================>]   1.25K  --.-KB/s    in 0s      

2022-09-26 17:16:12 (60.6 MB/s) - 'code.py' saved [1278/1278]

--2022-09-26 17:16:12--  https://artifacts.picoctf.net/c/101/codebook.txt
Reusing existing connection to artifacts.picoctf.net:443.
HTTP request sent, awaiting response... 200 OK
Length: 27 [application/octet-stream]
Saving to: 'codebook.txt'

codebook.txt        100%[==================>]      27  --.-KB/s    in 0s      

2022-09-26 17:16:13 (12.8 MB/s) - 'codebook.txt' saved [27/27]

FINISHED --2022-09-26 17:16:13--
Total wall clock time: 0.1s
Downloaded: 2 files, 1.3K in 0s (56.3 MB/s)
juan574-picoctf@webshell:~$ ls
README.txt  code.py  codebook.txt
```

Por último, corremos el archivo `code.py` y este nos dara la bandera
``` bash
juan574-picoctf@webshell:~$ python code.py
picoCTF{c0d3b00k_455157_7d102d7a}
```
## Notas


