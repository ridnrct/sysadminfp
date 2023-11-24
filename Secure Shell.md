# Secure Shell Config
**Konfigurasi IP Address**
```
nmtui
```
Konfigurasikan ip address serta gateway pada network yang diinginkan dan kemudian save. Pada konfigurasi saya menggunakan ip address 192.168.5.2/24 dan 192.168.5.1 sebagai gateway.

**Konfigurasi File sshd_config**
```
nano /etc/ssh/sshd_config
```
Pada file tersebut uncomment `permitRootLogin yes` dan `PasswordAuthentication yes`.
Kemudian save file tersebut, restart ssh dan cek status apakah ssh sudah berjalan.
```
service sshd restart
service sshd status
```
![](https://drive.google.com/file/d/1Pier2wKL8Uggxjjzg31m4-X9pnci1oIA/view?usp=sharing)

**Konfigurasi Client**

Penggunaan ip address pada client seperti 192.168.5.5 dengan gateway 192.168.5.1 menggunakan satu network yang sama, cobalah ping antar koneksi tersebut. 
Setelah terkoneksi, Kemudian ssh dapat dijalan dengan perintah `ssh root@192.168.52`
