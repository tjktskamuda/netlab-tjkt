# NetLab TJKT

Simulator jaringan untuk praktik Teknik Jaringan Komputer dan Telekomunikasi (TJKT) di SMK Negeri 1 Murung Pudak.
Alur kerjanya mirip Packet Tracer: susun topologi, sambung kabel, konfigurasi router/switch lewat CLI gaya IOS atau router MikroTik lewat Winbox, lalu uji dengan ping, PDU, dan mode simulasi.

**Buka aplikasi:** https://tjktskamuda.github.io/netlab-tjkt/

## Fitur

- Perangkat: Router 2911, Switch 2960, Router WiFi MikroTik (RB951Ui-2HnD), Access Point, PC, Laptop, Smartphone, Server
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
- Mode Simulasi untuk melihat paket berjalan
- Contoh lab siap pakai (termasuk MikroTik Internet Sekolah dan Hotspot & Limit Bandwidth), simpan otomatis, ekspor/impor proyek (.json)
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

Ganti `index.html` dengan versi baru, lalu naikkan nama versi di baris pertama `sw.js` (misalnya `netlab-tjkt-v2`) agar HP siswa ikut memperbarui salinan offline-nya.

## Struktur berkas

| Berkas | Fungsi |
| --- | --- |
| `index.html` | Seluruh aplikasi (satu berkas) |
| `manifest.webmanifest` | Nama, ikon, dan warna aplikasi saat dipasang |
| `sw.js` | Service worker untuk mode offline |
| `icons/` | Ikon aplikasi dari logo TJKT |
| `screenshots/` | Gambar pratinjau di jendela pemasangan |

## Catatan

NetLab adalah simulator untuk latihan di kelas. Tampilan dan perintahnya meniru Cisco IOS serta MikroTik RouterOS/Winbox, tetapi NetLab bukan produk resmi Cisco maupun MikroTik. Cisco, MikroTik, RouterOS, dan Winbox adalah merek dagang milik pemiliknya masing-masing.
