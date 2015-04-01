---
layout: post
status: publish
published: true
title: Menambahkan Custom Header Image Pada Template Wordpress
author:
  display_name: Yoga Hanggara
  login: yohang
  email: yogahanggara@gmail.com
  url: http://yohang.net
author_login: yohang
author_email: yogahanggara@gmail.com
author_url: http://yohang.net
wordpress_id: 1645
wordpress_url: http://yohang.net/?p=1645
date: '2013-03-17 10:54:27 +0700'
date_gmt: '2013-03-17 03:54:27 +0700'
---
Bagi para desainer juga programmer template **Wordpress, berikut ini adalah cara dan potongan kode (_snippet code) untuk membuat gambar header (Custom Header Image)&nbsp;sendiri pada template. Kode ini menggunakan fungsi native dari Wordpress, sehingga tidak memerlukan plugin baru dan tidak perlu coding baris program baru lagi. Pengguna template nantinya juga dapat dengan mudah merubah sendiri gambar header di halaman Administrator Wordpress._**

Pada file `functions.php template Anda, tulis baris kode berikut ini:`

[php]  
$args = array(  
 'width' => 700,  
 'height' => 300  
 );  
add\_theme\_support( 'custom-header' , $args);  
[/php]

Dan pada file template Anda (misal `header.php), tambahkan baris kode berikut ini di tempat dimana gambar Header Image akan ditampilkan:`

[php]  
// Untuk mengecek apakah Custom Header Image sudah disetting oleh user  
<?php if(get_header_image()): ?>  
 ![](<?php header_image(); ?>)  
<?php endif; ?>  
[/php]

Setelah itu, secara otomatis akan muncul menu baru di halaman **Wordpress Administrator, menu `Appearance > Header. Melalui halaman tersebut user dapat mengupload gambar header sendiri atau mengambil dari Media Library. Fungsi Image Cropping juga dilakukan saat mengganti gambar Header Image.`**

[![Wordpress Custom Header Image Config](http://yohang.net/wp-content/uploads/Wordpress-Custom-Header-Image-Config-700x393.png)](http://yohang.net/wp-content/uploads/Wordpress-Custom-Header-Image-Config.png)

Untuk parameter selengkapnya tentang pengaturan **Custom Header Image ini, bisa dibaca di dokumentasi [Wordpress Codex.](http://codex.wordpress.org/Custom_Headers)**

[php]  
$defaults = array(  
 'default-image' => '',  
 'random-default' => false,  
 'width' => 0,  
 'height' => 0,  
 'flex-height' => false,  
 'flex-width' => false,  
 'default-text-color' => '',  
 'header-text' => true,  
 'uploads' => true,  
 'wp-head-callback' => '',  
 'admin-head-callback' => '',  
 'admin-preview-callback' => '',  
);  
add\_theme\_support( 'custom-header', $defaults );  
[/php]

Selamat mencoba! :D

