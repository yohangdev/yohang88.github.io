---
layout: post
---

Lama tidak _ngeblog_, hari ini saya langsung mengumumkan migrasi blog platform. Jeng jeng. Dari _blogging platform_ [Wordpress](http://wordpress.org), sekarang menggunakan [Jekyll](http://jekyllrb.com).

> Dasar programmer, setiap tulisan baru, cuma tentang ganti desain tampilan baru, ganti teknologi, dsb. Mana tulisan lain yang lebih berbobot woy! :D

Jekyll ini sebenarnya bukan _blogging platform_ seutuhnya, melainkan seperti _content generator/transform_. Dari tulisan _plain text_ sederhana yang dibuat menggunakan aplikasi _text editor_ biasa, diubah menjadi sebuah website atau blog statis.

Beberapa alasan kenapa memilih _Jekyll_:

### Lightweight
**Wordpress** 8 tahun yang lalu masih sederhana, ukurannya kecil, ringan, dan sudah sangat memenuhi kebutuhan _blogging_ sederhana. Tapi hari ini, _Wordpress_ sudah jauh bertambah besar. Terlalu banyak fitur (_overkill_) yang sebenarnya tidak diperlukan. Akibatnya adalah kecepatan akses halaman dan _server_ yang lebih lambat.

Sebuah halaman _Jekyll_, besar ukuran _file_ hanya sekitar 10-20 KB, dan sudah dalam bentuk _HTML_, tidak ada proses _compile_, _parsing_, yang membebani _server_ setiap diakses.

### No Database
_Jekyll_ tidak memerlukan _database server_. Untuk membuat sebuah tulisan, kita cukup membuat sebuah file baru menggunakan teks editor biasa. Dengan menggunakan _tool_ seperti [Git](http://git-scm.com) _(source version control)_, proses _deployment_ juga jadi lebih cepat. Dengan tidak memakai _database_ server, juga mengurangi potensi serangan _hack/crack_ ke blog.

### Markdown Format
Format [Markdown](https://help.github.com/articles/markdown-basics/) cukup nyaman untuk melakukan _formatting_ teks lebih sederhana, simpel, dan cepat, dibandingkan menggunakan teks editor GUI / WYSIWYG.

> Melihat alasan-alasan tersebut, _Jekyll_ lebih ditujukan digunakan oleh orang-orang yang setiap hari bergelut dengan dunia _coding, programming_.

> Jadi jika Anda bingung dengan istilah-istilah diatas, tetap pakai saja Wordpress/Blogspot :D
