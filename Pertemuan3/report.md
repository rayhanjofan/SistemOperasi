# LAPORAN PERTEMUAN 3

<h4> Nama : Rayhan Jofan Halim<h4>
<h4>NIM : 254107020230<h4>
<h4>Kelas : TI-1H<h4>

## 1.11 Latihan
### Latihan 3.1
Buatlah script yang:
1. Menampilkan daftar 10 file terbesar di direktori ``` /var/log/ ```
2. Menyimpan hasilnya ke file ``` large-logs.txt ```
3. Menampilkan output juga di terminal menggunakan tee
4. Menangani error dengan redirect ke ```error.log ```


```
sudo find /var/log -type f -exec du -h {} + 2>error.log | \
```
```
> sort -rh | \
```
```
> head -n 10 | \
```
```
> tee large-logs.txt
```
```
8.0M    /var/log/journal/def514f7f4ef42a4b86cf293326f24cb/user-1000.journal
```
```
8.0M    /var/log/journal/def514f7f4ef42a4b86cf293326f24cb/system.journal
```
```
4.1M    /var/log/journal/def514f7f4ef42a4b86cf293326f24cb/system@b1ddf1d8ec3444c4b60a1c530290ee96-0000000000000237-00064a9ec994d73a.journal
```
```
680K    /var/log/dpkg.log
```
```
584K    /var/log/installer/installer-journal.txt
```
```
152K    /var/log/installer/subiquity-server-debug.log.1464
```
```
136K    /var/log/syslog
```
```
128K    /var/log/installer/curtin-install.log
```
```
72K     /var/log/cloud-init.log
```
```
72K     /var/log/apt/history.logswap 
```

## Latihan 3.2
Buat pipeline yang:
1. Membaca /etc/passwd
2. Mengekstrak username (kolom pertama)
3. Mengurutkan alfabetis
4. Menyimpan ke file sorted-users.txt
Hint: Gunakan cut, sort, dan operator redirect.
Latihan 3.2
Buat pipeline yang:
1. Membaca /etc/passwd
2. Mengekstrak username (kolom pertama)
3. Mengurutkan alfabetis
4. Menyimpan ke file sorted-users.txt
Hint: Gunakan cut, sort, dan operator redirect.
```
bukan11nya@happyending:~$ cut -d: -f1 /etc/passwd | sort > sorted-users.txt
```

## Latihan 3.3
Tulis script monitoring yang:
1. Mencatat penggunaan CPU dan memory setiap 5 detik
2. Menyimpan log dengan timestamp
3. Berjalan selama 1 menit (12 iterasi)
4. Output ditampilkan di terminal DAN disimpan ke file
```
#!/bin/bash
for i in {1..12}
do
   {
     echo "=== Timestamp: $(date) ==="
     echo "CPU Usage:"
     top -bn1 | grep "Cpu(s)"
     echo "Memory Usage:"
     free -h
     echo "--------------------------"
   } | tee -a monitor-system.log
   sleep 5
done
```
Hasilnya :
```
=== Timestamp: Mon Mar  2 04:50:49 AM UTC 2026 ===
CPU Usage:
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni, 88.9 id,  0.0 wa,  0.0 hi, 11.1 si,  0.0 st
Memory Usage:
               total        used        free      shared  buff/cache   available
Mem:           1.9Gi       320Mi       1.4Gi       1.1Mi       369Mi       1.6Gi
Swap:          2.0Gi          0B       2.0Gi
--------------------------
```

## Latihan 3.4
Buat perintah yang:
1. Mencari semua file .conf di sistem
2. Membuang pesan "Permission denied"
3. Menghitung jumlah file yang ditemukan
4. Menyimpan daftar path lengkap ke 

### Jawaban :
```
bukan11nya@happyending:~$ find / -name "*.conf" 2> /dev/null | tee list-conf.txt | wc -l
```
```
481
```

## Latihan 3.5
Implementasikan script backup yang:
1. Menggunakan tar untuk backup direktori
2. Menampilkan progress dengan tee
3. Mencatat stdout ke backup-success.log
4. Mencatat stderr ke backup-error.log
5. Menambahkan timestamp di setiap log entry
```
bukan11nya@happyending:~$ #!/bin/bash
```
```
bukan11nya@happyending:~$ LOG_SUCCESS="backup-success.log"
```
```
bukan11nya@happyending:~$ LOG_ERROR="backup-error.log"
```
```
bukan11nya@happyending:~$ TIMESTAMP=$(date "+%Y-%m-%d %H:%M:%S")
```
```
bukan11nya@happyending:~$ echo "[$TIMESTAMP] Memulai backup..." | tee -a "$LOG_SUCCESS"
```
```
[2026-03-02 05:02:20] Memulai backup...
```
```
bukan11nya@happyending:~$ tar -cvzf backup.tar.gz /path/ke/direktori 2> >(while read line; do echo "[$TIMESTAMP] $line"; done >> "$LOG_ERROR") | tee >(while read line; do echo "[$TIMESTAMP] $line"; done >> "$LOG_SUCCESS")
```
