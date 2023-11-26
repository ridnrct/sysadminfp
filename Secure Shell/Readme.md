# Secure Shell Config
### Konfigurasi IP Address
```
nmtui
```
Konfigurasikan ip address serta gateway pada network yang diinginkan dan kemudian save. Pada konfigurasi saya menggunakan ip address 192.168.5.2/24 dan 192.168.5.1 sebagai gateway.
<!-- ![](https://github.com/ridnrct/sysadminfp/blob/main/Secure%20Shell/ssh1.jpg) -->

### Konfigurasi File sshd_config
```
nano /etc/ssh/sshd_config
```
<!-- [](https://github.com/ridnrct/sysadminfp/blob/main/Secure%20Shell/ssh2.jpg) -->
Pada file tersebut uncomment `permitRootLogin yes` dan `PasswordAuthentication yes`.
Kemudian save file tersebut, restart ssh dan cek status apakah ssh sudah berjalan.
```
service sshd restart
```
```
service sshd status
```
![](https://github.com/ridnrct/sysadminfp/blob/main/Secure%20Shell/ssh3.jpg)

### Konfigurasi Client

<!-- ![](https://github.com/ridnrct/sysadminfp/blob/main/Secure%20Shell/ssh4.jpg) -->
Penggunaan ip address pada client seperti 192.168.5.5 dengan gateway 192.168.5.1 menggunakan satu network yang sama, cobalah ping antar koneksi tersebut. 
Setelah terkoneksi, Kemudian ssh dapat dijalan dengan perintah `ssh root@192.168.52`
![](https://github.com/ridnrct/sysadminfp/blob/main/Secure%20Shell/ssh5.jpg)
