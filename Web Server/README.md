# Web Server
### Konfigurasi Web Server
Installasi web server dengan package httpd.
```
yum install httpd
```
Konfigurasi firewall menambahkan untuk service http.
```
firewall-cmd --permanent --add-service=http
```
Konfigurasi firewall menambahkan untuk service https.
```
firewall-cmd --permanent --add-service=https
```
Muat ulang konfigurasi firewall.
```
firewall-cmd --reload
```
Tampilan pada web nantinya dapat dikonfigurasi atau dicoding pada file index.html.
```
nano /var/www/html/index.html
```
![](https://github.com/ridnrct/sysadminfp/blob/main/Web%20Server/web3.jpg)
