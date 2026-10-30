# NetLab TJKT

Simulator jaringan untuk praktik Teknik Jaringan Komputer dan Telekomunikasi (TJKT) di SMK Negeri 1 Murung Pudak.
Alur kerjanya mirip Packet Tracer: susun topologi, sambung kabel, konfigurasi router/switch lewat CLI gaya IOS atau router MikroTik lewat Winbox, instal Debian 9 atau Windows Server 2019 di server, lalu uji dengan ping, PDU, dan mode simulasi.

**Buka aplikasi:** https://tjktskamuda.github.io/netlab-tjkt/

## Fitur

- Perangkat: Router 2911, Switch 2960, Router WiFi MikroTik (RB951Ui-2HnD), Access Point, PC, Laptop, Smartphone, Server, Server OS, Internet (ISP)
- Kabel straight, crossover, serial DCE, console, dan otomatis, dengan lampu link
- CLI gaya IOS: VLAN & trunk, router-on-a-stick, static route, RIP, OSPF, DHCP, ACL, Telnet/SSH
- Desktop PC: IP Configuration (dengan rincian network, broadcast, dan biner), Command Prompt, Kalkulator IP, Web Browser, Wi-Fi, Terminal
- Server: DHCP, DNS, HTTP
- MikroTik + simulator Winbox (gaya Winbox v3, RouterOS 6.49):
  - Quick Set, Interfaces, VLAN, Bridge, Interface List
  - Wireless: mode AP/station, Virtual AP, Security Profile WPA/WPA2, Access List, Registration, Scanner
  - IP: Addresses, ARP, DHCP Client/Server/Relay (termasuk DHCP Setup), DNS, Pool, Routes, Services, Neighbors
  - Firewall Filter, NAT (masquerade, dst-nat/port forward, redirect), Address List, Connections
  - Hotspot lengkap dengan Hotspot Setup, user/profil, rate-limit, dan halaman login di Web Browser PC
  - Simple Queue (efeknya terlihat di aplikasi Speed Test), Users, Backup/Restore, Reset Configuration, Log, Safe Mode, Undo
  - Tools: Ping, Traceroute, IP Scan, Netwatch, Bandwidth Test, Telnet; New Terminal dengan CLI RouterOS
  - Aplikasi Winbox di Desktop PC: connect lewat MAC (Neighbors) atau IP
  - Menu lain ditampilkan sesuai Winbox asli dengan keterangan "belum disimulasikan"
- Internet (ISP): 4 port pelanggan dengan IP publik (DHCP atau statis), DNS publik 8.8.8.8, situs tiruan (google.com, detik.com, deb.debian.org, dll.), paket kecepatan, situs kustom, dan catatan paket IP privat yang ditolak karena belum NAT
- Server OS (kosong saat ditambahkan), pilih DVD instalasi:
  - **Debian 9**: installer mode teks (bahasa, lokasi, jaringan DHCP/manual, hostname, root & user, partisi, network mirror, tasksel, GRUB), lalu console dengan bash: nano, apt-get dari DVD/mirror, systemctl, ip/ifup, ping, nslookup/dig, curl, ssh, adduser, su/sudo; layanan bind9, isc-dhcp-server, apache2 (virtual host), openssh-server, dan lainnya. PC bisa SSH ke server.
  - **Windows Server 2019**: Windows Setup (edisi, lisensi, disk, password Administrator), layar kunci, desktop; Server Manager, Add Roles and Features, IP statis lewat Network Connections, Windows Firewall, Command Prompt & PowerShell; konsol DHCP (scope, exclusion, reservation, options), DNS Manager (zona, A, CNAME, MX, PTR, forwarder), IIS Manager (situs, binding host name), AD DS (promote domain controller) dan Active Directory Users and Computers
- Web server:
  - **Debian**: apache2 (virtual host `ServerName`/`ServerAlias`, `Alias`, a2ensite/a2enconf/a2enmod) atau nginx (`server_name`, `root`, `autoindex`); PHP 7.0 (subset: echo, variabel, `$_SERVER`, fungsi string/tanggal, `phpinfo()`), daftar isi folder, halaman galat 403/404 asli; uji dengan Web Browser PC, `curl`, dan `wget`
  - **Windows Server**: IIS (situs, binding host name, Default Document, Directory Browsing, galat 403.14/404.0/404.3)
- Mail server:
  - **Debian**: Postfix (dialog debconf saat instal dan `dpkg-reconfigure postfix`, `main.cf`, `postconf`, `mailq`, `/var/log/mail.log`), Dovecot IMAP/POP3, `mail`/`sendmail`, uji manual `telnet IP 25`, serta webmail Roundcube (dbconfig dengan MariaDB, `/etc/roundcube/config.inc.php`, Alias Apache)
  - **Windows Server**: unduh dan instal hMailServer (perlu fitur .NET Framework 3.5), hMailServer Administrator (domain, akun, alias, protokol SMTP/POP3/IMAP, IP Ranges & SMTP AUTH, Diagnostics), aturan Windows Firewall untuk port 25/110/143, fitur Telnet Client
  - Record MX di DNS (bind9 maupun DNS Manager) dipakai untuk kirim email antar-server dan antar-domain
  - Aplikasi **Email** di Desktop PC/Laptop (gaya Thunderbird/Outlook: akun IMAP/POP3, SMTP AUTH, kirim, terima, balas, hapus)
- Mode Simulasi untuk melihat paket berjalan
- Contoh lab siap pakai (termasuk MikroTik Internet Sekolah, Hotspot & Limit Bandwidth, Internet & Server Debian 9, Windows Server, dan Web & Mail Server), simpan otomatis, ekspor/impor proyek (.json)
- Bisa dipasang sebagai aplikasi dan dipakai tanpa internet

## Cara memasang di HP

**Android (Chrome)**
1. Buka https://tjktskamuda.github.io/netlab-tjkt/
2. Ketuk tombol **Pasang** di menu atas, atau menu **⋮** lalu **Instal aplikasi**.

**iPhone / iPad (Safari)**
1. Buka link di **Safari**.
2. Ketuk **Bagikan** (kotak dengan panah ke atas), pilih **Tambahkan ke Layar Utama**, lalu **Tambah**.

**Laptop (Chrome/Edge)**
Klik ikon pasang di ujung kanan kolom alamat.

Setelah dipasang, buka aplikasi sekali saat online supaya semua berkas tersimpan. Berikutnya aplikasi bisa dibuka tanpa internet.

## Membuat file APK Android (opsional)

1. Buka https://www.pwabuilder.com dan masukkan alamat aplikasi di atas.
2. Pilih **Package for stores → Android**, lalu unduh paketnya.
3. File `.apk` bisa dibagikan langsung ke siswa (izinkan "instal dari sumber tidak dikenal"), atau file `.aab` diunggah ke Google Play Console.

## Memperbarui aplikasi

Ganti `index.html` dengan versi baru, lalu naikkan nama versi di baris pertama `sw.js` (misalnya `netlab-tjkt-v6`) agar HP siswa ikut memperbarui salinan offline-nya.

## Struktur berkas

| Berkas | Fungsi |
| --- | --- |
| `index.html` | Seluruh aplikasi (satu berkas) |
| `manifest.webmanifest` | Nama, ikon, dan warna aplikasi saat dipasang |
| `sw.js` | Service worker untuk mode offline |
| `icons/` | Ikon aplikasi dari logo TJKT |
| `screenshots/` | Gambar pratinjau di jendela pemasangan |

## Catatan

NetLab adalah simulator untuk latihan di kelas. Tampilan dan perintahnya meniru Cisco IOS, MikroTik RouterOS/Winbox, Debian, dan Windows Server, tetapi NetLab bukan produk resmi Cisco, MikroTik, Debian, Microsoft, maupun pembuat perangkat lunak server lain yang ditiru, dan tidak memuat sistem operasi aslinya. Hanya bagian yang berkaitan dengan jaringan yang benar-benar bekerja; menu lain diberi keterangan "tidak disimulasikan". Internet di dalam NetLab juga tiruan: tidak ada koneksi ke situs sungguhan. Email juga hanya berjalan di dalam topologi NetLab (tidak ada SSL/TLS dan tidak bisa mengirim ke alamat email sungguhan). Cisco, MikroTik, RouterOS, Winbox, Debian, Microsoft, Windows Server, Postfix, Dovecot, Roundcube, dan hMailServer adalah merek dagang milik pemiliknya masing-masing.
