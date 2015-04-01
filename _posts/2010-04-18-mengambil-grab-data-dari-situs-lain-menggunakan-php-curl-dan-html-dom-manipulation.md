---
layout: post
status: publish
published: true
title: Mengambil (Grab) Data dari Situs Lain Menggunakan PHP, cURL, dan HTML DOM Manipulation
author:
  display_name: Yoga Hanggara
  login: yohang
  email: yogahanggara@gmail.com
  url: http://yohang.net
author_login: yohang
author_email: yogahanggara@gmail.com
author_url: http://yohang.net
wordpress_id: 850
wordpress_url: http://yohang.net/?p=850
date: '2010-04-18 03:10:55 +0700'
date_gmt: '2010-04-17 20:10:55 +0700'
---
[![](http://yohang.net/wp-content/uploads/batavia2-370x229.jpg "Batavia Air")Belakangan ini saya mendapatkan proyek untuk membuat sebuah website untuk perusahaan tour dan travel. Sempat ada keraguan dalam diri saya, karena ada permintaan dari klien agar dalam wesbite mereka disediakan fitur fungsi _online ticketing. Fungsi itu nantinya akan mempermudah user untuk mengecek, misal jadwal penerbangan, seat avaibility, reservasi, dsb. Bukan hal yang mudah tentu saja, mengingat jika ingin seperti itu, tentu saja dibutuhkan basis data online yang tersambung dengan perusahaan penerbangan langsung. Tentu saja perusahaan penerbangan tidak sembarangan dalam menyediakan data mereka. Tidak ada API ( [Application Programming Interface) yang bisa digunakan untuk mengakses data ke sana. Tapi dalam situs-situs resmi perusahaan penerbangan ada fitur-fitur untuk mengecek jadwal penerbangan juga. Nah di sanalah nampaknya kita bisa mendapatkan data-data.<!--more-->](http://en.wikipedia.org/wiki/Application_programming_interface)_](http://yohang.net/wp-content/uploads/batavia2.jpg)

Nah sekarang permasalahannya adalah bagaimana data tersebut bisa saya ambil dan ditampilkan di website saya. Nah sambil mencoba programming sana-sini, ternyata tadi malam saya menemukan kasus yang bisa diuji coba juga. Tanggal 17 April 2010 kemarin adalah momen pengumuman hasil seleksi ujian tulis UM UGM 2010. Mulai pagi dini hari situs pengumuman tersebut bisa diakses untuk mengecek kelulusan. Hasil seleksi tidak ditampilkan semua, namun hanya person per person saja, yaitu dengan cara memasukkan nomor peserta, barulah dia bisa mengecek hasilnya.

[![](http://yohang.net/wp-content/uploads/umugm1-370x224.jpg "umugm1")](http://yohang.net/wp-content/uploads/umugm1.jpg)

Jika peserta dinyatakan lulus:

[![](http://yohang.net/wp-content/uploads/umugm2-369x206.jpg "umugm2")](http://yohang.net/wp-content/uploads/umugm2.jpg)

Jika tidak:

[![](http://yohang.net/wp-content/uploads/umugm3-370x198.jpg "umugm3")Saat itu saya ingin mengecek kelulusan adik-adik kelas SMA saya. Akan sangat melelahkan jika saya harus mengecek satu persatu, itupun kalau jarak nomor peserta mereka berdekatan. Nah saya ingin mencoba mengambil data hasil seleksi tersebut dan menampilkannya di website saya, dengan format yang saya inginkan tentu saja.](http://yohang.net/wp-content/uploads/umugm3.jpg)

Nah setelah trial n error selama 1 jam di dini hari itu, dengan bantuan googling sana-sini dan mempelajari kembali cURL PHP, dan sebuah PHP class library untuk mempermudah melakukan manipulasi HTML DOM, saya menulis baris kode ini:

[php]  
include('simple\_html\_dom.php');  
set\_time\_limit(0);  
$start = $\_REQUEST['start'];  
$end = $\_REQUEST['end'];

if($\_REQUEST['start'] != '') {  
 echo "

";  
 echo "  
| Nomor Peserta | Nama | Hasil";  
 for($n=$start; $n $url = 'http://um1.ugm.ac.id/index.php?pModule=pengumuman\_lulus&pSub=pengumuman\_lulus&pAct=view&jlr=utul';  
 $data = 'kata\_kunci='.$n.'&lihat\_lokasi\_ujian=Cari';

$ch = curl\_init();  
 curl\_setopt($ch, CURLOPT\_RETURNTRANSFER, 1);  
 curl\_setopt($ch, CURLOPT\_URL, $url);  
 curl\_setopt($ch, CURLOPT\_POSTFIELDS, $data);  
 $Rec\_Data = curl\_exec($ch);

$html = str\_get\_html($Rec\_Data);

echo "

 |
|";  
 foreach($html->find('table') as $e) {  
 echo " " . $e->find('td', 2)->plaintext . "";  
 $lulus = $e->find('td', 9)->plaintext;  
 $pos = strpos($lulus, "Maaf,");  
 if($pos === false) {  
 echo " | " . ucwords(strtolower($e->find('td', 11)->plaintext)) . "";  
 echo " | ";  
 echo ucwords(strtolower($e->find('td', 18)->plaintext)) . " - " . ucwords(strtolower($e->find('td', 15)->plaintext));  
 echo "";  
 }  
 else {  
 echo " | " . ucwords(strtolower($e->find('td', 8)->plaintext)) . "";  
 echo " | Coba Lagi :)";  
 }  
 }  
 echo "";  
 }  
 echo "";  
}  
[/php]

Dan hasilnya adalah seperti ini:

[![](http://yohang.net/wp-content/uploads/umugm4-370x329.jpg "Hasil ")](http://yohang.net/wp-content/uploads/umugm4.jpg)

Demo: [Link Demo Script (tapi saya batasi 50 baris per request)  
Walau mungkin algoritma pemrogramannya agak serem bin ekstrim (karena bisa bikin down server karena banyaknya request), yang penting bisa memenuhi apa yang saya cari lah :D Setidaknya dalam waktu 1 jam saya bisa mengumpulkan dan menyimpan 3000 baris data hasil seleksi (dari total mungkin 20-30 ribu peserta UM UGM) :D Lalu jika ingin mencari sebuah nama, saya tinggal "Search" saja, dan dalam waktu 3 detik langsung ketemu. Walau sebenarnya ini proyek kurang kerjaan - karena toh paginya bisa dilihat juga di koran - tapi yang penting kan belajarnya :D](http://apps.yohang.net/umugm)

Dengan metode yang sama, saya yakin pasti bisa melakukan hal yang sama terhadap situs-situs lain, termasuk proyek situs reservasi online tour dan travel di atas tadi. Ada kawan-kawan yang berpengalaman dalam bidang ini? Share ya :-))

 |

