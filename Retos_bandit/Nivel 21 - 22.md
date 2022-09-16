# Bandit Level

## Objetivo
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed.

## Cosas utilies
user: bandit21
password: NvEJF7oVjkddltPSrdKEFOllh9V1IBcq

## Solucion
``` bash
bandit22@bandit:~$ cat /etc/cron.d/cronjob_bandit23  
@reboot bandit23 /usr/bin/cronjob_bandit23.sh &> /dev/null 

* * * * * bandit23 /usr/bin/cronjob_bandit23.sh &> /dev/null  
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh  
#!/bin/bash

myname=$(whoami)  
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"cat /etc/bandit_pass/$myname > /tmp/$mytarget
bandit22@bandit:~$ **myname=bandit23**  
bandit22@bandit:~$ echo I am user $myname | md5sum | cut -d ' ' -f 1  
8ca319486bfbbc3663ea0fbe81326349  
bandit22@bandit:~$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349  
WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff
```

## Notas
cron es un programa que sirve como un calendario y que ejecuta rutinas de software cada vez que un palzo de timepo se cumpla.