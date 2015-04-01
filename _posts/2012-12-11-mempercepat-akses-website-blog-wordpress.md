---
layout: post
status: publish
published: true
title: Mempercepat Akses Website Blog Wordpress
author:
  display_name: Yoga Hanggara
  login: yohang
  email: yogahanggara@gmail.com
  url: http://yohang.net
author_login: yohang
author_email: yogahanggara@gmail.com
author_url: http://yohang.net
wordpress_id: 1446
wordpress_url: http://yohang.net/?p=1446
date: '2012-12-11 07:40:55 +0700'
date_gmt: '2012-12-11 00:40:55 +0700'
---
Bagi pengguna Wordpress self-hosted atau blog yang menggunakan web hosting/serveri sendiri, tips ini mungkin dapat membantu mempercepat akses website berbasis CMS Wordpress Anda, terutama untuk diakses pengguna dari berbagai lokasi dan negara. Lalu, bagaimana cara mempercepat akses website kita?

[![](http://yohang.net/wp-content/uploads/CDN-525x225.png "Content Delivery Network (CDN)")  
Selain faktor-faktor besarnya dokumen web (seperti gambar/foto, animasi, video, flash, dsb), ada faktor lagi yang perlu diperhatikan yaitu kemampuan web server untuk diakses secara simultan oleh banyak pengguna dalam satu waktu dan dari berbagai tempat/negara. Lokasi web server yang digunakan juga sangat berpengaruh, misal jika website diletakkan di web server yang berlokasi di Amerika Serikat (US), tentu waktu akses dari Indonesia akan lebih lama dibandingkan dengan website yang diletakkan di web server Lokal Indonesia. Sebaliknya, jika kita letakkan website di server Indonesia, maka akan lama diakses dari luar negeri.](http://yohang.net/wp-content/uploads/CDN.png)

Wordpress kini dengan plugin **JetPack-nya, yang terkoneksi dengan server Wordpress.com, mempunyai fasilitas untuk membantu mempercepat akses website kita, dengan teknologi Content Delivery Network (CDN). CDN adalah teknologi untuk mendistribusikan _content/materi web kita ke&nbsp;server yang ada di datacenter-datacenter tersebar di seluruh dunia.&nbsp;Jadi, dengan CDN ini, pengguna dari Amerika Serikat akan mengakses materi web dari server Amerika, pengguna dari Eropa akan mengakses dari server di Eropa, dan server-server terdekat lainnya._**

## Wordpress JetPack: Photon> Photon is an image acceleration and modification service for Jetpack-connected WordPress sites. Converted images are cached automatically and served from the WordPress.com CDN. Images can be cropped, resized, and filtered by using a simple API controlled by GET query arguments. When Photon is enabled in Jetpack, images are updated on the fly. -- [Wordpress Developer Resources  
> Dengan fitur ini, materi gambar/foto dari website kita akan didistribusikan ke server-server CDN Wordpress di seluruh dunia. Ini dapat meningkatkan performa akses ke website kita karena pengguna akan mengakses data dari server yang terdekat dengan mereka saja. Ini juga dapat menghemat _resources&nbsp;/ sumber daya di server kita sendiri, karena beban server tidak terkumpul di satu titik yaitu server kita saja, tapi sudah dibagi-bagi ke server-server CDN._](http://developer.wordpress.com/docs/photon/)
> 
> 1. Login sebagai **Administrator dan masuk ke Dashboard- Tambah dan Aktifkan Plugin JetPack Wordpress  
> [![](http://yohang.net/wp-content/uploads/Wordpress-JetPack-Plugin-525x67.jpeg "Wordpress JetPack Plugin")&nbsp;- Masuk ke halaman administrasi JetPack  
> [![](http://yohang.net/wp-content/uploads/JetPack-Dashboard.jpeg "JetPack Dashboard")- Aktifkan Photon  
> [![](http://yohang.net/wp-content/uploads/Wordpress-Photon-CDN.jpeg "Wordpress Photon CDN")&nbsp;- Voila!  
> [![](http://yohang.net/wp-content/uploads/Wordpress-CDN-525x119.jpeg "Wordpress CDN")  
> ](http://yohang.net/wp-content/uploads/Wordpress-CDN.jpeg)
> ](http://yohang.net/wp-content/uploads/Wordpress-Photon-CDN.jpeg)
> ](http://yohang.net/wp-content/uploads/JetPack-Dashboard.jpeg)
> ](http://yohang.net/wp-content/uploads/Wordpress-JetPack-Plugin.jpeg)
> **
