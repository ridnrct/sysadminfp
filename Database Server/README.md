# Database Server
### Installasi Database Server Mysql
Sebelum installasi tambahkan link dibawah untuk mendowload package mysql dari mysql repositori langsung.
```
wget https://dev.mysql.com/get/mysql80-community-release-el7-3.noarch.rpm
```
Persiapkan repositori untuk penginstallan mysql.
```
rpm -Uvh mysql80-community-release-el7-3.noarch.rpm
```
```
rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2022
```
Installasi mysql.
```
yum install mysql-server
```
Mulai service mysql dan cek status.
```
systemctl start mysqld
```
```
systemctl status mysqld
```
![](https://github.com/ridnrct/sysadminfp/blob/main/Database%20Server/db1.jpg)
