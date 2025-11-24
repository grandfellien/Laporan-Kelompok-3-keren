# 💻  PENGEMBANGAN WEB SERVER DAN APLIKASI SEDERHANA

**Proyek:** [Memconfiguras Web server Menggunakan Open lite speed (OLS)]

Proyek ini dibuat untuk memenuhi tugas mata pelajaran **Administrasi Sistem Jaringan (ASJ)**, yang merupakan salah satu elemen Capaian Pembelajaran Konsentrasi Keahlian Teknik Komputer dan Jaringan (**CP KKTKJ**) pada program TJKT. Proyek ini berfokus pada implementasi layanan Web Server, konfigurasi PHP, dan pengamanan koneksi menggunakan SSL/HTTPS.

---

### 1. 👥 Informasi Kelompok dan Spesifikasi Lingkungan Praktik

#### 1.1. Informasi Kelompok

| Peran | Nama Lengkap | Kelas |
| :--- | :--- | :--- |
| **Ketua Kelompok** | Muhammad Rangga Maulana | XI-TJKT 2 |
| Anggota 1 | Aji Sanjani | XI-TJKT 2 |
| Anggota 2 | Aldy Fahri Firmansyah| XI-TJKT 2 |
| Anggota 3 | Siti Zhaira Ulul Albab | XI-TJKT 2 |
| **Nama Sekolah/Institusi** | SMK Negeri 1 Soreang | |

#### 1.2. Spesifikasi Alat dan Bahan (Host) 🛠️

| Komponen | Deskripsi / Versi |
| :--- | :--- |
| **Virtualisasi** | Vmware 17 Pro |
| **Sistem Operasi Host** | OS yang kami gunakan adalah Windows 10 (Cracked) |
| **RAM Host (Minimal)** | 4GB |
| **CPU Host** | i3-4130 |

#### 1.3. Spesifikasi Server Virtual (VM) 🖥️

| Spesifikasi | Detail |
| :--- | :--- |
| **Sistem Operasi Tamu (Guest OS)** | Debian Trixie (12.x) |
| **Alamat IP Server** | `103.193.178.63` |
| **RAM VM** | 2Gb |
| **vCPU** | 2 Core |
| **Web Server yang Dipilih** | **OpenLiteSpeed** |
| **Versi PHP yang Dipakai** | **lsphp** |

---

### 2. 📝 Dokumentasi Teknis dan Langkah-Langkah Pengerjaan

#### 2.1. Persiapan Dasar (Debian Trixie di VMware)

1.  Melakukan *update* dan *upgrade* sistem.
    ```bash
    sudo apt update
    sudo apt upgrade


    ```
2.  Memastikan konfigurasi jaringan (Bridge/NAT/Host-Only) sudah benar.

#### 2.2. Instalasi dan Konfigurasi Web Server 🌐

Kami menggunakan **[Open lite speed (OLS)]**. Berikut langkah-langkah utamanya:

* **Instalasi:**
    ```bash
    sudo apt update
    sudo apt install gnupg2 ca-certificates -y
    wget -O - https://repo.litespeed.sh | sudo bash
    sudo apt install openlitespeed -y


    ```
* **Konfigurasi Virtual Host/Server Block:**
    [Konfigurasi Virtual Host/Server Block:

Mengubah Document Root di:

/usr/local/lsws/conf/vhosts/Example/vhconf.conf


Document Root diarahkan ke:

/usr/local/lsws/Example/html/


Mengatur listener port 80 → diarahkan ke Default Virtual Host.]

#### 2.3. Konfigurasi PHP 🐘

Kami menggunakan lsphp sebagai modul PHP bawaan OpenLiteSpeed.

* **Instalasi PHP:**
    ```bash
    sudo apt install lsphp81 lsphp81-common lsphp81-mysql lsphp81-curl lsphp81-xml lsphp81-zip -y

    sudo apt install php-fpm php-mysql
    ```
* **Integrasi:**
    Integrasi PHP dengan OpenLiteSpeed:

Menambahkan eksternal app dengan type LiteSpeed SAPI App via Web Admin Panel.

Menambahkan script handler agar file .php diproses oleh lsphp81.

Path eksekusi PHP biasanya:
```path php
/usr/local/lsws/lsphp81/bin/lsphp
```

#### 2.4. Implementasi SSL (HTTPS) 🔒

Kami menggunakan self-signed certificate untuk mengaktifkan HTTPS.

1.  Membuat direktori untuk *certificate*.
   ``` Bash
sudo mkdir -p /etc/ssl/litespeed/
```
2.  Membuat *Key* dan *Certificate* menggunakan OpenSSL.
   ```bash
sudo openssl req -x509 -nodes -days 365 \
-newkey rsa:2048 \
-keyout /etc/ssl/litespeed/self.key \
-out /etc/ssl/litespeed/self.crt
```
3.  Konfigurasi Listener HTTPS di OpenLiteSpeed:

Buka panel admin:
https://IP_SERVER:7080

Listener → Add → Port: 443

Pilih SSL Certificate & Key:
```pilih
/etc/ssl/litespeed/self.crt
/etc/ssl/litespeed/self.key
```

---

### 3. 📊 Analisis Web Server

Berdasarkan pengalaman kami dalam proyek ini, berikut adalah analisis kelebihan dan kekurangan dari *Web Server* yang kami gunakan:

| Aspek | Kelebihan WEB SERVER 👍 | Kekurangan WEB SERVER 👎 |
| :--- | :--- | :--- |
| **Performa & Kecepatan** | [Tuliskan kelebihannya.] | [Tuliskan kekurangannya.] |
| **Kemudahan Konfigurasi**| Tersedia web admin GUI Sehingga konfigurasi gampang| [Struktur konfigurasi berbeda dari Apache/Nginx, perlu adaptasi.] |
| **Fitur & Modularitas** | [Built-in cache (LSCache) sangat cepat, dukungan OpenLiteSpeed API.] | [Tuliskan kekurangannya.] |

---

### 4. 🧠 Refleksi Proyek: Kesan dan Kendala

#### 4.1. Kesan Selama Proses Pengerjaan ✨

Kami merasa mendapatkan banyak ilmu baru, terutama dalam praktik Version Control menggunakan Git dan GitHub yang belum pernah kami lakukan sebelumnya.

#### 4.2. Kendala dan Solusi yang Diterapkan 💡

| Kendala yang Kalian Hadapi 🚧 | Solusi yang Ditemukan ✅ |
| :--- | :--- |
| [Tuliskan kendala teknis atau kolaborasi lain yang Kalian hadapi.] | [Jelaskan solusi spesifik Kalian.] |

---

### 5. 📂 Dokumentasi Konten Website

Seluruh *source code* (Halaman Utama dan Halaman Profil) yang berada di *document root* server telah disalin dan di-*commit* ke dalam folder `/html` di *repository* GitHub ini.

---

### 6. 🎬 Dokumentasi Video Pengerjaan

Seluruh proses pengerjaan telah direkam dan diunggah ke YouTube.

**Link Video YouTube:**

[![Thumbnail Video Pengerjaan](https://img.youtube.com/vi/1-qlNtQS1OA/0.jpg)](https://www.youtube.com/watch?v=1-qlNtQS1OA)

**PETUNJUK:** Ganti semua teks di dalam tanda kurung siku `[ ... ]` dengan informasi proyek yang relevan.
