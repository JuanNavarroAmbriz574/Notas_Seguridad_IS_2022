# Bandit Level

## Objetivo
There is a git repository at `ssh://bandit29-git@localhost/home/bandit29-git/repo`. The password for the user `bandit29-git` is the same as for the user `bandit29`.

Clone the repository and find the password for the next level.

## Cosas utilies
user: bandit29
password:  tQKvmcwNYcFS6vmPHIUSI3ShmsrQZK8S

## Solucion
``` bash

bandit29@bandit:~$ mktemp -d
/tmp/tmp.rom85qShfd
bandit29@bandit:~$ cd /^C
bandit29@bandit:~$ cd /tmp/tmp.rom85qShfd
bandit29@bandit:/tmp/tmp.rom85qShfd$ git clone ssh://bandit29-git@localhost:2220/home/bandit29-git/repo
Cloning into 'repo'...
The authenticity of host '[localhost]:2220 ([127.0.0.1]:2220)' can't be established.
ED25519 key fingerprint is SHA256:C2ihUBV7ihnV1wUXRb4RrEcLfXC5CXlhmAAM/urerLY.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Could not create directory '/home/bandit29/.ssh' (Permission denied).
Failed to add the host to the list of known hosts (/home/bandit29/.ssh/known_hosts).
                         _                     _ _ _
                        | |__   __ _ _ __   __| (_) |_
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_
                        |_.__/ \__,_|_| |_|\__,_|_|\__|


                      This is an OverTheWire game server.
            More information on http://www.overthewire.org/wargames

bandit29-git@localhost's password:
Permission denied, please try again.
bandit29-git@localhost''s password:
remote: Enumerating objects: 16, done.
remote: Counting objects: 100% (16/16), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 16 (delta 2), reused 0 (delta 0), pack-reused 0
Receiving objects: 100% (16/16), 1.44 KiB | 1.44 MiB/s, done.
Resolving deltas: 100% (2/2), done.
bandit29@bandit:/tmp/tmp.rom85qShfd$ cd repo/
bandit29@bandit:/tmp/tmp.rom85qShfd/repo$ ls -la
total 16
drwxrwxr-x 3 bandit29 bandit29 4096 Sep 15 13:16 .
drwx------ 3 bandit29 bandit29 4096 Sep 15 13:15 ..
drwxrwxr-x 8 bandit29 bandit29 4096 Sep 15 13:16 .git
-rw-rw-r-- 1 bandit29 bandit29  131 Sep 15 13:16 README.md
bandit29@bandit:/tmp/tmp.rom85qShfd/repo$ cat README.md
# Bandit Notes
Some notes for bandit30 of bandit.

## credentials

- username: bandit30
- password: <no passwords in production!>

bandit29@bandit:/tmp/tmp.rom85qShfd/repo$ git log
commit 1748acec99ba66676acd551c2932fb9fc14a98a3 (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 1 06:30:26 2022 +0000

    fix username

commit c27fff763003bb1d57d311e6763211110b94cc87
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 1 06:30:26 2022 +0000

    initial commit of README.md
bandit29@bandit:/tmp/tmp.rom85qShfd/repo$ git show 1748acec99ba66676acd551c2932fb9fc14a98a3
commit 1748acec99ba66676acd551c2932fb9fc14a98a3 (HEAD -> master, origin/master, origin/HEAD)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 1 06:30:26 2022 +0000

    fix username

diff --git a/README.md b/README.md
index 2da2f39..1af21d3 100644
--- a/README.md
+++ b/README.md
@@ -3,6 +3,6 @@ Some notes for bandit30 of bandit.

 ## credentials

-- username: bandit29
+- username: bandit30
 - password: <no passwords in production!>

bandit29@bandit:/tmp/tmp.rom85qShfd/repo$ git branches -a
git: 'branches' is not a git command. See 'git --help'.
bandit29@bandit:/tmp/tmp.rom85qShfd/repo$ git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/dev
  remotes/origin/master
  remotes/origin/sploits-dev
bandit29@bandit:/tmp/tmp.rom85qShfd/repo$ git chekout dev
git: 'chekout' is not a git command. See 'git --help'.

The most similar command is
        checkout
bandit29@bandit:/tmp/tmp.rom85qShfd/repo$ git checkout dev
Branch 'dev' set up to track remote branch 'dev' from 'origin'.
Switched to a new branch 'dev'
bandit29@bandit:/tmp/tmp.rom85qShfd/repo$ git log
commit 2b1395f00cfb986163082c50100be5be8f249f64 (HEAD -> dev, origin/dev)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Sep 1 06:30:26 2022 +0000

    add data needed for development

commit 989df8073e16b5f7ec337f51bc1f60bd2f6b7e0b
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 1 06:30:26 2022 +0000

    add gif2ascii

commit 1748acec99ba66676acd551c2932fb9fc14a98a3 (origin/master, origin/HEAD, master)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 1 06:30:26 2022 +0000

    fix username

commit c27fff763003bb1d57d311e6763211110b94cc87
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 1 06:30:26 2022 +0000

    initial commit of README.md
bandit29@bandit:/tmp/tmp.rom85qShfd/repo$ git show 1748acec99ba66676acd551c2932fb9fc14a98a3
commit 1748acec99ba66676acd551c2932fb9fc14a98a3 (origin/master, origin/HEAD, master)
Author: Ben Dover <noone@overthewire.org>
Date:   Thu Sep 1 06:30:26 2022 +0000

    fix username

diff --git a/README.md b/README.md
index 2da2f39..1af21d3 100644
--- a/README.md
+++ b/README.md
@@ -3,6 +3,6 @@ Some notes for bandit30 of bandit.

 ## credentials

-- username: bandit29
+- username: bandit30
 - password: <no passwords in production!>

bandit29@bandit:/tmp/tmp.rom85qShfd/repo$ git show 2b1395f00cfb986163082c50100be5be8f249f64
commit 2b1395f00cfb986163082c50100be5be8f249f64 (HEAD -> dev, origin/dev)
Author: Morla Porla <morla@overthewire.org>
Date:   Thu Sep 1 06:30:26 2022 +0000

    add data needed for development

diff --git a/README.md b/README.md
index 1af21d3..a4b1cf1 100644
--- a/README.md
+++ b/README.md
@@ -4,5 +4,5 @@ Some notes for bandit30 of bandit.
 ## credentials

 - username: bandit30
-- password: <no passwords in production!>
+- password: xbhV3HpNGlTIdnjUrdAlPzc2L6y9EOnS


```

## Notas
1. El comando git branch -a permite listar las ramas de un repositorio.
2. El comando git checkout <branch_name> te permite cambiar de rama, dentro de cada hay distintos commits o archivos que no los encontraras en la rama principal.n