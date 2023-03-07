<h3>Mencatat IP Address Pc</h3>

![IP](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas2/Foto/ip-a.jpg)

ip pc berada pada enp2s0 yaitu 192.168.2.254.

<h3>Mengakses Winbox64.exe </h3>

Winbox64.exe dapat dijalankan di debian engan cara menginstall wine terlebih dahulu. Setelah wine terinstall, selanjutnya mendownload winbox64.exe dan letakkan pada folder pada pc. Kemudian buka direktori tempat menyimpan file winbox64.exe. Jalankan perintah "wine winbox64.exe". Tampilan winbox pada foto dibawah ini.

![winbox](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas2/Foto/winbox.jpg)

Setelah winbox berhasil dibuka, untuk menyambungkan semua pc yang berada di lab, kita harus melakukan setting routing tiap pc satu per satu. Proses routing akan digambarkan dibawah ini.

![route](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas2/Foto/routing-mikrotik.jpg)

Dengan dst address diisi dengan network address pc yang ingin dituju, gateway diisi dengan network ethernet 1 pada mikrotik pc yang ingin dituju.

<h3>Instalasi Virtualbox </h3>

Hal pertama yang harus dilakukan adalah menambahkan "contrib" dan "non-free" components di /etc/apt/sources.list.

![sourceslist](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas2/Foto/dependency-virtualbox.jpg)

kemudian melakukan 
> sudo apt update

setelah proses update selesai selanjutnya kita menjalankan perintah untuk install virtualboxnya

>sudo apt install virtualbox

Setelah terinstall virtualbox akan berada di menu debian kita. Proses terakhir adalah melakukan instalasi / copy OS kedalam virtualbox.

![install OS](https://github.com/alvianfazlur/Administrasi-Jaringan/blob/main/Tugas2/Foto/create-ubuntu-user.jpg)
