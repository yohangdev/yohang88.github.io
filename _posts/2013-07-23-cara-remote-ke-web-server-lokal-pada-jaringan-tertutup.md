---
layout: post
status: publish
published: true
title: Cara Remote ke Web Server Lokal Pada Jaringan Tertutup
author:
  display_name: Yoga Hanggara
  login: yohang
  email: yogahanggara@gmail.com
  url: http://yohang.net
author_login: yohang
author_email: yogahanggara@gmail.com
author_url: http://yohang.net
wordpress_id: 1841
wordpress_url: http://yohang.net/?p=1841
date: '2013-07-23 16:16:27 +0700'
date_gmt: '2013-07-23 09:16:27 +0700'
---
[![SSH Tunnel Diagram (Source: engadget.com)](http://yohang.net/wp-content/uploads/ssh-tunnel-diagram-350x214.jpg) Kasus ini sering terjadi jika kita membuat sebuah aplikasi khususnya berbasis Web untuk klien, namun aplikasi tersebut hanya akan digunakan dalam lingkungan Intranet atau **local area network di klien (misal: aplikasi semacam Groupware, Project Management, Paperless Office, dsb).** ](http://yohang.net/wp-content/uploads/ssh-tunnel-diagram.jpg)

Kesulitan yang akan kita hadapi sebagai pengembang/_developer atau programmer adalah saat akan melakukan perbaikan atau&nbsp;update aplikasi jika sudah terpasang. Merepotkan jika setiap saat harus mendatangi klien untuk update kecil atau&nbsp;proses maintenance rutin._

Untuk&nbsp;melakukan&nbsp;_remote&nbsp;ke server di klien dapat dengan mudah menggunakan SSH (Secure Shell) yang cukup handal proteksi keamanannya. Dengan SSH, operasi file bisa dilakukan dari jarak jauh via Terminal/Shell. Tapi bagaimana jika kita ingin mengakses tampilan Web Server di jaringan lokal klien?_

Misal kita ingin melihat tampilan aplikasi web yang berjalan di server lokal sana? Ada beberapa aktivitas sulit jika dilakukan melalui perintah-perintah&nbsp;_command shell, misal membutuhkan mengklik sana-sini di halaman administrator aplikasi web.&nbsp;Membuka akses Web Server port 80 ke public (jaringan Internet) tentu tidak diinginkan. Kita hanya boleh menggunakan 'jalan' SSH untuk mengakses dari luar._

Cara mudahnya adalah dengan melakuan Port Forwarding, dari Port komputer yang diremote ke Port komputer lokal kita. Berikut perintah-nya di Terminal, misal:

`ssh root@serverklien.net -L 8080:localhost:80`

Perintah di atas adalah berarti kita mengakses ke server klien via SSH dengan user **root, dan melakukan_ Local Port Forwading&nbsp;dengan meneruskan akses ke localhost port 80 (HTTP web server) dari komputer kita di port 8080. Jika sudah terkoneksi, maka di komputer kita, jika mengakses `http://localhost:8080 di web browser, maka yang kita akses dan akan tampil adalah halaman web yang ada di Web server klien.`_**

