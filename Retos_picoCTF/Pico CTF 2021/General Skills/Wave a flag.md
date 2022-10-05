## Objetivo
Can you invoke help flags for a tool or binary? [This program](https://mercury.picoctf.net/static/beec4f433e5ee5bfcd71bba8d5863faf/warm)
has extraordinarily helpful information...

## Solución
``` bash
juan574-picoctf@webshell:/home$ cd /tmp/
juan574-picoctf@webshell:/tmp$ mktemp -d
/tmp/tmp.pYSoh4lmVa
juan574-picoctf@webshell:/tmp$ cd tmp.pYSoh4lmVa
juan574-picoctf@webshell:/tmp/tmp.pYSoh4lmVa$ wget https://mercury.picoctf.net/static/beec4f433e5ee5bfcd71bba8d5863faf/warm
--2022-09-22 22:00:29--  https://mercury.picoctf.net/static/beec4f433e5ee5bfcd71bba8d5863faf/warm
Resolving mercury.picoctf.net (mercury.picoctf.net)... 18.189.209.142
Connecting to mercury.picoctf.net (mercury.picoctf.net)|18.189.209.142|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10936 (11K) [application/octet-stream]
Saving to: 'warm'

warm                100%[==================>]  10.68K  --.-KB/s    in 0s      

2022-09-22 22:00:29 (315 MB/s) - 'warm' saved [10936/10936]

juan574-picoctf@webshell:/tmp/tmp.pYSoh4lmVa$ ls
warm
juan574-picoctf@webshell:/tmp/tmp.pYSoh4lmVa$ ls -l 
total 12
-rw-rw-r-- 1 juan574-picoctf juan574-picoctf 10936 Mar 16  2021 warm
juan574-picoctf@webshell:/tmp/tmp.pYSoh4lmVa$ file warm 
warm: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=506b7be935d8940c672ab0d40d2e03ebd746155b, with debug_info, not stripped
juan574-picoctf@webshell:/tmp/tmp.pYSoh4lmVa$ chmod+x warm 
-bash: chmod+x: command not found
juan574-picoctf@webshell:/tmp/tmp.pYSoh4lmVa$ chmod +x warm 
juan574-picoctf@webshell:/tmp/tmp.pYSoh4lmVa$ ls -l
total 12
-rwxrwxr-x 1 juan574-picoctf juan574-picoctf 10936 Mar 16  2021 warm
juan574-picoctf@webshell:/tmp/tmp.pYSoh4lmVa$ ./warm 
Hello user! Pass me a -h to learn what I can do!
juan574-picoctf@webshell:/tmp/tmp.pYSoh4lmVa$ ./warm -h
Oh, help? I actually don't do much, but I do have this flag here: picoCTF{b1scu1ts_4nd_gr4vy_616f7182}
```

## Notas
1. `chmod +x` sirve para hacer a  un archivo ejecutable para todos los usuarios. 