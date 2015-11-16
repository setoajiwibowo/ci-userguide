###########################
Sekilas Tentang CodeIgniter
###########################

CodeIgniter adalah *Framework* Aplikasi
=======================================

CodeIgniter adalah sebuah *toolkit* untuk orang-orang yang membangun aplikasi web menggunakan PHP.
Tujuannya adalah untuk memungkinkan Anda untuk mengembangkan proyek-proyek yang jauh lebih cepat
daripada Anda bisa jika Anda sedang menulis kode dari awal, dengan menyediakan *library*
untuk tugas-tugas yang biasa diperlukan, serta antarmuka yang sederhana, dan struktur logis untuk 
mengakses *library* ini. CodeIgniter memungkinkan Anda kreatif fokus pada proyek Anda dengan 
meminimalkan jumlah kode yang diperlukan untuk suatu tugas.

CodeIgniter Gratis
===================

CodeIgniter berlisensi di bawah lisensi MIT sehingga Anda dapat menggunakannya. Untuk informasi lebih lanjut silahkan baca
:doc:`Perjanjian Lisensi <../license>`.

CodeIgniter Ringan
===========================

Benar-benar ringan. Sistem inti hanya memerlukan beberapa *library* sangat kecil. 
Hal ini kontras dengan banyak *framework* yang membutuhkan secara signifikan lebih banyak sumber daya.
*Library* tambahan yang dimuat secara dinamis atas permintaan, berdasarkan kebutuhan Anda untuk proses
tertentu, sehingga sistem dasar sangat ramping dan cukup cepat.

CodeIgniter Cepat
===================

Sangat cepat.  Kami menantang Anda untuk menemukan framework yang memiliki kinerja yang lebih baik dari CodeIgniter.

CodeIgniter Menggunakan M-V-C
=============================

CodeIgniter menggunakan pendekatan *Model-View-Controller*, yang memungkinkan pemisahan yang besar antara logika dan presentasi. Hal ini terutama baik untuk proyek-proyek di mana desainer bekerja 
dengan file template Anda, seperti kode file-file ini berisi akan diminimalkan.
Kami menjelaskan MVC secara lebih rinci pada halaman sendiri.

CodeIgniter Menghasilkan *URL* Bersih
=====================================

URL yang dihasilkan oleh CodeIgniter bersih dan *search-engine friendly*.
Daripada menggunakan standar "query string" pendekatan ke URL yang identik dengan sistem dinamis,
CodeIgniter menggunakan pendekatan segmen berdasarkan::

	example.com/news/article/345

Catatan: Secara default file **index.php** disertakan dalam URL tetapi bisa
dihapus menggunakan file **.htaccess** sederhana.

CodeIgniter Membungkus Sebuah Pukulan
=====================================

CodeIgniter dilengkapi dengan *full-range library* yang memungkinkan tugas-tugas pengembangan web yang
paling sering dibutuhkan, seperti mengakses database, mengirimkan email, memvalidasi data formulir,
menjaga sesi, memanipulasi gambar, bekerja dengan XML- RPC data dan masih banyak lagi.

CodeIgniter Dapat Diperpanjang
==============================

Sistem ini dapat dengan mudah diperluas melalui penggunaan *library Anda sendiri, *helper*, 
atau melalui *class extensions* atau *system hooks*.

CodeIgniter Tidak Memerlukan Mesin Template
==============================================

Meskipun CodeIgniter datang dengan template parser sederhana yang bisa
digunakan secara opsional, CodeIgniter tidak memaksa Anda untuk menggunakannya. 
Mesin template tidak bisa cocok dengan kinerja PHP asli, dan sintaks yang harus belajar untuk
menggunakan mesin template biasanya hanya sedikit lebih mudah daripada belajar dasar-dasar PHP.
Pertimbangkan blok kode PHP::

	<ul>
	<?php foreach ($addressbook as $name):?>
		<li><?=$name?></li>
	<?php endforeach; ?>
	</ul>

Bandingkan ini dengan *pseudo-code* yang digunakan oleh mesin template::

	<ul>
	{foreach from=$addressbook item="name"}
		<li>{$name}</li>
	{/foreach}
	</ul>

Ya, contoh mesin template sedikit lebih bersih, tapi itu datang pada harga kinerja, 
sebagai *pseudo-code* harus dikonversi kembali ke PHP untuk menjalankanny.  
Karena salah satu tujuan kami adalah *maximum performance*, kami memilih untuk tidak memerlukan
penggunaan mesin template.

CodeIgniter Benar-benar Terdokumentasi
======================================

Programmer suka kode dan membenci menulis dokumentasi. Kita tidak berbeda, tentu saja, tapi karena 
dokumentasi **sama pentingnya** sebagai kode itu sendiri, kami berkomitmen untuk melakukannya.  
Kode sumber kami sangat bersih dan baik dikomentasi baik juga.

CodeIgniter Memiliki Komunitas Pengguna yang Ramah
==================================================

Komunitas pengguna kami yang berkembang dapat dilihat secara aktif berpartisipasi di
`Forum Komunitas <http://forum.codeigniter.id/>`_. kami
