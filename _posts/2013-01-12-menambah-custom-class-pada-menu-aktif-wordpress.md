---
layout: post
status: publish
published: true
title: Menambah Custom Class Pada Menu Aktif Wordpress
author:
  display_name: Yoga Hanggara
  login: yohang
  email: yogahanggara@gmail.com
  url: http://yohang.net
author_login: yohang
author_email: yogahanggara@gmail.com
author_url: http://yohang.net
wordpress_id: 1628
wordpress_url: http://yohang.net/?p=1628
date: '2013-01-12 13:31:00 +0700'
date_gmt: '2013-01-12 06:31:00 +0700'
---
[![wordpress-cover](http://yohang.net/wp-content/uploads/wordpress-cover-350x196.jpg)](http://yohang.net/wp-content/uploads/wordpress-cover.jpg)

Saat menampilkan menu dengan fungsi `wp_nav_menu() secara otomatis Wordpress akan memberikan class-class unik untuk masing-masing item menu. Salah satunya adalah pada menu halaman aktif, menu tersebut akan memiliki class current-menu-item. Dengan class ini kita dapat melakukan styling sendiri. Jika Anda ingin menambahkan class baru untuk menu aktif selain current-menu-item tersebut, tambahkan pada file functions.php template Anda:`

[php]  
add\_filter( 'nav\_menu\_css\_class', 'additional\_active\_item\_classes', 10, 2 );  
function additional\_active\_item\_classes($classes = array(), $menu\_item = false){  
 if(in\_array('current-menu-item', $menu\_item->classes)){  
 $classes[] = 'active';  
 }

return $classes;  
}  
[/php]

Sekarang setiap item menu yang aktif, akan ada class baru yaitu class `active.`

