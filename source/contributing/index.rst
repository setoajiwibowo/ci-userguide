###############################
Berkontribusi untuk CodeIgniter
###############################

.. toctree::
	:titlesonly:

	../documentation/index
	../DCO

CodeIgniter sebuah proyek komunitas didorong dan menerima kontribusi kode
dan dokumentasi dari komunitas. Kontribusi-kontribusi ini dibuat dalam bentuk
isu-isu atau `Pull Requests <https://help.github.com/articles/using-pull-requests/>`_ 
di `Repositori CodeIgniter <https://github.com/bcit-ci/CodeIgniter>`_ di GitHub.

Isu adalah cara cepat untuk menunjukkan bug. Jika Anda menemukan bug atau kesalahan dokumentasi 
dalam CodeIgniter kemudian silakan periksa beberapa hal pertama:

- Tidak ada masalah terbuka
- Masalah telah diperbaiki (check cabang mengembangkan, atau mencari
  Masalah ditutup)
- Apakah itu sesuatu yang benar-benar jelas bahwa Anda memperbaikinya?

Melaporkan masalah sangat membantu tapi pendekatan yang lebih baik adalah untuk mengirim sebuah 
*Pull Request*, yang dilakukan oleh "Forking" repositori utama dan berkomitmen untuk 
salinan Anda sendiri. Ini akan mengharuskan Anda untuk menggunakan sistem kontrol versi 
yang disebut *Git*.

********
Dukungan
********

Harap dicatat bahwa GitHub tidak untuk dukungan pertanyaan umum! Jika Anda mengalami 
kesulitan menggunakan fitur CodeIgniter, mintalah bantuan pada
`forum <http://forum.codeigniter.com/>`_ kami.

Jika Anda tidak yakin apakah Anda menggunakan sesuatu dengan benar atau jika Anda
telah menemukan bug, sekali lagi - silahkan bertanya di forum dahulu.

**********
Keamananan
**********

Apakah Anda menemukan masalah keamanan dalam CodeIgniter?

Tolong *jangan* mengungkapkan secara terbuka, tetapi kirim e-mail kepada kami di 
security@codeigniter.com, atau laporan melalui halaman kami 
di `HackerOne <https://hackerone.com/codeigniter>`_.

Jika Anda telah menemukan kerentanan kritis, kami akan senang untuk meng-kredit Anda di
`Perubahan Log <../changelog>` kami.

************************************
Tips untuk Laporan Masalah yang Baik
************************************

Menggunakan baris subjek deskriptif (misalnya parser Librari tersedak pada koma) daripada yang samar-samar (misalnya. kode pecah).

Alamat satu masalah dalam laporan.

Mengidentifikasi versi CodeIgniter (misalnya 3.0-develop) dan komponennya jika Anda tahu itu (misalnya. parser Librari)

Jelaskan apa yang Anda diharapkan untuk terjadi, dan apa yang terjadi.
Termasuk pesan kesalahan dan stacktrace, jika ada.

Meliputi segmen kode singkat jika mereka membantu untuk menjelaskan.
Menggunakan pastebin atau hanya fasilitas dropbox untuk memasukkan lagi segmen kode atau screenshot - tidak termasuk mereka dalam laporan masalah itu sendiri.
Ini berarti pengaturan kedaluwarsa wajar bagi mereka, sampai masalah diselesaikan atau ditutup.

Jika Anda tahu bagaimana untuk memperbaiki masalah, Anda dapat melakukannya dengan *fork & branch* Anda sendiri, dan menyerahkan *pull request*.
Laporan masalah informasi di atas harus menjadi bagian dari itu.

Jika laporan masalah Anda dapat menjelaskan langkah-langkah untuk mereproduksi masalah, itu besar.
Jika Anda dapat memasukkan unit test yang mereproduksi masalah, itu lebih baik, karena memberikan siapapun memperbaiki
itu jelas target!


*******
Pedoman
*******

Sebelum kita melihat ke dalam bagaimana, berikut adalah panduan. Jika *Pull Requests* Anda 
gagal untuk lulus pedoman itu akan ditolak dan Anda akan perlu untuk mengajukan kembali 
ketika Anda telah melakukan perubahan. Hal ini mungkin terdengar agak sulit, tetapi 
diperlukan bagi kita untuk menjaga kualitas kode-dasar.

Gaya PHP
========

Semua kode harus memenuhi `Pedoman Gaya <http://www.codeigniter.com/userguide3/general/styleguide.html>`_, yang pada dasarnya adalah `Allman indent style <http://en.wikipedia.org/wiki/Indent_style#Allman_style>`_, garis bawah dan operator dapat dibaca. Hal ini membuat yakin bahwa semua kode adalah format yang sama seperti kode yang ada dan cara-cara yang akan dibaca sebagaimana mungkin.

Dokumentasi
===========

Jika Anda mengubah apa pun yang memerlukan perubahan dokumentasi maka Anda akan
perlu untuk menambahkannya. Kelas baru, metode, parameter, mengubah nilai default, dll
adalah segala sesuatu yang akan memerlukan perubahan dokumentasi. Perubahan log
harus juga diperbaharui untuk setiap perubahan. Juga PHPDoc blok harus dijaga.

Kompatibilitas
==============

Merekomendasikan CodeIgniter PHP 5.5 atau yang lebih baru untuk digunakan, tetapi harus
kompatibel dengan PHP 5.2.4 sehingga semua kode yang diberikan harus tetap ini
persyaratan. Jika fungsi PHP 5.3 (dan di atas) atau fitur yang digunakan kemudian
harus ada untuk PHP 5.2.4.

Percabangan
===========

CodeIgniter menggunakan `Git-Flow
<http://nvie.com/posts/a-successful-git-branching-model/>`_ branching model
yang memerlukan semua *pull requests* untuk dikirim ke cabang "develop". Ini adalah 
dimana versi berikutnya direncanakan akan dikembangkan. Cabang "master" akan selalu 
berisi versi stabil terbaru dan tetap bersih sehingga "hotfix" (misalnya: patch 
keamanan darurat) dapat diterapkan ke master untuk membuat versi baru, tanpa khawatir 
tentang fitur-fitur lainnya yang memegangnya. Untuk alasan ini semua komit perlu dibuat 
untuk "develop" dan apa pun yang dikirim ke "master" akan ditutup secara otomatis. 
Jika Anda memiliki beberapa perubahan untuk mengirimkan, harap cantumkan semua
perubahan ke cabang *fork* Anda sendiri.

Satu hal pada suatu waktu: sebuah *pull request* hanya boleh berisi satu perubahan. 
Itu tidak berarti hanya satu commit, tetapi satu perubahan - namun banyak komit. 
Alasan untuk ini adalah bahwa jika Anda mengubah X dan Y tetapi kirim menarik 
meminta keduanya pada saat yang sama, kita mungkin benar-benar ingin X tetapi 
tidak setuju dengan Y, berarti kami tidak dapat menggabungkan *request*. 
Menggunakan model branching Git-aliran Anda dapat membuat cabang baru untuk 
kedua fitur tersebut dan mengirim dua permintaan.

Penandatanganan
===============
Anda harus menandatangani pekerjaan Anda, menyatakan bahwa Anda baik menulis 
pekerjaan atau jika tidak memiliki hak untuk menularkannya kepada proyek sumber 
terbuka. Git membuat ini sepele seperti Anda hanya harus menggunakan '--signoff' 
pada komit Anda untuk *fork* CodeIgniter Anda.

.. code-block:: bash

	git commit --signoff

or simply

.. code-block:: bash

	git commit -s

Ini akan menandatangani commit Anda dengan setup informasi di git config Anda , misalnya.

	Signed-off-by: John Q Public <john.public@example.com>

Jika Anda menggunakan *Tower* ada kotak centang "Sign-Off" di jendela komit. 
Anda bisa bahkan alias git commit untuk menggunakan bendera -s sehingga Anda 
tidak perlu berpikir tentang hal itu.

Dengan menandatangani Anda bekerja dengan cara ini, Anda menyatakan untuk sebuah "Sertifikat Pengembang Asal". 
Versi terbaru dari sertifikat ini di berkas :doc:`/DCO`
di dalam akar dokumentasi ini.
