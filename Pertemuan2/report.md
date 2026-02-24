# LAPORAN PERTEMUAN 2

<h4> Nama : Rayhan Jofan Halim<h4>
<h4>NIM : 254107020230<h4>
<h4>Kelas : TI-1H<h4>

## Praktikum 2.1 — Identifikasi CPU dan Memori


1. Tampilkan informasi CPU:

![1](<images/Screenshot 2026-02-23 113938.png>)

2. Tampilkan ringkasan memori & 3. (Opsional) cek informasi hardware dari DMI/BIOS (butuh sudo):

![2&3](<images/Screenshot 2026-02-23 114236.png>)


### Latihan 2.1
Jelaskan perbedaan RAM vs swap dalam 2–3 kalimat!
Catat:
* 1. Jumlah CPU(s), core/thread
* 2. Total RAM
* 3. Total swap

### Jawaban Latihan 2.1
* 1. 6 CPU, 1 Core, 1 Thread
* 2. 1,9 GB
* 3. 2 GB

RAM adalah perangkat keras yang digunakan untuk menyimpan data sementara. Sedangkan, swap adalah bentuk lain dari RAM yang menggunakan sebagian storage dari hdd atau ssd untuk dijadikan sebagai RAM. Swap digunakan ketika RAM sudah habis digunakan.

## Praktikum 2.2 — Identifikasi Perangkat PCI/USB dan
Driver
Temukan 1 perangkat PCI (misal NIC) dan tuliskan: Vendor:Device ID (angka
heksadesimal), nama driver/modul kernel, dan deskripsi singkat fungsinya.


1. Lihat daftar perangkat PCI:

![1](<images/Screenshot 2026-02-23 123210.png>)

2. Lihat perangkat PCI beserta driver kernel yang digunakan:

![2](<images/Screenshot 2026-02-23 123238.png>)

3, 4, 5. Fokus pada NIC (Ethernet) untuk mencari modul driver, lihat perangkat USB, dan lihat topologi USB (tree):

![3,4,5](<images/Screenshot 2026-02-23 123433.png>)

### Pertanyaan Latihan 2.2
Tentukan 1 perangkat PCI (misal NIC) dan tuliskan:
* Vendor: Device ID (angka heksadesimal)
* nama driver/modul kernel
* deskripsi singkat fungsinya

### Jawaban Latihan 2.2
* Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e]
* Kernel Driver: e100
* Digunakan untuk menyambungkan internet dengan perangkat

## Praktikum 2.3 -- Identifikasi Storage dan Filesystem

1. Lihat daftar disk/partisi:
2. Tampilkan UUID dan tipe filesystem:

3. Lihat mount point untuk root filesystem

![1,2,3](<images/Screenshot 2026-02-23 123737.png>)

## Praktikum 2.4 -- Melihat Modul Aktif dan Informasinya

Langkah-langkah:
1. Cek versi kernel:
2. Tampilkan daftar modul aktif:
3. Pilih salah satu modul (contoh aman: loop) dan lihat detailnya:
4. Muat modul (jika belum akitf), lalu verifikasi:
5. (Opsional) lihat pesan kernel terbaru:

![1,2,3,4,5](<images/Screenshot 2026-02-23 124621.png>)

## Praktikum 2.5 -- Konfigurasi Auto-load dan Blacklist

Langkah-langkah:
1. Buat file auto-load:
2. Simulasikan verifikasi (tanpa reboot) dengan memastikan modul sudah aktif

![1,2](<images/Screenshot 2026-02-23 124907.png>)

## Praktikum 2.6 -- Mengenali Block vs Character Device

Langkah-langkah:
1. Lihat detail salah satu disk (sesuaikan dengan perangkat Anda, misal sda):
2. Lihat detail device terminal:
3. Lihat disk dan partisi untuk mengaitkan dengan /dev:

![1,2,3](<images/Screenshot 2026-02-23 125106.png>)

### Pertanyaan Latihan 2.3
Dari output ls -l jelaskan perbedaan penanda file untuk block device dan character device. (Hint: karakter pertama pada permission string)

### Jawaban Latihan 2.3
Karakter pertama pada permission string menunjukkan tipe filenya. B untuk Block device, sedangkan C untuk Character device

## Praktikum 2.7 -- Melihat Informasi udev

Langkah-langkah:
1. Cek atribut udev untuk disk:

![1](<images/Screenshot 2026-02-23 125217.png>)
## Praktikum 2.8 -- Membuat Workspace Praktikum

Langkah-langkah:
1. Buat direktori praktikum dan masuk ke dalamnya & 2. Buat beberapa file contoh:
2. Buat beberapa file contoh:

![alt text](<images/Screenshot 2026-02-23 130156.png>)
3. Isi file log contoh (simulasi) & 4. Baca file dengan less:

![alt text](<images/Screenshot 2026-02-23 130553.png>)

## Praktikum 2.9 -- Pencarian Pola dengan grep

Langkah-langkah:
1. Cari baris yang mengandung ERROR pada data.log:
2. Cari tanpa memperhatikan huruf besar/kecil:
3. Tampilkan nomor baris:
4. Tampilkan baris yang tidak cocok (invert match):

![1](<images/Screenshot 2026-02-23 203135.png>)

### Pertanyaan Latihan 2.4

Gunakan grep untuk menampilkan hanya baris yang mengandung INFO atau WARN dari data.log (Hint: gunakan grep -E dengan pola alternatif)

### Jawaban Latihan 2.4
![Jawaban](img/jawprak24.png "Jawaban")


## Praktikum 2.10 -- Substitusi dengan sed (Aman di File Latihan)

Langkah-langkah:
1. Siapkan file konfigurasi latihan, 2. Ganti dev menjadi prod (tanpa mengubah file asli), 3. Terapkan perubahan langsung ke file (-i), 4. Ganti semua kemunculan kata (g untuk global), contoh ubah myserver menjadi node:

![1,2,3,4](<images/Screenshot 2026-02-24 105210.png>)

## Praktikum 2.11 -- Ekstraksi Kolom dengan awk

Langkah-langkah:
1. Lihat output df -h
2. Ambil kolom filesystem dan persentase pemakaian:
3. Filter hanya yang pemakaian di atas 80%:

![1,2,3](<images/Screenshot 2026-02-24 105611.png>)
## Praktikum 2.12 -- Melihat Proses dengan ps

Langkah-langkah:
1. Tampilkan semua proses (format BSD) & 2. Cari proses tertentu (misal sshd):

![1,2](<images/Screenshot 2026-02-24 105802.png>)

## Praktikum 2.13 -- Monitoring Real-time dengan top
Langkah-langkah:
1. Jalankan top:
2. Amati nilai load average, pemakaian CPU, dan proses teratas. Tekan q untuk keluar

![1,2](<images/Screenshot 2026-02-24 105850.png>)

## Praktikum 2.14 -- Menghentikan Proses dengan kill

Langkah-langkah:
1. Jalankan proses dummy di background:
2. Cari PID proses sleep:
3. Hentikan dengan SIGTERM:
4. Verifikasi proses berhenti:

![1,2,3,4](<images/Screenshot 2026-02-24 110249.png>)
## Praktikum 2.15 -- Cek Disk, Load, dan Service

Langkah-langkah:
1. Cek penggunaan disk:
2. Cari direktori yang besar (contoh pada /var):
3. Cek load dan uptime:
4. Cek service yang gagal:
5. Ambil log error terbaru (jika ada indikasi masalah):
![123](<images/Screenshot 2026-02-24 110943.png>)


## Praktikum 2.16 -- Monitoring Port dan Koneksi (Network Basic)

Langkahl-langkah:
1. Lihat interface dan IP:

![1](<images/Screenshot 2026-02-24 110742.png>)

2. Lihat routing table & 3. Lihat port yang sedang listening:
[text](report.md) ![text](<images/Screenshot 2026-02-24 111523.png>)

### Pertanyaan Latihan 2.5
Pilih salah satu port yang listerning dari output ss -tulpn(misal port 22), lalu tuliskan service/proses yang membukanya. Jelaskan kegunaan port tersebut secara singkat

### Jawaban Latihan 2.5
Saya memilih port 22, service yang membukanya adalah sshd. sshd (Secure Shell Daemon) berfungsi untuk digunakan untuk remote login, mengakses dan mengelola server dari jarak jauh secara aman dan terenkripsi

## 1. 9 Latihan

### Pertanyaan 2.A
Jalankan lspci -nnk. Pilih 1 perangkan PCI dan tuliskan: nama perangkat, ID vendor:device, dan kernel driver in use

### Jawaban 2.A

![A](<images/Screenshot 2026-02-23 123238.png>)

Nama perangkat          : SATA controler 
ID vendor:device        : 8086:2829
Kernel driver in use    : ahci

### Pertanyaan 2.B
Tentukan device root filesystem dengan fndmnt /. Lalu cocokkan dengan lsblk -f dan tuliskan tipe filesystem serta UUID-nya

### Jawaban 2.B

![B](<images/Screenshot 2026-02-24 192747.png>)
Device root filysytem berada di sda3 dengan nama ubuntu--vg-ubuntu--lv. Tipe filesystemnya adalah ext4 dan UUIDnya adalah e476159e-ad73-4bee-bb75-bd6aa8972b6d

### Pertanyaan 2.C
Buat file server.log berisi minimal 10 baris dengan variasi kata: INFO, WARN, ERROR. gunakan grep untuk menampilkan hanya baris ERROR.

### Jawaban 2.C

![C](<images/Screenshot 2026-02-24 200045.png>)
### Pertanyaan 2.D
Gunakan sed untuk mengganti semua kata server menjadi node pada file latihan. Tunjukkan sebelum dan sesudah.

### Jawaban 2.D
![D](<images/Screenshot 2026-02-24 105210.png>)

### Pertanyaan 2.E
Gunakan df -h lalu awk untuk menamplkan filesystem yang penggunan disk di atas 70%

### Jawaban 2.E

![E](<images/Screenshot 2026-02-24 194339.png>)

### Pertanyaan 2.F
Jalankan sleep 600 &. Tentukan PID-nya dengan ps. Hentikan dengan SIGTERM. jelaskan beda SIGTERM vs SIGKILL

### Jawaban 2.F

![F](<images/Screenshot 2026-02-24 202308.png>)
Perbedaan antara SIGTERM dan SIGKILL adalah SIGKILL akan langsung dieksekusi. Jika dianalogikan sebagai perintah maka SIGTERM adalah perintah yang sopan yang masih bisa dinego, tetapi jika SIGKILL adalah perintah mutlak yang tidak bisa dibantah

### Pertanyaan 2.G
Gunakan systemctl --failed. Jika tidak ada yang gagal, pilih salah satu service aktif (misal ssh) dan ampikan status serta 30 baris log terkahirnya.

### Jawaban 2.G
![G](<images/Screenshot 2026-02-24 203548.png>)