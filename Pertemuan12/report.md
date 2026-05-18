# **Laporan OS Pertemuan 12**

**Nama** : Rayhan Jofan Halim  
**NIM** : 254107020230  
**Kelas** : TI-1H  

##  Praktikum 10.1 — Amati Layanan Aktif Saat Boot

Langkah 1 — Lihat semua layanan yang sedang berjalan:
```
bukan11nya@happyending:~$ mkdir -p ~/lab-os/chapter10-services
bukan11nya@happyending:~$ cd ~/lab-os/chapter10-services
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl list-units --type=service --state=running
  UNIT                        LOAD   ACTIVE SUB     DESCRIPTION>
  cron.service                loaded active running Regular bac>
  dbus.service                loaded active running D-Bus Syste>
  getty@tty1.service          loaded active running Getty on tt>
  ModemManager.service        loaded active running Modem Manag>
  multipathd.service          loaded active running Device-Mapp>
  polkit.service              loaded active running Authorizati>
  rsyslog.service             loaded active running System Logg>
  snapd.service               loaded active running Snap Daemon
  ssh.service                 loaded active running OpenBSD Sec>
  systemd-journald.service    loaded active running Journal Ser>
  systemd-logind.service      loaded active running User Login >
  systemd-networkd.service    loaded active running Network Con>
  systemd-resolved.service    loaded active running Network Nam>
  systemd-timesyncd.service   loaded active running Network Tim>
  systemd-udevd.service       loaded active running Rule-based >
  udisks2.service             loaded active running Disk Manager
  unattended-upgrades.service loaded active running Unattended >
  user@1000.service           loaded active running User Manage>

Legend: LOAD   → Reflects whether the unit definition was prope>
        ACTIVE → The high-level unit activation state, i.e. gen>
        SUB    → The low-level unit activation state, values de>

18 loaded units listed.
lines 1-25/25 (END)
```

Langkah 2 — Lihat semua unit service (aktif maupun tidak):
```
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl list-unit-files --type=service | head -30
UNIT FILE                                    STATE           PRESET
apparmor.service                             enabled         enabled
apport-autoreport.service                    static          -
apport-coredump-hook@.service                static          -
apport-forward@.service                      static          -
apport.service                               enabled         enabled
apt-daily-upgrade.service                    static          -
apt-daily.service                            static          -
apt-news.service                             static          -
autovt@.service                              alias           -
blk-availability.service                     enabled         enabled
bolt.service                                 static          -
cloud-config.service                         enabled         enabled
cloud-final.service                          enabled         enabled
...
```

Langkah 3 — Analisis waktu boot:

```
bukan11nya@happyending:~/lab-os/chapter10-services$ systemd-analyze
Startup finished in 5.602s (kernel) + 11.351s (userspace) = 16.953s
graphical.target reached after 11.305s in userspace.
bukan11nya@happyending:~/lab-os/chapter10-services$
bukan11nya@happyending:~/lab-os/chapter10-services$ systemd-analyze blame | head -15
5.921s snapd.seeded.service
5.782s snapd.service
2.719s systemd-networkd-wait-online.service
2.540s dpkg-db-backup.service
2.289s dev-mapper-ubuntu\x2d\x2dvg\x2dubuntu\x2d\x2dlv.device
2.120s logrotate.service
2.053s apport.service
1.426s rsyslog.service
1.341s ModemManager.service
1.302s udisks2.service
1.124s apparmor.service
1.085s grub-common.service
 970ms polkit.service
 924ms grub-initrd-fallback.service
 754ms ssh.service
bukan11nya@happyending:~/lab-os/chapter10-services$
```

##  Praktikum 10.2 — Kelola Layanan SSH

```
Langkah 1 — Periksa status SSH:
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabl>
     Active: active (running) since Mon 2026-05-18 12:12:50 UTC>
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 809 ExecStartPre=/usr/sbin/sshd -t (code=exited, s>
   Main PID: 830 (sshd)
      Tasks: 1 (limit: 2266)
     Memory: 4.1M (peak: 5.1M)
        CPU: 118ms
     CGroup: /system.slice/ssh.service
             └─830 "sshd: /usr/sbin/sshd -D [listener] 0 of 10->

May 18 12:12:49 happyending systemd[1]: Starting ssh.service - >
May 18 12:12:50 happyending sshd[830]: Server listening on 0.0.>
May 18 12:12:50 happyending sshd[830]: Server listening on :: p>
May 18 12:12:50 happyending systemd[1]: Started ssh.service - O>
May 18 12:13:17 happyending sshd[1092]: Accepted password for b>
May 18 12:13:17 happyending sshd[1092]: pam_unix(sshd:session):>
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl is-active ssh
active
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl is-enabled ssh
enabled
bukan11nya@happyending:~/lab-os/chapter10-services$
```
```
bukan11nya@happyending:~/lab-os/chapter10-services$ sudo systemctl restart ssh
[sudo] password for bukan11nya:
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabl>
     Active: active (running) since Mon 2026-05-18 12:23:47 UTC>
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 1316 ExecStartPre=/usr/sbin/sshd -t (code=exited, >
   Main PID: 1318 (sshd)
      Tasks: 1 (limit: 2266)
     Memory: 1.2M (peak: 1.5M)
        CPU: 99ms
     CGroup: /system.slice/ssh.service
             └─1318 "sshd: /usr/sbin/sshd -D [listener] 0 of 10>

May 18 12:23:47 happyending systemd[1]: Starting ssh.service - >
May 18 12:23:47 happyending sshd[1318]: Server listening on 0.0>
May 18 12:23:47 happyending sshd[1318]: Server listening on :: >
May 18 12:23:47 happyending systemd[1]: Started ssh.service - O>
log file: ystemctl status ssh...skipping...
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabled; preset: enabled)
     Active: active (running) since Mon 2026-05-18 12:23:47 UTC; 4s ago
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 1316 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 1318 (sshd)
      Tasks: 1 (limit: 2266)
     Memory: 1.2M (peak: 1.5M)
        CPU: 99ms
     CGroup: /system.slice/ssh.service
             └─1318 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

May 18 12:23:47 happyending systemd[1]: Starting ssh.service - OpenBSD Secure Shell server...
May 18 12:23:47 happyending sshd[1318]: Server listening on 0.0.0.0 port 22.
May 18 12:23:47 happyending sshd[1318]: Server listening on :: port 22.
May 18 12:23:47 happyending systemd[1]: Started ssh.service - OpenBSD Secure Shell server.
```
Langkah 3 — Lihat dependensi SSH:

```
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl list-dependencies ssh
ssh.service
● ├─-.mount
● ├─ssh.socket
● ├─system.slice
● └─sysinit.target
●   ├─apparmor.service
●   ├─blk-availability.service
●   ├─dev-hugepages.mount
●   ├─dev-mqueue.mount
●   ├─finalrd.service
●   ├─keyboard-setup.service
●   ├─kmod-static-nodes.service
○   ├─ldconfig.service
●   ├─lvm2-lvmpolld.socket
●   ├─lvm2-monitor.service
●   ├─multipathd.service
○   ├─open-iscsi.service
●   ├─plymouth-read-write.service
○   ├─plymouth-start.service
●   ├─proc-sys-fs-binfmt_misc.automount
●   ├─setvtrgb.service
●   ├─sys-fs-fuse-connections.mount
●   ├─sys-kernel-config.mount
●   ├─sys-kernel-debug.mount
●   ├─sys-kernel-tracing.mount
●   ├─systemd-ask-password-console.path
●   ├─systemd-binfmt.service
○   ├─systemd-firstboot.service
○   ├─systemd-hwdb-update.service
○   ├─systemd-journal-catalog-update.service
●   ├─systemd-journal-flush.service
```

Langkah 4 — Cek unit yang gagal:

```
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl --failed
  UNIT LOAD ACTIVE SUB DESCRIPTION

0 loaded units listed.
```

##  Praktikum 10.3 — Buat Layanan Sederhana dari Skrip Bash

Langkah 1 — Siapkan konten:

```
<!DOCTYPE html>
<html>
<body>
<h1>Halo dari layanan systemd kustom!</h1>
<p>Layanan ini dibuat pada praktek Bab 10.</p>
</body>
</html>
```

Langkah 2 — Buat skrip wrapper:

```
#!/bin/bash
DIREKTORI="$HOME/lab-os/chapter10-services/situs-demo"
PORT=9090
echo "Memulai server di port $PORT ..."
exec python3 -m http.server $PORT --directory "$DIREKTORI"
```

Langkah 3 — Buat berkas unit systemd:

```
[Unit]
Description=Demo Web Server Praktek Bab 10
After=network.target

[Service]
Type=simple
User=nama-pengguna-kamu
WorkingDirectory=/home/nama-pengguna-kamu/lab-os/chapter10-serv>
ExecStart=/usr/bin/python3 -m http.server 9090
Restart=on-failure
RestartSec=3s

[Install]
WantedBy=multi-user.target
```

## Tantangan 1

### Temukan 3 layanan terlama
```
bukan11nya@happyending:~/lab-os/chapter10-services$ systemd-analyze blame | head -3
5.921s snapd.seeded.service
5.782s snapd.service
2.719s systemd-networkd-wait-online.service
```

### Cari tahu fungsi masing-masing

```
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl cat snapd.service
# /usr/lib/systemd/system/snapd.service
```
```
[Unit]
Description=Snap Daemon
After=snapd.socket
After=time-set.target
After=snapd.mounts.target
Wants=time-set.target
Wants=snapd.mounts.target
Requires=snapd.socket
OnFailure=snapd.failure.service
# This is handled by snapd
# X-Snapd-Snap: do-not-start

[Service]
# Disabled because it breaks lxd
# (https://bugs.launchpad.net/snapd/+bug/1709536)
#Nice=-5
OOMScoreAdjust=-900
ExecStart=/usr/lib/snapd/snapd
EnvironmentFile=-/etc/environment
EnvironmentFile=-/var/lib/snapd/environment/snapd.conf
Restart=always
# with systemd v254+, skip going through failed state during re>
RestartMode=direct
WatchdogSec=5m
Type=notify
NotifyAccess=all
SuccessExitStatus=42
RestartPreventExitStatus=42
KillMode=process
KeyringMode=shared
lines 1-31
```

## Tantangan 2 — Script cek-layanan.sh:

```
bukan11nya@happyending:~/lab-os/chapter10-services$ nano ~/lab-os/chapter10-services/cek-layanan.sh
bukan11nya@happyending:~/lab-os/chapter10-services$ chmod +x ~/lab-os/chapter10-services/cek-layanan.sh
bukan11nya@happyending:~/lab-os/chapter10-services$ cd ~/lab-os/chapter10-services
./cek-layanan.sh
[2026-05-18 12:29:05] ssh: ACTIVE
[2026-05-18 12:29:05] cron: ACTIVE
[2026-05-18 12:29:05] rsyslog: ACTIVE

Laporan disimpan ke: laporan-layanan.log
bukan11nya@happyending:~/lab-os/chapter10-services$ cat laporan-layanan.log
[2026-05-18 12:29:05] ssh: ACTIVE
[2026-05-18 12:29:05] cron: ACTIVE
[2026-05-18 12:29:05] rsyslog: ACTIVE
bukan11nya@happyending:~/lab-os/chapter10-services$
```

```
#!/bin/bash
# Script: cek-layanan.sh
# Memeriksa status layanan dari berkas teks

DAFTAR="daftar-layanan.txt"
LAPORAN="laporan-layanan.log"

# Buat daftar layanan jika belum ada
if [ ! -f "$DAFTAR" ]; then
    echo "ssh" > "$DAFTAR"
    echo "cron" >> "$DAFTAR"
    echo "rsyslog" >> "$DAFTAR"
fi

# Kosongkan laporan lama
> "$LAPORAN"

while IFS= read -r LAYANAN; do
    STATUS=$(systemctl is-active "$LAYANAN" 2>/dev/null)
    TANGGAL=$(date '+%Y-%m-%d %H:%M:%S')

    if [ "$STATUS" = "active" ]; then
        echo "[$TANGGAL] $LAYANAN: ACTIVE" | tee -a "$LAPORAN"
    else
        echo "[$TANGGAL] $LAYANAN: INACTIVE" | tee -a "$LAPORAN"
    fi
done < "$DAFTAR"
```


## Latihan 10.1 — Audit Layanan dan Analisis Boot

### Soal 1: Catat semua layanan aktif

```
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl list-units --type=service --state=running
  UNIT                        LOAD   ACTIVE SUB     DESCRIPTION>
  cron.service                loaded active running Regular bac>
  dbus.service                loaded active running D-Bus Syste>
  fwupd.service               loaded active running Firmware up>
  getty@tty1.service          loaded active running Getty on tt>
  ModemManager.service        loaded active running Modem Manag>
  multipathd.service          loaded active running Device-Mapp>
  polkit.service              loaded active running Authorizati>
  rsyslog.service             loaded active running System Logg>
  snapd.service               loaded active running Snap Daemon
  ssh.service                 loaded active running OpenBSD Sec>
  systemd-journald.service    loaded active running Journal Ser>
  systemd-logind.service      loaded active running User Login >
  systemd-networkd.service    loaded active running Network Con>
  systemd-resolved.service    loaded active running Network Nam>
  systemd-timesyncd.service   loaded active running Network Tim>
  systemd-udevd.service       loaded active running Rule-based >
  udisks2.service             loaded active running Disk Manager
  unattended-upgrades.service loaded active running Unattended >
  upower.service              loaded active running Daemon for >
  user@1000.service           loaded active running User Manage>

Legend: LOAD   → Reflects whether the unit definition was prope>
        ACTIVE → The high-level unit activation state, i.e. gen>
        SUB    → The low-level unit activation state, values de>

20 loaded units listed.
```

### Periksa 3 layanan yang kamu kenal

```
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabl>
     Active: active (running) since Mon 2026-05-18 12:23:47 UTC>
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 1318 (sshd)
      Tasks: 1 (limit: 2266)
     Memory: 3.1M (peak: 4.0M)
        CPU: 220ms
     CGroup: /system.slice/ssh.service
             └─1318 "sshd: /usr/sbin/sshd -D [listener] 0 of 10>

May 18 12:23:47 happyending systemd[1]: Starting ssh.service - >
May 18 12:23:47 happyending sshd[1318]: Server listening on 0.0>
May 18 12:23:47 happyending sshd[1318]: Server listening on :: >
May 18 12:23:47 happyending systemd[1]: Started ssh.service - O>
May 18 12:32:11 happyending sshd[1798]: Accepted password for b>
May 18 12:32:11 happyending sshd[1798]: pam_unix(sshd:session):>
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl status cron
● cron.service - Regular background program processing daemon
     Loaded: loaded (/usr/lib/systemd/system/cron.service; enab>
     Active: active (running) since Mon 2026-05-18 12:12:49 UTC>
       Docs: man:cron(8)
   Main PID: 803 (cron)
      Tasks: 1 (limit: 2266)
     Memory: 444.0K (peak: 1.9M)
        CPU: 139ms
     CGroup: /system.slice/cron.service
             └─803 /usr/sbin/cron -f -P

May 18 12:15:01 happyending CRON[1160]: pam_unix(cron:session):>
May 18 12:17:01 happyending CRON[1275]: pam_unix(cron:session):>
May 18 12:17:01 happyending CRON[1276]: (root) CMD (cd / && run>
May 18 12:17:01 happyending CRON[1275]: pam_unix(cron:session):>
May 18 12:25:01 happyending CRON[1326]: pam_unix(cron:session):>
May 18 12:25:01 happyending CRON[1327]: (root) CMD (command -v >
May 18 12:25:01 happyending CRON[1326]: pam_unix(cron:session):>
May 18 12:35:01 happyending CRON[1872]: pam_unix(cron:session):>
May 18 12:35:01 happyending CRON[1873]: (root) CMD (command -v >
May 18 12:35:01 happyending CRON[1872]: pam_unix(cron:session):>
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl status rsyslog
● rsyslog.service - System Logging Service
     Loaded: loaded (/usr/lib/systemd/system/rsyslog.service; e>
     Active: active (running) since Mon 2026-05-18 12:12:48 UTC>
TriggeredBy: ● syslog.socket
       Docs: man:rsyslogd(8)
             man:rsyslog.conf(5)
             https://www.rsyslog.com/doc/
   Main PID: 741 (rsyslogd)
      Tasks: 4 (limit: 2266)
     Memory: 3.1M (peak: 5.1M)
        CPU: 224ms
     CGroup: /system.slice/rsyslog.service
             └─741 /usr/sbin/rsyslogd -n -iNONE

May 18 12:12:47 happyending systemd[1]: Starting rsyslog.servic>
May 18 12:12:48 happyending rsyslogd[741]: imuxsock: Acquired U>
May 18 12:12:48 happyending systemd[1]: Started rsyslog.service>
May 18 12:12:48 happyending rsyslogd[741]: rsyslogd's groupid c>
May 18 12:12:48 happyending rsyslogd[741]: rsyslogd's userid ch>
May 18 12:12:48 happyending rsyslogd[741]: [origin software="rs>
May 18 12:12:49 happyending systemd[1]: rsyslog.service: Sent s>
May 18 12:12:49 happyending rsyslogd[741]: [origin software="rs>
bukan11nya@happyending:~/lab-os/chapter10-services$
```

### Soal 2: 5 layanan terlama saat boot

```
bukan11nya@happyending:~/lab-os/chapter10-services$ systemd-analyze blame | head -5
16min 18.268s snapd.service
      43.520s fwupd-refresh.service
       5.921s snapd.seeded.service
       2.719s systemd-networkd-wait-online.service
       2.540s dpkg-db-backup.service
```

### Soal 3: Layanan yang gagal

```
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl --failed
  UNIT LOAD ACTIVE SUB DESCRIPTION

0 loaded units listed.
```

### Jika ada yang gagal, cari penyebabnya
```
bukan11nya@happyending:~/lab-os/chapter10-services$ journalctl -u nama-layanan -n 30
-- No entries --
```

##  Latihan 10.2 — Layanan Kustom dengan Restart Otomatis

### Soal 1 — Buat script monitor-disk.sh:

```
#!/bin/bash
# Script: monitor-disk.sh
# Catat penggunaan disk setiap 30 detik

LOG_FILE="$HOME/lab-os/chapter10-services/disk-usage.log"

while true; do
    TANGGAL=$(date '+%Y-%m-%d %H:%M:%S')
    echo "[$TANGGAL] === Penggunaan Disk ===" >> "$LOG_FILE"
    df -h >> "$LOG_FILE"
    echo "" >> "$LOG_FILE"
    sleep 30
done
```

### Soal 2 — Buat berkas unit:

```
[Unit]
Description=Monitor Penggunaan Disk
After=network.target

[Service]
Type=simple
User=nama-pengguna-kamu
ExecStart=/home/nama-pengguna-kamu/lab-os/chapter10-services/mo>
Restart=always
RestartSec=5s
StandardOutput=journal
StandardError=journal

[Install]
WantedBy=multi-user.target
```

### Soal 3 — Aktifkan dan verifikasi:

```
bukan11nya@happyending:~/lab-os/chapter10-services$ sudo systemctl daemon-reload
bukan11nya@happyending:~/lab-os/chapter10-services$ sudo systemctl enable --now monitor-disk
Created symlink /etc/systemd/system/multi-user.target.wants/monitor-disk.service → /etc/systemd/system/monitor-disk.service.
bukan11nya@happyending:~/lab-os/chapter10-services$ systemctl status monitor-disk
● monitor-disk.service - Monitor Penggunaan Disk
     Loaded: loaded (/etc/systemd/system/monitor-disk.service; >
     Active: activating (auto-restart) (Result: exit-code) sinc>
    Process: 2234 ExecStart=/home/nama-pengguna-kamu/lab-os/cha>
   Main PID: 2234 (code=exited, status=217/USER)
        CPU: 45ms
bukan11nya@happyending:~/lab-os/chapter10-services$ journalctl -u monitor-disk -f
May 18 12:46:41 happyending systemd[1]: monitor-disk.service: Scheduled restart job, restart counter is at 2.
May 18 12:46:41 happyending systemd[1]: Started monitor-disk.service - Monitor Penggunaan Disk.
May 18 12:46:41 happyending (-disk.sh)[2241]: monitor-disk.service: Failed to determine user credentials: No such process
May 18 12:46:41 happyending systemd[1]: monitor-disk.service: Main process exited, code=exited, status=217/USER
May 18 12:46:41 happyending systemd[1]: monitor-disk.service: Failed with result 'exit-code'.
May 18 12:46:46 happyending systemd[1]: monitor-disk.service: Scheduled restart job, restart counter is at 3.
May 18 12:46:46 happyending systemd[1]: Started monitor-disk.service - Monitor Penggunaan Disk.
May 18 12:46:46 happyending (-disk.sh)[2243]: monitor-disk.service: Failed to determine user credentials: No such process
May 18 12:46:46 happyending systemd[1]: monitor-disk.service: Main process exited, code=exited, status=217/USER
May 18 12:46:46 happyending systemd[1]: monitor-disk.service: Failed with result 'exit-code'.
May 18 12:46:52 happyending sys
```

### Soal 4 — Simulasi crash:

```
bukan11nya@happyending:~$ systemctl status monitor-disk | grep "Main PID"
   Main PID: 2408 (code=exited, status=217/USER)
bukan11nya@happyending:~$ sudo kill -9 $(systemctl show monitor-disk --property=MainPID --value)
[sudo] password for bukan11nya:
Killed
bukan11nya@happyending:~$ sleep 10
bukan11nya@happyending:~$ systemctl status monitor-disk
● monitor-disk.service - Monitor Penggunaan Disk
     Loaded: loaded (/etc/systemd/system/monitor-disk.service; >
     Active: activating (auto-restart) (Result: exit-code) sinc>
    Process: 2435 ExecStart=/home/nama-pengguna-kamu/lab-os/cha>
   Main PID: 2435 (code=exited, status=217/USER)
        CPU: 15ms

May 18 12:50:21 happyending systemd[1]: monitor-disk.service: M>
May 18 12:50:21 happyending systemd[1]: monitor-disk.service: F>
bukan11nya@happyending:~$
```

### Soal 5 — Bersihkan:

```
bukan11nya@happyending:~$ sudo systemctl disable --now monitor-disk
Removed "/etc/systemd/system/multi-user.target.wants/monitor-disk.service".
bukan11nya@happyending:~$ sudo rm /etc/systemd/system/monitor-disk.service
bukan11nya@happyending:~$ sudo systemctl daemon-reload
```

## Latihan 10.3 — Investigasi Log dan Keamanan SSH

### Soal 1 — Temukan semua error sejak boot:

```
bukan11nya@happyending:~$ journalctl -b -p err --no-pager > ~/lab-os/chapter10-services/error-boot.txt
bukan11nya@happyending:~$ wc -l ~/lab-os/chapter10-services/error-boot.txt
309 /home/bukan11nya/lab-os/chapter10-services/error-boot.txt
bukan11nya@happyending:~$ cat ~/lab-os/chapter10-services/error-boot.txt
May 18 12:12:43 happyending kernel: ITS: WARNING: ITS mitigation depends on retpoline and rethunk support
May 18 12:12:45 happyending kernel: vmwgfx 0000:00:02.0: [drm] *ERROR* vmwgfx seems to be running on an unsupported hypervisor.
May 18 12:12:45 happyending kernel: vmwgfx 0000:00:02.0: [drm] *ERROR* This configuration is likely broken.
May 18 12:12:45 happyending kernel: vmwgfx 0000:00:02.0: [drm] *ERROR* Please switch to a supported graphics device to avoid problems.
May 18 12:12:57 happyending login[836]: PAM unable to dlopen(pam_lastlog.so): /usr/lib/security/pam_lastlog.so: cannot open shared object file: No such file or directory
May 18 12:12:57 happyending login[836]: PAM adding faulty module: pam_lastlog.so
May 18 12:38:23 happyending (python3)[1952]: demo-web.service: Failed to determine user credentials: No such process
...
```

### Soal 2 — Tiga perubahan keamanan SSH:

```
bukan11nya@happyending:~$ sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup.latihan103
[sudo] password for bukan11nya:
bukan11nya@happyending:~$ sudo nano /etc/ssh/sshd_config
bukan11nya@happyending:~$ sudo nano /etc/ssh/sshd_config
bukan11nya@happyending:~$ sudo sshd -t
bukan11nya@happyending:~$ echo "Kode keluar: $?"
Kode keluar: 0
bukan11nya@happyending:~$ sudo systemctl reload ssh
bukan11nya@happyending:~$
```
```
# no default banner path
#Banner none

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

# override default of no subsystems
Subsystem       sftp    /usr/lib/openssh/sftp-server

# Example of overriding settings on a per-user basis
#Match User anoncvs
#       X11Forwarding no
#       AllowTcpForwarding no
#       PermitTTY no
#       ForceCommand cvs server

PermitRootLogin no
MaxAuthTries 3
LoginGraceTime 30
```

### Soal 3 — Verifikasi tiga hal:

```
bukan11nya@happyending:~$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabl>
     Active: active (running) since Mon 2026-05-18 12:23:47 UTC>
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 2805 ExecReload=/usr/sbin/sshd -t (code=exited, st>
    Process: 2806 ExecReload=/bin/kill -HUP $MAINPID (code=exit>
   Main PID: 1318 (sshd)
      Tasks: 1 (limit: 2266)
     Memory: 3.0M (peak: 4.5M)
        CPU: 603ms
     CGroup: /system.slice/ssh.service
             └─1318 "sshd: /usr/sbin/sshd -D [listener] 0 of 10>

May 18 12:32:11 happyending sshd[1798]: pam_unix(sshd:session):>
May 18 12:48:55 happyending sshd[2309]: Accepted password for b>
May 18 12:48:55 happyending sshd[2309]: pam_unix(sshd:session):>
May 18 12:53:47 happyending sshd[2675]: Accepted password for b>
May 18 12:53:47 happyending sshd[2675]: pam_unix(sshd:session):>
May 18 12:55:50 happyending systemd[1]: Reloading ssh.service ->
May 18 12:55:50 happyending sshd[1318]: Received SIGHUP; restar>
May 18 12:55:50 happyending sshd[1318]: Server listening on 0.0>
May 18 12:55:50 happyending sshd[1318]: Server listening on :: >
May 18 12:55:50 happyending systemd[1]: Reloaded ssh.service - >
bukan11nya@happyending:~$ ss -tlnp | grep ssh
bukan11nya@happyending:~$ grep -E "PermitRoot|MaxAuth|GraceTime" /etc/ssh/sshd_config
#LoginGraceTime 2m
#PermitRootLogin prohibit-password
#MaxAuthTries 6
# the setting of "PermitRootLogin prohibit-password".
PermitRootLogin no
MaxAuthTries 3
LoginGraceTime 30
```

### Soal 4 — Kembalikan konfigurasi:

```
bukan11nya@happyending:~$ sudo cp /etc/ssh/sshd_config.backup.latihan103 /etc/ssh/sshd_config
bukan11nya@happyending:~$ sudo sshd -t
bukan11nya@happyending:~$ sudo systemctl reload ssh
bukan11nya@happyending:~$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/usr/lib/systemd/system/ssh.service; enabl>
     Active: active (running) since Mon 2026-05-18 12:23:47 UTC>
TriggeredBy: ● ssh.socket
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 2858 ExecReload=/usr/sbin/sshd -t (code=exited, st>
    Process: 2860 ExecReload=/bin/kill -HUP $MAINPID (code=exit>
   Main PID: 1318 (sshd)
      Tasks: 1 (limit: 2266)
     Memory: 3.0M (peak: 4.5M)
        CPU: 713ms
     CGroup: /system.slice/ssh.service
             └─1318 "sshd: /usr/sbin/sshd -D [listener] 0 of 10>

May 18 12:55:50 happyending systemd[1]: Reloading ssh.service ->
May 18 12:55:50 happyending sshd[1318]: Received SIGHUP; restar>
May 18 12:55:50 happyending sshd[1318]: Server listening on 0.0>
May 18 12:55:50 happyending sshd[1318]: Server listening on :: >
May 18 12:55:50 happyending systemd[1]: Reloaded ssh.service - >
May 18 12:57:22 happyending systemd[1]: Reloading ssh.service ->
May 18 12:57:22 happyending sshd[1318]: Received SIGHUP; restar>
May 18 12:57:22 happyending sshd[1318]: Server listening on 0.0>
May 18 12:57:22 happyending sshd[1318]: Server listening on :: >
May 18 12:57:22 happyending systemd[1]: Reloaded ssh.service - >
bukan11nya@happyending:~$ ss -tlnp | grep ssh
bukan11nya@happyending:~$
```


