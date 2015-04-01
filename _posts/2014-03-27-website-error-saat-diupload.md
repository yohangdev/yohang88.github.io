---
layout: post
status: publish
published: true
title: Website Error Saat Diupload
author:
  display_name: Yoga Hanggara
  login: yohang
  email: yogahanggara@gmail.com
  url: http://yohang.net
author_login: yohang
author_email: yogahanggara@gmail.com
author_url: http://yohang.net
wordpress_id: 2519
wordpress_url: http://yohang.net/?p=2519
date: '2014-03-27 07:56:37 +0700'
date_gmt: '2014-03-27 00:56:37 +0700'
---
Ini adalah masalah yang sering ditemui oleh para programmer website/web developer. Seringkali ditemukan error atau fungsi tidak berjalan dengan benar setelah _source code diupload ke web hosting/server. Padahal saat dijalankan di server lokal tidak ada masalah. Kenapa?_

Seringkali programmer web/web developer saat melakukan _coding di komputer atau laptop, kebanyakan masih menggunakan sistem operasi Microsoft Windows. Sedangkan web hosting/server yang digunakan menggunakan sistem operasi Linux. Tentu ada banyak perbedaan diantara dua sistem operasi ini._

Diantara error/fungsi yang sering tidak berjalan adalah masalah _upload file. Di Windows, masalah hak akses user untuk melakukan baca dan tulis (read & write file permission) ini tidak terlalu ketat. Sedangkan di Linux, hak akses sangat ketat demi keamanan._

Kemudian masalah sensitifitas huruf kapital, baik penamaan **file, class object, dsb. Di Windows, penggunaan huruf kapital ini tidak terlalu berpengaruh. Misal, file bernama `foto.jpg dan Foto.jpg tetap akan dianggap sama. Sedangkan di Linux, akan dianggap dua file yang berbeda.`**

Masalah modul-modul webserver/PHP yang digunakan juga seringkali jadi masalah. Saat development kita menggunakan banyak modul sesuai yang kita butuhkan. Tapi di web hosting (shared), kita tidak bisa menggunakan modul-modul di luar standard penyedia layanan.

Konfigurasi dan versi software web server (Apache/Nginx, PHP, MySQL, dsb) juga seringkali berbeda antara di lokal saat development dan saat live di web hosting/server.

### Solusinya?
Untuk menghindari masalah-masalah yang muncul akibat perbedaan sistem ini, usahakan saat _ coding kita menggunakan sistem dan konfigurasi yang sama/mirip dengan sistem di web hosting/server live nantinya. Jika server yang nanti akan digunakan menggunakan Linux, maka sebaiknya kita juga coding dan testing dengan Linux.

Jika sistem operasi utama di komputer/laptop kita adalah Windows, kita bisa menggunakan software virtualisasi seperti Virtual Box, VMware, dsb. Memang sedikit repot ketika kita harus melakukan instalasi OS, Apache, PHP, MySQL sendiri di Linux dibandingkan menggunakan paket XAMPP/WAMP di Windows. Tapi ini menjadi nilai tambah knowledge dan experience kita. Kita bisa lebih tahu dimana error terjadi, apakah di source code atau di konfigurasi web server, sehingga lebih cepat penangangannya.

_
