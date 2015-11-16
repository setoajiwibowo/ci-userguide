############################
Panduan Pengguna CodeIgniter
############################

*******************
Instruksi Persiapan
*******************

Panduan pengguna CodeIgniter menggunakan *Sphinx* untuk mengelola dokumentasi 
dan keluaran ke berbagai format. Halaman ditulis dalam format
`ReStructured Text <http://sphinx.pocoo.org/rest.html>`_ yang *human-readable*.

Prasyarat
=========

*Sphinx* membutuhkan *Python*, yang sudah diinstal jika Anda menjalankan OS X. 
Anda dapat mengkonfirmasi di jendela *Terminal* dengan menjalankan perintah ``python``
tanpa parameter apapun. Itu harus termuat dan memberitahu Anda versi yang telah Anda instal.  
Jika Anda tidak pada versi 2.7+, download dan instal versi 2.7.2 dari
http://python.org/download/releases/2.7.2/

Instalasi
=========

1. Install `easy_install <http://peak.telecommunity.com/DevCenter/EasyInstall#installing-easy-install>`_
2. ``easy_install "sphinx==1.2.3"``
3. ``easy_install sphinxcontrib-phpdomain``
4. Install CI Lexer yang mengijinkan *syntax highlighting* pada PHP, HTML, CSS, and JavaScript di contoh kode (lihat *cilexer/README*)
5. ``cd user_guide_src``
6. ``make html``

Mengedit dan Membuat Dokumentasi
================================

Semua sumber file ada di bawah *source/* dan di mana Anda akan menambahkan 
dokumentasi baru atau memodifikasi dokumentasi yang ada. Sama seperti dengan 
perubahan kode, kami sarankan bekerja dari *feature branches* dan membuat 
*pull requests* ke cabang *develop* repo ini.

Jadi, di mana HTML-nya?
=======================

Jelas, dokumentasi HTML adalah apa yang kita paling peduli, karena merupakan dokumentasi 
utama yang menghadapi pengguna kami. Sejak revisi ke file dibangun tidak dari nilai, 
mereka tidak berada di bawah kontrol sumber. Hal ini juga memungkinkan Anda untuk 
regenerasi yang diperlukan jika Anda ingin "preview" pekerjaan Anda. Menghasilkan HTML 
yang sangat sederhana.  Dari *root directory* repo *fork* panduan pengguna 
mengeluarkan perintah yang digunakan pada akhir petunjuk instalasi::

	make html

Anda akan melihatnya melakukan *whiz-bang compilation*, di mana titik panduan pengguna 
sepenuhnya diberikan dan gambar akan di *build/html/*. Setelah HTML telah dibangun, 
setiap membangun berturut-turut hanya akan membangun kembali file yang telah berubah,
menghemat waktu yang cukup.  Jika untuk alasan apapun Anda ingin "reset " file Anda 
yang anda bangun, hanya menghapus isi folder *build* dan membangun kembali.

***************
Pedoman Gaya
***************

Silakan lihat source/documentation/index.rst untuk pedoman umum untuk menggunakan 
*Sphinx* untuk mendokumentasikan CodeIgniter.