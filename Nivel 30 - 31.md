# Bandit Level

## Objetivo
There is a git repository at `ssh://bandit30-git@localhost/home/bandit30-git/repo`. The password for the user `bandit30-git` is the same as for the user `bandit30`.

Clone the repository and find the password for the next level.

## Cosas utilies
user: bandit30
password: xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS

## Solucion
``` bash
bandit30@bandit:~$ mktemp -d
/tmp/tmp.pWAQWdt8re
bandit30@bandit:~$ cd /tmp/tmp.pWAQWdt8re
bandit30@bandit:/tmp/tmp.pWAQWdt8re$ git clone ssh://bandit30-git@localhost:2220/home/bandit30-git/repo
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit30/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit30/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit30-git@localhost's password:
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (4/4), done.
bandit30@bandit:/tmp/tmp.pWAQWdt8re$

bandit30@bandit:/tmp/tmp.pWAQWdt8re/repo$ ls
README.md
bandit30@bandit:/tmp/tmp.pWAQWdt8re/repo$ cat README.md
just an epmty file... muahaha
bandit30@bandit:/tmp/tmp.pWAQWdt8re/repo$ git log
commit a325f29e1cc26b0f0dc5f89b4348e389b408cc87 (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 1 06:30:28 2022 +0000

    initial commit of README.md
bandit30@bandit:/tmp/tmp.pWAQWdt8re/repo$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
bandit30@bandit:/tmp/tmp.pWAQWdt8re/repo$ git checkout master
Already on 'master'
Your branch is up to date with 'origin/master'.
bandit30@bandit:/tmp/tmp.pWAQWdt8re/repo$ git tag
secret
bandit30@bandit:/tmp/tmp.pWAQWdt8re/repo$ git show secret
OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt


```

## Notas
1. Git tags son una forma de referenciar puntos clave del desarollo de un proyecto dentro de un repositorio. El uso más común que se les da a las git tags son para marcar versiónes de un proyecto.
2. El comando git tag sirve para poder ver todas las tags de un repositorio.
3. Para crear una tag en git usamos el siguiente comando: git tag -a <tag_name>  -m <tag_message>