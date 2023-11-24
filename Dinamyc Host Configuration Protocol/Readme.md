# Konfigurasi DHCP Server
### Install Package DHCP
```
yum install dhcp
```
### Konfigurasi File Config
File config dhcp berapa pada file dhcpd.conf
```
nano /etc/dhcp/dhcpd.conf
```
Pada file dhcpd.conf isikan konfigurasi seperti dibawah :
```
option domain-name    "rid.xy";
option domain-name-servers    1.1.1.1;
default-lease-time 600;
max-lease-time 7200
authoritative;
subnet 192.168.5.0 netmask 255.255.255.0 {
        range dynamic-bootp 192.168.5.3 192.168.5.10;
        option broadcast-address 192.168.5.255;
        option routers 192.168.5.1;
}
```
Kemudian mulai service dhcpd :
```
systemctl start dhcpd
```
```
systemctl enable dhcpd
```
```
systemctl status dhcpd
```
![](https://github.com/ridnrct/sysadminfp/blob/main/Dinamyc%20Host%20Configuration%20Protocol/dhcp3.jpg)
Setelah service dhcp berjalan, client dengan semula static ip address diubah menjadi dynamic dan nantinya akan mendapat ip address dengan range 192.168.5.3 hingga 192.168.5.10.
![](https://github.com/ridnrct/sysadminfp/blob/main/Dinamyc%20Host%20Configuration%20Protocol/dhcp6.jpg)
