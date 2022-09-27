## Objetivo
Run the `runme.py` script to get the flag. Download the script with your browser or with `wget` in the webshell.[Download runme.py Python script](https://artifacts.picoctf.net/c/86/runme.py)

## Solución
``` bash
juan574-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/86/runme.py
--2022-09-23 00:10:07--  https://artifacts.picoctf.net/c/86/runme.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 108.156.172.6, 108.156.172.74, 108.156.172.120, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|108.156.172.6|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 270 [application/octet-stream]
Saving to: 'runme.py'

runme.py            100%[==================>]     270  --.-KB/s    in 0.002s  

2022-09-23 00:10:07 (137 KB/s) - 'runme.py' saved [270/270]

juan574-picoctf@webshell:~$ ls -l
total 12
-rw-r--r-- 1 root            root            4448 Sep 22 23:58 README.txt
-rw-rw-r-- 1 juan574-picoctf juan574-picoctf  270 Jan  4  2022 runme.py
juan574-picoctf@webshell:~$ python runme.py
picoCTF{run_s4n1ty_run}
```

## Notas



