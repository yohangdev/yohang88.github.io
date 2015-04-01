---
layout: post
status: publish
published: true
title: Composer Update "Process Killed"
author:
  display_name: Yoga Hanggara
  login: yohang
  email: yogahanggara@gmail.com
  url: http://yohang.net
author_login: yohang
author_email: yogahanggara@gmail.com
author_url: http://yohang.net
wordpress_id: 2433
wordpress_url: http://yohang.net/?p=2433
date: '2013-11-08 16:41:13 +0700'
date_gmt: '2013-11-08 09:41:13 +0700'
---
[caption id="attachment\_2437" align="aligncenter" width="300"] [![Composer, Dependency Manager for PHP](/wp-content/uploads/logo-composer.png) Composer, Dependency Manager for PHP[/caption]](/wp-content/uploads/logo-composer.png)

Menemui masalah _error saat melakukan perintah `composer update? Hal ini sering terjadi pada server yang memiliki sumber daya memori RAM kecil. Sepertinya saat proses update, composer ini melakukan banyak looping untuk cek versi lama dan versi baru dari semua packages.`_

Solusi alternatif selain _upgrade kapasitas memori RAM server adalah:_

1. Lakukan perintah `composer update hanya di server development lokal kita.
Ambil file composer.lock setelah proses update di lokal berhasil.
Pasang file composer.lock tersebut ke server production (yang tadi gagal update), dan lakukan replace.
Lakukan perintah composer install pada server produksi.
Composer akan segera melakukan update paket-paket yang baru.

`
