# **Laporan OS Pertemuan 7**

**Nama** : Rayhan Jofan Halim  
**NIM** : 254107020230
**Kelas** : TI-1H  

---

## **Tugas Praktikum 1 — Toolkit Bash Administrator Pribadi**
**Instruksi tugas:**  
1.Menambahkan Konfigurasi ke .bashrc
```
bukan11nya@happyending:~$ cat << 'EOF' >> ~/.bashrc
> export PATH="$HOME/praktikum-os/week07-bash/bin:$PATH"
> alias update-sys='sudo apt update && sudo apt upgrade -y'
> alias cek-port='netstat -tulpn'
> info_jaringan() {
> echo "=== Info Jaringan Server ==="
> ip -brief address show
> echo "Gateway Default:"
> ip route | grep default
> }
> EOF
bukan11nya@happyending:~$ source ~/.bashrc
```
2.Menerapkan Konfigurasi dan Membuat Script
```
bukan11nya@happyending:~$ source ~/.bashrc
bukan11nya@happyending:~$ mkdir -p ~/praktikum-os/week07-bash/bin
bukan11nya@happyending:~$ cat << 'EOF' > ~/praktikum-os/week07-bash/bin/sys-summary
> echo "=== Ringkasan Sistem Cepat ==="
> echo "Waktu   : $(date)"
> echo "User    : $(pakinghensop)"
> echo "Uptime  : $(uptime -p)"
> EOF
bukan11nya@happyending:~$ chmod +x ~/praktikum-os/week07-bash/bin/sys-summary
```
3.Membuat Laporan Pembuktian 
```
bukan11nya@happyending:"$ chmod +x "/praktikum-os/week07-bash/bin/sys-summary bukan11nya@happyending:"s export PATH="$HOME/praktikum-os/week07-bash/bin:$PATH" bukan11nya@happyending: "s source "/.bashrc 
bukan11nya@happyending:"${ 
> echo "=== 1. BLOK KONFIGURASI ===" 
> tail -n 13 "/.bashrc 
> echo -e "\n=== 2. OUTPUT PATH ===" 
> echo $PATH 
> echo -e "\n=== 3. OUTPUT TYPE ===" 
> type update-sys 
> type cek-port 
> type info-Jaringan 
> type sys-summary 
> } > "/praktikum-os/week07-bash/toolkit-bash-report.txt
-bash: type: sys-summary: not found 
bukan11nya@happyending :"s cat "/praktikum-os/week07-bash/toolkit-bash-report.txt
=== 1. BLOK KONFIGURASI ===
 elif [ -f /etc/bash_completion ]; then
   . /etc/bash_completion 
   fi
fi
export PATH="SHOME/praktikum-os/week07-bash/bin:$PATH"
alias update-sys='sudo apt update && sudo apt upgrade -y' 
allas cek-port='netstat -tulpn' 
Info-Jaringan() { 
    echo " Info Jaringan Server ===="
    ip -brief address show 
    echo "Gateway Default:" 
    ip route | grep default 
}

=== 2. OUTPUT PATH ===
/home /akbarr/praktikum-os/week07-bash/bin:/home/akbarr/praktikum-os/week07-bash/bin:/home/akbarr/praktikum-os/week07-bash/bin:/home/akbarr/praktikum-os/week07-b ash/bin:/home/akbarr/praktikum-os/week07-bash/bin:/home/akbarr/praktikum-os/week07-bash/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/ga mes:/usr/local/games:/snap/bin

=== 3. OUTPUT TYPE ====
update-sys is allased to 'sudo apt update && sudo apt upgrade -y
cek-port is aliased to netstat -tulpn info-jaringan is a function
info-jaringan ()
{
    echo " Info Jaringan Server ====";
    ip-brief address show 
    echo "Gateway Default::
    ip route | grep --color-auto default
}
bukan11nya@happyending:~$
```
### **Tugas Praktikum 2 — Audit File Konfigurasi dan Logging Aman**  
**Instruksi tugas:**  
1.Menjalankan Pencarian dan Memisahkan Error
```
bukan11nya@happyending:cd ~/praktikum-os/week07-bash
bukan11nya@happyending:find /etc -type f -name "*.conf" > audit-konfigurasi-$(date +%F).txt 2> audit-error.log
bukan11nya@happyending:TOTAL_CONF=$(wc -l < audit-konfigurasi-$(date +%F).txt)
bukan11nya@happyending:echo "" >> audit-konfigurasi-$(date +%F).txt
bukan11nya@happyending:echo "TOTAL FILE KONFIGURASI: $TOTAL_CONF" >> audit-konfigurasi-$(date +%F).txt
```
2.Membuat Ringkasan dan Menampilkan Laporan (Tee)
```
bukan11nya@happyending:"s cd ~/praktikum-os/week07-bash
bukan11nya@happyending:~/praktikum-os/week07-bashs find /etc -type f -name "*.conf"> audit-konfigurasi-$(date +%F).txt 2>
audit-error.log
-bash: syntax error near unexpected token 'newline'
bukan11nya@happyending:"/praktikum-os/week07-bashs find /etc -type f -name "*.conf"> audit-konfigurasi-$(date +%F).txt 2>
bukan11nya@happyending:"/praktikum-os/week07-bashs TOTAL CONF=$(wc-1 < audit-konfigurasi-$(date +%F).txt)
---" >> audit-konfigurasi-$(date +%F).txt bukan11nya@happyending:~/praktikum-os/week07-bash$ echo "TOTAL FILE KONFIGURASI: $TOTAL CONF" >> audit-konfigurasi-s(date +%F).txt
bukan11nya@happyending:"/praktikum-os/week07-bash$ echo
bukan11nya@happyending:~/praktikum-os/week07-bash$ {
> echo "=== LAPORAN AUDIT KONFIGURASI ===
tail -n 5 audit-konfigurasi-s(date +%F).txt > echo -e "in=== ANALISIS PENTINGNYA REDIRECTION ==="
> echo "Pemisahan stdout dan stderr (menggunakan 2>) sangat penting dalam operasional."
echo "Hal ini menjaga agar file log/laporan utama tetap bersih dari pesan peringatan" > echo "atau 'permission denied". Administrator dapat menganalisis data valid di satu file,"
> echo "Sementara isu akses/error dapat ditelusuri secara terpisah melalui log error.
>| tee hasil-audit-final.txt
LAPORAN AUDIT KONFIGURASI ===
/etc/iscsi/iscsid.conf
/etc/e2scrub.conf
/etc/ucf.conf
TOTAL FILE KONFIGURASI: 128
ANALISIS PENTINGNYA REDIRECTION ===
Pemisahan stdout dan stderr (menggunakan 2>) sangat penting dalam operasional. Hal ini menjaga agar
file log/laporan utama tetap bersih dari pesan peringatan atau 'permission denied". Administrator dapat menganalisis data valid di satu file,
Sementara isu akses/error dapat ditelusuri secara terpisah melalui log error.   
```
## **Tugas Praktikum 3 — Mini Health Check Harian Server**  
**Instuksi tugas:**  
1.Membuat Script Health Check
```
bukan11nya@happyending:/$ cat << 'EOF' > ~/praktikum-os/week07-bash/bin/daily-healthcheck
> echo "        DAILY HEALTH CHECK SERVER        "
> echo "=================================================="
> echo "Tanggal & Waktu   : $(date)"
> echo "Hostname          : $(hostname)"
> echo "User Aktif        : $(whoami)"
> echo "Shell Aktif       : $SHELL"
> echo "Uptime            : $(uptime -p)"
> echo ""
> echo "--- Pengguna Memori ---"
> echo ""
> echo "--- Pengguna Filesystem Root (/) ---"
> df -h /
> echo ""
> cho "--- 10 Command History Terakhir ---"
> tail -n 10 ~/.bash_history
> echo "=================================================="
> EOF

chmod +x ~/praktikum-os/week07-bash/bin/daily-healthcheck
``` 
2.Menjalankan Script dan Menyimpan Log 
```
bukan11nya@happyending:~$ daily-healthcheck | tee ~/praktikum-os/week07-bash/healthcheck-$(date +%F).log
==================================================
        DAILY HEALTH CHECK SERVER        
==================================================
Tanggal & Waktu   : Tue Apr 14 06:22:37 AM UTC 2026
Hostname          : ubuntu-server-lab
User Aktif        : akbarr
Shell Aktif       : /bin/bash
Uptime            : up 1 hour, 28 minutes

--- Pengguna Memori ---
               total        used        free      shared  buff/cache   available
Mem:           1.9Gi       386Mi       349Mi       1.0Mi       1.4Gi       1.5Gi
Swap:          2.0Gi       268Ki       2.0Gi

--- Pengguna Filesystem Root (/) ---
Filesystem                         Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-ubuntu--lv   12G  5.3G  5.4G  50% /

--- 10 Command History Terakhir ---
clear
cat > contoh Membuat sebuah file
clear
ls -l
clear
cat > contoh Membuat sebuah file
clear
cat > contoh
clear
cat > contoh
==================================================
bukan11nya@happyending:~$
```
### **Tugas Praktikum 4 — Penanganan File dengan Nama Kompleks dan Arsip Aman**  
**Instruksi tugas:**  
1.Menyiapkan File dan Menguji Akses (Quoting)  
```
bukan11nya@happyending:~$ mkdir -p ~/praktikum-os/week07-bash/tugas4-files
bukan11nya@happyending:~$ ~/praktikum-os/week07-bash/tugas4-files
bukan11nya@happyending:~$ ~/praktikum-os/week07-bash/tugas4-filestouch "laporan server april.txt"
bukan11nya@happyending:~$ ~/praktikum-os/week07-bash/tugas4-filestouch "config[utama]_server.conf"
bukan11nya@happyending:~$ ~/praktikum-os/week07-bash/tugas4-filestouch system-log-01.txt system-log-02.txt
bukan11nya@happyending:~$ ~/praktikum-os/week07-bash/tugas4-filesecho system-log-*.txt
system-log-01.txt system-log-02.txt
```  
2.Menyalin File Secara Aman dan Membuat Arsip Tar    
```
bukan11nya@happyending:~$ mkdir -p ../backup-aman
mkdir: cannot create directory '../backup-aman': Permission denied
bukan11nya@happyending:~$ cd ~/praktikum-os/week07-bash/tugas4-files
bukan11nya@happyending:~/praktikum-os/week07-bash/tugas4-files mkdir -p ../backup-aman
bukan11nya@happyending:~/praktikum-os/week07-bash/tugas4-files  cp "laporan server april.txt" "../backup-aman"
bukan11nya@happyending:~/praktikum-os/week07-bash/tugas4-files cp "config[utama]_server.conf" "../backup-aman"
cp: cannot stat 'config[utama]_sever.conf': No such file or directory
bukan11nya@happyending:~/praktikum-os/week07-bash/tugas4-files "config[utama]_server.conf" "../backup-aman/"
bukan11nya@happyending:~/praktikum-os/week07-bash/tugas4-files cp "laporan server april.txt" "../backup-aman/"
cp: target '../backup-aman/' No such file or directory
bukan11nya@happyending:~/praktikum-os/week07-bash/tugas4-files cp system-log-*.txt "../backup/aman/"
bukan11nya@happyending:~/praktikum-os/week07-bash/tugas4-files cp system-log-*.txt "../backup-aman/"
bukan11nya@happyending:~/praktikum-os/week07-bash/tugas4-files cd ~/praktikum-os/week07-bash
tar -czvf backup-$(date +%F).tar.gz backup-aman/
```
3.Membuat Refleksi Quoting dan Riwayat 
```
bukan11nya@happyending:~/praktikum-os/week07-bash$ {
> echo "=== 10 RIWAYAT COMMAND TERAKHIR ==="
> history | tail -n 10
> echo -e "\n=== REFLEKSI QUOTING ==="
> echo "Quoting (' atau \" ) dan escaping (\\) amat krusial di Bash."
> echo "Karena Bash menggunakan spasi sebagai pemisah argumen, nama file"
> echo "seperti 'file saya.txt' akan dianggap sebagai dua target berbeda"
> echo "jika tidak dikutip. Quoting juga menonaktifkan sifat 'spesial' dari karakter"
> echo "seperti tanda kurung siku dan asterisk, mencegah Bash melakukan ekspansi"
> echo "sebelum waktunya sehingga proses administrasi menjadi presisi dan tidak salah target."
} > riwayat-arsip.txt
bukan11nya@happyending:~/praktikum-os/week07-bash$ cat riwayat-arsip.txt
=== 10 RIWAYAT COMMAND TERAKHIR ===
132  cp "laporan server april.txt" "../backup-aman"
133  cp "config[utama]_sever.conf" "../backup-aman"
134  cp "config[utama]_server.conf" "../backup-aman/"
135  cp "laporan server april.txt" "../backup-aman/"
136  cp system-log-*.txt "../backup/aman/"
137  cp system-log-*.txt "../backup-aman/"
138  cd ~/praktikum-os/week07-bash
139  tar -czvf backup-server-$(date +%F).tar.gz backup-aman/
140  clear
141  { echo "=== 10 RIWAYAT COMMAND TERAKHIR ==="; history | tail -n 10; echo -e "\n=== REFLEKSI QUOTING ==="; echo "Quoting (' atau \" ) dan escaping (\\) amat krusial di Bash."; echo "Karena Bash menggunakan spasi sebagai pemisah argumen, nama file"; echo "seperti 'file saya.txt' akan dianggap sebagai dua target berbeda"; echo "jika tidak dikutip. Quoting juga menonaktifkan sifat 'spesial' dari karakter"; echo "seperti tanda kurung siku dan asterisk, mencegah Bash melakukan ekspansi"; echo "sebelum waktunya sehingga proses administrasi menjadi presisi dan tidak salah target."; } > riwayat-arsip.txt

=== REFLEKSI QUOTING ===
Quoting (' atau " ) dan escaping (\) amat krusial di Bash.
Karena Bash menggunakan spasi sebagai pemisah argumen, nama file
seperti 'file saya.txt' akan dianggap sebagai dua target berbeda
jika tidak dikutip. Quoting juga menonaktifkan sifat 'spesial' dari karakter
seperti tanda kurung siku dan asterisk, mencegah Bash melakukan ekspansi
sebelum waktunya sehingga proses administrasi menjadi presisi dan tidak salah target.
bukan11nya@happyending:~/praktikum-os/week07-bash$
```