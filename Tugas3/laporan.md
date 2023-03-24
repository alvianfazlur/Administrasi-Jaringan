<h2>
Praktikum Minggu 4 ||
Mohamad Alvian (3121600032)
</h2>


Mengecek apakah komputer sudah mendapatkan IP menggunakan perintah
> ip a

![IPCOM](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/ipcom.jpg)

Apabila pc telah mendapatkan ip, selanjutnya adalah melakukan pengecekan terhadap ip laptop / interface lainnya.

![IPVM](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/ipvm.jpg)

IP laptop disini harus dipastikan sesuai dengan mikrotik yang sudah disetting sebelumnya. yaitu menggunakan 192.168.x.x, disini ip yang digunakan oleh pc dan komputer adalah 192.168.10.x karena berada di kelompok 10.

Sebelum melanjutkan praktikum, pastikan jaringan sudah mengenali semua jaringan yang berada di lab, apabila belum kita harus melakukan new route pada winbox seperti gambar dibawah ini

![NR](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/newroute.jpg)
![Routing](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/routelist(1).jpg)

Isikan dst address dan gateway sesuai dengan jaringan yang ada di lab. Apabila sudah selesai melakukan routing, maka tampilan akan seperti ini

![RL](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/routelist.jpg)

Setelah routing ke semua jaringan yang ada di lab selesai, maka selanjutnya adalah menjalankan Virtual Machine dan memastikan setting jaringan VM nya berupa Bridge dan pastikan mendapatkan ip via dhcp dengan benar

![VM](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/settingvm.jpg)

Setelah itu, melakukan setting ip vm menjadi static (192.168.10.10)

![stat](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/staticip.jpg)
![cek](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/ipstaticvm.jpg)

Praktikum selanjutnya adalah melakukan konfigurasi NTP menjadi 0.id.pool.ntp.org

![ntp](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/timedatectl.jpg)
![ntp](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/settingntp.jpg)
![ntp](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/cektimedatectl.jpg)
![ntp](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/confirmtimesync.jpg)

Setelah melakukan konfigurasi NTP kita melakukan penggantian hostname Virtual Machine menjadi server10.kelompok10.takehome.com menggunakan perintah
> sudo nano /etc/hostname

![hostname](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas3/Foto/hostname.jpg)
