<h1>Praktikum 6 : Instalasi dan Konfigurasi DNS Server menggunakan BIND 9 </h1>

## Nama : Mohamad Alvian (3121600032)

Sebelum memulai konfigurasi dns server menggunakan bind9, kita melakukan pengecekan terhadap /etc/hosts apakah komputer telah mengenali komputer di lab jarkom

![hosts](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/etc_hosts(1).jpg)

Setelah semua komputer di lab dikenali, kita lakukan percobaan untuk ping ke komputer lainnya menggunakan domain atau namanya.

![ping](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/ping_komputer.jpg)

### Percobaan 1 nslookup
Melakukan nslookup terhadap www.detik.com. nslookup adalah sebuah perintah baris (command-line) pada sistem operasi Windows dan Unix-like yang digunakan untuk mengambil informasi dari server Domain Name System (DNS). nslookup digunakan untuk melakukan kueri DNS untuk mencari informasi tentang alamat IP yang terkait dengan nama domain atau untuk mencari nama domain yang terkait dengan alamat IP.

![detik](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/nslookup_detik.com)

Kemudian untuk melakukan pengecekan apakah dns termasuk tcp / udp kita melihatnya melalui wireshark. Dan berdasarkan wireshark, dns merupakan UDP.

![dns](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/wireshark_nslookup.jpg)

### Percobaan 2 Setting DNS

Sebelum melakukan instalasi aplikasi terlebih dahulu lakukan update menggunakan perintah
>sudo apt update && sudo apt upgrade

Kemudian melakukan installasi bind9 menggunakan perintah

>sudo apt install bind9

![bind9](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/install_bind9.jpg)

Untuk mememulai konfigurasi DNS menggunakan BIND 9 terlebih dahulu kita pindah kedalam direktori /etc/bind. Menggunakan perintah
>cd /etc/bind

Selanjutnya kita buat file db.ip dengan cara melakukan copy dari file db.127. Copy juga file db.local dengan nama db.domain menggunakan perintah

>sudo cp /etc/bind/db.local /etc/bind/db.example.com

Setelah 2 file tersebut terbuat kita edit file db.domain terlebih dahulu. Menggunakan perintah
>sudo nano db.domain

![nano](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/nano_db.domain.jpg)

Pada file db.domain replace / ubah localhost menjadi nama domain yang ingin kita buat. Jangan lupa kita berikan IP Address server DNS kita.

Selanjutnya kita lakukan edit pada file db.ip. Replace / ubah localhost sesuai dengan nama domain kalian. Ingat pada angka 27 tersebut ganti dengan angka terakhir (host) dari IP Address Server.

![ip](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/nano_dbip.jpg)

Lanjut pada file named.conf.local kita lakukan pendefinisian zone berdasarkan Nama Domain yang kita buat beserta IP Address DNS Servernya. Pada bagian 1.1.10.in-addr.arpa perlu diperhatikan bahwa ini sebenarnya adalah reverse dari IP Address DNS kita.Mengapa angka terakhir dari IP Address tidak ikut direverse ? Angka terakhir ini sudah ada pada file db.ip.

![named](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/nano_named.conf.local)

Karena DNS Server kita hanya mengelola domain kita sendiri, maka untuk domain lain yang kita tidak kelola seperti google.com, facebook.com , dll. Agar kita dapat melakukan akses ke domain lainya maka kita harus menambahkan DNS Forwarding. Sebagai contoh disini saya menggunakan Google Public DNS 8.8.8.8 sebagai DNS forwarding.

![option](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/nano_named.conf.option.jpg)

Langkah terakhir kita harus lakukan restart service BIND 9 agar melakukan load konfigurasi terbaru. Pastikan service berjalan dengan normal tidak ada error. Menggunakan perintah
>sudo systemctl restart bind9.service

![res](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/restart_bind9.jpg)

![stats](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/stats_bind9.jpg)

### Testing

menambahkan Alamat IP nameserver ke host resolver. Nameserver utama harus dikonfigurasi seperti halnya host lain untuk memeriksa ulang berbagai hal. Buka DNS client untuk mengetahui detail tentang cara menambahkan alamat nameserver ke network client. Edit nameserver dan parameter untuk domain pada file. Menggunakan perintah

> sudo nano /etc/resolv.conf 

![resolv](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/nano_resolv.conf.jpg)

Setelah resolv.conf diedit, selanjutnya melakukan testing apakah dns server berhasil berjalan atau tidak.

![test](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas6/Foto/testing.jpg)
