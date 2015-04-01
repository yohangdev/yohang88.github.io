---
layout: post
status: publish
published: true
title: Mengurangi Beban Apache Server dengan Nginx Server sebagai Reverse Proxy untuk
  File Statis
author:
  display_name: Yoga Hanggara
  login: yohang
  email: yogahanggara@gmail.com
  url: http://yohang.net
author_login: yohang
author_email: yogahanggara@gmail.com
author_url: http://yohang.net
wordpress_id: 2401
wordpress_url: http://yohang.net/?p=2401
date: '2013-09-04 14:20:56 +0700'
date_gmt: '2013-09-04 07:20:56 +0700'
---
Sebelumnya, mari kita baca tulisan ini, [Serving static files: a comparison between Apache, Nginx, Varnish and G-WAN. Dari ujicoba tersebut bisa kita simpulkan bahwa Nginx Server memiliki performa yang jauh lebik cepat dibandingkan Apache Server dalam hal menangani file-file statis, misal JPG, PNG, GIF, dsb.](http://nbonvin.wordpress.com/2011/03/14/apache-vs-nginx-vs-varnish-vs-gwan/)

Saya juga mencoba melakukan _benchmark sendiri dengan sebuah file statis JPG pada server saya. Berikut hasilnya, menggunakan **Apache Benchmark/ab dan setting konfigurasi server sesuai default install:** _

#### Apache  
[bash]  
[root@yohang ~]# ab -n 10000 -c 100 http://xxx/test.jpg

Server Software: Apache  
Server Hostname: xxx.com  
Server Port: 8080

Document Path: /xxx/test.jpg  
Document Length: 184100 bytes

Concurrency Level: 100  
Time taken for tests: 12.359 seconds  
Complete requests: 10000  
Failed requests: 0  
Write errors: 0  
Total transferred: 1843450000 bytes  
HTML transferred: 1841000000 bytes  
Requests per second: 809.13 [#/sec] (mean)  
Time per request: 123.590 [ms] (mean)  
Time per request: 1.236 [ms] (mean, across all concurrent requests)  
Transfer rate: 145662.83 [Kbytes/sec] received

Connection Times (ms)  
 min mean[+/-sd] median max  
Connect: 0 1 1.9 0 50  
Processing: 18 122 135.2 82 1010  
Waiting: 17 119 135.2 78 1010  
Total: 25 123 135.1 82 1010  
[/bash]

#### Nginx  
[bash]  
[root@yohang ~]# ab -n 10000 -c 100 http://xxx/test.jpg

Server Software: nginx  
Server Hostname: xxx.com  
Server Port: 80

Document Path: /xxx/test.jpg  
Document Length: 184100 bytes

Concurrency Level: 100  
Time taken for tests: 2.929 seconds  
Complete requests: 10000  
Failed requests: 0  
Write errors: 0  
Total transferred: 1845187780 bytes  
HTML transferred: 1841736400 bytes  
Requests per second: 3414.54 [#/sec] (mean)  
Time per request: 29.287 [ms] (mean)  
Time per request: 0.293 [ms] (mean, across all concurrent requests)  
Transfer rate: 615280.27 [Kbytes/sec] received

Connection Times (ms)  
 min mean[+/-sd] median max  
Connect: 0 2 1.7 2 23  
Processing: 9 27 7.7 25 89  
Waiting: 1 4 5.5 2 38  
Total: 11 29 8.5 27 100  
[/bash]

#### Grafik  
[caption id="attachment\_2413" align="aligncenter" width="640"] [![Grafik Performa Apache dan Nginx untuk Static Files](/wp-content/uploads/grafik-apache-nginx.png) Grafik Performa Apache dan Nginx untuk Static Files[/caption]

Dengan melakukan uji coba berulang kali, hasil yang didapatkan tidak jauh berbeda dengan ini. Server Nginx bisa memproses _request lebih banyak dan lebih cepat dibanding Apache untuk file statis._

### Mengkombinasikan Nginx dan Apache  
Kita dapat mengkombinasikan kelebihan masing-masing dari Apache dan Nginx untuk mendapatkan performa terbaik dan mengurangi penggunaan sumber daya server. Untuk file dinamis seperti PHP tetap akan diproses oleh Apache, sedangkan file statis akan diproses oleh Nginx. Berikut ilustrasinya:

[caption id="attachment\_2412" align="aligncenter" width="700"] [![Skema Apache dan Nginx sebagai Reverse Proxy untuk Static Files](/wp-content/uploads/apache-nginx-reverse-proxy-static-files-700x131.jpg) Skema Apache dan Nginx sebagai Reverse Proxy untuk Static Files[/caption]](http://yohang.net/wp-content/uploads/apache-nginx-reverse-proxy-static-files.jpg)

#### Install Nginx  
Pada server dengan sistem operasi **CentOS, kita tinggal menggunakan perintah `yum install nginx. Ikuti petunjuk installasi di sini http://nginx.org/en/linux_packages.html untuk menggunakan repository terbaru. Setelah installasi pastikan Nginx server daemon sudah diatur untuk otomatis berjalan saat server start.
Konfigurasi Nginx
Lakukan konfigurasi umum untuk Nginx, terutama untuk banyak virtual server.
[bash]
user nginx;
worker_processes 1;
pid /var/run/nginx.pid;
events {
    worker_connections 1024;
}
http {
    include /etc/nginx/mime.types;
    default_type application/octet-stream;
    log_format main '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';
    sendfile on;
    keepalive_timeout 65;
    gzip on;
    gzip_types application/javascript application/x-javascript text/css text/xml application/xml;
    # Virtual Server
    server {
        listen 80;
        server_name xxx.com;
        root /home/xxx/public_html;
        access_log /home/xxx/logs/nginx_access.log main;
        error_log /home/xxx/logs/nginx_error.log warn;
        index index.php index.html index.htm;
        location ~* \.(?:ico|css|js|gif|jpe?g|png)$ {
            expires max;
            add_header Pragma public;
            add_header Cache-Control "public";
        }
        location / {
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_redirect off;
            proxy_set_header Host $host;
            proxy_pass http://127.0.0.1:8080;
        }
        location ~ /\.ht {
            deny all;
        }
    }
}
[/bash]
Penjelasan
[bash]
        location ~* \.(?:ico|css|js|gif|jpe?g|png)$ {
            expires max;
            add_header Pragma public;
            add_header Cache-Control "public";
        }
[/bash]
Baris konfigurasi di atas untuk memilih file-file statis yang akan dilayani oleh Nginx server. Sekaligus untuk mengatur Cache Control.
[bash]
        location / {
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_redirect off;
            proxy_set_header Host $host;
            proxy_pass http://127.0.0.1:8080;
        }
[/bash]
Baris konfigurasi di atas untuk mengatur agar file-file dinamis PHP di-forward dan diproses Apache Webserver yang listening di port 8080 pada localhost.
[bash]
        location ~ /\.ht {
            deny all;
        }
[/bash]
Baris konfigurasi di atas untuk mengatur agar file-file milik Apache seperti .htaccess tidak bisa diakses publik.
Konfigurasi Apache
Kita akan menaruh Apache dibelakang Nginx dan listening di localhost dan port 8080 (forward dari Nginx).
[bash]
Listen 127.0.0.1:8080
NameVirtualHost 127.0.0.1:8080

    ServerName xxx.com
    DocumentRoot /home/xxx/public_html

[/bash]
Uji Coba
Lakukan Start Server:
[bash]
$ service nginx start
$ service httpd start
[/bash]
Coba akses website dengan web browser dan lihat informasi HTTP Request.
[caption id="attachment_2419" align="aligncenter" width="595"] Informasi HTTP Request[/caption]
Pastikan dalam Response Headers servernya adalah Nginx.
Kemudian di server, kita amati Logs pada server Apache dan Nginx kita. Jika konfigurasi tidak ada masalah, harusnya dalam logs bisa kita temukan: file-file PHP akan muncul di Logs Apache. Sedangkan file-file statis (JPG, PNG, GIF, dsb) akan muncul di Logs Nginx. Sekarang beban Apache Server sudah jauh berkurang, karena hanya mengeksekusi file PHP, sedangkan file-file statis akan dilayani oleh Nginx Server.
Dengan cara ini, fungsi URL Rewrite di Apache yang dibutuhkan untuk website-website yang memiliki unique permalinks tetap akan berjalan.
`**
](/wp-content/uploads/grafik-apache-nginx.png)
