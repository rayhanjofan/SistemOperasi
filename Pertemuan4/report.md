# LAPORAN PERTEMUAN 4

<h4> Nama : Rayhan Jofan Halim<h4>
<h4>NIM : 254107020230<h4>
<h4>Kelas : TI-1H<h4>

## Percobaan 1 : Direktori

1. Melihat direktori HOME
```bukan11nya@happyending:~$ pwd
/home/bukan11nya
bukan11nya@happyending:~$ echo $HOME
/home/bukan11nya
```
2. Melihat direktori aktual dan parent direktori
```
bukan11nya@happyending:~$ pwd
/home/bukan11nya
bukan11nya@happyending:~$ cd .
bukan11nya@happyending:~$ pwd
/home/bukan11nya
bukan11nya@happyending:~$ cd ..
bukan11nya@happyending:/home$ pwd
/home
bukan11nya@happyending:/home$ cd
bukan11nya@happyending:~$
```
Membuat satu direktori, lebih dari satu direktori atau sub direktori
```
bukan11nya@happyending:~$ pwd
/home/bukan11nya
```
```
bukan11nya@happyending:~$ mkdir A B C A/D A/E B/F A/D/A
```
```
bukan11nya@happyending:~$ ls -l
total 72
drwxrwxr-x 4 bukan11nya bukan11nya  4096 Mar  4 01:45 A
drwxrwxr-x 3 bukan11nya bukan11nya  4096 Mar  4 01:45 B
-rw-rw-r-- 1 bukan11nya bukan11nya   588 Mar  4 01:42 backup-error.log
-rw-rw-r-- 1 bukan11nya bukan11nya  1537 Mar  4 01:42 backup-success.log
-rw-rw-r-- 1 bukan11nya bukan11nya    37 Mar  4 01:42 backup-success.logq
-rw-rw-r-- 1 bukan11nya bukan11nya  7799 Mar  4 01:42 backup.tar.gz
drwxrwxr-x 2 bukan11nya bukan11nya  4096 Mar  4 01:45 C
-rw-rw-r-- 1 bukan11nya bukan11nya   262 Mar  4 01:39 lat5jb3.bash
-rw-rw-r-- 1 bukan11nya bukan11nya 21370 Mar  2 04:57 list-conf.txt
-rw-rw-r-- 1 bukan11nya bukan11nya 10557 Mar  3 06:19 monitor-system.log
bukan11nya@happyending:~$ ls -l A
total 8
drwxrwxr-x 3 bukan11nya bukan11nya 4096 Mar  4 01:45 D
drwxrwxr-x 2 bukan11nya bukan11nya 4096 Mar  4 01:45 E
bukan11nya@happyending:~$ ls -l A/D
total 4
drwxrwxr-x 2 bukan11nya bukan11nya 4096 Mar  4 01:45 A
```
4. Menghapus satu atau lebih direktori hanya dapat dilakukan pada direktori kosong dan hanya dapat dihapus oleh pemiliknya kecuali bial adiberika ijin aksesnya
```
bukan11nya@happyending:~$ rmdir B
```
```rmdir: failed to remove 'B': Directory not empty```

error karena di dalam directory masih terdapat file
```
bukan11nya@happyending:~$ ls -l B
```

```total 4```
```

drwxrwxr-x 2 bukan11nya bukan11nya 4096 Mar  4 01:45 F

bukan11nya@happyending:~$ rmdir B/F B

bukan11nya@happyending:~$ ls -l B

ls: cannot access 'B': No such file or directory
error karena tidak terdapat file di dalam direktori
```
5. Navigasi direktotri dengan instruksi dengn instruksi cd untuk pindah dari satu direktori ke direktori lain
```
bukan11nya@happyending:~$ pwd
/home/bukan11nya
bukan11nya@happyending:~$ ls -l
total 68
drwxrwxr-x 4 bukan11nya bukan11nya  4096 Mar  4 02:21 A
-rw-rw-r-- 1 bukan11nya bukan11nya   588 Mar  4 01:42 backup-error.log
-rw-rw-r-- 1 bukan11nya bukan11nya  1537 Mar  4 01:42 backup-success.log
-rw-rw-r-- 1 bukan11nya bukan11nya    37 Mar  4 01:42 backup-success.logq
-rw-rw-r-- 1 bukan11nya bukan11nya  7799 Mar  4 01:42 backup.tar.gz
drwxrwxr-x 2 bukan11nya bukan11nya  4096 Mar  4 01:45 C
-rw-rw-r-- 1 bukan11nya bukan11nya   262 Mar  4 01:39 lat5jb3.bash
-rw-rw-r-- 1 bukan11nya bukan11nya 21370 Mar  2 04:57 list-conf.txt
-rw-rw-r-- 1 bukan11nya bukan11nya 10557 Mar  3 06:19 monitor-system.log
bukan11nya@happyending:~$ cd A
bukan11nya@happyending:~/A$ pwd
/home/bukan11nya/A
bukan11nya@happyending:~/A$ cd ..
bukan11nya@happyending:~$ pwd
/home/bukan11nya
bukan11nya@happyending:~$ cd /home/bukan11nya/C
bukan11nya@happyending:~/C$ pwd
/home/bukan11nya/C
bukan11nya@happyending:~/C$ cd /bukan11nya/C
-bash: cd: /bukan11nya/C: No such file or directory
error karena harus terdapat home nya
bukan11nya@happyending:~/C$ pwd
/home/bukan11nya/C
```
## Percobaan 2 : Manipulasi File

1. perintah ```cp``` untuk mengkopi file atau seluruh direktori
```
bukan11nya@happyending:~$ cat > contoh
membuat sebuah file
bukan11nya@happyending:~$ cp contoh contoh1
bukan11nya@happyending:~$ ls -l
total 76
drwxrwxr-x 4 bukan11nya bukan11nya  4096 Mar  4 02:21 A
-rw-rw-r-- 1 bukan11nya bukan11nya   588 Mar  4 01:42 backup-error.log
-rw-rw-r-- 1 bukan11nya bukan11nya  1537 Mar  4 01:42 backup-success.log
-rw-rw-r-- 1 bukan11nya bukan11nya    37 Mar  4 01:42 backup-success.logq
-rw-rw-r-- 1 bukan11nya bukan11nya  7799 Mar  4 01:42 backup.tar.gz
drwxrwxr-x 2 bukan11nya bukan11nya  4096 Mar  4 01:45 C
-rw-rw-r-- 1 bukan11nya bukan11nya    19 Mar  4 02:30 contoh
-rw-rw-r-- 1 bukan11nya bukan11nya    19 Mar  4 02:30 contoh1
-rw-rw-r-- 1 bukan11nya bukan11nya   262 Mar  4 01:39 lat5jb3.bash
-rw-rw-r-- 1 bukan11nya bukan11nya 21370 Mar  2 04:57 list-conf.txt
-rw-rw-r-- 1 bukan11nya bukan11nya 10557 Mar  3 06:19 monitor-system.log
bukan11nya@happyending:~$ cp contoh A
bukan11nya@happyending:~$ ls -l A
total 12
-rw-rw-r-- 1 bukan11nya bukan11nya   19 Mar  4 02:31 contoh
drwxrwxr-x 3 bukan11nya bukan11nya 4096 Mar  4 01:45 D
drwxrwxr-x 2 bukan11nya bukan11nya 4096 Mar  4 01:45 E
bukan11nya@happyending:~$ cp contoh contoh1 A/D
bukan11nya@happyending:~$ ls -l A/D
total 12    
drwxrwxr-x 2 bukan11nya bukan11nya 4096 Mar  4 01:45 A
-rw-rw-r-- 1 bukan11nya bukan11nya   19 Mar  4 02:32 contoh
-rw-rw-r-- 1 bukan11nya bukan11nya   19 Mar  4 02:32 contoh1
```

2. Perintah ```mv``` untuk meminah file

```
bukan11nya@happyending:~$ mv contoh contoh2
bukan11nya@happyending:~$ ls -l
total 68
drwxrwxr-x 4 bukan11nya bukan11nya  4096 Mar  4 02:31 A
-rw-rw-r-- 1 bukan11nya bukan11nya   588 Mar  4 01:42 backup-error.log
-rw-rw-r-- 1 bukan11nya bukan11nya  1537 Mar  4 01:42 backup-success.log
-rw-rw-r-- 1 bukan11nya bukan11nya    37 Mar  4 01:42 backup-success.logq
-rw-rw-r-- 1 bukan11nya bukan11nya  7799 Mar  4 01:42 backup.tar.gz
drwxrwxr-x 2 bukan11nya bukan11nya  4096 Mar  4 01:45 C
-rw-rw-r-- 1 bukan11nya bukan11nya   262 Mar  4 01:39 lat5jb3.bash
-rw-rw-r-- 1 bukan11nya bukan11nya 21370 Mar  2 04:57 list-conf.txt
-rw-rw-r-- 1 bukan11nya bukan11nya 10557 Mar  3 06:19 monitor-system.log
```
```
bukan11nya@happyending:~$ mv contoh1 contoh2 A/D
bukan11nya@happyending:~$ ls -1 A/D
A
contoh
contoh1
contoh2
bukan11nya@happyending:~/A/D$ mv contoh contoh1 ~/C
bukan11nya@happyending:~$ ls -l C
total 8
-rw-rw-r-- 1 bukan11nya bukan11nya 19 Mar  4 02:32 contoh
-rw-rw-r-- 1 bukan11nya bukan11nya 19 Mar  4 02:30 contoh1
```
3. perintah ```rm``` untuk menghapus file
```
bukan11nya@happyending:~/A/D$ rm contoh2
bukan11nya@happyending:~/A/D$ ls -l
total 0
bukan11nya@happyending:~$ ls -l
total 68
drwxrwxr-x 4 bukan11nya bukan11nya  4096 Mar  4 02:31 A
-rw-rw-r-- 1 bukan11nya bukan11nya   588 Mar  4 01:42 backup-error.log
-rw-rw-r-- 1 bukan11nya bukan11nya  1537 Mar  4 01:42 backup-success.log
-rw-rw-r-- 1 bukan11nya bukan11nya    37 Mar  4 01:42 backup-success.logq
-rw-rw-r-- 1 bukan11nya bukan11nya  7799 Mar  4 01:42 backup.tar.gz
drwxrwxr-x 2 bukan11nya bukan11nya  4096 Mar  9 03:24 C
-rw-rw-r-- 1 bukan11nya bukan11nya   262 Mar  4 01:39 lat5jb3.bash
-rw-rw-r-- 1 bukan11nya bukan11nya 21370 Mar  2 04:57 list-conf.txt
-rw-rw-r-- 1 bukan11nya bukan11nya 10557 Mar  3 06:19 monitor-system.log

bukan11nya@happyending:~/C$ rm -i contoh
rm: remove regular file 'contoh'? yes
bukan11nya@happyending:~/C$ ls
contoh1
bukan11nya@happyending:~/C$ rm -rf A C
bukan11nya@happyending:~/C$ ls -l
total 4
-rw-rw-r-- 1 bukan11nya bukan11nya 19 Mar  4 02:30 contoh1
bukan11nya@happyending:~/C$ bukan11nya@happyending:~/A/D$ rm contoh2
bukan11nya@happyending:~/A/D$ ls -l
total 0
```
## Percobaan 3 : Symbolic Link
```
bukan11nya@happyending:~$ echo "Hallo apa khabar" > halo.txt
bukan11nya@happyending:~$ ls -l
total 72
drwxrwxr-x 4 bukan11nya bukan11nya  4096 Mar  4 02:31 A
-rw-rw-r-- 1 bukan11nya bukan11nya   588 Mar  4 01:42 backup-error.log
-rw-rw-r-- 1 bukan11nya bukan11nya  1537 Mar  4 01:42 backup-success.log
-rw-rw-r-- 1 bukan11nya bukan11nya    37 Mar  4 01:42 backup-success.logq
-rw-rw-r-- 1 bukan11nya bukan11nya  7799 Mar  4 01:42 backup.tar.gz
drwxrwxr-x 2 bukan11nya bukan11nya  4096 Mar  9 03:34 C
-rw-rw-r-- 1 bukan11nya bukan11nya    17 Mar  9 03:39 halo.txt
-rw-rw-r-- 1 bukan11nya bukan11nya   262 Mar  4 01:39 lat5jb3.bash
-rw-rw-r-- 1 bukan11nya bukan11nya 21370 Mar  2 04:57 list-conf.txt
-rw-rw-r-- 1 bukan11nya bukan11nya 10557 Mar  3 06:19 monitor-system.log
bukan11nya@happyending:~$ ln halo.txt z
bukan11nya@happyending:~$ ls -l
total 76
drwxrwxr-x 4 bukan11nya bukan11nya  4096 Mar  4 02:31 A
-rw-rw-r-- 1 bukan11nya bukan11nya   588 Mar  4 01:42 backup-error.log
-rw-rw-r-- 1 bukan11nya bukan11nya  1537 Mar  4 01:42 backup-success.log
-rw-rw-r-- 1 bukan11nya bukan11nya    37 Mar  4 01:42 backup-success.logq
-rw-rw-r-- 1 bukan11nya bukan11nya  7799 Mar  4 01:42 backup.tar.gz
drwxrwxr-x 2 bukan11nya bukan11nya  4096 Mar  9 03:34 C
-rw-rw-r-- 2 bukan11nya bukan11nya    17 Mar  9 03:39 halo.txt
-rw-rw-r-- 1 bukan11nya bukan11nya   262 Mar  4 01:39 lat5jb3.bash
-rw-rw-r-- 1 bukan11nya bukan11nya 21370 Mar  2 04:57 list-conf.txt
-rw-rw-r-- 1 bukan11nya bukan11nya 10557 Mar  3 06:19 monitor-system.log
-rw-rw-r-- 2 bukan11nya bukan11nya    17 Mar  9 03:39 z
bukan11nya@happyending:~$ cat z
Hallo apa khabar
bukan11nya@happyending:~$ mkdir mydir
bukan11nya@happyending:~$ ln z mydir/halo.juga
bukan11nya@happyending:~$ cat mydir/halo.juga
Hallo apa khabar
bukan11nya@happyending:~$ ln -s z bye.txt
bukan11nya@happyending:~$ ls -l bye.txt
lrwxrwxrwx 1 bukan11nya bukan11nya 1 Mar  9 03:41 bye.txt -> z
bukan11nya@happyending:~$ cat bye.txt
Hallo apa khabar
```
## Percobaan 4 : Melihat isi File
```
bukan11nya@happyending:~$ ls -l
total 80
drwxrwxr-x 4 bukan11nya bukan11nya  4096 Mar  4 02:31 A
-rw-rw-r-- 1 bukan11nya bukan11nya   588 Mar  4 01:42 backup-error.log
-rw-rw-r-- 1 bukan11nya bukan11nya  1537 Mar  4 01:42 backup-success.log
-rw-rw-r-- 1 bukan11nya bukan11nya    37 Mar  4 01:42 backup-success.logq
-rw-rw-r-- 1 bukan11nya bukan11nya  7799 Mar  4 01:42 backup.tar.gz
lrwxrwxrwx 1 bukan11nya bukan11nya     1 Mar  9 03:41 bye.txt -> z
drwxrwxr-x 2 bukan11nya bukan11nya  4096 Mar  9 03:34 C
-rw-rw-r-- 3 bukan11nya bukan11nya    17 Mar  9 03:39 halo.txt
-rw-rw-r-- 1 bukan11nya bukan11nya   262 Mar  4 01:39 lat5jb3.bash
-rw-rw-r-- 1 bukan11nya bukan11nya 21370 Mar  2 04:57 list-conf.txt
-rw-rw-r-- 1 bukan11nya bukan11nya 10557 Mar  3 06:19 monitor-system.log
drwxrwxr-x 2 bukan11nya bukan11nya  4096 Mar  9 03:40 mydir
-rw-rw-r-- 3 bukan11nya bukan11nya    17 Mar  9 03:39 z
bukan11nya@happyending:~$ file halo.txt
halo.txt: ASCII text
bukan11nya@happyending:~$ file bye.txt
bye.txt: symbolic link to z
```
## Percobaan 5 : Mencari file
1. Perintah find
```
bukan11nya@happyending:~$ find /home -name "*.txt" -print > myerror.txt
bukan11nya@happyending:~$ cat myerror.txt
/home/bukan11nya/halo.txt
/home/bukan11nya/myerror.txt
/home/bukan11nya/list-conf.txt
/home/bukan11nya/bye.txt
bukan11nya@happyending:~$ find . -name "*.txt" -exec wc -l `{}' `;'
```
2. Perintah which
```
bukan11nya@happyending:~$ which ls
/usr/bin/ls
```
3. Perintah locate
bukan11nya@happyending:~$ locate "*.txt"
```
/boot/grub/gfxblacklist.txt
/home/bukan11nya/bye.txt
/home/bukan11nya/halo.txt
/home/bukan11nya/list-conf.txt
/home/bukan11nya/myerror.txt
/snap/core20/2717/usr/lib/python3/dist-packages/Jinja2-2.10.1.egg-info/dependency_links.txt
/snap/core20/2717/usr/lib/python3/dist-packages/Jinja2-2.10.1.egg-info/entry_points.txt
/snap/core20/2717/usr/lib/python3/dist-packages/Jinja2-2.10.1.egg-info/requires.txt
/snap/core20/2717/usr/lib/python3/dist-packages/Jinja2-2.10.1.egg-info/top_level.txt
/snap/core20/2717/usr/lib/python3/dist-packages/MarkupSafe-1.1.0.egg-info/dependency_links.txt
/snap/core20/2717/usr/lib/python3/dist-packages/MarkupSafe-1.1.0.egg-info/top_level.txt
/snap/core20/2717/usr/lib/python3/dist-packages/PyJWT-1.7.1.egg-info/dependency_links.txt
/snap/core20/2717/usr/lib/python3/dist-packages/PyJWT-1.7.1.egg-info/entry_points.txt
/snap/core20/2717/usr/lib/python3/dist-packages/PyJWT-1.7.1.egg-info/requires.txt
/snap/core20/2717/usr/lib/python3/dist-packages/PyJWT-1.7.1.egg-info/top_level.txt
/snap/core20/2717/usr/lib/python3/dist-packages/attrs-19.3.0.egg-info/dependency_links.txt
/snap/core20/2717/usr/lib/python3/dist-packages/attrs-19.3.0.egg-info/requires.txt
/snap/core20/2717/usr/lib/python3/dist-packages/attrs-19.3.0.egg-info/top_level.txt
/snap/core20/2717/usr/lib/python3/dist-packages/certifi-2019.11.28.egg-info/dependency_links.txt
/snap/core20/2717/usr/lib/python3/dist-packages/certifi-2019.11.28.egg-info/top_level.txt
/snap/core20/2717/usr/lib/python3/dist-packages/chardet-3.0.4.egg-info/dependency_links.txt
/snap/core20/2717/usr/lib/python3/dist-packages/chardet-3.0.4.egg-info/entry_points.txt
...dan masih banyak lagi
```
## Percobaan 6 : Mencari text pada file
```
bukan11nya@happyending:~$ grep Hallo *.txt
bye.txt:Hallo apa khabar
halo.txt:Hallo apa khabar
```

## LATIHAN

1.
```
bukan11nya@happyending:~$ cd
bukan11nya@happyending:~$ pwd
/home/bukan11nya
bukan11nya@happyending:~$ ls -al
total 128
drwxr-x--- 9 bukan11nya bukan11nya  4096 Mar  9 03:45 .
drwxr-xr-x 3 root       root        4096 Feb 12 11:28 ..
drwxrwxr-x 4 bukan11nya bukan11nya  4096 Mar  4 02:31 A
-rw-rw-r-- 1 bukan11nya bukan11nya   588 Mar  4 01:42 backup-error.log
-rw-rw-r-- 1 bukan11nya bukan11nya  1537 Mar  4 01:42 backup-success.log
-rw-rw-r-- 1 bukan11nya bukan11nya    37 Mar  4 01:42 backup-success.logq
-rw-rw-r-- 1 bukan11nya bukan11nya  7799 Mar  4 01:42 backup.tar.gz
-rw------- 1 bukan11nya bukan11nya  1364 Mar  3 06:19 .bash_history
-rw-r--r-- 1 bukan11nya bukan11nya   220 Mar 31  2024 .bash_logout
-rw-r--r-- 1 bukan11nya bukan11nya  3771 Mar 31  2024 .bashrc
lrwxrwxrwx 1 bukan11nya bukan11nya     1 Mar  9 03:41 bye.txt -> z
drwxrwxr-x 2 bukan11nya bukan11nya  4096 Mar  9 03:34 C
drwx------ 2 bukan11nya bukan11nya  4096 Feb 12 11:30 .cache
drwx------ 3 bukan11nya bukan11nya  4096 Mar  2 04:50 .config
-rw-rw-r-- 3 bukan11nya bukan11nya    17 Mar  9 03:39 halo.txt
-rw-rw-r-- 1 bukan11nya bukan11nya   262 Mar  4 01:39 lat5jb3.bash
-rw------- 1 bukan11nya bukan11nya    20 Mar  9 03:43 .lesshst
-rw-rw-r-- 1 bukan11nya bukan11nya 21370 Mar  2 04:57 list-conf.txt
drwxrwxr-x 3 bukan11nya bukan11nya  4096 Mar  4 01:38 .local
-rw-rw-r-- 1 bukan11nya bukan11nya 10557 Mar  3 06:19 monitor-system.log
drwxrwxr-x 2 bukan11nya bukan11nya  4096 Mar  9 03:40 mydir
-rw-rw-r-- 1 bukan11nya bukan11nya   111 Mar  9 03:45 myerror.txt
-rw-r--r-- 1 bukan11nya bukan11nya   807 Mar 31  2024 .profile
drwx------ 2 bukan11nya bukan11nya  4096 Feb 12 11:28 .ssh
-rw-r--r-- 1 bukan11nya bukan11nya     0 Mar  2 02:59 .sudo_as_admin_successful
-rw-rw-r-- 3 bukan11nya bukan11nya    17 Mar  9 03:39 z
bukan11nya@happyending:~$ cd .
bukan11nya@happyending:~$ pwd
/home/bukan11nya
bukan11nya@happyending:~$ cd ..
bukan11nya@happyending:/home$ pwd
/home
bukan11nya@happyending:/home$ ls- al
Command 'ls-' not found, did you mean:
  command 'lsd' from snap lsd (0.16.0)
  command 'lsc' from deb livescript (1.6.1+dfsg-3)
  command 'lsm' from deb lsm (1.0.4-2)
  command 'ls' from deb coreutils (9.4-3ubuntu6.1)
  command 'lsd' from deb lsd (0.23.1-8)
  command 'lsh' from deb lsh-client (2.1-14)
  command 'lsw' from deb suckless-tools (47-1)
See 'snap info <snapname>' for additional versions.
bukan11nya@happyending:/home$ cd ..
bukan11nya@happyending:/$ pwd
/
bukan11nya@happyending:/$ ls -al
total 2097244
drwxr-xr-x  23 root root       4096 Feb 12 11:01 .
drwxr-xr-x  23 root root       4096 Feb 12 11:01 ..
lrwxrwxrwx   1 root root          7 Apr 22  2024 bin -> usr/bin
drwxr-xr-x   2 root root       4096 Feb 26  2024 bin.usr-is-merged
drwxr-xr-x   4 root root       4096 Feb 12 11:22 boot
dr-xr-xr-x   2 root root       4096 Aug  5  2025 cdrom
drwxr-xr-x  20 root root       4140 Mar  9 03:04 dev
drwxr-xr-x 108 root root       4096 Mar  9 03:49 etc
drwxr-xr-x   3 root root       4096 Feb 12 11:28 home
lrwxrwxrwx   1 root root          7 Apr 22  2024 lib -> usr/lib
lrwxrwxrwx   1 root root          9 Apr 22  2024 lib64 -> usr/lib64
drwxr-xr-x   2 root root       4096 Feb 26  2024 lib.usr-is-merged
drwx------   2 root root      16384 Feb 12 10:31 lost+found
drwxr-xr-x   2 root root       4096 Aug  5  2025 media
drwxr-xr-x   2 root root       4096 Aug  5  2025 mnt
drwxr-xr-x   2 root root       4096 Aug  5  2025 opt
dr-xr-xr-x 165 root root          0 Mar  9 03:03 proc
drwx------   3 root root       4096 Mar  4 01:18 root
drwxr-xr-x  29 root root        880 Mar  9 03:48 run
lrwxrwxrwx   1 root root          8 Apr 22  2024 sbin -> usr/sbin
drwxr-xr-x   2 root root       4096 Dec 11  2024 sbin.usr-is-merged
drwxr-xr-x   5 root root       4096 Mar  2 03:47 snap
drwxr-xr-x   2 root root       4096 Aug  5  2025 srv
-rw-------   1 root root 2147483648 Feb 12 11:01 swap.img
dr-xr-xr-x  13 root root          0 Mar  9 03:03 sys
drwxrwxrwt  14 root root       4096 Mar  9 03:49 tmp
drwxr-xr-x  12 root root       4096 Aug  5  2025 usr
drwxr-xr-x  13 root root       4096 Feb 12 11:28 var
bukan11nya@happyending:/$ cd /etc
bukan11nya@happyending:/etc$ ls -al | more
total 932
drwxr-xr-x 108 root root       4096 Mar  9 03:49 .
drwxr-xr-x  23 root root       4096 Feb 12 11:01 ..
-rw-r--r--   1 root root       3444 Jul  5  2023 adduser.con
f
drwxr-xr-x   2 root root       4096 Mar  9 03:48 alternative
s
drwxr-xr-x   2 root root       4096 Aug  5  2025 apparmor
drwxr-xr-x   9 root root       4096 Aug  5  2025 apparmor.d
drwxr-xr-x   3 root root       4096 Aug  5  2025 apport
drwxr-xr-x   9 root root       4096 Feb 12 10:30 apt
-rw-r--r--   1 root root       2319 Mar 31  2024 bash.bashrc
-rw-r--r--   1 root root         45 Aug  5  2025 bash_comple
tion
drwxr-xr-x   2 root root       4096 Aug  5  2025 bash_comple
tion.d
-rw-r--r--   1 root root        367 Aug  2  2022 bindresvpor
t.blacklist
drwxr-xr-x   2 root root       4096 Jul  2  2025 binfmt.d
drwxr-xr-x   2 root root       4096 Aug  5  2025 byobu
drwxr-xr-x   3 root root       4096 Aug  5  2025 ca-certific
ates
-rw-r--r--   1 root root       6288 Aug  5  2025 ca-certific
ates.conf
drwxr-xr-x   5 root root       4096 Feb 12 11:28 cloud
drwxr-xr-x   2 root root       4096 Feb 12 10:32 console-set
up
drwx------   2 root root       4096 Jul  2  2025 credstore
drwx------   2 root root       4096 Jul  2  2025 credstore.e
bukan11nya@happyending:/etc$ cat passwd
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
_apt:x:42:65534::/nonexistent:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:998:998:systemd Network Management:/:/usr/sbin/nologin
systemd-timesync:x:997:997:systemd Time Synchronization:/:/usr/sbin/nologin
dhcpcd:x:100:65534:DHCP Client Daemon,,,:/usr/lib/dhcpcd:/bin/false
messagebus:x:101:102::/nonexistent:/usr/sbin/nologin
systemd-resolve:x:992:992:systemd Resolver:/:/usr/sbin/nologin
pollinate:x:102:1::/var/cache/pollinate:/bin/false
polkitd:x:991:991:User for polkitd:/:/usr/sbin/nologin
syslog:x:103:104::/nonexistent:/usr/sbin/nologin
uuidd:x:104:105::/run/uuidd:/usr/sbin/nologin
tcpdump:x:105:107::/nonexistent:/usr/sbin/nologin
tss:x:106:108:TPM software stack,,,:/var/lib/tpm:/bin/false
landscape:x:107:109::/var/lib/landscape:/usr/sbin/nologin
fwupd-refresh:x:989:989:Firmware update daemon:/var/lib/fwupd:/usr/sbin/nologin
usbmux:x:108:46:usbmux daemon,,,:/var/lib/usbmux:/usr/sbin/nologin
sshd:x:109:65534::/run/sshd:/usr/sbin/nologin
bukan11nya:x:1000:1000:Jofan:/home/bukan11nya:/bin/bash
bukan11nya@happyending:/etc$ cd -
/
bukan11nya@happyending:/$ pwd
/
```
2. Lanjutkan penelusuran pohon pada sistem file menggunakan ```cd```, ```ls```, ```pwd``` dan ```cat```. telusuri direktory ```/bin```, ```/usr/bin```,```/sbin```, ```/tmp``` dan ```/boot```.
```
bukan11nya@happyending:~$ cd /bin
bukan11nya@happyending:/bin$ ls
'['                                   jsonschema                         setmetamode
 aa-enabled                           kbdinfo                            setpci
 aa-exec                              kbd_mode                           setpriv
 aa-features-abi                      kbxutil                            setsid
 acpidbg                              keep-one-running                   setterm
 add-apt-repository                   kernel-install                     setupcon
 addpart                              kill                               sftp
 apport-bug                           killall                            sg
 apport-cli                           kmod                               sg_bg_ctl
 apport-collect                       kmodsign                           sg_compare_and_write
 apport-unpack                        landscape-sysinfo                  sg_copy_results
 appstreamcli                         last                               sg_dd
 apropos                              lastb                              sg_decode_sense
 apt                                  lastlog                            sg_emc_trespass
 apt-add-repository                   lcf                                sg_format
 apt-cache                            ldd                                sg_get_config
 apt-cdrom                            ld.so                              sg_get_elem_status
 apt-config                           less                               sg_get_lba_status
 apt-extracttemplates                 lessecho                           sg_ident
 apt-ftparchive                       lessfile                           sginfo
 apt-get                              lesskey                            sg_inq
 apt-key                              lesspipe                           sg_logs
 apt-mark                             lexgrog                            sg_luns
 apt-sortpkgs                         libnetcfg                          sg_map
 arch                                 link                               sg_map26
 automat-visualize3                   linux32                            sgm_dd
 awk                                  linux64                            sg_modes
 b2sum                                linux-boot-prober                  sg_opcodes
 base32                               linux-check-removal                sgp_dd
 base64                               linux-update-symlinks              sg_persist
 ...dan masih banyak lagi
```
```
bukan11nya@happyending:/$ cd /usr/bin
bukan11nya@happyending:/usr/bin$ ls
```
```
'['                                   jsonschema                         setmetamode
 aa-enabled                           kbdinfo                            setpci
 aa-exec                              kbd_mode                           setpriv
 aa-features-abi                      kbxutil                            setsid
 acpidbg                              keep-one-running                   setterm
 add-apt-repository                   kernel-install                     setupcon
 addpart                              kill                               sftp
 apport-bug                           killall                            sg
 apport-cli                           kmod                               sg_bg_ctl
 apport-collect                       kmodsign                           sg_compare_and_write
 apport-unpack                        landscape-sysinfo                  sg_copy_results
 appstreamcli                         last                               sg_dd
 apropos                              lastb                              sg_decode_sense
 apt                                  lastlog                            sg_emc_trespass
 apt-add-repository                   lcf                                sg_format
 apt-cache                            ldd                                sg_get_config
 apt-cdrom                            ld.so                              sg_get_elem_status
 apt-config                           less                               sg_get_lba_status
 apt-extracttemplates                 lessecho                           sg_ident
 apt-ftparchive                       lessfile                           sginfo
 apt-get                              lesskey                            sg_inq
 apt-key                              lesspipe                           sg_logs
 apt-mark                             lexgrog                            sg_luns
 apt-sortpkgs                         libnetcfg                          sg_map
 arch                                 link                               sg_map26
 automat-visualize3                   linux32                            sgm_dd
 awk                                  linux64                            sg_modes
 b2sum                                linux-boot-prober                  sg_opcodes
 base32                               linux-check-removal                sgp_dd
 base64                               linux-update-symlinks              sg_persist
 basename                             linux-version                      sg_prevent
 basenc                               ln                                 sg_raw
 bash                                 lnstat                             sg_rbuf
 bashbug                              loadkeys                           sg_rdac
 bc                                   loadunimap                         sg_read
 boltctl                              locale                             sg_read_attr
 bpftrace                             locale-check                       sg_read_block_limits
 bpftrace-aotrt                       localectl                          sg_read_buffer
 btrfs                                localedef                          sg_readcap
 btrfsck                              locate                             sg_read_long
 btrfs-convert                        logger                             sg_reassign
 btrfs-find-root                      login                              sg_referrals
 btrfs-image                          loginctl                           sg_rep_pip
 btrfs-map-logical                    logname                            sg_rep_zones
 btrfs-select-super                   look                               sg_requests
 btrfstune                            lowntfs-3g                         sg_reset
 busctl                               ls                                 sg_reset_wp
 busybox                              lsattr                             sg_rmsn
 byobu                                lsblk                              sg_rtpg
 byobu-config                         lsb_release                        sg_safte
 byobu-ctrl-a                         lscpu                              sg_sanitize
 byobu-disable                        lshw                               sg_sat_identify
 byobu-disable-prompt                 lsinitramfs                        sg_sat_phy_event
 byobu-enable                         lsipc                              sg_sat_read_gplog
 ... dan masih banyak lagi
```
```
bukan11nya@happyending:/$ cd /sbin
bukan11nya@happyending:/sbin$ ls
```
```
aa-load                ebtables-restore             killsnoop.bt           pidpersec.bt       thin_metadata_size
aa-remove-unknown      ebtables-save                klockstat-bpfcc        pivot_root         thin_repair
aa-status              ebtables-translate           kpartx                 plocate-build      thin_restore
aa-teardown            era_check                    kvmexit-bpfcc          plymouthd          thin_rmap
accessdb               era_dump                     ldattach               poweroff           thin_trim
addgnupghome           era_invalidate               ldconfig               ppchcalls-bpfcc    threadsnoop-bpfcc
addgroup               era_restore                  ldconfig.real          profile-bpfcc      threadsnoop.bt
add-shell              ethtool                      llcstat-bpfcc          pvchange           tipc
adduser                execsnoop-bpfcc              loads.bt               pvck               tplist-bpfcc
agetty                 execsnoop.bt                 locale-gen             pvcreate           trace-bpfcc
apparmor_parser        exitsnoop-bpfcc              logrotate              pvdisplay          ttysnoop-bpfcc
apparmor_status        ext4dist-bpfcc               logsave                pvmove             tune2fs
applygnupgdefaults     ext4slower-bpfcc             losetup                pvremove           ucalls
argdist-bpfcc          faillock                     lsmod                  pvresize           u-d-c-print-pci-ids
arpd                   fatlabel                     luksformat             pvs                uflow
arptables              fdisk                        lvchange               pvscan             ufw
arptables-nft          filefrag                     lvconvert              pwck               ugc
arptables-nft-restore  filegone-bpfcc               lvcreate               pwconv             umount.udisks2
arptables-nft-save     filelife-bpfcc               lvdisplay              pwhistory_helper   undump.bt
arptables-restore      fileslower-bpfcc             lvextend               pwunconv           unix_chkpwd
arptables-save         filetop-bpfcc                lvm                    pythoncalls-bpfcc  unix_update
badblocks              findfs                       lvmconfig              pythonflow-bpfcc   uobjnew
bashreadline-bpfcc     fixparts                     lvmdiskscan            pythongc-bpfcc     update-ca-certificates
bashreadline.bt        fsadm                        lvmdump                pythonstat-bpfcc   update-catalog
bcache-super-show      fsck                         lvmpolld               rdmaucma-bpfcc     updatedb.plocate
bindsnoop-bpfcc        fsck.btrfs                   lvmsadc                readahead-bpfcc    update-grub
biolatency-bpfcc       fsck.cramfs                  lvmsar                 readprofile        update-grub2
biolatency.bt          fsck.ext2                    lvreduce               reboot             update-grub-gfxpayload
biolatency-kp.bt       fsck.ext3                    lvremove               remove-shell       update-ieee-data
```
```
bukan11nya@happyending:/$ cd /tmp
bukan11nya@happyending:/tmp$ ls
snap-private-tmp
systemd-private-ed09b0a8f4be48ef9e65a10f006eb058-ModemManager.service-ELqAyd
systemd-private-ed09b0a8f4be48ef9e65a10f006eb058-polkit.service-wlHgJZ
systemd-private-ed09b0a8f4be48ef9e65a10f006eb058-systemd-logind.service-StJpJI
systemd-private-ed09b0a8f4be48ef9e65a10f006eb058-systemd-resolved.service-NRSZ8b
systemd-private-ed09b0a8f4be48ef9e65a10f006eb058-systemd-timesyncd.service-BU57zO
```
```
bukan11nya@happyending:/$ cd /boot
bukan11nya@happyending:/boot$ ls
config-6.8.0-100-generic  initrd.img-6.8.0-100-generic  System.map-6.8.0-100-generic  vmlinuz.old
grub                      initrd.img.old                vmlinuz
initrd.img                lost+found                    vmlinuz-6.8.0-100-generic
```

3. Telusuri directory /dev. Identifikasi perangkat yang tersedia. Identifikasi tty (terminal)
```
bukan11nya@happyending:/$ cd /dev
bukan11nya@happyending:/dev$ ls
autofs           full       loop-control  sda2      tty13  tty30  tty48  tty8       ttyS23     uinput       vcsa6
block            fuse       mapper        sda3      tty14  tty31  tty49  tty9       ttyS24     urandom      vcsu
bsg              hidraw0    mcelog        sg0       tty15  tty32  tty5   ttyprintk  ttyS25     userfaultfd  vcsu1
btrfs-control    hpet       mem           sg1       tty16  tty33  tty50  ttyS0      ttyS26     userio       vcsu2
bus              hugepages  mqueue        sg2       tty17  tty34  tty51  ttyS1      ttyS27     vboxguest    vcsu3
cdrom            hwrng      net           shm       tty18  tty35  tty52  ttyS10     ttyS28     vboxuser     vcsu4
char             i2c-0      null          snapshot  tty19  tty36  tty53  ttyS11     ttyS29     vcs          vcsu5
console          initctl    nvram         snd       tty2   tty37  tty54  ttyS12     ttyS3      vcs1         vcsu6
core             input      port          sr0       tty20  tty38  tty55  ttyS13     ttyS30     vcs2         vfio
cpu              kmsg       ppp           sr1       tty21  tty39  tty56  ttyS14     ttyS31     vcs3         vga_arbiter
cpu_dma_latency  log        psaux         stderr    tty22  tty4   tty57  ttyS15     ttyS4      vcs4         vhci
cuse             loop0      ptmx          stdin     tty23  tty40  tty58  ttyS16     ttyS5      vcs5         vhost-net
disk             loop1      pts           stdout    tty24  tty41  tty59  ttyS17     ttyS6      vcs6         vhost-vsock
dm-0             loop2      random        tty       tty25  tty42  tty6   ttyS18     ttyS7      vcsa         zero
dma_heap         loop3      rfkill        tty0      tty26  tty43  tty60  ttyS19     ttyS8      vcsa1        zfs
dri              loop4      rtc           tty1      tty27  tty44  tty61  ttyS2      ttyS9      vcsa2
ecryptfs         loop5      rtc0          tty10     tty28  tty45  tty62  ttyS20     ubuntu-vg  vcsa3
fb0              loop6      sda           tty11     tty29  tty46  tty63  ttyS21     udmabuf    vcsa4
fd               loop7      sda1          tty12     tty3   tty47  tty7   ttyS22     uhid       vcsa5
```
```
bukan11nya@happyending:/dev$ ls
autofs           full       loop-control  sda2      tty13  tty30  tty48  tty8       ttyS23     uinput       vcsa6
block            fuse       mapper        sda3      tty14  tty31  tty49  tty9       ttyS24     urandom      vcsu
bsg              hidraw0    mcelog        sg0       tty15  tty32  tty5   ttyprintk  ttyS25     userfaultfd  vcsu1
btrfs-control    hpet       mem           sg1       tty16  tty33  tty50  ttyS0      ttyS26     userio       vcsu2
bus              hugepages  mqueue        sg2       tty17  tty34  tty51  ttyS1      ttyS27     vboxguest    vcsu3
cdrom            hwrng      net           shm       tty18  tty35  tty52  ttyS10     ttyS28     vboxuser     vcsu4
char             i2c-0      null          snapshot  tty19  tty36  tty53  ttyS11     ttyS29     vcs          vcsu5
console          initctl    nvram         snd       tty2   tty37  tty54  ttyS12     ttyS3      vcs1         vcsu6
core             input      port          sr0       tty20  tty38  tty55  ttyS13     ttyS30     vcs2         vfio
cpu              kmsg       ppp           sr1       tty21  tty39  tty56  ttyS14     ttyS31     vcs3         vga_arbiter
cpu_dma_latency  log        psaux         stderr    tty22  tty4   tty57  ttyS15     ttyS4      vcs4         vhci
cuse             loop0      ptmx          stdin     tty23  tty40  tty58  ttyS16     ttyS5      vcs5         vhost-net
disk             loop1      pts           stdout    tty24  tty41  tty59  ttyS17     ttyS6      vcs6         vhost-vsock
dm-0             loop2      random        tty       tty25  tty42  tty6   ttyS18     ttyS7      vcsa         zero
dma_heap         loop3      rfkill        tty0      tty26  tty43  tty60  ttyS19     ttyS8      vcsa1        zfs
dri              loop4      rtc           tty1      tty27  tty44  tty61  ttyS2      ttyS9      vcsa2
ecryptfs         loop5      rtc0          tty10     tty28  tty45  tty62  ttyS20     ubuntu-vg  vcsa3
fb0              loop6      sda           tty11     tty29  tty46  tty63  ttyS21     udmabuf    vcsa4
fd               loop7      sda1          tty12     tty3   tty47  tty7   ttyS22     uhid       vcsa5
```
Mengidentifikasi Perangkat yang Tersedia :
```
bukan11nya@happyending:/dev$ ls -l
total 0
crw-r--r--   1 root       root     10, 235 Mar 10 01:59 autofs
drwxr-xr-x   2 root       root         340 Mar 10 02:00 block
drwxr-xr-x   2 root       root         100 Mar 10 01:59 bsg
crw-rw----   1 root       disk     10, 234 Mar 10 01:59 btrfs-control
drwxr-xr-x   3 root       root          60 Mar 10 01:59 bus
lrwxrwxrwx   1 root       root           3 Mar 10 01:59 cdrom -> sr0
drwxr-xr-x   2 root       root        3740 Mar 10 01:59 char
crw--w----   1 root       tty       5,   1 Mar 10 02:00 console
lrwxrwxrwx   1 root       root          11 Mar 10 01:59 core -> /proc/kcore
drwxr-xr-x   3 root       root          60 Mar 10 01:59 cpu
crw-------   1 root       root     10, 123 Mar 10 01:59 cpu_dma_latency
crw-------   1 root       root     10, 203 Mar 10 01:59 cuse
drwxr-xr-x  11 root       root         220 Mar 10 01:59 disk
brw-rw----   1 root       disk    252,   0 Mar 10 01:59 dm-0
drwxr-xr-x   2 root       root          60 Mar 10 01:59 dma_heap
drwxr-xr-x   3 root       root         100 Mar 10 01:59 dri
crw-------   1 root       root     10, 125 Mar 10 01:59 ecryptfs
crw-rw----   1 root       video    29,   0 Mar 10 01:59 fb0
lrwxrwxrwx   1 root       root          13 Mar 10 01:59 fd -> /proc/self/fd
crw-rw-rw-   1 root       root      1,   7 Mar 10 01:59 full
crw-rw-rw-   1 root       root     10, 229 Mar 10 01:59 fuse
crw-------   1 root       root    241,   0 Mar 10 01:59 hidraw0
crw-------   1 root       root     10, 228 Mar 10 01:59 hpet
drwxr-xr-x   2 root       root           0 Mar 10 01:59 hugepages
crw-------   1 root       root     10, 183 Mar 10 01:59 hwrng
crw-------   1 root       root     89,   0 Mar 10 01:59 i2c-0
lrwxrwxrwx   1 root       root          12 Mar 10 01:59 initctl -> /run/initctl
drwxr-xr-x   4 root       root         340 Mar 10 01:59 input
crw-r--r--   1 root       root      1,  11 Mar 10 01:59 kmsg
lrwxrwxrwx   1 root       root          28 Mar 10 01:59 log -> /run/systemd/journal/dev-log
brw-rw----   1 root       disk      7,   0 Mar 10 01:59 loop0
brw-rw----   1 root       disk      7,   1 Mar 10 01:59 loop1
brw-rw----   1 root       disk      7,   2 Mar 10 02:00 loop2
brw-rw----   1 root       disk      7,   3 Mar 10 01:59 loop3
brw-rw----   1 root       disk      7,   4 Mar 10 01:59 loop4
brw-rw----   1 root       disk      7,   5 Mar 10 01:59 loop5
brw-rw----   1 root       disk      7,   6 Mar 10 01:59 loop6
brw-rw----   1 root       disk      7,   7 Mar 10 01:59 loop7
crw-rw----   1 root       disk     10, 237 Mar 10 01:59 loop-control
drwxr-xr-x   2 root       root          80 Mar 10 01:59 mapper
crw-------   1 root       root     10, 227 Mar 10 01:59 mcelog
crw-r-----   1 root       kmem      1,   1 Mar 10 01:59 mem
drwxrwxrwt   2 root       root          40 Mar 10 01:59 mqueue
drwxr-xr-x   2 root       root          60 Mar 10 01:59 net
crw-rw-rw-   1 root       root      1,   3 Mar 10 01:59 null
crw-------   1 root       root     10, 144 Mar 10 01:59 nvram
crw-r-----   1 root       kmem      1,   4 Mar 10 01:59 port
crw-------   1 root       root    108,   0 Mar 10 01:59 ppp
crw-------   1 root       root     10,   1 Mar 10 01:59 psaux
crw-rw-rw-   1 root       tty       5,   2 Mar 10 02:17 ptmx
drwxr-xr-x   2 root       root           0 Mar 10 01:59 pts
crw-rw-rw-   1 root       root      1,   8 Mar 10 01:59 random
crw-rw-r--+  1 root       root     10, 242 Mar 10 01:59 rfkill
lrwxrwxrwx   1 root       root           4 Mar 10 01:59 rtc -> rtc0
crw-------   1 root       root    248,   0 Mar 10 01:59 rtc0
brw-rw----   1 root       disk      8,   0 Mar 10 01:59 sda
brw-rw----   1 root       disk      8,   1 Mar 10 01:59 sda1
brw-rw----   1 root       disk      8,   2 Mar 10 01:59 sda2
brw-rw----   1 root       disk      8,   3 Mar 10 01:59 sda3
crw-rw----+  1 root       cdrom    21,   0 Mar 10 01:59 sg0
crw-rw----+  1 root       cdrom    21,   1 Mar 10 01:59 sg1
crw-rw----   1 root       disk     21,   2 Mar 10 01:59 sg2
drwxrwxrwt   2 root       root          40 Mar 10 01:59 shm
crw-------   1 root       root     10, 231 Mar 10 01:59 snapshot
drwxr-xr-x   3 root       root         180 Mar 10 01:59 snd
brw-rw----+  1 root       cdrom    11,   0 Mar 10 01:59 sr0
brw-rw----+  1 root       cdrom    11,   1 Mar 10 01:59 sr1
lrwxrwxrwx   1 root       root          15 Mar 10 01:59 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root       root          15 Mar 10 01:59 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root       root          15 Mar 10 01:59 stdout -> /proc/self/fd/1
crw-rw-rw-   1 root       tty       5,   0 Mar 10 01:59 tty
crw--w----   1 root       tty       4,   0 Mar 10 01:59 tty0
crw-------   1 bukan11nya tty       4,   1 Mar 10 02:00 tty1
crw--w----   1 root       tty       4,  10 Mar 10 01:59 tty10
crw--w----   1 root       tty       4,  11 Mar 10 01:59 tty11
crw--w----   1 root       tty       4,  12 Mar 10 01:59 tty12
crw--w----   1 root       tty       4,  13 Mar 10 01:59 tty13
crw--w----   1 root       tty       4,  14 Mar 10 01:59 tty14
crw--w----   1 root       tty       4,  15 Mar 10 01:59 tty15
crw--w----   1 root       tty       4,  16 Mar 10 01:59 tty16
crw--w----   1 root       tty       4,  17 Mar 10 01:59 tty17
crw--w----   1 root       tty       4,  18 Mar 10 01:59 tty18
crw--w----   1 root       tty       4,  19 Mar 10 01:59 tty19
crw--w----   1 root       tty       4,   2 Mar 10 01:59 tty2
crw--w----   1 root       tty       4,  20 Mar 10 01:59 tty20
crw--w----   1 root       tty       4,  21 Mar 10 01:59 tty21
crw--w----   1 root       tty       4,  22 Mar 10 01:59 tty22
crw--w----   1 root       tty       4,  23 Mar 10 01:59 tty23
crw--w----   1 root       tty       4,  24 Mar 10 01:59 tty24
crw--w----   1 root       tty       4,  25 Mar 10 01:59 tty25
crw--w----   1 root       tty       4,  26 Mar 10 01:59 tty26
crw--w----   1 root       tty       4,  27 Mar 10 01:59 tty27
crw--w----   1 root       tty       4,  28 Mar 10 01:59 tty28
crw--w----   1 root       tty       4,  29 Mar 10 01:59 tty29
crw--w----   1 root       tty       4,   3 Mar 10 01:59 tty3
crw--w----   1 root       tty       4,  30 Mar 10 01:59 tty30
crw--w----   1 root       tty       4,  31 Mar 10 01:59 tty31
crw--w----   1 root       tty       4,  32 Mar 10 01:59 tty32
crw--w----   1 root       tty       4,  33 Mar 10 01:59 tty33
crw--w----   1 root       tty       4,  34 Mar 10 01:59 tty34
crw--w----   1 root       tty       4,  35 Mar 10 01:59 tty35
crw--w----   1 root       tty       4,  36 Mar 10 01:59 tty36
crw--w----   1 root       tty       4,  37 Mar 10 01:59 tty37
crw--w----   1 root       tty       4,  38 Mar 10 01:59 tty38
crw--w----   1 root       tty       4,  39 Mar 10 01:59 tty39
crw--w----   1 root       tty       4,   4 Mar 10 01:59 tty4
crw--w----   1 root       tty       4,  40 Mar 10 01:59 tty40
crw--w----   1 root       tty       4,  41 Mar 10 01:59 tty41
crw--w----   1 root       tty       4,  42 Mar 10 01:59 tty42
crw--w----   1 root       tty       4,  43 Mar 10 01:59 tty43
crw--w----   1 root       tty       4,  44 Mar 10 01:59 tty44
crw--w----   1 root       tty       4,  45 Mar 10 01:59 tty45
crw--w----   1 root       tty       4,  46 Mar 10 01:59 tty46
crw--w----   1 root       tty       4,  47 Mar 10 01:59 tty47
crw--w----   1 root       tty       4,  48 Mar 10 01:59 tty48
crw--w----   1 root       tty       4,  49 Mar 10 01:59 tty49
crw--w----   1 root       tty       4,   5 Mar 10 01:59 tty5
crw--w----   1 root       tty       4,  50 Mar 10 01:59 tty50
crw--w----   1 root       tty       4,  51 Mar 10 01:59 tty51
crw--w----   1 root       tty       4,  52 Mar 10 01:59 tty52
crw--w----   1 root       tty       4,  53 Mar 10 01:59 tty53
crw--w----   1 root       tty       4,  54 Mar 10 01:59 tty54
crw--w----   1 root       tty       4,  55 Mar 10 01:59 tty55
crw--w----   1 root       tty       4,  56 Mar 10 01:59 tty56
crw--w----   1 root       tty       4,  57 Mar 10 01:59 tty57
crw--w----   1 root       tty       4,  58 Mar 10 01:59 tty58
crw--w----   1 root       tty       4,  59 Mar 10 01:59 tty59
crw--w----   1 root       tty       4,   6 Mar 10 01:59 tty6
crw--w----   1 root       tty       4,  60 Mar 10 01:59 tty60
crw--w----   1 root       tty       4,  61 Mar 10 01:59 tty61
crw--w----   1 root       tty       4,  62 Mar 10 01:59 tty62
crw--w----   1 root       tty       4,  63 Mar 10 01:59 tty63
crw--w----   1 root       tty       4,   7 Mar 10 01:59 tty7
crw--w----   1 root       tty       4,   8 Mar 10 01:59 tty8
crw--w----   1 root       tty       4,   9 Mar 10 01:59 tty9
crw-------   1 root       root      5,   3 Mar 10 01:59 ttyprintk
crw-rw----   1 root       dialout   4,  64 Mar 10 01:59 ttyS0
crw-rw----   1 root       dialout   4,  65 Mar 10 01:59 ttyS1
crw-rw----   1 root       dialout   4,  74 Mar 10 01:59 ttyS10
crw-rw----   1 root       dialout   4,  75 Mar 10 01:59 ttyS11
crw-rw----   1 root       dialout   4,  76 Mar 10 01:59 ttyS12
crw-rw----   1 root       dialout   4,  77 Mar 10 01:59 ttyS13
crw-rw----   1 root       dialout   4,  78 Mar 10 01:59 ttyS14
crw-rw----   1 root       dialout   4,  79 Mar 10 01:59 ttyS15
crw-rw----   1 root       dialout   4,  80 Mar 10 01:59 ttyS16
crw-rw----   1 root       dialout   4,  81 Mar 10 01:59 ttyS17
crw-rw----   1 root       dialout   4,  82 Mar 10 01:59 ttyS18
crw-rw----   1 root       dialout   4,  83 Mar 10 01:59 ttyS19
crw-rw----   1 root       dialout   4,  66 Mar 10 01:59 ttyS2
crw-rw----   1 root       dialout   4,  84 Mar 10 01:59 ttyS20
crw-rw----   1 root       dialout   4,  85 Mar 10 01:59 ttyS21
crw-rw----   1 root       dialout   4,  86 Mar 10 01:59 ttyS22
crw-rw----   1 root       dialout   4,  87 Mar 10 01:59 ttyS23
crw-rw----   1 root       dialout   4,  88 Mar 10 01:59 ttyS24
crw-rw----   1 root       dialout   4,  89 Mar 10 01:59 ttyS25
crw-rw----   1 root       dialout   4,  90 Mar 10 01:59 ttyS26
crw-rw----   1 root       dialout   4,  91 Mar 10 01:59 ttyS27
crw-rw----   1 root       dialout   4,  92 Mar 10 01:59 ttyS28
crw-rw----   1 root       dialout   4,  93 Mar 10 01:59 ttyS29
crw-rw----   1 root       dialout   4,  67 Mar 10 01:59 ttyS3
crw-rw----   1 root       dialout   4,  94 Mar 10 01:59 ttyS30
crw-rw----   1 root       dialout   4,  95 Mar 10 01:59 ttyS31
crw-rw----   1 root       dialout   4,  68 Mar 10 01:59 ttyS4
crw-rw----   1 root       dialout   4,  69 Mar 10 01:59 ttyS5
crw-rw----   1 root       dialout   4,  70 Mar 10 01:59 ttyS6
crw-rw----   1 root       dialout   4,  71 Mar 10 01:59 ttyS7
crw-rw----   1 root       dialout   4,  72 Mar 10 01:59 ttyS8
crw-rw----   1 root       dialout   4,  73 Mar 10 01:59 ttyS9
drwxr-xr-x   2 root       root          60 Mar 10 01:59 ubuntu-vg
crw-rw----   1 root       kvm      10, 124 Mar 10 01:59 udmabuf
crw-------   1 root       root     10, 239 Mar 10 01:59 uhid
crw-------   1 root       root     10, 223 Mar 10 01:59 uinput
crw-rw-rw-   1 root       root      1,   9 Mar 10 01:59 urandom
crw-------   1 root       root     10, 126 Mar 10 01:59 userfaultfd
crw-------   1 root       root     10, 240 Mar 10 01:59 userio
crw-------   1 root       root     10, 122 Mar 10 01:59 vboxguest
crw-------   1 root       root     10, 121 Mar 10 01:59 vboxuser
crw-rw----   1 root       tty       7,   0 Mar 10 01:59 vcs
crw-rw----   1 root       tty       7,   1 Mar 10 01:59 vcs1
crw-rw----   1 root       tty       7,   2 Mar 10 01:59 vcs2
crw-rw----   1 root       tty       7,   3 Mar 10 01:59 vcs3
crw-rw----   1 root       tty       7,   4 Mar 10 01:59 vcs4
crw-rw----   1 root       tty       7,   5 Mar 10 01:59 vcs5
crw-rw----   1 root       tty       7,   6 Mar 10 01:59 vcs6
crw-rw----   1 root       tty       7, 128 Mar 10 01:59 vcsa
crw-rw----   1 root       tty       7, 129 Mar 10 01:59 vcsa1
crw-rw----   1 root       tty       7, 130 Mar 10 01:59 vcsa2
crw-rw----   1 root       tty       7, 131 Mar 10 01:59 vcsa3
crw-rw----   1 root       tty       7, 132 Mar 10 01:59 vcsa4
crw-rw----   1 root       tty       7, 133 Mar 10 01:59 vcsa5
crw-rw----   1 root       tty       7, 134 Mar 10 01:59 vcsa6
crw-rw----   1 root       tty       7,  64 Mar 10 01:59 vcsu
crw-rw----   1 root       tty       7,  65 Mar 10 01:59 vcsu1
crw-rw----   1 root       tty       7,  66 Mar 10 01:59 vcsu2
crw-rw----   1 root       tty       7,  67 Mar 10 01:59 vcsu3
crw-rw----   1 root       tty       7,  68 Mar 10 01:59 vcsu4
crw-rw----   1 root       tty       7,  69 Mar 10 01:59 vcsu5
crw-rw----   1 root       tty       7,  70 Mar 10 01:59 vcsu6
drwxr-xr-x   2 root       root          60 Mar 10 01:59 vfio
crw-------   1 root       root     10, 127 Mar 10 01:59 vga_arbiter
crw-------   1 root       root     10, 137 Mar 10 01:59 vhci
crw-rw----   1 root       kvm      10, 238 Mar 10 01:59 vhost-net
crw-rw----   1 root       kvm      10, 241 Mar 10 01:59 vhost-vsock
crw-rw-rw-   1 root       root      1,   5 Mar 10 01:59 zero
crw-------   1 root       root     10, 249 Mar 10 01:59 zfs
```
Mengetahui terminal yang digunakan
```
bukan11nya@happyending:/dev$ who am i
bukan11nya pts/0        2026-03-10 02:01 (192.168.75.55)
```

Mengetahui pemilik tty:
```
bukan11nya@happyending:/$ ls -l /dev/pts/0
crw--w---- 1 bukan11nya tty 136, 0 Mar 10 02:20 /dev/pts/0
```

4. Telusuri derectory /proc. Tampilkan isi file interrupts, devices, cpuinfo, meminfo dan uptime menggunakan perintah cat. Dapatkah Anda melihat mengapa directory /proc disebut pseudo-filesystem yang memungkinkan akses ke struktur data kernel ?
```
bukan11nya@happyending:/$ cd /proc
bukan11nya@happyending:/proc$ cat interrupts
           CPU0
  0:        148   IO-APIC   2-edge      timer
  1:         63   IO-APIC   1-edge      i8042
  8:          0   IO-APIC   8-edge      rtc0
  9:          0   IO-APIC   9-fasteoi   acpi
 12:        158   IO-APIC  12-edge      i8042
 14:       3046   IO-APIC  14-edge      ata_piix
 15:          0   IO-APIC  15-edge      ata_piix
 18:          0   IO-APIC  18-fasteoi   vmwgfx
 19:      17305   IO-APIC  19-fasteoi   ehci_hcd:usb1, enp0s3
 20:          0   IO-APIC  20-fasteoi   vboxguest
 21:       6855   IO-APIC  21-fasteoi   ahci[0000:00:0d.0], snd_intel8x0
 22:         25   IO-APIC  22-fasteoi   ohci_hcd:usb2
NMI:          0   Non-maskable interrupts
LOC:    1393442   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
IWI:          0   IRQ work interrupts
RTR:          0   APIC ICR read retries
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
DFR:          0   Deferred Error APIC interrupts
MCE:          0   Machine check exceptions
MCP:          5   Machine check polls
ERR:          0
MIS:          0
PIN:          0   Posted-interrupt notification event
NPI:          0   Nested posted-interrupt event
PIW:          0   Posted-interrupt wakeup event
```
bukan11nya@happyending:/proc$ cat devices
Character devices:
  1 mem
  4 /dev/vc/0
  4 tty
  4 ttyS
  5 /dev/tty
  5 /dev/console
  5 /dev/ptmx
  5 ttyprintk
  7 vcs
 10 misc
 13 input
 21 sg
 29 fb
 89 i2c
108 ppp
116 alsa
128 ptm
136 pts
180 usb
189 usb_device
202 cpu/msr
204 ttyMAX
226 drm
241 hidraw
242 ttyDBC
243 bsg
244 watchdog
245 remoteproc
246 ptp
247 pps
248 rtc
249 dma_heap
250 dax
251 dimmctl
252 ndctl
253 tpm
254 gpiochip
261 accel

Block devices:
  7 loop
  8 sd
  9 md
 11 sr
 65 sd
 66 sd
 67 sd
 68 sd
 69 sd
 70 sd
 71 sd
128 sd
129 sd
130 sd
131 sd
132 sd
133 sd
134 sd
135 sd
252 device-mapper
253 virtblk
254 mdp
259 blkext
```
bukan11nya@happyending:/proc$ cat cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 154
model name      : 12th Gen Intel(R) Core(TM) i5-12450H
stepping        : 3
microcode       : 0xffffffff
cpu MHz         : 1113.604
cache size      : 12288 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 22
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm constant_tsc rep_good nopl xtopology nonstop_tsc cpuid tsc_known_freq pni pclmulqdq ssse3 fma cx16 pcid sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand hypervisor lahf_lm abm 3dnowprefetch ibrs_enhanced fsgsbase bmi1 avx2 bmi2 invpcid rdseed adx clflushopt sha_ni arat md_clear flush_l1d arch_capabilities
bugs            : spectre_v1 spectre_v2 spec_store_bypass swapgs retbleed eibrs_pbrsb rfds bhi its
bogomips        : 2227.20
clflush size    : 64
cache_alignment : 64
address sizes   : 39 bits physical, 48 bits virtual
power management:
```
```
bukan11nya@happyending:/proc$ cat meminfo
MemTotal:        2015316 kB
MemFree:         1516168 kB
MemAvailable:    1662760 kB
Buffers:           19624 kB
Cached:           258768 kB
SwapCached:            0 kB
Active:           256352 kB
Inactive:          68908 kB
Active(anon):      56700 kB
Inactive(anon):        0 kB
Active(file):     199652 kB
Inactive(file):    68908 kB
Unevictable:       27448 kB
Mlocked:           27448 kB
SwapTotal:       2097148 kB
SwapFree:        2097148 kB
Zswap:                 0 kB
Zswapped:              0 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:         74316 kB
Mapped:            82444 kB
Shmem:              1080 kB
KReclaimable:      19088 kB
Slab:              61080 kB
SReclaimable:      19088 kB
SUnreclaim:        41992 kB
KernelStack:        1996 kB
PageTables:         2492 kB
SecPageTables:         0 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3104804 kB
Committed_AS:     366640 kB
VmallocTotal:   34359738367 kB
VmallocUsed:       22452 kB
VmallocChunk:          0 kB
Percpu:              500 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
FileHugePages:         0 kB
FilePmdMapped:         0 kB
Unaccepted:            0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
Hugetlb:               0 kB
DirectMap4k:       98240 kB
DirectMap2M:     1998848 kB
bukan11nya@happyending:/proc$ cat uptime
1468.17 1080.75
```

5. Ubahlah direktory home ke user lain secara langsung menggunakan cd ~username.
```
bukan11nya@happyending:/proc$ cd ~bukan11nya
bukan11nya@happyending:~$
```
6. Ubah kembali ke direktory home Anda.
```
bukan11nya@happyending:~$ cd ~
bukan11nya@happyending:~$
```

7. Buat subdirektory work dan play.
```
bukan11nya@happyending:~$ mkdir work play
```

8. Hapus subdirektory work.
```
bukan11nya@happyending:~$ rmdir work
```
9. Copy file /etc/passwd ke direktory home Anda.
```
bukan11nya@happyending:~$ cp /etc/passwd ~
bukan11nya@happyending:~$
```
10. Pindahkan ke subirectory play.
```
bukan11nya@happyending:~$ mv passwd play
bukan11nya@happyending:~$
```
11. Ubahlah ke subdirektory play dan buat symbolic link dengan nama terminal yang menunjuk ke perangkat tty. Apa yang terjadi jika melakukan hard link ke perangkat tty ?
```
bukan11nya@happyending:~$ cd play
bukan11nya@happyending:~/play$ ln -s /dev/tty terminal
bukan11nya@happyending:~/play$
```

12. Buatlah file bernama hello.txt yang berisi kata "hello word". Dapatkah Anda gunakan "cp" menggunakan "terminal" sebagai file asal untuk menghasilkan efek yang sama ?
```
bukan11nya@happyending:~$ echo "hello world" > hello.txt
bukan11nya@happyending:~$ cp
cp: missing file operand
Try 'cp --help' for more information.
```
tidak bisa mengggunakan cp karena terminal adalah device, bukan file eks biasa

13.Copy hello.txt ke terminal. Apa yang terjadi ?
```
bukan11nya@happyending:~$ cp hello.txt terminal
bukan11nya@happyending:~$
```
hasilnya : Isi file akan langsung tampil di layar terminal karena terminal adalah device output.

14. Masih direktory home, copy keseluruhan direktory play ke direktory bernama work menggunakan symbolic link.
```
bukan11nya@happyending:~$ ln -s play work
bukan11nya@happyending:~
```
ini membuat work sebagai symbolic link ke direktori play.

15. Hapus direktory work dan isinya dengan satu perintah.
```
bukan11nya@happyending:~$ rm -rf work
bukan11nya@happyending:~$
```