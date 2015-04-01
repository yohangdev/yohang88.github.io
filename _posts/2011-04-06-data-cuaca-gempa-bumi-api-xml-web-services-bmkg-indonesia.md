---
layout: post
status: publish
published: true
title: Data Cuaca & Gempa Bumi (API-XML Web Services BMKG Indonesia)
author:
  display_name: Yoga Hanggara
  login: yohang
  email: yogahanggara@gmail.com
  url: http://yohang.net
author_login: yohang
author_email: yogahanggara@gmail.com
author_url: http://yohang.net
wordpress_id: 1158
wordpress_url: http://yohang.net/?p=1158
date: '2011-04-06 19:31:18 +0700'
date_gmt: '2011-04-06 12:31:18 +0700'
---
Beberapa waktu yang lalu saya sempat memposting artikel berjudul [Info Gempa Terkini, dimana disana terdapat beberapa link ke situs yang menyediakan informasi tentang gempa bumi yang baru saja terjadi, baik di Indonesia maupun di dunia. Bagi para pengembang software dan aplikasi web, sebenarnya ada cara lain untuk bisa mendapatkan data 'mentah' dari informasi tersebut. Data tersebut bisa kita ambil, gunakan, dan tampilkan sesuai selera dan kebutuhan kita.](http://yohang.net/info-gempa-terkini.html)

Bagi teman-teman yang sudah pernah bersentuhan dengan pemrograman lintas platform, sistem, dsb, yang membutuhkan pertukaran data yang terbuka, mudah, dan fleksibel, pastilah sudah berkawan akrab dengan yang namanya **Application Programming Interface (API) dan Web Services. Tanpa itu, maka akan mengalami kesulitan seperti [kasus saya ini.](http://yohang.net/mengambil-grab-data-dari-situs-lain-menggunakan-php-curl-dan-html-dom-manipulation.html)**

[caption id="attachment\_1163" align="aligncenter" width="516" caption="Twitter BMKG Indonesia"] [![](http://yohang.net/wp-content/uploads/bmkg_api2.jpg "Twitter BMKG Indonesia")[/caption]](http://yohang.net/wp-content/uploads/bmkg_api2.jpg)

Nah, ternyata **Badan Meteorologi Klimatologi dan Geofisika [BMKG Indonesia, juga menyediakan basis data yang bisa digunakan oleh para pengembang aplikasi desktop maupun berbasis web. Data tersebut tersedia dalam bentuk format XML (eXtensible Markup Language), sehingga dengan _XML parser/decoder yang sudah banyak tersedia di berbagai bahasa pemrograman, data tersebut bisa diolah dengan mudah. FYI, sebenarnya saya sendiri lebih suka format JSON (JavaScript Object Notation). Data XML informasi gempa terkini, info tsunami, info ramalan cuaca, dsb yang ada di sana cukup update. Hanya saja kadang terlambat :D Beberapa data juga bukan dalam format XML, alias teks saja. Sehingga harus di-parsing secara manual. Hehehe._](http://bmkg.go.id)**

Koleksi basis **data XML tersebut ada di sini: [http://data.bmkg.go.id](http://data.bmkg.go.id)**

[xml]  
<infogempa><br>
 <gempa><br>
  <tanggal>19-Apr-11<br>
  <jam>05:40:38 WIB</jam></tanggal></gempa></infogempa>

<point><coordinates>98.78,0.58<br>
  <lintang>0.58 LU<br>
  <bujur>98.78 BT<br>
  <magnitude>5.0 SR<br>
  <kedalaman>35 Km<br>
  <_symbol>imagesSWF/m2b.swf<br>
  <wilayah1>90 km TimurLaut TANAHMASA-SUMUT<br>
  <wilayah2>92 km BaratDaya PANYABUNGAN-SUMUT<br>
  <wilayah3>103 km BaratDaya PDGSIDEMPUAN-SUMUT<br>
  <wilayah4>120 km TimurLaut TANAHBALA-SUMUT<br>
  <wilayah5>1167 km BaratLaut JAKARTA-INDONESIA<br>
  <potensi>tidak berpotensi TSUNAMI<br>
 <br>
<br>
[/xml]
<p>Di atas adalah contoh data gempa bumi terkini dalam format XML. Menurut saya, info parameter dalam data tersebut tidak cukup fleksibel dan belum cukup kaya. Misal parameter Tanggal dan Jam yang menggunakan format standard seperti itu. Mungkin bagi para pengembang aplikasi, akan lebih mudah jika data tersebut berupa <em>UNIX Timestamps (microtime), sehingga bisa dengan mudah dikonversi ke format yang lain. Informasi koordinat lintang dan bujur juga tidak bisa langsung digunakan pada <strong>Google Maps karena format <strong>Latitude (LAT) dan <strong>Longitude (LNG) -nya harus valid (tanda plus-minus).</strong></strong></strong></em></p>
<p>Ini adalah terobosan cukup bagus yang dilakukan BMKG Indonesia terkait berbagi data dan informasi. Contoh lain yang menarik lainnya adalah situs Balai Penyelidikan dan Pengembangan Teknologi Kegunungapian <a href="http://merapi.bgl.esdm.go.id/">BPPTK Yogyakarta yang juga menyediakan akses data seismik, vulkanik, bahkan hingga kamera CCTV. Sehingga ketika Gunung Merapi meletus beberapa hari yang lalu, orang-orang dapat ikut memantau dari sana. Tapi jika dibandingkan dengan negara lain, mungkin data yang tersedia masih belum cukup 'kaya' (<em>rich). Situs badan geologi milik Amerika Serikat <a href="http://www.usgs.gov/">U.S. Geological Survey (USGS) ini misalnya, menyediakan informasi detail tentang gempa bumi yang cukup lengkap. Situs-situs luar negeri yang menyediakan jasa prediksi cuaca (weather forecasting) juga menyediakan akses data web services yang cukup lengkap.</a></em></a></p>
<p>Ditunggu aplikasi-aplikasi yang bisa menggunakan data-data ini :D</p>
</potensi></wilayah5></wilayah4></wilayah3></wilayah2></wilayah1></_symbol></kedalaman></magnitude></bujur></lintang></coordinates></point>