---
layout: post
status: publish
published: true
title: 'Belajar Java: Input & Output (Tugas 4)'
author:
  display_name: Yoga Hanggara
  login: yohang
  email: yogahanggara@gmail.com
  url: http://yohang.net
author_login: yohang
author_email: yogahanggara@gmail.com
author_url: http://yohang.net
wordpress_id: 383
wordpress_url: http://yohang.net/?p=383
date: '2008-10-20 10:33:19 +0700'
date_gmt: '2008-10-20 03:33:19 +0700'
---
Berikut adalah source code progam jadinya:

**R\_Total.java**

[sourcecode language='java']  
import java.util.Scanner;

class R\_Total  
{  
 public static void main (String[] args)  
 {  
 double r1, r2, r3, r\_total\_seri, r\_total\_pararel;

Scanner scan = new Scanner(System.in );

System.out.println("Masukkan nilai R1:");  
 r1 = scan.nextDouble();

System.out.println("Masukkan nilai R2:");  
 r2 = scan.nextDouble();

System.out.println("Masukkan nilai R3:");  
 r3 = scan.nextDouble();

r\_total\_seri = r1 + r2 + r3;  
 r\_total\_pararel = ((r1\*r2\*r3) / (r2\*r3+r1\*r3+r1\*r2));

System.out.println("Total nilai R pada Rangkaian Seri R1, R2, R3 = " + r\_total\_seri );  
 System.out.println("Total nilai R pada Rangkaian Pararel R1, R2, R3 = " + r\_total\_pararel );  
 }  
}

[/sourcecode]

Kalau mau copy-paste dan dikumpulkan sebagai tugas, tolong **modifikasi terlebih dahulu sesuai selera/kemampuan Anda. Yang paling penting adalah memahaminya dulu.**

### Bedah Code  
[sourcecode language='java']  
import java.util.Scanner;  
[/sourcecode]

Kode ini digunakan untuk meload library **Scanner. Library ini memiliki fungsi salah satunya untuk fungsi menerima input dari user (input dari keyboard).**

[sourcecode language='java']  
double r1, r2, r3, r\_total\_seri, r\_total\_pararel;  
[/sourcecode]

Kode ini digunakan untuk mendeklarasikan variabel-variabel (beserta tipe datanya) yang dibutuhkan.  
**double = tipe data yang digunakan untuk r1, r2, r3, r\_total\_seri, r\_total\_pararel;**

**r1 = nilai R1  
r2 = nilai R2  
r3 = nilai R3  
r\_total\_seri = variabel yang akan menampung hasil operasi penghitungan R Total pada rangkaian seri.  
r\_total\_pararel = variabel yang akan menampung hasil operasi penghitungan R Total pada rangkaian pararel.**

[sourcecode language='java']  
Scanner scan = new Scanner(System.in );  
[/sourcecode]  
Untuk menjalankan **objek Scanner (input) dengan nama alias scan.**

[sourcecode language='java']  
 System.out.println("Masukkan nilai R1:");  
[/sourcecode]

Perintah ini akan mencetak baris tulisan "Masukkan nilai R :" pada program.

[sourcecode language='java']  
 r1 = scan.nextDouble()  
[/sourcecode]  
Perintah ini akan meminta input dari user ketika program dijalankan. Input tersebut nantinya akan dimasukkan ke dalam variabel **r1. Tapi ingat, tipe data r1 adalah double, sehingga data yang bisa diinputkan adalah bilangan double. Fungsi scan.nextDouble() juga perlu diperhatikan di sini. Kalau tipe datanya bukan Double, berarti juga harus disesuaikan.**

Begitu juga dengan perintah-perintah berikutnya (r1, r2, r3)

[sourcecode language='java']  
 r\_total\_seri = r1 + r2 + r3;  
 r\_total\_pararel = ((r1\*r2\*r3) / (r2\*r3+r1\*r3+r1\*r2));  
[/sourcecode]  
Kode ini untuk melakukan operasi perhitungan mencari nilai R Total dalam rangkaian seri dan R Total dalam rangkaian pararel, kemudian hasil operasi hitungan tersebut, dimasukkan ke dalam variabel-variabel yang sudah kita deklrasikan di awal.

Operasi perhitungan ini adalah operasi matematika biasa (ingat rumus Fisika juga). Algoritmanya juga dibuat yang sesuai dengan rumus.

[sourcecode language='java']  
 System.out.println("Total nilai R pada Rangkaian Seri R1, R2, R3 = " + r\_total\_seri );  
 System.out.println("Total nilai R pada Rangkaian Pararel R1, R2, R3 = " + r\_total\_pararel );  
[/sourcecode]

Kode ini untuk mencetak output nilai variabel **r\_total\_seri dan r\_total\_pararel. Variabel tersebut berisi hasil operasi perhitungan matematika tadi.**

### Compile dan Run  
Compile dengan perintah **javac R\_Total.java  
Run dengan perintah java R\_Total

Hasil eksekusi program:  
[sourcecode language='bash']  
Masukkan nilai R1:  
3  
Masukkan nilai R2:  
4  
Masukkan nilai R3:  
12  
Total nilai R pada Rangkaian Seri R1, R2, R3 = 19.0  
Total nilai R pada Rangkaian Pararel R1, R2, R3 = 1.5  
[/sourcecode]

**
