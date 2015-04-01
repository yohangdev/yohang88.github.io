---
layout: post
status: publish
published: true
title: Menggunakan Custom Font CSS3 Pada Desain Web (Typography)
author:
  display_name: Yoga Hanggara
  login: yohang
  email: yogahanggara@gmail.com
  url: http://yohang.net
author_login: yohang
author_email: yogahanggara@gmail.com
author_url: http://yohang.net
wordpress_id: 1149
wordpress_url: http://yohang.net/?p=1149
date: '2011-04-05 13:13:18 +0700'
date_gmt: '2011-04-05 06:13:18 +0700'
---
[caption id="attachment\_1150" align="alignright" width="304" caption="CSS3: Custom Font Face"] [![](http://yohang.net/wp-content/uploads/customfontcss3.jpg "CSS3: Custom Font Face")[/caption]](http://yohang.net/wp-content/uploads/customfontcss3.jpg)

Bertahun-tahun yang lalu, desain web kebanyakan menggunakan font-font standard seperti _Arial, Verdana, Times New Roman, dsb. Jika ingin menggunakan tampilan font selain itu, trik yang dulu biasa digunakan adalah membuat tulisan tersebut dalam Bitmap/JPEG image, atau menggunakan vector image. Tentu saja ukuran datanya akan menjadi lebih besar jika ingin digunakan dalam jumlah banyak. Bentuk bitmap/vector tentu saja juga tidak bisa di-index, terutama oleh search engine._

Kini dengan kehadiran CSS 3, para web desainer dapat lebih bebas mengeksplorasi kreatifitasnya dengan menggunakan berbagai macam jenis font. Maka hari ini bisa kita lihat, banyak website yang mulai menggunakan font yang tidak biasa, ada yang lebih artistik dan ada yang lebih elegan.

Tulisan ini dibuat ketika CSS 3 sudah banyak digunakan browser-browser terbaru (Mozilla Firefox 4, Chrome 11, Internet Explorer 9, Safari, dsb). Jika _user menggunakan browser dengan versi sebelum itu, custom font ini tidak bisa digunakan._

**Berikut ini cara menggunakan _custom font pada CSS :_**

**Dengan melakukan deklarasi _font-face. Misal:_**

Sebelumnya Anda harus meng-_upload font tersebut di server._

[css]  
 @font-face {  
 font-family: 'Droid Serif';  
 src: url('Droid-Serif.ttf');  
 }  
[/css]

Lalu pada_ element yang mau menggunakan custom font face:_

[css]  
p {  
 font-family: 'Droid Serif';  
}  
[/css]

_**Atau Anda dapat melakukan import custom font face dengan cara berikut:  
Pada head dokumen HTML, masukkan kode:**_

[html]

<link href="http://fonts.googleapis.com/css?family=Droid+Serif:regular,bold" rel="stylesheet" type="text/css">[/html]

Lalu pada CSS, langsung dapat digunakan, misal:

[css]  
h1 { font-family: 'Droid Serif'; }  
[/css]

Katalog font online yang siap digunakan bisa menggunakan koleksi [Google Web Fonts.](http://www.google.com/webfonts)

