# Domain Name System
### Install DNS Server
DNS server yang digunakan yakni bind.
```
yum install bind bind-utils -y
```
### Konfigurasi File DNS Server
Buka file konfigurasi pada fila named.conf.
``` 
nano /etc/named.conf
```
Ubah dan modifikasi baris kode di bawah :
```
listen-on port 53 { 127.0.0.1; 192.168.5.2; };
allow-query { localhost; 192.168.5.2; any; };
allow-query-cache { localhost; 192.168.5.2; any; };
```
Kemudian scroll kebawah dan tambahkan zone(nama domain) dan reverse(alamat ip address) :
```
zone "rid.xy" {
    type master;
    file "/etc/named/rid.xy.zone";
};
zone "5.168.192.in-addr.arpa" IN {
    type master;
file "/etc/named/5.168.182.rev";
};
```
Save dan exit dari file terbut kemudian konfigurasi file rid.xy.zone sesuai dengan letak yang telah dikonfigurasi.
```
nano /etc/named/rid.xy.zone
```
Konfigurasi :
```
$TTL    86400
@       IN      SOA     rid.xy. root.rid.xy. (
                2018092501      ;Serial
                3600            ;Refresh
                1800            ;Retry
                604800          ;Expire
                86400           ;Minimum TTL
)

@       IN      NS      ns1.rid.xy.
@       IN      NS      ns2.rid.xy.
@       IN      A       192.168.5.2
ns1     IN      A       192.168.5.2
ns2     IN      A       192.168.5.2
www     IN      CNAME   rid.xy.
blog    IN      A       192.168.5.2
```

Selanjutnya membuat zone reverse.
```
nano /etc/named/5.168.192.rev
```
Konfigurasi :
```
$TTL    86400
@       IN      SOA     rid.xy. root.rid.xy. (
                2018092501      ;Serial
                3600            ;Refresh
                1800            ;Retry
                604800          ;Expire
                86400           ;Minimum TTL
)

        IN      NS      ns1.rid.xy.
        IN      NS      ns2.rid.xy.
@       IN      A       192.168.5.2
ns1     IN      A       192.168.5.2
ns2     IN      A       192.168.5.2
50      IN      PTR     rid.xy.
50      IN      PTR     blog.rid.xy.
```

Setelah kedua file zone dan reverse dibuat, aktifkan dan restart service named.
```
systemctl enable named
```
```
systemctl restart named
```
Ubah fule DNS resolv.conf.
```
nano /etc/resolv.conf
```
Konfigurasi :
```
search rid.xy
nameserver 192.168.5.2
```

### Install Web Server
Web Server untuk pengujian akses nama domain di web browser.
```
yum install httpd -y
```
```
systemctl enable httpd
```
```
systemctl start httpd
```

### Konfigurasi Firewall
Konfigurasi firewall sebagai permission DNS server dan web server dapat diakses oleh client.
```
firewall-cmd --add-service=dns --permanent
```
```
firewall-cmd --add-service=http --permanent
```
```
firewall-cmd --reload
```

### Pengujian
Jalankan perintah nslookup :
```
nslookup rid.xy
```
Hasilnya :

![](https://github.com/ridnrct/sysadminfp/blob/main/Domain%20Name%20System/dns106.jpg)

Pada Web browser, pastikan client sudah terhubung dan pengujian menggunakan akses web browser menggunakan domain name :

![](https://github.com/ridnrct/sysadminfp/blob/main/Domain%20Name%20System/dns110.jpg)

![](https://github.com/ridnrct/sysadminfp/blob/main/Domain%20Name%20System/dns111.jpg)
